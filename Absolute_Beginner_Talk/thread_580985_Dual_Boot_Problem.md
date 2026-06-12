---
title: "Dual Boot Problem"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by Chuffer on 2007-10-19
Ok, used Partition Magic 8 in Xp to make a 2Gb Linux Swap partition, then I made a 30Gb Linux ext2 partition. This was all on the same HDD with Xp which has 160 Gb. Next I set the Linux partition active and rebooted, set my BIOS to boot from the Ubuntu 7.04 cd and away it went. Installed with no problems. Played around with Ubuntu but never changed anything and decided to boot into Xp but all I get after selecting Xp at the boot up screen is another screen that comes up saying that Autochk  failed, then in less time than it takes to blink another screen flashes up and it reboots, from there it just goes around in circles trying to boot Xp. I can access Linux which is why I'm managing to get onto this forum. I've tried booting Xp into Safe Mode but it's coming up with the same error. Can anyone help me get Xp booting?

:confused:

Chuffer

---

### Post by skymera on 2007-10-19
i dont know what youve done exactly.

but all you should do in windows is esize windows.

nothing more,
perhaps try the microsoft website?

this is more ofa windows problem thn ubuntu

sorry couldnt help more, i chjeck ms webste

---

### Post by Chuffer on 2007-10-19
Ok quick update, rebooted after my initial post and managed to pause the screen after autochk had come up, the second error screen was only there briefly but from the part I managed to read before it rebooted was to do with Session Manager. I hope this is of some help.

Chuffer

---

### Post by Chuffer on 2007-10-19
> **skymera said:**
> i dont know what youve done exactly.

but all you should do in windows is esize windows.

nothing more,
perhaps try the microsoft website?

this is more ofa windows problem thn ubuntu

sorry couldnt help more, i chjeck ms webste

I wasn't aware that the Ubuntu cd was going to offer to partition the HDD hence the reason I used Partition Magic 8

Chuffer

---

### Post by TeaSwigger on 2007-10-19
Hello Chuffer and welcome,

This may not be the best advice, but I offer the thought. It sounds like using Partition Magic has thrown us some complications. As you are already unable to boot into XP, I can only suggest that you attempt a reinstall of ubuntu. That may sound strange but the resoning is this: 

Windows has a component in the MBR of the hard drive related to booting. Perhaps something has either written in the XP partition or the MBR or corrupted data. Could be an error Partition Magic made, a consequence of the way Partition Magic works or a mistake in choice during ubuntu install, but whatever it be. If something has corrupted the XP parition, it's possibly a goner, but if not perhaps whatever Partition Magic did can be "overwritten."

Because Microsoft naturally does not give you the choice to install anything else, ubuntu must install its own means to boot both itself and XP (called GRUB). When you use ubuntu's provided partitioner upon install, it offers to install GRUB in the MBR. Perhaps Partition Magic also did something in there. Did you chose this option or recall where you installed GRUB? Any case, you can opt for this in the ubuntu install process. Suggest you may as well. Go through with the rest of the ubuntu install and then try booting into XP. 

If no joy, then you can still recover all your data from the XP partition through ubuntu, as ubuntu now offers read and write support for NTFS (XP's file system). After saving your data, reinstall XP, then ubuntu, all without involving Partition Magic. I'm sorry I don't know more to suggest, and appologize if I'm not making a load of sense, as it is absurdly late here and I must be off to bed!

Ubuntu is a beautiful system, I hope it will work out for you :)

---

### Post by Tyke91 on 2007-10-19
NO! don't reinstall ubuntu yet!

i've had this problem as well on two computers, all that is needed is a boot into windowze recovery console via their install CD. then when you are in the console, type the command 

```
CHKDSK
```


It does have to do with windows thinking the MBR settings are corrupt, but it can fix those its self without resorting to a reinstall... W1ndows CHKDSK also has no effect on the way ubuntu works, so all in all... only try a reinstall after you have exhausted all other available options :)

---

### Post by Chuffer on 2007-10-19
> **Tyke91 said:**
> NO! don't reinstall ubuntu yet!

i've had this problem as well on two computers, all that is needed is a boot into windowze recovery console via their install CD. then when you are in the console, type the command 

```
CHKDSK
```


It does have to do with windows thinking the MBR settings are corrupt, but it can fix those its self without resorting to a reinstall... W1ndows CHKDSK also has no effect on the way ubuntu works, so all in all... only try a reinstall after you have exhausted all other available options :)

I've already tried the chkdsk option, it came up saying something about unrecoverable errors or similar, can't quite remember. Should I try FixMBR or one of the other options? Or just try a reinstall of Xp or Linux?

Chuffer

---

### Post by Chuffer on 2007-10-19
Ok now sorted the problem. Downloaded this rescue cd: [http://www.sysresccd.org/Main_Page](http://www.sysresccd.org/Main_Page) and booted it up, used the startx gui and ran gpart and managed to switch the boot flag from the Ubuntu partition to the Xp one, I've now got Xp back but I've lost Ubuntu. So I'm going to delete the Linux partitions and merge all the free space, then reload the Live CD and install using the built in Linux partition software.

:guitar:

Chuffer

---

