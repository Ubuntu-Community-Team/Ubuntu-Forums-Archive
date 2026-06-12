---
title: "Help me uninstall Ubuntu"
date: 2007-04-09
forum: Absolute Beginner Talk
---

### Post by xthund3rh3adx on 2007-04-09
i need to uninstall Ubuntu. i do not want to get into why, i just need to :(. 

i have GRUB installed, also.

i dual boot Windows XP and Ubuntu. XP is on my main 200GB Hard Drive. Ubuntu is on a second 7GB Hard Drive.

I need to know how to uninstall ubuntu and GRUB, but keep XP. 

I need XP to boot up on start up without GRUB, like it did before i installed Ubuntu. 


Any suggestions?

---

### Post by dhughes on 2007-04-09
Well you could use Gparted or I guess Windows to wipe the data and the partitions Ubuntu created.

 The big problem would be to repair the MBR (Master Boor Record) of your hard drive Windows boots from, you need to put the Windows bootloader back there once GRUB is gone. I believe you'll need to boot using your Windows install CD, choose Repair to get to a command prompt and then type the command C:/FIXMBR

 Search the forums here for FIXMBR or restore MBR to see a better explanation than I gave, the more info the better just in case I'm not 100% correct.

---

### Post by taurus on 2007-04-09
Boot your machine with XP CD and remove GRUB from MBR with fixmbr from the CD.  Then, use Ubuntu LiveCD to delete Ubuntu partitions.

---

### Post by divague on 2007-04-09
boot from the windows cd, and it will come to a screen with options, select the recovery console (or something like that) and then put fixmbr, this should remove grub

---

### Post by xthund3rh3adx on 2007-04-09
ok thank you. once i uninstall GRUB, then Windows will boot automatically right?

---

### Post by taurus on 2007-04-09
Yip.

---

### Post by divague on 2007-04-09
that's right

---

### Post by xthund3rh3adx on 2007-04-09
ok. do once GRUB is removed, then ubuntu will automatically be gone, or will it still be there? how would i get rid of it?

its not on a partion, instead its on a 7GB HD

---

### Post by taurus on 2007-04-09
You only remove GRUB, not Ubuntu itself.  Therefore, you need to either remove the partitions or format that harddrive if you want to remove Ubuntu.

---

### Post by xthund3rh3adx on 2007-04-09
maybe i can keep grub, but reformat and get rid of  ubuntu insteaD?

oh....but then i cannot edit the GRUB menu...right?

---

### Post by Catsworth on 2007-04-09
Once you're back into your Windows install, use Windows to reformat that 7GB HDD to something like FAT32 or NTFS - that should overwrite (and therefore 'remove') Ubuntu.

---

### Post by oilchangeguy on 2007-04-09
grub is the bootloader nothing more. so if that's gone, ubuntu will still be there.

---

### Post by taurus on 2007-04-09
If you remove Ubuntu, GRUB is DEAD as well since it can't find /boot/grub/menu.lst because there is none now.  So, if you don't want Ubuntu on your machine anymore, you must remove GRUB also.

---

### Post by xthund3rh3adx on 2007-04-09
ok thank you. i understand now.

so what i have to do is...


1.) Remove GRUB via the Windows XP Set-up Disc>Recover>goes into a command prompt, then type C:/FIXMBR

2.) Windows will boot automatically w/o GRUB

3.) Remove Ubuntu by reformating the 7GB drive to NTFS

is that all? :)?

---

### Post by xthund3rh3adx on 2007-04-09
i need a confirmation, please! i need one so that i know i will not screw something up. this is very very crucial. thanks!

---

### Post by CJay554 on 2007-04-09
yeah dude thats how u do it..
u take out grub first by fixing windows by using the cd to install the original boot files
so that when u restart the comp it boots somewhere,
if u were to take out ubuntu first my guess is that ur comp will freeze for it needs the directory stated earlier to boot... something /boot/menu/etc,
too lazy to go back and see it
so u repair windows
reboot
it should log u in WINDOWS 
should not even display GRUB,
then use a Partition manager or such to pretty much erase what is there, thats all
if u do screw it up u can just reinstall windows :/
if ur so worried about it backup your data.

---

### Post by xthund3rh3adx on 2007-04-09
ok man, thanks a lot. im gonna try it see waht happens

---

### Post by Matt1632 on 2007-04-09
You can use the partition editor in the Ubuntu live-cd to reformat the drive to NTFS.

---

### Post by xthund3rh3adx on 2007-04-09
thanks a lot guys. 

i used my WinXP set up disc to get rid of GRUB, so that is gone.

Now, all i need to do is reformat it to NTFS, which Matt1632 told me how.

thanks guys, and just for the record, im not getting rid of Ubuntu altogether, i absolutly lvoe it. i just needed to get it off this perticular computer. i still have it on my MacBook Pro.
:)

---

