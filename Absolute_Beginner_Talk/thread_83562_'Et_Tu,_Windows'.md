---
title: "'Et Tu, Windows?'"
date: 2005-10-29
forum: Absolute Beginner Talk
---

### Post by NYPD on 2005-10-29
Hi Guys!

I'm Windows user who is considering Ubuntu. I've always wanted to try a linux system, and maybe free myself from the evil of Microsoft...:smile:

But at the moment, I want to know if Ubuntu can operate in a dual boot capacity and wheter I need to manually create a new partion on my hard drive? Does the installer do this for me? (I would be using one of the CD's that you guys ship out) 

Could someone tell me how to make an XP/Ubuntu Dual boot system?

---

### Post by audax321 on 2005-10-29
I've had SuSE resize my windows partition before and it worked fine. I might be wrong but I believe Ubuntu v5.10 (Breezy Badger) will resize NTFS partitions. Most likely this will come up as an option after you boot from the CD. This will make the windows partition smaller and create a linux partition for you to install Ubuntu into and later on in the installation you will be asked if you want to install GRUB which will allow you to dual boot. I dual boot on my laptop, and it works great. Although, after using Ubuntu for the past year, I stopped using Windows and actually replaced it on my desktop. :)

---

### Post by matthew on 2005-10-29
From the Ubuntu wiki...

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)

---

### Post by niobe_logos on 2005-10-29
Yes, Ubuntu can operate quite happily in a dual boot system. I ran dual boot ( Ubuntu/Win98 ) for about a year. When I ran out of reasons to boot Windows, I ditched it...

As to whether you need to manually create a new partition for Ubuntu, the real answer is: 

**"Only if you feel like it".**

No, seriously.  If you want to keep everything on one drive, and there's space left over from Windows :rolleyes: you can resize the Windows partition so there's room for a Linux one. The installer can resize things, or you can use a Windows program called Partition Magic to prep the hard drive for dual boot. Take as much time as you need to figure stuff out. The partitioning program will show you what your drive will look like with the new partitions, but it doesn't make the changes permanent until you confirm them. Then you can use a program like Grub or Lilo to choose what you want to boot up.

OTOH, hard drives are cheap. It's just as easy to stick a second drive in your system--assuming it's a desktop--install Ubuntu on it, and just use Grub to choose which drive starts up. One advantage of this method is that you then don't have to worry about accidentally wiping anything out of Windows, but you do have to do a smidgen of editing in Grub before it's happy.

---

### Post by Qrk on 2005-10-29
Also, the liveCD of ubuntu comes with gparted, which is a graphical disk partitioning tool. The one that comes in the install cd is part of the installer.

---

### Post by aysiu on 2005-10-29
An awesome step-by-step with screenshots for setting up a dual-boot:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

Resizing an NTFS partition:
[http://www3.telus.net/linux4u/ubuntu.html](http://www3.telus.net/linux4u/ubuntu.html)

Combine the two--you're set.

---

### Post by carlosqueso on 2005-10-30
Also, if you are feelin a bit intimidated....start by installing Mandrake (I guess it's Mandriva now), which will set up your partitions automatically, then, since it's a crappy distro, install Ubuntu or BLAG.

---

### Post by kingsidy on 2005-10-30
One way to do it without problems is to first resize your windows partition and convert to the ext filesystem by using a program lile partition magic, and then install ubuntu. Worked perfect for me.

[HTML]Also, if you are feelin a bit intimidated....start by installing Mandrake (I guess it's Mandriva now), which will set up your partitions automatically, then, since it's a crappy distro, install Ubuntu or BLAG.[/HTML]
The way carlosqueso outline also works great, i used it when i first installed SuSE on my computer a while back

---

### Post by aysiu on 2005-10-30
[QUOTE=carlosqueso]Also, if you are feelin a bit intimidated....start by installing Mandrake (I guess it's Mandriva now), which will set up your partitions automatically, then, since it's a crappy distro, install Ubuntu or BLAG.[/QUOTE] I agree with this strategy as well. Ubuntu and Blag have partitioning tools, too, but Mandriva's DiskDrake is very powerful and clean--nothing's ever "greyed out" as it can sometimes be in QTParted, for example. It's also very easy to use (which can't necessarily be said for Ubuntu's partitioning "tool."

I use DiskDrake for partitioning and then install some other distro.

---

### Post by Cufishing on 2005-10-31
Things I have learned about WinXP, NTFS, and Ubuntu.
If ALL of the following are true, you are out of luck. 
1. WinXp SP2
2. NTFS
3. Dynamic disk set-up

It reports cannot adjust a WinXp NTFS Dynamic disk. Partition failed, Format failed, install failed.

I have not tried the other programs that are mentioned above.

---

### Post by derekr44 on 2005-10-31
[QUOTE=Cufishing]Things I have learned about WinXP, NTFS, and Ubuntu.
If ALL of the following are true, you are out of luck. 
1. WinXp SP2
2. NTFS
3. Dynamic disk set-up[/QUOTE]

4. IDE/SCSI expansion card setup (More than 4 drives)

I had to remove my IDE card and drop down from 6 to 4 drives (primary master/slave & secondary master/slave) in order to get Grub to work.  I now successfully am running a dual-boot of XP SP2 and Ubuntu.  I'll fully switch to Ubuntu when I get Wine to run and gradually wean my wife off XP :p

---

