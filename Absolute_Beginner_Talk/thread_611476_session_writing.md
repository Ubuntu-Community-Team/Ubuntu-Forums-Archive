---
title: "session writing"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by dineshs on 2007-11-13
I am using Feisty. Is there any programme for writing CD/DVD by parts.(session writing/Allow files to be added later)

---

### Post by jfinkels on 2007-11-13
You can use wodim (the de facto standard for writing discs) with the -multi flag like thus:```
wodim -multi dev=/dev/cdrom *whatever*
``` Read more about that by typing:```
man wodim
```

Does nautilus, the graphical file browser, not let you read and write files to a mounted rewritable disc by default?

---

### Post by dineshs on 2007-11-14
I am new to linux I havent tried anything except gnomebaker, which i couldnt fully understand

---

### Post by jfinkels on 2007-11-14
> **dineshs said:**
> I am new to linux I havent tried anything except gnomebaker, which i couldnt fully understand

To view some introductory information on linux commands, read here: [http://linuxcommand.org/](http://linuxcommand.org/) and take a look at the link in my signature to [http://www.psychocats.net/ubuntu](http://www.psychocats.net/ubuntu) for more basic information. I highly recommend doing these FIRST as they will give you a basis with which to start. Also, as always, experiment! You can't learn it unless you try it.

Open the terminal by selectin "Applications > Accessories > Terminal".

The terminal lets you browse the filesystem and run programs. Enter a command by typing it, then pressing enter. For example, to list the contents of the current working directory, type:```
ls
```To change the current working directory, type ```
cd */path/to/directory*
``` To move up one directory level in the directory hierarchy, type:```
cd ..
``` Read more at [http://www.linuxcommand.org/](http://www.linuxcommand.org/) .

Read about the program "wodim", which reads and writes to CDs by typing the following:```
man wodim
```and type <Q> to exit. Scroll up and down with arrow keys.

It looks like to write to a rewritable, multi-session disc, use wodim with the "-multi" option. So, to write a file located at "/home/*yourusername*/file.name" to a multi-session disc, you would write:```
wodim -multi dev=/dev/cdrom /home/*yourusername*/file.name
```

There are other graphical burning utilities, including K3B (a very popular one) and Brasero. Install them and try them out.

---

### Post by dineshs on 2007-11-16
Thank you very much for the guidance.I shall try K3B .(Gui is simpler for a beginner like me).

---

### Post by dineshs on 2007-11-17
I tried brasero and it works fine.once again thank you forr a detailed reply

---

### Post by erginemr on 2007-11-17
> **dineshs said:**
> I tried brasero and it works fine.once again thank you forr a detailed reply

Hello,

Is Brasero able to do and resume multisession disks?

---

### Post by dineshs on 2007-11-17
yes.I am using Gutsy.I tried a CD-RW disc , I wrote some files,Then reinserted the CD, there is an option for multisession writing. This was not available in earlier versions i think

---

### Post by erginemr on 2007-11-17
> **dineshs said:**
> yes.I am using Gutsy.I tried a CD-RW disc , I wrote some files,Then reinserted the CD, there is an option for multisession writing. This was not available in earlier versions i think

Thank you, you made my day! I was also looking forward to this feature in Gnome based CD Burning programs.

---

### Post by dineshs on 2007-11-18
please see the attachment

---

