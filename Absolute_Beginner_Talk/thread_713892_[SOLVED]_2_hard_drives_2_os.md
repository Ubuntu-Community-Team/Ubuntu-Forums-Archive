---
title: "[SOLVED] 2 hard drives 2 os ???????"
date: 2008-03-03
forum: Absolute Beginner Talk
---

### Post by 888mafia on 2008-03-03
i have two hard drives on my computer and would like to put a server to run a hour radio show 
3 times a week i have read the [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu]("http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu")
But it speaks on 1 hard drive partitioned is it possible to do this clean on a new hard drive

---

### Post by zerhacke on 2008-03-03
Why do you read it three times a week?

Yes, you can install Ubuntu on its own hard drive.

---

### Post by steveneddy on 2008-03-03
yes

---

### Post by Xarok on 2008-03-03
If you would like the windows hardrive to be untouched, disconnected while you install Ubuntu on the clean hardrive. Otherwise it will install a bootloader on the WIndows HDD, disallowing you to boot WIndows if the Linux HDD is not attached.

After Linux is installed, simpley reconnect your Windows HDD.

Then you can select which HDD to boot from within the BIOS at startup.

(At home I run a desktop with a WIndows XP HDD and a Linux HDD and it works great for me)

If you do have the bootler installed on the WIndows HDD, you can simply restore WIndow's MBR with a Super Grub CD.

---

### Post by sajro on 2008-03-03
> **zerhacke said:**
> Why do you read it three times a week?

Yes, you can install Ubuntu on its own hard drive.

:lolflag:

He means he hosts the show 3 times a week. He forgot a period.

---

### Post by 888mafia on 2008-03-03
> **Xarok said:**
> If you would like the windows hardrive to be untouched, disconnected while you install Ubuntu on the clean hardrive. Otherwise it will install a bootloader on the WIndows HDD, disallowing you to but WIndows if the Linux HDD is not attached.

After Linux is installed, simpley reconnect your Windows HDD.

Then you can select which HDD to boot from within the BIOS at startup.

(At home I run a desktop with a WIndows XP HDD and a Linux HDD and it works great for me)
can you direct me to a how too please i just dont want to get in there and do the wrong thing ty

---

### Post by James Haigh on 2008-03-03
Xarok, when you say disconnect, do you mean physically? I would also like to install a copy of Ubuntu to a 2nd HDD (external) but I cannot physically remove my 1st. I have a laptop.

---

### Post by LowSky on 2008-03-03
> **Xarok said:**
> If you would like the windows hardrive to be untouched, disconnected while you install Ubuntu on the clean hardrive. Otherwise it will install a bootloader on the WIndows HDD, disallowing you to boot WIndows if the Linux HDD is not attached.

After Linux is installed, simpley reconnect your Windows HDD.

Then you can select which HDD to boot from within the BIOS at startup.

(At home I run a desktop with a WIndows XP HDD and a Linux HDD and it works great for me)

If you do have the bootler installed on the WIndows HDD, you can simply restore WIndow's MBR with a Super Grub CD.

No bad idea, windows wont show up in Grub then or boot ubuntu. simply go into bios choose the hard drive that you want ubuntu on, so it boots first that way Grub will load onto that hard drive. that way if you disconnect the ubuntu drive windows will boot with no issues.

---

### Post by Yoke &amp; Chung on 2008-03-03
> **James Haigh said:**
> Xarok, when you say disconnect, do you mean physically? I would also like to install a copy of Ubuntu to a 2nd HDD (external) but I cannot physically remove my 1st. I have a laptop.

Yes disconnect the hard disk physically. In Desktop case, you need just to unplug the power supply to the hard disk.

For laptop, you probably have to unscrew from the bottom, and remove the hard disk.

---

### Post by Yoke &amp; Chung on 2008-03-03
> **888mafia said:**
> can you direct me to a how too please i just dont want to get in there and do the wrong thing ty

Hi,

I assume the 2 hard disks are already in your computer and one of them is already loaded with Windows XP. 

You have to identify which hard disk is the Windows XP residing, and disconnect the power or the SATA/ IDE cable to it. Double check and make sure you disconnect the correct one, if not, your Windows XP disk will be erased completely if you follow the process below.

Now, insert your Ubuntu Live CD, and go through the installation process, and make it to use the entire disk. 

After Ubuntu installation, connect all the cables that you have unplugged. Now you should be able to chose boot from either one, you gotta chose the hard disk to boot from BIOS. There is no grub menu in this case.

---

### Post by LowSky on 2008-03-03
i guess no one looked at my post..

DONT DISCONNECT THE OTHER DRIVE!!!

just go into BIOS and switch which drive is called the primary (make window the secondary)

do this and it wont mess up windows MBR

save yourself a headache later

---

### Post by zerhacke on 2008-03-03
AGAIN, DO NOT DiSCONNECT THE PRIMARY MASTER HARD DRIVE.  If you do so grub will not detect a windows partition present and will not build the menu.lst file accordingly.  You won't be able to boot into Windows if you do this.

Also, don't remap the boot order of the drives as it makes no sense to do so.  Ubuntu is perfectly capable of installing the grub bootloader on the primary master and still boot Ubuntu and Windows both.

---

### Post by Radioman991 on 2008-03-03
> **zerhacke said:**
> AGAIN, DO NOT DiSCONNECT THE PRIMARY MASTER HARD DRIVE.  If you do so grub will not detect a windows partition present and will not build the menu.lst file accordingly.  You won't be able to boot into Windows if you do this.

Also, don't remap the boot order of the drives as it makes no sense to do so.  Ubuntu is perfectly capable of installing the grub bootloader on the primary master and still boot Ubuntu and Windows both.

I am a noob but wholeheartedly agree.  I have 2 HDDs in my Dell Desktop.  GRUB lets me boot to either.  I even edited the menu.lst to default to XP...for the wife.

---

### Post by 888mafia on 2008-03-03
> **LowSky said:**
> i guess no one looked at my post..

DONT DISCONNECT THE OTHER DRIVE!!!

just go into BIOS and switch which drive is called the primary (make window the secondary)

do this and it wont mess up windows MBR

save yourself a headache later
now  im really con fused i ask you since you are the highest rated here is there a printable version

---

### Post by 888mafia on 2008-03-03
> **LowSky said:**
> i guess no one looked at my post..

DONT DISCONNECT THE OTHER DRIVE!!!

just go into BIOS and switch which drive is called the primary (make window the secondary)

do this and it wont mess up windows MBR

save yourself a headache later
now  im really con fused i ask you since you are the highest rated here is there a printable version

---

### Post by Duck2006 on 2008-03-03
> **zerhacke said:**
> AGAIN, DO NOT DiSCONNECT THE PRIMARY MASTER HARD DRIVE.  If you do so grub will not detect a windows partition present and will not build the menu.lst file accordingly.  You won't be able to boot into Windows if you do this.

Also, don't remap the boot order of the drives as it makes no sense to do so.  Ubuntu is perfectly capable of installing the grub bootloader on the primary master and still boot Ubuntu and Windows both.

Yes this is the way to do it.
May be this will help.

[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by bulmer247 on 2008-03-03
yes it is posible and good luck with the show

---

### Post by BobLand on 2008-03-03
888,
When your computer boots, you have the option of getting into the bios.  On my computer I hit F2.  On many computers it is the DEL key.  You have to hit the key before any splash screen or grub menu comes up.

If you don't see the prompt then keep hitting the DEL key.  If that doesn't work, try one of the F keys.  Eventually, you'll get into the bios.  Once you are there be careful about changing things.  Look for a tab that says something like "boot."  Under that tab there should be an option that lets you put all the drives in your system in an order designated by you.

I have Ubuntu on a SATA drive and XP on an IDE drive.  If I want to go to XP I change the order in the bios so the IDE drive boots first.  That way I get into  XP.  I do it this way because I don't want Windows anywhere near Ubuntu.

One could do this with grub but I don't even want the slightest mention of Windows on my Ubuntu drive so they are totally separate and independent. 

When the selected OS is shutdown/restarted, go into the bios again to change to back.

bobland

---

### Post by zerhacke on 2008-03-03
That's one giant PITA, Bob.  You gotta remember that the OP asked if it's even possible, so you can't assume they understand that much about computers to remember to change BIOS boot orders.

It's so much easier to let GRUB manage it for you.  Who gives two twinkies if GRUB mentions Windows... do you really spend that much time in GRUB?

---

### Post by James Haigh on 2008-03-04
As far as I'm aware, changing boot order and the master/slave setting of the HD is not the same thing.

After what's been said, I really do not want to disconnect my fixed HD. I want to install Ubuntu on an external USB HD leaving my fixed HD intact. I want it to be a bit like a live CD, Portable. The boot loader does not need links to OSs on my fixed HD but I don't mind extra links (like zerhacke). It does however, need to be completely independent of my laptop and fixed HD. Although it will mainly be booted from my laptop, I would like it to be able to boot from other machines.

I have tried 'Advanced' on step 7 of installer and changed install boot loader from (hd0) to (hd1). My fixed HD remained intact, good. GRUB was on my USB HD, good. But when I press enter (or timed out), I get error 17, cannot mount partition.

Thanks.

James.

---

### Post by 888mafia on 2008-03-04
ok im confused whos i think were talking about two seprate things ill start another post because i dont have external
i have 2 hardwired drives and i cant tell any more which computer were talking about

---

### Post by James Haigh on 2008-03-04
I'm sorry for confusing you. Maybe I should have started a new thread because this thread is about your problem. I just thought my problem was similar with HDs and boot-loaders, that's all.

Sorry.


Anyway, if this thread is no longer being used, can anyone answer my question?

---

### Post by 888mafia on 2008-03-05
Ok  heres where im at i have down loaded (ubuntu-7.10-server-i386) i have done a clean reinstall of xp
on my pc  i have cleaned the 2nd hard drive 40 gig available what is the first step

---

### Post by Duck2006 on 2008-03-05
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by 888mafia on 2008-03-05
I might be wrong but this link is for installing UB in XP i would like to install on the second hard drive if im wrong ill go back and read some more
thanks for answering

---

### Post by Duck2006 on 2008-03-06
Where it comes to partitioning just partition the second hard drive.

---

### Post by 888mafia on 2008-03-06
ok this has been solved installed now a whole new set of problems  HOW do i get it off

---

### Post by jken146 on 2008-03-06
I alreasy answered that in your other thread.

---

