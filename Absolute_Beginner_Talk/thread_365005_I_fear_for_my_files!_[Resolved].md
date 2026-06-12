---
title: "I fear for my files! [Resolved]"
date: 2007-02-19
forum: Absolute Beginner Talk
---

### Post by Zephr on 2007-02-19
I just got Ubuntu working after a long hard process, of partitioning, boot managing and, a ludicris amout of DVD burning.

So, I'm all happy that it's working and suddenly, my boot manager doesn't show up! so I'm forced to run Ubuntu, even though it's 100X better than windows, all my programs are on WIndows. I need to finish a website in 2 days and If I don't get there soon I could lose alot of money!

I know the files are there, the disk manager says that the correct amout of disk space is on the WIndows drive.

I'm extremely new to Ubuntu so if theres some boot order option I don;t know about, or any way to fix it. I'd be eternally grateful.

I'm using GAG 4.5 Boot manager if that helps.

Thanks!

---

### Post by aysiu on 2007-02-19
You can mount the Windows partition to get the files:
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

Ubuntu has plenty of web development tools.

---

### Post by Zephr on 2007-02-19
Thanks? I'm going to have to work at this for a bit, it's very confusing.

---

### Post by rccharles on 2007-02-19
> **Zephr said:**
> I just got Ubuntu working after a long hard process, of partitioning, boot managing and, a ludicris amout of DVD burning.

So, I'm all happy that it's working and suddenly, my boot manager doesn't show up! so I'm forced to run Ubuntu, even though it's 100X better than windows, all my programs are on WIndows. I need to finish a website in 2 days and If I don't get there soon I could lose alot of money!

I know the files are there, the disk manager says that the correct amout of disk space is on the WIndows drive.

I'm extremely new to Ubuntu so if theres some boot order option I don;t know about, or any way to fix it. I'd be eternally grateful.

I'm using GAG 4.5 Boot manager if that helps.

Thanks!

Typically, Ubuntu replaces the MBR with a pointer to it's own boot manager called grub.  I do not know what checks it makes before doing the replacement.

1) To get the grub menu to display, I'd change the /boot/grub/menu.lst

applications>accessories>terminal
sudo nano /boot/grub/menu.lst
## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

control-o
to file

notice that I commented out hiddenmenu


2)  You could try superGrub. This will let you pick what harddrive and partition to boot.

An option would be to use superGrub. This has grub on a bootable CD. In a series of menus, superGrub lets you boot any partition.

Main page:
[http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

download page:
[http://forjamari.linex.org/frs/?group_id=61](http://forjamari.linex.org/frs/?group_id=61)

superGrub can be a little cryptic, but looking at the screenshot page helps.

[http://supergrub.forjamari.linex.org...on=screenshots](http://supergrub.forjamari.linex.org...on=screenshots)

You cursor down to the line you want.

The help line is
| ================> Windows <=============== |

You cursor down below this line and press enter.

I wrote superGrub out to cd and it worked for me. You can boot your partition even without grub on the partition.

This wouldn't be a permanent solution, but it would get you started.


Robert

---

### Post by Zephr on 2007-02-19
**Thank you!** This is exactly what I wanted. * hands favorite person sticker*::KS 

You win!

---

