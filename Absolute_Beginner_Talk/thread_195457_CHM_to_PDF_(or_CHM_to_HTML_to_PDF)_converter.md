---
title: "CHM to PDF (or CHM to HTML to PDF) converter?"
date: 2006-06-12
forum: Absolute Beginner Talk
---

### Post by Jucato on 2006-06-12
I have a few documents from Windows that are in .CHM format. Although I have kchmviewer installed, I want to convert them into PDF format so that I could read them on my mobile device (doesn't have a CHM reader). I was wondering if there's a way in Linux that would let me convert CHM to PDF, or to HTML first then to PDF? In Windows, Microsoft has a software that decompile CHM into HTML, but I haven't been able to successfully run it in Linux.

Thanks for any help.

---

### Post by uzi09 on 2006-06-12
i don't know if there is anything to convert, but there is a program called **xchm** that allows you to read these files.

you should be able to get it with aptitude
try both:
chm
and
xchm

let us know if you hit any problems

---

### Post by Jucato on 2006-06-12
Like I said, I have kchmviewer, which is basically the same as xCHM, except that kchmviewer integrates with KDE.

Thanks for trying, :D

---

### Post by uzi09 on 2006-06-12
LOL! sorry, kinda skimmed through :S
but interesting question, it should be handy to have.

---

### Post by dogen2 on 2006-06-22
$ sudo apt-get install chmlib-bin
 $ extract_chmLib tero.chm tero/

This will extract all the HTML files from the CHM. But then you have to find something that will convert it all to PDF..still working on it

---

### Post by Jucato on 2006-06-22
wow! that's a great app! Thanks! btw, Ubuntu uses **libchm-bin** rather than chmlib-bin.

Just one more question: the extracted files have some files/folders that begin with either # or $. Are they necessary if I were to view the document as HTML? I wonder if they will be needed later on if the HTML would be turned into PDF. 

Again thanks a lot!! :D

---

### Post by siccness on 2006-06-22
I think there's a utility called 'htmldoc'. 

```

apt-cache search htmldoc

```

htmldoc - HTML processor that generates indexed HTML, PS, and PDF

I'm not sure if that's what you want though?

---

### Post by Jucato on 2006-06-22
It's exactly what I was looking for! :D
Actually, in between testing libchm-bin and posting this, I have tried htmldoc. Thanks for confirming it for me. 

Thank you all! I'm satisfied... for now :D

---

### Post by siccness on 2006-06-22
Good to hear champ, hope it all goes well!

---

