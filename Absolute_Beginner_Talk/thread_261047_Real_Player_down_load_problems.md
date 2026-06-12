---
title: "Real Player down load problems"
date: 2006-09-19
forum: Absolute Beginner Talk
---

### Post by Tobster on 2006-09-19
I go to the Real player web site

down load the file

type:

chmod a+x RealPlayer10GOLD.bin

and it should work righ?  wrong

The following is what I got after two attemps
 
toby@toby-desktop:~$ chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
toby@toby-desktop:~$ chmod a+x RealPlayer10GOLD.bin
chmod: cannot access `RealPlayer10GOLD.bin': No such file or directory
toby@toby-desktop:~$

:sad:

---

### Post by kpkeerthi on 2006-09-19
Try 
chmod a+x ./RealPlayer10GOLD.bin

(...assuming RealPlayer10GOLD.bin does really exists in the current directory)

---

### Post by Sef on 2006-09-19
You can download replayer from the repositories too.

How to do it is in the [Restriced Formats.]("https://help.ubuntu.com/community/RestrictedFormats")

---

