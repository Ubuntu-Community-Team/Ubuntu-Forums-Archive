---
title: "Can't access GUI"
date: 2008-02-19
forum: Absolute Beginner Talk
---

### Post by mkl6 on 2008-02-19
I've just installed 7.10 on a Mac Mini (Running OS X 10.5.2) using BootCamp. I've done the install just fine but i'm stuck at the GRUB command line.

I'm simply trying to get out of text mode and into the GUI. I've tried using StartX but get "Error 27: Unknown Command". 

If it helps the screen is displaying something like this:

[some text]
[more text]
[more text]

grub>_


I am a total Ubuntu newbie. (Have used computers for years but first time using Linux.] So i can imagined this has been asked thousands of time's before. Just in a bit of a rush (I wonder how many times that excuse has been used?)

---

### Post by Hobo Joe on 2008-02-19
Looks like GRUB (The bootloader) is broken, you'll need to re-install it to even get into Ubuntu itself.

Check out the [Super GRUB Disk.]("http://supergrub.forjamari.linex.org/")

---

### Post by mkl6 on 2008-02-19
That seems to have been the problem. Did a Re-Install and no longer get that menu. Boot up is now very quick. Thanks for that. 

If i didn't need my Pro App's on OS X I would for sure switch to Ubuntu.

---

### Post by neurostu on 2008-02-19
Ok so when you are at the **grub** command line you are running **GRUB** as the operating system. You need to start LINUX before you can **startx**. I would highly recommend going over to the apple section of the ubuntu forums. They will know a lot more then we do here as they are all using or are familar with apple hardware! ;-)

---

