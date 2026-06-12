---
title: "dual boot fails"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by eldar on 2007-04-21
Well I tried what I wanted and it did not work. I put a ntfs, ext3,swap, and fat32 on a drive.  XP first, then ubuntu. Well I get the grub loader as I understand i should. When I try to boot xp, it fails but feisty works. Now I did some looking around and it appears that the ubuntu install wipes out the master boot record for XP.  

So I really dont want to have to do everything all over again so would I be correct in my assumption that if I can get into the windows disk, I can repair the MBR and XP should boot forth as it is supposed to?  

I ask this cause I had parted the disk before hand and xp wanted to just do its own thing. So obviously XP needs to go on first. I would assume.

---

### Post by BoneKracker on 2007-04-21
Yes, it's best to put XP on first, because of limitations in its boot loader.

Please post the contents of:  /boot/grub/menu.lst
and the contents of /etc/fstab

---

### Post by jiminycricket on 2007-04-21
Yes you can just do fixmbr and it will be fine.

But, maybe grub is pointing at the wrong hard drive for the xp boot?  What error do you get?  The grub menu is in /boot/grub/menu.1st

---

### Post by BoneKracker on 2007-04-21
just so nobody gets hosed while cutting-and-pasting...

[INDENT]it's /boot/grub/menu.lst (as in "menu list")
not /boot/grub/menu.1st (as in "menu first")[/INDENT]

[Edit]: and what he means is "if you want to restore the MBR to the way Windows had it, you can do "fixmbr" from within the Windows install CD's "recovery console".  However, then you will only be able to boot Windows.

---

### Post by lingnoi on 2007-04-21
To get no problems with a dual boot setup the best method is to install XP with however much of a partition you want to give it **first**. Then install Ubuntu on the rest of the disk **second**. Ubuntu will automatically setup the dual boot for you.

You don't need windows master boot record to boot into windows you can use grub. This is all automatically setup by Ubuntu as long as you don't try to install with some weird partitioning (IE. XP on the second partition, etc).

---

### Post by eldar on 2007-04-22
Well it is all on one disk. It is a 200gb drive. I installed xp on about an 85gb part. XP booted fine then.
Then I used gparted and made a fat32, exts and swap parts. I never went and tested xp after that.  Went and installed feisty which proceeded to boot fine. Well after that, I tried xp and again and got a blue screen with an error  "unmountable boot drive" or something pretty close to that. Ubuntu still booted fine though and grub showed xp under its list of other operating systems.  

Read that grub sometimes has issues and so I tried to reinstall it. No good.  still no xp.  Went and did fixmbr from the recovery console and now xp still delivers the same error and I dont get grub anymore at all. So I cant get into feisty at all now. 

Should I wipe everything out and load windows normally and then just load feisty normally and not worry about all the parts? I would like to be able to access music and pic files from both systems.

I am learning but with 2 jobs and 2 little kids, free time is pretty valuable and I dont want to spend ALL of it working on a computer.

---

### Post by BoneKracker on 2007-04-22
It sounds to me like you did things correctly but there was some kind of problem with the Windows install, possibly one that you created when you were making partitions with Gparted prior to installing ubuntu.

Do it again.

Install Windows.  Boot.  Windows should boot.

Install Ubuntu.  Make your partitions at this time, using the partitioning tool in the installer.

Boot.  You should get the GRUB menu.  Load Ubuntu.

Reboot.  At the GRUB menu select Windows; it should boot.

---

### Post by redgilda on 2007-04-22
Well I decided to try the new Ubuntu (while having Windows XP installed long time ago). Wanted to have the dual boot. I started the installation, created partitions bla bla, went to the kitchen, when I came back it said installation is complete so I restarted the pc but then it went straight to Windows without loading Grub. Does it mean that the Grub did not install at all? Someone mentioned somewhere (maybe in another thread< i read many already) that sometimes Bios doesnt allow any changes in the MBR or something.. where could I check that? I'll probably just try to (re)-install Grub from the live cd but well... I thought it was weird... but well - at least Windows works ;-)

---

### Post by eldar on 2007-04-22
Well I tried to wipe averything and put windows on first. I once again was able to boot into windows. So I put in the feisty disk and set up the parts I wanted. I put in the ext3,fat32, then the swap last. In THAT order. and proceeded to install feisty.
Well windows blues screens again. I got a ntos kernal error once then after that it just tells me to run chkdsk which I am unable to do since I cant even boot into safemode with command prompt.  Should I have done the parts different as in order? Should it be windows, then fat32 then swap and finally ext3?

---

