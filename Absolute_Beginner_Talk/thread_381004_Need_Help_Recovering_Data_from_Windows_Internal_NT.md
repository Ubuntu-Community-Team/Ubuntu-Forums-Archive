---
title: "Need Help Recovering Data from Windows Internal NTFS Drive"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by eponaflora on 2007-03-10
My Dell laptop completely died yesterday and I am just trying to recover my files and data from the internal Windows NTFS drive using Ubuntu and transfer them to my external hard drive (which Ubuntu recognizes and I can access no problem). I've been trying various things from these forums and still can't get to my files. I can see the hard drive through GNOME Partition Editor, but that's as far as I've gotten.

Can anyone suggest a good way to get started or how I might do this? I'm not new to computers, but I'm new to Ubuntu and just can't get anything to work.

Your responses are greatly appreciated.

Eponaflora

---

### Post by enopepsoo on 2007-03-10
Have you chmod'ed the files so that you can have full control?

```
sudo chmod 777 /media/ntfs-clunker
```

Or whatever the path you mounted on happens to be.:)

---

### Post by pveith on 2007-03-10
As Ubuntu does not enable NTFS write you might be better off using KNOPPIX or some other live-system with NTFS support. In Knoppix it should be a matter of two clicks. On Ubuntu-Live you will have to install some extra packages, which is not that easy...

---

### Post by taurus on 2007-03-10
Have you managed to mount your ntfs in Ubuntu?  What's the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```

---

### Post by redsoftretro on 2007-03-10
Hi

Have you installed Ubuntu or are ou running from the live disk?

---

### Post by Crooksey on 2007-03-10
Add an external hard-drive, then copy and paste the files from your windows partition to the drive to recover important doc's

---

### Post by kgr132 on 2007-03-10
Although it's not Linux, the Ultimate Boot CD 4 Windows saved my butt once when I needed to recover data from an NTFS drive that wouldn't boot.

[http://www.ubcd4win.com/](http://www.ubcd4win.com/)

Good Luck.

---

### Post by FuhrerNGod on 2007-03-10
Yeah, I'm trying to do the same thing except I don't know how to add an external Hard Drive. I'm completely lost when it comes to Linux. I just bought a new external Hard Drive and I want to move all my files onto it. I'm running Kubuntu after my computer seemed to have died. It would start and then I'd get the BSOD while Windows was loading. I'm running on live CD. If anyone's willing to help, I'll be more than grateful.

-Luis-

---

