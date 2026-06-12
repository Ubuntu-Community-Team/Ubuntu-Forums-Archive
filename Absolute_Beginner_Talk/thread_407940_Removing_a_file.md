---
title: "Removing a file"
date: 2007-04-12
forum: Absolute Beginner Talk
---

### Post by x-ray vision on 2007-04-12
I'm supposed to "remove the xpti.dat from the
components directory of the Mozilla or Netscape browser."

Does anyone know how I can do this?

---

### Post by taurus on 2007-04-12
You need to be in the directory where that file is and run

```
sudo rm xpti.dat
```

---

### Post by x-ray vision on 2007-04-12
How do I get in the directory that file is? I'm using Firefox.

---

### Post by Raptor45 on 2007-04-12
Try:
```
sudo rm /usr/lib/firefox/components/xpti.dat
```

In the console.

---

### Post by x-ray vision on 2007-04-12
I got:

rm: cannot remove `/usr/lib/firefox/components/xpti.dat': No such file or directory

---

### Post by Raptor45 on 2007-04-12
That is where the file is located for me in Fiesty.

You can do a search for it, by hitting "Places">"Search for Files..." and typing in xpti.dat. Make sure you say to look in File System instead of your home directory.

---

### Post by x-ray vision on 2007-04-12
No files found? :confused:

---

### Post by Raptor45 on 2007-04-12
Perhaps it is already deleted? Try...

```
ls /usr/lib/firefox/components/
```

If that returns a bunch of files, I'm guessing that this is the case.

---

### Post by x-ray vision on 2007-04-12
Yeah, got back a bunch of files and that one wasn't in there. Oh well. Thanks for the help. :)

---

### Post by click4851 on 2007-04-12
your headed in the right direction, sometimes the tough part is locating files. I don't have my system in front of me, but using Places>---Search For Files> is where I would go, is there a option to search other/more areas?

---

### Post by taurus on 2007-04-12
```
sudo find / -name xpti.dat -print
```

---

