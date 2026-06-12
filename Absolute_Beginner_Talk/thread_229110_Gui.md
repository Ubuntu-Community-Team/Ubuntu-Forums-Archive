---
title: "Gui"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by elchinovi on 2006-08-04
I've just installed the Ubuntu on my pc, i've restarted it and now I have the command line... how do I start the GUI?
Thanks!

---

### Post by cantormath on 2006-08-04
> **elchinovi said:**
> I've just installed the Ubuntu on my pc, i've restarted it and now I have the command line... how do I start the GUI?
Thanks!

You downloaded the Server CD.  You should have downloaded the Desktop CD.
simple mistake.
you have two options.
1) Download the Desktop CD and reinstall
2) login to the commandline and type

terminal:~$ sudo apt-get update
terminal:~$ sudo apt-get install ubuntu-desktop

then reboot.

also, before you reboot, you might want to do the updates, if you have not yet. This may take a few mins, but is good to do.

terminal:~$ sudo apt-get upgrade 
If you are prompted with (y/n) type y

then reboot.

---

### Post by elchinovi on 2006-08-04
Yeap, that's what I did...
It was the Server one...
Thanks for your help!
;)

---

