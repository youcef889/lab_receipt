**وصف المستند بالعربية:**

هذا ملف **LaTeX** لنموذج إداري جزائري بعنوان **«وصل استلام»**، مُعدّ للكتابة باللغة العربية باستخدام حزمة `polyglossia` والخط `Amiri`، وموجّه أساسًا للاستعمال داخل المؤسسات التربوية.

**الهدف من المستند:**
توثيق عملية استلام شخصٍ ما لمواد أو أجهزة من شخص آخر، مع تسجيل بيانات المستلم والجهة المعنية وقائمة المواد المستلمة.

**محتوى المستند:**
- ترويسة إدارية رسمية تتضمن:
  - الجمهورية الجزائرية الديمقراطية الشعبية
  - وزارة التربية الوطنية
  - مديرية التربية لولاية تيزي وزو
  - اسم الثانوية
- عنوان الوثيقة: **وصل استلام**
- فقرة إقرار يذكر فيها المستلم:
  - الاسم واللقب
  - الوظيفة
  - المصلحة
  - اسم الشخص الذي تم الاستلام منه
- جدول جرد يتضمن الأعمدة التالية:
  - الرقم
  - اسم الجهاز أو المادة
  - الكمية
  - رقم الجرد
  - ملاحظات
- خانات التوقيع والتاريخ.
- خانة خاصة باسم المدير وتوقيعه.

**الاستخدام:**
يمكن استعمال هذا النموذج في الثانوية أو أي مؤسسة تعليمية أخرى لتسجيل عمليات تسليم واستلام العتاد أو المواد الإدارية والبيداغوجية.

**ملاحظة تقنية:**
لتجميع هذا الملف بشكل صحيح، يُفضَّل استخدام **XeLaTeX** أو **LuaLaTeX**، لأن الحزم والخطوط العربية المستخدمة مثل `polyglossia` و`Amiri` لا تعمل جيدًا مع `pdfLaTeX`.






To run this LaTeX document, you need to compile it with **XeLaTeX** or **LuaLaTeX** (not pdfLaTeX) because it uses Arabic and `polyglossia`.

## 1. Fix a small error first
Your table has **6 columns** in the definition:
```latex
\begin{tabularx}{\textwidth}{|c|X|c|c|c|c|}
```
but only **5 columns** in the header and rows. Change it to:
```latex
\begin{tabularx}{\textwidth}{|c|X|c|c|c|}
```
Otherwise you will get a “Misplaced alignment tab” or similar error.

## 2. Local compilation (TeX Live / MiKTeX / MacTeX)

1. **Rename the file**
   Change `documentclass[12pt,a4paper]{article}.txt` to something like `wasl.tex`.

2. **Install a LaTeX distribution**
   - Windows: MiKTeX or TeX Live
   - macOS: MacTeX
   - Linux: TeX Live (`sudo apt install texlive-full`)

3. **Install the Amiri font**
   - Windows: download Amiri and install it
   - macOS: install via Font Book
   - Linux: `sudo apt install fonts-amiri` (or install manually)

4. **Open a terminal in the file’s folder** and run:
   ```bash
   xelatex wasl.tex
   ```
   or
   ```bash
   lualatex wasl.tex
   ```
   For automatic multiple runs:
   ```bash
   latexmk -xelatex wasl.tex
   ```

5. The output will be `wasl.pdf`.

## 3. Using Overleaf (easiest)

1. Go to [Overleaf](https://www.overleaf.com) and create a new project.
2. Upload your file and rename it to `wasl.tex`.
3. In the **Menu**, set **Compiler** to **XeLaTeX**.
4. Click **Recompile**.

If Overleaf complains about the `Amiri` font, either:
- Use a font available on Overleaf, e.g. `Noto Naskh Arabic`, or
- Upload the Amiri font files to your project and adjust the `\newfontfamily` line.

## 4. Common issues

- **`polyglossia` error**: you must use XeLaTeX or LuaLaTeX.
- **Font not found**: install Amiri or change the font name.
- **Table error**: fix the column count as shown above.
- **Missing packages**: install them via MiKTeX’s automatic installer or `tlmgr install <package>`.

Once compiled, you will get a PDF of the “وصل استلام” form ready to print.
