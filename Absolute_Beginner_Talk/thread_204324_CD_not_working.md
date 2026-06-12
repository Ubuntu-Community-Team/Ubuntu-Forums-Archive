---
title: "CD not working"
date: 2006-06-26
forum: Absolute Beginner Talk
---

### Post by bollocks on 2006-06-26
I have done some searching on the forum for this, but did not turn up anything useful.  Feel free to answer or redirect.

I am completely new to Linux, currently running Windows XP Pro.  I downloaded the .iso image from ubuntu.com and burned it to a cd, no problem.  However, when I boot from the cd drive, my computer seems to ignore the cd altogether.  I tried it on my laptop with no avail, and then the same on my desktop.  I"m pretty sure I burned it correctly, since this is basically the same process I went through to hack my xbox (which went off without a hitch).  Any thoughts on how to get the cd recognized?

---

### Post by taurus on 2006-06-26
Make sure you burn that iso file as an image file, NOT as a data file!!!  Also, you should consider burning it at a slow speed like 4x because high speed burning could cause it to choke during the installing process.  However, the main thing is to burn it as an image, not date file...  Then, make sure your BIOS boots from a CD first.

---

### Post by bollocks on 2006-06-26
I've tried 2 cd's actually, one as an iso and one as an image - no luck either way.  I will try burning it at a slower speed, maybe that's the problem.

---

### Post by T700 on 2006-06-26
Quoting taurus, "Then, make sure your BIOS boots from a CD first.", you did do this, right?  It is an easy step to overlook.

Paul

---

### Post by bollocks on 2006-06-26
[QUOTE=T700]Quoting taurus, "Then, make sure your BIOS boots from a CD first.", you did do this, right?  It is an easy step to overlook.

Paul[/QUOTE]
Not technically - I am just doing F12 and choosing the boot device manually.  My laptop waits a few seconds then resumes booting from the hard drive.  My desktop says boot failed and to press F1 to retry or F2 to enter setup.  Either way, no go.  Is this any different than choosing to boot from a CD first?

---

### Post by taurus on 2006-06-26
You must tell your machine to boot from CD first or it will dump you directly into HD!!!  Also, what program do you use to burn the ISO file?  After you finish burning it, you should be a bunch of files and directories on the CD, not a one big file.  So, don't try to unpack it first before you burn it.  Use the burning program to burn it as image file.  Again, a lot of people think that they have to unpack the ISO somewhere, then burn it to a CD.  It will not boot if you do that...

---

### Post by bollocks on 2006-06-26
I am using Nero, and burning slower didn't work.  I do not have it to the point where I see a bunch of files on the CD after I burn it.  Anyone know how to get this with Nero, or can suggest a free program to burn it?  Thanks!

---

### Post by jrd on 2006-06-26
Use nero express and select "burn image to disk" then choose the iso file. As far as making sure bios is booting off the cd correctly, put in onother cd like windows install or something, then see if it boots off that.

---

### Post by siccness on 2006-06-26
You also have the choice of using another good application: CDRWin, which I HIGHLY recommend.

---

### Post by bollocks on 2006-06-27
Problem resolved - seems the exact same settings have different effects in Nero vs Nero Express.  Oh well, everything is working now...
Will definitely look into CDRWin, thanks

---

