---
title: "Urgent - Grub"
date: 2007-02-13
forum: Absolute Beginner Talk
---

### Post by KAL9000 on 2007-02-13
I need to know quite quickly where grub installs itself when youinstall Ubuntu. I have a duel boot system and to beable to use linux better I need to shift files around and convert my file systems. 

I need the 40GB drive that Linux is installed on (I intend to reinstall anyway) but I know from the past if Grub is on there then it will mess up like hell and wont boot anything when bits of it are missing. 

So how do am I able to check so I can format the Linux drive and NOT mess up how XP boots?

is there anyway I can edit the XP MBR so It can bypass Grub when the drive is formated?

---

### Post by dannyboy79 on 2007-02-13
it overwrites the mbr of the drive you installed it on by default. you could have used the alt. install cd to install grub in the first partition instead but if you used the default I am pretty sure it overwrote your mbr. the location is in /boot/grub/. i am kind of confussed on what all you are saying and asking to be honest. i hope I have helped though.

---

### Post by KAL9000 on 2007-02-13
Well I am going to reinstall Ubuntu. clean start (why not :P)

but what I am also doing is moving lots of data around. to speed it up (immoving tens of GB) a streght drive to drive is ALOT quicker then partiton topartition on the same drive.

So what I want to know is how to edit my windows MBR back to normal so that when I format the drive with grub on it will boot windows normaly.

---

### Post by haricharan on 2007-02-13
well your question is still unclear..sorry i couldnt understand it...The grub replaces the MBR(Master Boot Record)....which has both the linux and windows entries in it......you can use FIXBOOT in windows recovery to get back to windows...however if you are planning to reinstall Ubuntu...nothing to worry as it would add your Windows partition to grub menu as well.....

---

### Post by dannyboy79 on 2007-02-13
If your Windows is Win XP and you have either WinXP install disk or a Win98 install disk you're OK. If you don't have a disk then have a friend bring one of either 98 or XP over (Always observe licensing requirements). If you use the 98-type disk, just use the fdisk/mbr routine shown above. If you use the XP disk then boot off the install disk and select Recovery. when you get the prompt select the XP installation (probably C drive), enter "fixmbr" and when it comes back to the prompt enter "exit", reboot etc. This should restore access to Windows. You can reboot without the install disk to test Windows. You won't see the Grub or Lilo menu because you have just cleaned it out of the master boot record.

---

### Post by confused57 on 2007-02-13
Here's how to restore your Windows mbr:
[http://www.users.bigpond.net.au/hermanzone/p18.htm](http://www.users.bigpond.net.au/hermanzone/p18.htm)

If you want to reinstall Ubuntu & not install grub to your Windows mbr:
[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

The Super Grub Disk can also restore a Windows mbr:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by KAL9000 on 2007-02-13
Basicly I will be wanting to just ripout the Linux partition to temp use the disk space.

Now when I do this cos grub modified the old MBR and grub is on the drive i will be formating  windows will become unbootable. how do I resolve this.

---

### Post by dannyboy79 on 2007-02-13
you not giving us really info that is useful, how may hard drives arre you using, what is the order in which they are listed in the bios, did you install grub onto the mbr of the drive that contains windows? all these questions need to be answered. but from the sound of it, you're fretting over nothing as it sounds like you have more than one hard drive since you are talking about formating a drive per this statement, "grub is on the drive i will be formating" so really you have nothing to worry about if you are simply taking this drive that used to have grub and ubuntu on it and want to format it so that you can use it for space temporarily. now if you're talking about 1 hard drive and different partitions than yes, you'll need to follow the info I posted earlier about booting to a winxp cd, going into the recovery console, and do what I posted BUT before you do that, see if windows will boot by itself first, if it does, than you have been freeting over nothing.

---

### Post by KAL9000 on 2007-02-13
Well the problem I foresaw was listed or commented on in one of the links you gave.

that is : 
When the BOIS looks in the bootable partition (hda0) it sees the "link" to look in hdb1 for grub.
now if I format hdb1 and try to boot theres no grub in hdb1 anymore and gives (apparently) a "grub error 22"
so you have to repair hda0 (the boot sector or MBR) to point correctly to NTLDR again or windows cant boot.

I have from the links provided secured against this (wich has happend to me before)
so thanks for those. also the grub CD thing looks and sounds very useful. 

im almost done throwing data around. and now due to all the useage it will fail in 3 hours so it was all pointless!
:lolflag: 
wouldnt that be ironic. in the act of trying to save data i loose the whole disk. hopefuly not!!

looks like ill be sorted from here tho. Just need to get the clean install of Ubuntu on soon and then I will have the system fully set to where I need it to be. 

Next step will be to mount the new vfat partitions with all my stuff on into my home folder perminantly...no doubt I will be looking on here again for that.

(I think Ive learned more about the core software on a PC in the 3-4 days I've had ubuntu  then i have in the 6-7 years ive used "Micro$haft Winblow$ (TM)" :P)

thanks for all the help so far guys. and being patient :)

---

