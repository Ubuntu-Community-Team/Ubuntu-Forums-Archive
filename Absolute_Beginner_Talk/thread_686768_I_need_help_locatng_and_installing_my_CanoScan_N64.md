---
title: "I need help locatng and installing my CanoScan N640P Scanner."
date: 2008-02-03
forum: Absolute Beginner Talk
---

### Post by Reggie Manzer on 2008-02-03
I recently Installed Ubuntu ( and loved it) and I have had much success in all but a few areas, and this is one of them: I can't install my CanoScan N640P scanner. Its Connected to my computer using parallel port. I can't seem to locate its where abouts on my computer and when I run Xsane It doesn't even recognize that I have it turned on and connected to the computer. I'm very new at this kind of thing, so any help would be greatly appreciated. Thanks! 
-Reggie

---

### Post by coolbrook on 2008-02-03
Perhaps it's the same solution as the other **P**arallel printers

[https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon](https://wiki.ubuntu.com/HardwareSupportComponentsScannersCanon)

---

### Post by benyau on 2008-02-04
1.  become root and uncomment canon_pp in /etc/sane.d/dll.conf

2. uncomment force-nibble in /etc/sane.d/canon_pp.conf

3. run xsane as root, e.g. sudo xsane.

Cheers,

---

### Post by Reggie Manzer on 2008-02-04
I Can do the Third Step but I have not a clue how to uncomment canon_pp I when to the file, But I have no idea what to do next. I need you to explain it step by step, as I am very new to Ubuntu lol. Thanks. -Reggie

---

### Post by coolbrook on 2008-02-04
Applications > Accessories > Terminal

Then type

```

sudo gedit /etc/sane.d/dll.conf

```

remove the # sign from the canon_pp line

Close the text editor window and choose to save your edit.

```

sudo gedit /etc/sane.d/canon_pp.conf

```

remove the # sign from force-nibble

Close the text editor window and choose to save your edit.

---

### Post by Reggie Manzer on 2008-02-05
Thank You! It worked awesome after I made the adjustments. Thanks. -Reggie

---

### Post by coolbrook on 2008-02-06
Nice!  Just mark this thread as 'Solved' under **Thread Tools**

---

