---
title: "Tomboy"
date: 2006-11-18
forum: Absolute Beginner Talk
---

### Post by helphope on 2006-11-18
Hi all.

While installing tomboy in dapper I got this message from terminal:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
:confused: 
What can I do? Thanks for any help

---

### Post by ComplexNumber on 2006-11-18
> **helphope said:**
> Hi all.

While installing tomboy in dapper I got this message from terminal:

checking for XML::Parser... configure: error: XML::Parser perl module is required for intltool
:confused: 
What can I do? Thanks for any help
fire up synaptic package manager and install 'perl-xml-parser'. the error message is saying that its required but its not presently installed.

---

### Post by helphope on 2006-11-18
Thanks for answering, bt I can't find any xml  Parser perl module in the:confused:  repositories

---

### Post by ComplexNumber on 2006-11-18
> **helphope said:**
> Thanks for answering, bt I can't find any xml  Parser perl module in the:confused:  repositories
i think you need to enable the universe and multiverse repositories. once you've added them and reloaded, it should appear.

---

### Post by helphope on 2006-11-18
Thanks a lot.
That seems to work.
But now I've got this message

checking for gcc... no
checking for cc... no
checking for cl.exe... no
configure: error: no acceptable C compiler found in $PATH

??

---

### Post by LLRNR on 2006-11-18
Try ```
sudo aptitude install build-essential
```

---

### Post by helphope on 2006-11-18
Great, now it works.
I've got Tomboy now, only that I hoped that I could past more CRTL+V than one; instead every time I have to paste my selection.

---

