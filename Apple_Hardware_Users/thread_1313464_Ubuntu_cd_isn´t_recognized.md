---
title: "Ubuntu cd isn´t recognized"
date: 2009-11-03
forum: Apple Hardware Users
---

### Post by knutf on 2009-11-03
Hi.

I´m trying to install Ubuntu on my Macbook Pro. I downloaded the 9.04 cd and burned the image on a cd, made a 10gb partition in BootCamp, restarted my computer and pressed alt option when the start sound came, but nothing but the Macintosh HD u icon showed up. Then I installed rEFIt, and tried to boot the cd from there, but when i restarted the computer and got to the rEFIt menu, no Linux-symbol, just the Mac and the Windows icon. I tried the Windows icon, but i just get a black screen saying "No bootable device".

This is starting to really annoy me, and I have tried almost everything. I have tried 8.10 and 9.04, I made a partition in disc utility which actually made another HD icon when I pressed the alt opt when starting up my mac, but no luck.


Can anyone help me with this?

---

### Post by N_Nick on 2009-11-04
You have to press and hold "C" to boot from the CD Rom. I had the same problem for a long time and couldn't figure it out.

Some CD's would be recognized by refit and some wouldn't.

---

### Post by linuxopjemac on 2009-11-04
With the option key pressed you should also see the CD. Your CD is probably burnt in a wrong way. Did you md5 sum the iso ? You can try to burn at lower speed.

---

### Post by Dayofswords on 2009-11-04
did you actually burn the image to the cd, now just burn the .iso file onto the disc

---

### Post by knutf on 2009-11-04
I checked the md5 sum, and it was correct. I have tried to press c, but nothing happened. It just booted into OSX. I have tried to burn the content in the .iso file, and I have tried to burn only the .iso file. I have also tried to burn at the lowest speed. But I never get it right.

---

### Post by linuxopjemac on 2009-11-04
how do you burn ? Under OSX or Linux ? And how ?

---

### Post by knutf on 2009-11-04
Under OSX. I have used the standard burning app in finder, and another app which I can't remember the name. I burn with lowest speed.

---

### Post by Muflon on 2009-11-04
When you look at the contents of the CD do you see one file with a iso extension or a number of files and folders including md5sum.txt?

Muflon

---

### Post by linuxopjemac on 2009-11-04
If you look at the contents of the CD under OSX, what do you see ? Do you see something like ubuntu-9.10-desktop-i386.iso or do you see folders and programs ?

---

### Post by knutf on 2009-11-04
I see folders and programs.

---

### Post by linuxopjemac on 2009-11-04
Is your burner still ok ? I would burn it on another machine. PS I would go for 9.10 by the way ;)

---

### Post by linuxopjemac on 2009-11-04
You should also use a good program to burn iso files. I recommend Toast.

---

### Post by knutf on 2009-11-04
So I have to burn to content to the cd, not the .iso file itself?
 
 
I'll try Toast when I get home :)

---

### Post by linuxopjemac on 2009-11-04
You have the option in Toast to burn a disk image. Select the iso file as image and let it burn. That should work provided that the md5 sum is correct and your burner works correctly.

PS Don't mount the iso on the desktop and try to copy the files as data on a cd, that's NOT the way to burn iso files.

---

### Post by linuxopjemac on 2009-11-04
Here you see a pic of what I mean in Toast:
[http://mac.linux.be/Ubuntu/toast.tiff](http://mac.linux.be/Ubuntu/toast.tiff)

---

### Post by knutf on 2009-11-04
I have now tried to burn a cd in magic iso. When i started my mac and pressed c, a starting screen windows style appeared. It said it loaded some drivers, and said something about "this is gonna take a few minutes" and then it said A:\> and nothing happened after that. I could write some commands, but I dont think I have to do that?

---

### Post by knutf on 2009-11-04
now im running ubuntu. it was much easier than i thought. i just burned the iso file in disc utilility, restarted my computer, pressed c and then it worked. i must have done something wrong i guess :)

thank you guys!

---

