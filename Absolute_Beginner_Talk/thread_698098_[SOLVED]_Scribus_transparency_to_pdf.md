---
title: "[SOLVED] Scribus: transparency to pdf"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by jaredssix on 2008-02-15
Hey all,

I'm trying to export a Scribus file to pdf. I have a shape with the opacity set to 5%. This has proven an obstacle in the export to pdf. In fact, Scribus won't allow me to export to pdf. 

Any ideas?

---

### Post by Bubba64 on 2008-02-15
docs.scribus.net/index.php?lang=en&page=pdfx3  I am not familiar with Scribus but I found this link.

---

### Post by jaredssix on 2008-02-15
Thanks, but the issue lies in step 3 (at the link you provided): "Select File > Export...> Save as PDF.. or select the PDF icon from the tool bar."

I can't export a Scribus file with opacity/tranparency to pdf.

---

### Post by jaredssix on 2008-02-16
Solved!
In pre-flight--the pdf window--File Options/Compatibility must be set to PDF 1.4+.

And, Scribus defaulted to a save to file path which didn't exist! (All of the files in the folder were correct, but the file path was erroneous.) I browsed to the real file path location, and the issue was solved.

---

