---
title: "Copy directories in Terminal"
date: 2007-04-05
forum: Absolute Beginner Talk
---

### Post by Stephen_A on 2007-04-05
I have a bunch of subdirectories full of files on a USB drive, /dev/media/usbdisk/Directory, that I wish to shift over to my  home on the hard drive,  on a directory of the same name. Each time I try to copy I get an error message 'missing file operand.' 
Could someone kindly tell what 'operand' I should put in? At present I'm using: 

stephen@stephen-laptop:/media/usbdisk$ cp *.* -t /home/stephen/Word

...which isn't doing anything. 

Thanks in advance.

---

### Post by IYY on 2007-04-05
cp *  /home/stephen/Word

should be enough (*.* would imply only files with extensions). If you also have directories in there,

cp -r  *  /home/stephen/Word

---

### Post by Skrynesaver on 2007-04-05
You are trying to copy a file called "Directory", there is no "." 
[code]cp -r * /home/stephen/Word[code]

---

### Post by Stephen_A on 2007-04-05
Thanks, IYY and Skrynesaver. Your instructions did the trick. 

Stephen

---

### Post by Posterus on 2008-02-17
thank you guys, this thread came in handy while im trying to triple boot ubuntu, backtrack3, and xp

---

