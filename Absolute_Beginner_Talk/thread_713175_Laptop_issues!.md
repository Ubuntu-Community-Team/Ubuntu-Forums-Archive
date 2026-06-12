---
title: "Laptop issues!"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by marshall700 on 2008-03-02
I have a Dell Inspirion 1501 and im trying to install ubuntu 7.10 however my dvd rom drive doesnt recognise the disk with it on.... the disk works fine on my desktop however it doesnt want to load on the laptop any pointers? all other disks work fine on laptop its just the ubuntu one that doesnt....

---

### Post by mike.desmo on 2008-03-02
Is your bios set to boot from cd?? Could be that simple:)

---

### Post by overdrank on 2008-03-02
> **marshall700 said:**
> I have a Dell Inspirion 1501 and im trying to install ubuntu 7.10 however my dvd rom drive doesnt recognise the disk with it on.... the disk works fine on my desktop however it doesnt want to load on the laptop any pointers? all other disks work fine on laptop its just the ubuntu one that doesnt....

Hi and welcome, you mean other cd's boot on the laptop and the Ubuntu live cd does not?

---

### Post by northern lights on 2008-03-02
If it ain't your BIOS, the easiest way of installation might be via the net/Wubi.

Download this [.exe]("http://downloads.sourceforge.net/lubi/unetbootin-ubuntu710rev113.exe?modtime=1202111429&big_mirror=0") executable run it from Windows. Reboot. Your NT Loader should now not go to Windows directly, but also offer you the choice to install Ubuntu.

---

### Post by Mazza558 on 2008-03-02
You're in luck, I'm using the exact same laptop. Whilst I'm not sure about that issue (didn't happen for me), I can advise you on a few things:

- You might struggle with the wireless. fwcutter is the fastest way to get wireless working, but I seriously advise you to use ndiswrapper as it is much more reliable. Note that you'll need an ethernet connection to get things working internet-wise

-Video drivers are very, very easy - they're in the restricted driver manager in Ubuntu.

-You cannot change the screen brightness at all. 

-Due to the ATi drivers, you can't run compiz and other 3d applications at the same time. Google Earth crashes and a lot of other programs will run very very slowly. 2D games are fine.

---

### Post by marshall700 on 2008-03-02
Thanks guys, Yeah its got Xp running atm and even in xp it doesnt detect the Ubuntu 7.10 disk. i downloaded it and burnt it to disk using infra recorder and ive gone though the BIOS and set it to boot from dvd rom, im more in luck i dont got wireless :P, im gonna use it for programing and php no games lol and who cares bout brightness......  but thanks anyway ill try that .exe

---

### Post by marshall700 on 2008-03-02
Me again the exe worked thatnks a lot guy its installing now!!!

---

### Post by Crafty Kisses on 2008-03-02
> **marshall700 said:**
> Thanks guys, Yeah its got Xp running atm and even in xp it doesnt detect the Ubuntu 7.10 disk. i downloaded it and burnt it to disk using infra recorder and ive gone though the BIOS and set it to boot from dvd rom, im more in luck i dont got wireless :P, im gonna use it for programing and php no games lol and who cares bout brightness......  but thanks anyway ill try that .exe
You'd have to reboot your computer with the disc in.

---

