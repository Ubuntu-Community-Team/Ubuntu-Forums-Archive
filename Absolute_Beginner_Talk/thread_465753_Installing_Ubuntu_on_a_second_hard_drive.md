---
title: "Installing Ubuntu on a second hard drive"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by Elderlygent on 2007-06-06
Hullo Everyone,

I've got my Ubuntu CD, thank you, and I've got a computer with two hard drives on it. I'd like to install Ub on the second one, which seems a neat way of doing so. I know how to use the Command Prompt in XP to change from one disk to the other, but I"m loathe to go ahead in case there's something else I should do that I don't know about.

I'm sure loads of people have done this. Could someone please assist?

Thanks in advance.

---

### Post by sandeep108 on 2007-06-06
I am not too sure you can do that, especially if you want to keep your xp install absolutely separate. What I have done is connect the second HDD to the second IDE channel as master and then enable/disable each IDE channel through bios depending which OS I want to boot into. I cannot afford to bork my xp install through dual booting using grub, though mostly unlikely. I still have to set up my networking / mobile sync properly in my spare time. Once I do that, then maybe I can keep using the Ubuntu install HDD.

---

### Post by Ripfox on 2007-06-06
If I remember right, I just set the second or "spare" hard drive to slave, hooked it up to the second slot on the IDE cable, booted up to the live cd, chose the slave drive (carefully, making sure it's not the xp drive) and  installed Ubuntu on it. The next time I booted up. I had the option of using either OS...don't take my word for this, I would prefer if someone backed me up before you go ahead, but I am preeety sure this is how I used to do it. Now I am windows free, so no need anymore :)

---

### Post by sandeep108 on 2007-06-06
> **ripfox said:**
> If I remember right, I just set the second or "spare" hard drive to slave, hooked it up to the second slot on the IDE cable, booted up to the live cd, chose the slave drive (carefully, making sure it's not the xp drive) and  installed Ubuntu on it. The next time I booted up. I had the option of using either OS...don't take my word for this, I would prefer if someone backed me up before you go ahead, but I am preeety sure this is how I used to do it. Now I am windows free, so no need anymore :)
You have installed grub and dual booting. This alters the MBR of the first HDD as well. I simply do not want to take any chance and if the OP also feels the same way, I had offered my method.

---

### Post by Dedoimedo on 2007-06-06
Hello,

You have 2 options:

1. Install on second HD, install GRUB on the same HD. Then to boot from this HD, you will need to change the boot order in BIOS.

2. Install on second HD, install GRUB on the first HD. Then, you will have the GRUB menu with options to boot either Windows or Ubuntu.

During install, you will have to specify where you want to install GRUB. You need to understand the GRUB notation to do this effectively.

Spend some time reading:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Briefly, a bit about notation:

First hard disk (hd0)

First partition on first hard disk (hd0,0)

It can also be sd for SCSI drives.

So, if you go with option 2, your GRUB needs to be installed on (hd0). Otherwise, on (hd1).

Aside from this, you should not need to do anything. But if you are interested in advanced editing of GRUB, please tell me, I'll help you.

Regards,
Dedoimedo

---

### Post by eddieb on 2007-06-06
Hi, Please don't think that I am patronising, but from the way you have phrased your question It is obvious that your computer knowledge is somewhat limited. The answers from the others to your question requires a fair amount of computer experience. If I was you I would stick to the Live Cd.
( I am 61 yrs but with 30 plus years experience in computing) Good luck.

---

### Post by Dedoimedo on 2007-06-06
The youngster wants to learn the Force.
We must help him.
Dedoimedo

---

### Post by majed on 2007-06-06
> **Dedoimedo said:**
> Hello,

You have 2 options:

1. Install on second HD, install GRUB on the same HD. Then to boot from this HD, you will need to change the boot order in BIOS.

2. Install on second HD, install GRUB on the first HD. Then, you will have the GRUB menu with options to boot either Windows or Ubuntu.

During install, you will have to specify where you want to install GRUB. You need to understand the GRUB notation to do this effectively.

Spend some time reading:
[http://www.gnu.org/software/grub/manual/grub.html](http://www.gnu.org/software/grub/manual/grub.html)

Briefly, a bit about notation:

First hard disk (hd0)

First partition on first hard disk (hd0,0)

It can also be sd for SCSI drives.

So, if you go with option 2, your GRUB needs to be installed on (hd0). Otherwise, on (hd1).

Aside from this, you should not need to do anything. But if you are interested in advanced editing of GRUB, please tell me, I'll help you.

Regards,
Dedoimedo

There is a better way -- if you really don't want to have GRUB on the MBR.

I have done this more than once and it works like a charm (now I am more comfortable with GRUB but you can start with this).. here you go: [http://ubuntuforums.org/showthread.php?t=56723]("http://ubuntuforums.org/showthread.php?t=56723")

You can do it! Just have good backups, just in case!

Majed

---

### Post by steve-shinn on 2007-06-06
Which of the 2 options mentioned above is preferable, and would both options give you the option at start up to select Xp or Ubuntu ?? without changing boot order priority in BIOS everytime you started up ??

---

### Post by Dedoimedo on 2007-06-06
Yes majed, very good!

Booting from floppy is as cumbersome as replacing the disk order.

Editing the boot.ini is OK, but I prefer GRUB over NTLDR.

steve, all options are valid. Choose what you are most comfortable with.

Regards,
Dedoimedo

---

### Post by kyphi on 2007-06-06
Hello to the Elderlygent.  What you want to do is very easily achieved.

I run two SATA hard drives on my computer, one for Windows XP and the other for Ubuntu 6.06.  It all works perfectly.

Remember that in Linux, drives are not called A, B, C or D.

Having a second hard drive means that you can devote all the space on that drive to Ubuntu.  All you have to remember is what that drive is called in Linux parlance.  Generally the first hard drive is hda and a secondary drive is hdb (unless you have SATA drives which are called sda and sdb).

Ubuntu will install and partition for its own use your second drive if you give it permission to use the whole drive.

Put the Ubuntu disc into the drive and just sit back and let Ubuntu do its stuff.

BUT REMEMBER WHICH DRIVE WINDOWS IS ON (hda).  You don't want Ubuntu to wipe Windows.  At least, not yet.

---

### Post by Elderlygent on 2007-06-07
Thanks to all who have replied to my query. Once upon a time I was quite adapt with DOS but, yes, I've been in thrall to Microsoft Windows for too long. So I'm going to take a good look at all your posts and suggestions. Thanks again and watch this space for progress reports.

---

