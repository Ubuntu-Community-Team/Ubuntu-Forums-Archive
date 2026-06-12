---
title: "Ubuntu in Parallels"
date: 2007-06-09
forum: Apple Intel Users
---

### Post by Pjawsk on 2007-06-09
Hi, i really want to try ubuntu, but when i install during Parallels it all look fine, i press ENTER and then it should load, but it dont, it says: 0.000000] ACPI: Unable to locate RSDP

WTF is that all about? Please help i rly want to try ubuntu!

---

### Post by ronocdh on 2007-06-09
> **Pjawsk said:**
> Hi, i really want to try ubuntu, but when i install during Parallels it all look fine, i press ENTER and then it should load, but it dont, it says: 0.000000] ACPI: Unable to locate RSDP

WTF is that all about? Please help i rly want to try ubuntu!
The forums are here to help! Try searching through them to see whether anyone's had your problem before. By researching for "RSDP," I found [this post]("http://ubuntuforums.org/showthread.php?t=446338&highlight=rsdp"), and it seems to address your problem directly.

---

### Post by Pjawsk on 2007-06-09
i looked at it, but somehow i cant type = on my macbook in the install window? you know why?

---

### Post by ronocdh on 2007-06-09
> **Pjawsk said:**
> i looked at it, but somehow i cant type = on my macbook in the install window? you know why?
Hm, that's a problem. I don't use Parallels, but is there anyway you can copy/paste between OS X and the Parallels session? If so, you prepare the command in OS X in TextEdit or something, then insert in in the Parallels session when needed.

Also, from my brief look at the how-to, it appears that the **live vga=790** line is only to get the live session to run in better resolution; you'd still have to install and then edit the resolution on that installation.

---

### Post by Pjawsk on 2007-06-09
> **ronocdh said:**
> Hm, that's a problem. I don't use Parallels, but is there anyway you can copy/paste between OS X and the Parallels session? If so, you prepare the command in OS X in TextEdit or something, then insert in in the Parallels session when needed.

Also, from my brief look at the how-to, it appears that the **live vga=790** line is only to get the live session to run in better resolution; you'd still have to install and then edit the resolution on that installation.

What would you recommend insteed of parallels?

---

### Post by thully on 2007-06-09
VMware Fusion (currently a free beta, google it for more info) works much better than Parallels in my experience - from my usage I'd say it's noticeably faster (I have them running on the same machine).  I am going to try some more tweaking, though - I just realized my Parallels Ubuntu VM only has 256MB of RAM, which may be the cause of the slowdowns.

You can also run natively using Boot Camp - which is the fastest way and supports Beryl/Compiz/3D games, but the driver support isn't as good (i.e. the trackpad is much less responsive, wi-fi isn't as good, and suspend-to-RAM is sometimes problematic).  It may be worth it if you find yourself using Ubuntu nearly all of the time, though...

BTW - with Parallels, the newest version (3.0) should work better with Ubuntu as it has Parallels Tools for Linux

---

### Post by Pjawsk on 2007-06-09
Ty everyone for support, its installing now, now i just have to find out how to use it in widescreen :D ill do that later, anyways, ty!

---

### Post by cragthehack on 2007-06-10
> **Pjawsk said:**
> Ty everyone for support, its installing now, now i just have to find out how to use it in widescreen :D ill do that later, anyways, ty!

Can you report back if you get Ubuntu to run under Parallels 3.0? I could not. Finally ran to Fusion. Which is wondrful. If you do get Ubuntu to run I'd like to know what you did. Since I shelled out cash for Parallels.

Thanks...

---

### Post by thully on 2007-06-10
Just create a new VM and use the standard "Ubuntu" setting in Parallels  3.0.  It should work - the only issue is that you will be staring at a funny-looking screen for 30 sec-1min while the system boots, as Parallels doesn't handle Ubuntu's graphical boot screen and progress bar properly.  Also, it is definitely slower than Fusion...

---

### Post by cragthehack on 2007-06-10
Ahh that was my mistake. I saw the screen and waited maybe 20 secnds beforing calling it a crash and starting over.

I love Fusion and am eager to see the actual release.

---

### Post by black_raven2525 on 2007-07-13
I got Kubuntu 7.04 live running in Parallels 3.0 with minimal hassle.  To get the live CD to boot I had to follow these step I found in another thread.

Boot from the CD.
Choose "save graphics mode" and press F6.
Remove "splash", "quiet" and "--" then add "all_generic_ide"

After that the install was smooth ad standard.  At first I couldn't get the Live CD to boot because I had the VM set with 1500MB RAM and 64MB Graphics RAM and that caused it to hang while it was starting X.  Once I turned those down to 512 and 32 respectively, it went without a hitch.  To install parallels tools you have to click "Install Parallels Tools" under "Actions" then ```
sudo mount /dev/cdrom /media/cdrom0
``` and ```
sudo sh /media/cdrom/parallels-tools.run
```

---

