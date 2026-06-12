---
title: "help installing UT2004-LNX-Demo3334.run.gz"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by blinkja on 2007-08-23
i just finished downloading UT2004-LNX-Demo3334.run.gz ,

how to install?

---

### Post by Inxsible on 2007-08-23
A bit more info would help. What is it? a linux demo? a live CD for some distro ?

.gz files are zipped files that you would need to extract, mebbe using file-roller or other such app

---

### Post by asmoore82 on 2007-08-23
First of all, I think you should check and make sure that the file is what the extenstion says it is...

Open a terminal, navigate to where the file is (if you can't get this far on your own let me know)
and then ...

```
~ $ file UT<Tab><Enter>
```

IF that says that it really is gzipped compressed, you need to "G"-unzip it,
change its file permission to make it executable, and run it ...

```
~ $ gunzip UT<Tab><Enter>
~ $ chmod +x UT<Tab><Enter>
~ $ ./UT<Tab><Enter>
```

Then the GUI installer should pop up and follow the steps, 
:KS Happy Fragging!!

---

