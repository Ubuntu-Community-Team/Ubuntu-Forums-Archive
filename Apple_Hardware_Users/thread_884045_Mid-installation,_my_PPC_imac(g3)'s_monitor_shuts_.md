---
title: "Mid-installation, my PPC imac(g3)'s monitor shuts off!"
date: 2008-08-08
forum: Apple Hardware Users
---

### Post by The Flame Lilith on 2008-08-08
I pop the freshly burned disk of [http://releases.ubuntu.com/6.06/ubuntu-6.06.1-desktop-powerpc.iso](http://releases.ubuntu.com/6.06/ubuntu-6.06.1-desktop-powerpc.iso), it works until loading the actual installer is almost done, and one of the things it was loading says "Failed". It then turns into a black screen until the monitor shuts off.

It disappears too fast to read what it is that it couldn't load, but I'm hoping someone has a solution for me.

Am I doing something wrong?

I'm installing this on an imac g3 with a powerpc processor, 8GB hard drive(I think) and upgraded to 350MB something RAM.

I'm trying to install it on a formatted hard drive. I messed up the mac OS some how, so I thought I'd try ubuntu. So then, this hard drive is completely empty.

---

### Post by tiresia on 2008-08-08
Why don't you try Hardy? 
Here is the link: [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
After the download make a checksum and burn (with Apple Disk Utility if you have OSX) at low speed!!!

---

### Post by The Flame Lilith on 2008-08-08
> **tiresia said:**
> Why don't you try Hardy? 
Here is the link: [http://cdimage.ubuntu.com/ports/releases/hardy/release/](http://cdimage.ubuntu.com/ports/releases/hardy/release/)
After the download make a checksum and burn (with Apple Disk Utility if you have OSX) at low speed!!!
I just tried, and it didn't help. Same result.

---

### Post by tiresia on 2008-08-08
If you have another MacPPC can you try to start with the CD (just to be sure that the CD works)
Have you downloaded the Live-CD or the AlternateCD?
You should try with the Alternate!

After that, when you start your imac, at the first prompt hit TAB
If you have the live-cd, you can choose: live-nosplash-powerpc video=ofonly

Please, read this link:
[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank) screen on iMac G3

---

### Post by The Flame Lilith on 2008-08-08
> **tiresia said:**
> If you have another MacPPC can you try to start with the CD (just to be sure that the CD works)
Have you downloaded the Live-CD or the AlternateCD?
You should try with the Alternate!

After that, when you start your imac, at the first prompt hit TAB
If you have the live-cd, you can choose: live-nosplash-powerpc video=ofonly

Please, read this link:
[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank) screen on iMac G3

That command just made my screen black, and nothing in that link has seemed to help, or even work.

Can you give me a link for the alternate though? I would really appreciate it, and I can't find the right version.

---

### Post by mkvnmtr on 2008-08-08
The second post in this Mac forum has got a list of all the Mac disks you could ever want to download.

---

### Post by stream303 on 2008-08-09
When installing onto G3 iMacs, you'll definitely want to use the "alternate" installers which are text-based during install to avoid that screen shutdown.  Afterwards, you'll need to manually edit your /etc/X11/xorg.conf file after installation to make sure that the horizontal and vertical frequencies are correct.  This is because the G3's don't always give back any / correct values, and you have to do it manually:

[https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3](https://wiki.ubuntu.com/PowerPCKnownIssues#Blank%20screen%20on%20iMac%20G3)

That means that you'll need to boot into rescue-mode from the installer disk after you actually have the system laid out on the disk, and then do your edits there to correct the xorg.conf file.

In addition, you'll probably want to specify the video driver.  Some good hints and tweaks are here:

[https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz](https://wiki.ubuntu.com/PowerPCFAQ#3D%20video%20drivers,%20Beryl,%20Compiz)

With Hardy, you won't find any pre-existing lines in xorg.conf to make it immediately easy - you'll have to manually add those full lines yourself, rather than just change some existing options.  There should be quite a few G3 iMac threads here that can help out.

---

