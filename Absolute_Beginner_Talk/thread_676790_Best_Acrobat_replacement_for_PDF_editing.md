---
title: "Best Acrobat replacement for PDF editing"
date: 2008-01-24
forum: Absolute Beginner Talk
---

### Post by tqprvn on 2008-01-24
hi there

Looking for a recommendation for an Acrobat Pro replacement on Ubuntu.

At the moment, PDFs open in Evince, which doesnt appear to allow me to do things such as combine several PDFs into one document, or to delete or rearrange pages.

Can anyone suggest a suitable application for that?

Thanks

Matt

---

### Post by Rhubarb on 2008-01-24
There is an application that allows you to edit some parts of pdf files, but it's not too easy to use.
Get it from the repositories:
```
sudo aptitude install pdfedit
```

Try it out, it might work fine for your needs.

---

### Post by peabody on 2008-01-24
The gimp can open pdf for editing as if they were images.  Each page opens as a layer.

Saving back to a pdf is a problem however.  Best solution I can come up with is to paste each layer separately into an open office document and save as pdf.

---

### Post by vanadium on 2008-01-24
To combine PDF's or split them into different pages or rearagne pages, yuo can use pdftoolkit: pdftk, which is a command line utility.

---

### Post by tqprvn on 2008-01-24
wow, harder than I was expecting...thought there would just be some surrogate app out there.

Unfortunately noone in my team is tech enough to go doing the command line thing, editing in GIMP doesnt strike me as particularly appealing (we never edited them in Photoshop on Win).  Will test out pdfedit and see how it goes.

Tks all

---

### Post by Sonja on 2008-01-28
pdfedit kept crashing, so I tried pdftk and it did the trick!

---

### Post by Ainab on 2008-01-30
Thanks vanadium you saved my day!

---

