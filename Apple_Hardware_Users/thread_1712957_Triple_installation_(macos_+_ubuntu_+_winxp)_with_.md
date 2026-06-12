---
title: "Triple installation (macos + ubuntu + winxp) with Windows after Ubuntu"
date: 2011-03-23
forum: Apple Hardware Users
---

### Post by cryoff on 2011-03-23
Hello!
I've got Macbook 5.1 on the work, so i'm not a proficient user of macos. I have installed Ubuntu 10.10 on it (using rEFIt). Both systems work perfectly ok. But now there is a need to install also WinXP on the same MacBook. I was struggling for 2 days with ubuntu to make it work correctly so i don't want to install everything from the beginning.
I scanned (maybe, i did small effort..) through forums etc., but i had found only ways to install ubuntu after windows.

I had a hope that i could create a new NTFS partition for WinXP and just install it. But it seems like it is kind of difficult to make WinXP loader friendly with already installed OS loaders.

Can you please help me to find a way, how to install WinXP in my situation. I really need Visual Studio for work now and i think that virtualization is not the best way to go.

---

### Post by Joe of loath on 2011-03-23
You will need to install Windows XP, then reinstall your previous bootloader afterwards. Windows rewrites it with its own during the install.

---

### Post by cryoff on 2011-03-23
> **Joe of loath said:**
> You will need to install Windows XP, then reinstall your previous bootloader afterwards. Windows rewrites it with its own during the install.

Thank you!
Can you please describe the process in more details?
So, i will need to create new partition with NTFS file system. Then using rEFIt i will boot from WinXP and install it into this new partition. Afterwards i will probably see only WinXP in the system.
So the question is how to reinstall bootloaders then? I'm afraid of damage this fragile loaders structure :)

---

### Post by Joe of loath on 2011-03-23
I'm afraid I'm not familiar with the process of booting other OS's on Macs. On a PC you would boot from the CD and update grub, but I don't know how well this would work, if at all.

---

### Post by cryoff on 2011-03-23
> **Joe of loath said:**
> I'm afraid I'm not familiar with the process of booting other OS's on Macs. On a PC you would boot from the CD and update grub, but I don't know how well this would work, if at all.

Ok. I read several threads and guides on this topic. This seems to be non-trivial and the order of installations really matters due to features of HFS as i understand (and lack of BIOS-type boot options)

---

### Post by cryoff on 2011-03-30
Some other opinions?
Seems like i will have to create an image of my Ubuntu partition, delete it and then istall Windows and Ubuntu only afterwards.

---

### Post by |preetcher| on 2011-04-01
Hi there.

I was trying the same concept, but with windows 7.  It seems that it could be done by using parallels, and running the ubuntu and windows as virtual machines within the os.  But, I am not really sure.  Does anyone else know if this would work?

If not that route, could one have windows and ubuntu both bootcamped?  I have windows 7 already bootcamped.  Could I add ubuntu?

Thanks much.

---

### Post by henry8596 on 2011-04-01
Hi there,

In the past week I was doing the same thing too. But I am installing Windows 7 and using Macbook 2.1. I also installed ubuntu on 2nd to just make sure it works, then installed Windows as the 3rd. Then cannot boot into ubuntu.

Did some research and can't really find a detail instruction to make it work. And since I need to work and only got 1-2 hours to do this habit, I decided to just reinstall the ubuntu, after installing 3 OS and finally, able to get into 3 OS.

However, I don't know if you have done this yet. After reinstalling Ubuntu, yes, 3 OS choice for you at rEFIt at startup. But, the Ubuntu and Windows both bring me to Grub(?not sure what it called), where you choose boot from Ubuntu or Windows.

But after a week, I just decide to live with that!

---

### Post by cryoff on 2011-04-13
I decided to create a full backup of linux partitions and then recovery needed ones after installation of Windows.
So, actually i will have to delete linux partitions and go through the scheme MacOS -> Win installation -> Ubuntu installation

Now the question is how to make the backup correctly since i don't want to lose all those settings and packages i have to make it easy to work on Mac under Ubuntu =)

---

### Post by Joe of loath on 2011-04-13
Try CloneZilla.

---

