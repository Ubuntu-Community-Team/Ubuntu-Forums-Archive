---
title: "[SOLVED] Command line command for combining pdfs?"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by slughappy1 on 2008-02-15
I was just told that there is a command that combines two (or hopefully more) pdfs together into one. Does anyone know the command?

---

### Post by mali2297 on 2008-02-15
> **slughappy1 said:**
> I was just told that there is a command that combines two (or hopefully more) pdfs together into one. Does anyone know the command?

You can use the tool [Pdftk]("http://www.accesspdf.com/pdftk/") which is available in the repositories.

To combine file1.pdf and file2.pdf to file12.pdf,
```

pdftk file1.pdf file2.pdf cat output file12.pdf

```

---

### Post by slughappy1 on 2008-02-15
Thank you

---

