---
title: "is it possible from DOS"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by tom69 on 2007-03-04
I have an old computer that was running windows 98se and I decided to format the hard drive to clean it up and start over.  Everything went fine till it asked for the windows keycode and I realized I didn't have it, it was lost long ago.  SO  I decided to download the startup disk for ubuntu, which I did.  I put the disk in and found the start.exe file.  

It came back with an error message 'this program cannot be run in DOS mode'.

If anyone has a solution I would appreciate it, but please stay as non-technical as possible.  Im not that advanced on the computer as you can tell from my problem:(

---

### Post by oilchangeguy on 2007-03-04
i can provide you w/a keycode. as for ubuntu what version are you trying to install?

---

### Post by Bachstelze on 2007-03-04
This "start.exe" file is not the installer. To install Ubuntu, you just need to boot from the CD and follow the instructions.

But you might have another problem, if the coputer was running Win98, the hardware specs might not be sufficient to run the Ubuntu Live CD. If that's the case, you'll need to download the Alternate one.

---

### Post by jfinkels on 2007-03-04
> **HymnToLife said:**
> This "start.exe" file is not the installer. To install Ubuntu, you just need to boot from the CD and follow the instructions.
To boot from the CD, you should put your CD in the drive and restart the computer. You might get a message that says "Press any key to boot from CD..." or something similar. You want to do that. If you don't get a message like that, the Ubuntu loader might boot on its own. That's good.

If you neither get a message nor see the Ubuntu boot screen, you will need to change the boot order for your computer. Post here if you need help with this.

> But you might have another problem, if the coputer was running Win98, the hardware specs might not be sufficient to run the Ubuntu Live CD. If that's the case, you'll need to download the Alternate one.

I put Ubuntu on a computer that was designed for Windows 98 with no problems, so it is definitely possible.

---

### Post by Bachstelze on 2007-03-04
That's why I saud "might". If the computer was running Win 98 and was not upgraded to XP, it  is very possible that it has less than 256 MiB of RAM, which is the minimum to run the Ubuntu Live CD.

---

### Post by omrsafetyo on 2007-03-04
Thats true - but it sounds like the problem is that he was navigating through the CD from DOS, and tried launching a random EXE file to start the CD.

The solution will be in your BIOS.  Ensure that your system boots from the CD before it boots from the HDD in your boot priority list.  This will ensure that your CD loads before your PC accesses your MBR, and boots into DOS.  This will launch the CD automatically, allowing you to use the LiveCD (hopefully) or install Ubuntu without having to go through DOS.

---

### Post by noalternative on 2007-03-07
> **HymnToLife said:**
> This "start.exe" file is not the installer. To install Ubuntu, you just need to boot from the CD and follow the instructions.

But you might have another problem, if the coputer was running Win98, the hardware specs might not be sufficient to run the Ubuntu Live CD. If that's the case, you'll need to download the Alternate one.

That being the case it probably won't break any records with the gnome desktop.   He should probably install [xubuntu]("http://xubuntu.org").

---

