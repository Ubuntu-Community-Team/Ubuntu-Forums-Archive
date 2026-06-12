---
title: "Trynig to install GRUB on a secondy HD"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by nick24 on 2007-02-28
Hi every body :) 

I will get to the point. I am trying installing Ubuntu 6.10 on an internal secondary HD. I want to install GRUB on the same HD not on the MBR. When I get to the installation process of Step 6 of 6 Ubuntu tells me GRUB will be installed to (hd0), What should I type instead in order to install GRUB on the secondary HD? Please help. I would like to thank a lot of people who tried to help me with this same issue last night. BTW the secondary hard drive in which I intend to install Ubuntu in set as a secondary HD. Thanks

---

### Post by mahy on 2007-02-28
I'm afraid you can't prevent Ubuntu from installing Grub to the MBR. But you can install it later wherever you wish; then remove it from MBR (for instance by means of Windows Recovery Console). Hope this helps you. Feel free to ask more questions.

---

### Post by nick24 on 2007-02-28
> **mahy said:**
> I'm afraid you can't prevent Ubuntu from installing Grub to the MBR. But you can install it later wherever you wish; then remove it from MBR (for instance by means of Windows Recovery Console). Hope this helps you. Feel free to ask more questions.

Thanks Mahy for your instant reply. 

Your idea seems great but I am afraid I need Windows installation CD to use Windows recovery system? or not ? I don't have that CD since I have the OEM version.

---

### Post by Duck2006 on 2007-02-28
On 6 of 6 tell the installer that your installing the grub loader to hd1 then it will install it to the secondary hard drive and not the first. You will have to change your BOIS to boot from the secondary hard drive to boot your system.

---

### Post by nick24 on 2007-02-28
> **Duck2006 said:**
> On 6 of 6 tell the installer that your installing the grub loader to hd1 then it will install it to the secondary hard drive and not the first. You will have to change your BOIS to boot from the secondary hard drive to boot your system.

Thanks Duck 
I tried that already .........it seemed logical to me too but after installation Ubuntu won't boot. Right now I am trying this instead (hd1,0)  I will let you know if it works.

---

### Post by Duck2006 on 2007-02-28
Do a 

fdisk -l

and post the output.

---

### Post by Milner_07 on 2007-02-28
i was wondering ,if i removed my windows HD during the install would grub not overwrite the MBR?

I could them put the widows one back and make it the normal boot disk and just select the second disk from the boot menu when i want to use Ubuntu. Would that work? It would be really useful as last time i tried Ubuntu i wrecked my MBR!! Also would resizing my second hard drives partition to make way for Ubuntu would it damage the stuff that's already there (all my docs, pics etc.)

TMhttp://ubuntuforums.org/images/smilies/icon_smile.gif
:)

---

### Post by hanzomon4 on 2007-02-28
If it's your 2nd drive first partition tell grub to install on (hd1,0) or /dev/hdb I think.

---

### Post by Duck2006 on 2007-02-28
Yes you could do it that way. Is the the secondary hard drive a ntfs or fat32?
Do a defrag on the drive befor you resize the hard drive.

---

### Post by nick24 on 2007-02-28
Hi there :) 

I just tried with (hd1,0) to on avail.l Its an an ongoing battle :)  I don't know what else to do anymore.

---

### Post by nick24 on 2007-02-28
And here is the output of fdisk 

ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1         784     6297448+  12  Compaq diagnostics
/dev/sda2   *         785       19929   153782212+   7  HPFS/NTFS

Disk /dev/sdb: 300.0 GB, 300090728448 bytes
255 heads, 63 sectors/track, 36483 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1       35727   286977096   83  Linux
/dev/sdb2           35728       36483     6072570    5  Extended
/dev/sdb5           35728       36483     6072538+  82  Linux swap / Solaris
ubuntu@ubuntu:~$

---

### Post by Milner_07 on 2007-02-28
My second drive is NTFS. With 91% free!

Defraging the drive wont make all the files at the front of the disk thoe will it? Is there a way to do that? Cause then i wont screw up my drive.

TM

---

### Post by OldTimeTech on 2007-02-28
Ubuntu doesn't read ntfs without help.  Go to [www.fs-driver.org](www.fs-driver.org)  this is a driver to help Ubuntu to read ntfs files.

---

### Post by mahy on 2007-02-28
> **nick24 said:**
> Hi there :) 

I just tried with (hd1,0) to on avail.l Its an an ongoing battle :)  I don't know what else to do anymore.

If everything else fails, try removing all other disks, install ubuntu with grub on the one you want, and then plug the disks back into their former positions.

Maybe if you tried to explain why you need such a layout, we'd be able to help you more.

---

### Post by mahy on 2007-02-28
> **OldTimeTech said:**
> Ubuntu doesn't read ntfs without help.  Go to [www.fs-driver.org](www.fs-driver.org)  this is a driver to help Ubuntu to read ntfs files.

That's simply wrong. Ubuntu needs no extra help to read ntfs and the page you suggested is about something VERY different. It's a software for windows to read ext2 filesystems!

---

### Post by Duck2006 on 2007-02-28
So your running sata's and not pata's so the hd1 i think sould be sd1.
From the live cd in the terminal run

sudo grub

at the grub prompt

find /boot/grub/stage1

it will come back with something like sd1,0 what it comes back is what you place in the next line

root (sd1,0)

setup (sd1)
quit

then reboot

---

### Post by Duck2006 on 2007-02-28
One other way round this may be to download this

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

and run it, it sould set things up for you or even boot from it to your linux and windoze

---

### Post by mackinax on 2007-02-28
here's what I do to get this working on my PCs, where hda= windows , hdb=ubuntu

*note: change for serial -vs- ide drives where appropriate*

1. make grub install to "hdb" {or "(1,0)"}
2. set BIOS to boot to second disk
3. when you first try to boot ubuntu, grub will give an error. 
... with the first boot option highlighted, press "E" key (for edit)
... next, down arrow to highlight the 2nd line (IIRC) and press "E" again
... edit the drive spec to **(0,0)** instead of **(1,0)** - and then press enter
... press "B" key to boot ~ and if your edit was correct, ubuntu should now boot up

4. after getting into ubuntu, enter into terminal:```
gksudo gedit /boot/grub/menu.lst
```
change line that says: ```
# groot=(hd1,0)
```
 to: ```
# groot=(hd0,0)
```
and change lines that say: ```
root		(hd1,0)
``` 
to: ```
root		(hd0,0)
```
and change windows boot section to this:
```
title		Windows <version>
root		(hd1,0)
savedefault
map		(hd0) (hd1)
map		(hd1) (hd0)
chainloader	+1
```

---

### Post by Milner_07 on 2007-02-28
So will the way i asked about work?

TM

---

### Post by Duck2006 on 2007-02-28
> Milner_07
i was wondering ,if i removed my windows HD during the install would grub not overwrite the MBR?

I could them put the widows one back and make it the normal boot disk and just select the second disk from the boot menu when i want to use Ubuntu. Would that work? It would be really useful as last time i tried Ubuntu i wrecked my MBR!! Also would resizing my second hard drives partition to make way for Ubuntu would it damage the stuff that's already there (all my docs, pics etc.)


Yes with just the second hard drive in you can install ubuntu to it and then later add the windoze drive back and make a boot it boot it.

---

### Post by nick24 on 2007-02-28
Thank you very much every body for your help I really mean it.

I will try all the methods one by one and see what happens. Mahy I wanted this arrangement so to keep my Linux and windows COMPLETELY separate. I don't trust the integrity of Windows  
plus I don't have the installation CD for Windows if something goes wrong. Thanks again

---

### Post by Duck2006 on 2007-02-28
> plus I don't have the installation CD for Windows if something goes wrong.

Then you sould look at downloading one of these cd's so you can repair your mbr if something sould go wrong

[http://www.ultimatebootcd.com/](http://www.ultimatebootcd.com/)

[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)

---

### Post by dannyboy79 on 2007-02-28
> **Duck2006 said:**
> So your running sata's and not pata's so the hd1 i think sould be sd1.
From the live cd in the terminal run

sudo grub

at the grub prompt

find /boot/grub/stage1

it will come back with something like sd1,0 what it comes back is what you place in the next line

root (sd1,0)

setup (sd1)
quit

then reboot


no, incorrect. Grub doesn't see the drive as "sd" anything, (that's only inside Ubuntu) it's always hd, meaning hard drive. what does your /boot/grub/device.map file show? 

Also, to whoever said that Ubuntu or grub screwed up their mbr, Ubuntu most likely didn't screw up your mbr, you did, when you told it to install grub to it. so then when you wanted to boot to your hard drive, there was no more normal windows mbr which would point to ntldr and ntdetect.com. so all you had to do was use your windows xp cd, boot to the recovery console and type in fixmbr and your mbr would have been back to normal.

NOTE:   Just so people know, when you take out hard drives, then install grub, then put the hard drive back is about the hardest way to install multiple os's and grub. you need to just leave your drives in there and go for it. Of course there is always a slight chance that your data can get lost but that's why you back your important files first.

---

### Post by Duck2006 on 2007-02-28
Thanks dannyboy79 i wasn't sure as to how ubuntu looks at sata drives i don't have them i use pata and ide drives in my system.

---

### Post by kittyhawk63 on 2007-02-28
Still open for suggestions from noobies?

I disconnected my HDD that had Windows XP on it. I set the jumpers on the HDD with Linux to Master. I installed GRUB on that HDD. I set the Windows HDD as Slave. I reconnected the HDD with Windows. At bootup , I get GRUB and am given a choice of what OS I want to start.

Just another suggestion.

kh

---

### Post by nick24 on 2007-02-28
Thanks everybody for your advise. 

Well I went ahead and unplugged my primary HD and installed Ubuntu on my secondary HD (thanks Mahy for the tip).  Everything seems to work , right now I am updating Ubuntu. After I hook my  other HD back up I hope everything works :).  I will update you guys on the outcome. Thanks again

---

### Post by kittyhawk63 on 2007-02-28
> **mahy said:**
> If everything else fails, try removing all other disks, install ubuntu with grub on the one you want, and then plug the disks back into their former positions.
Maybe if you tried to explain why you need such a layout, we'd be able to help you more.

Mahy, looks like I gave the same advise. You beat me to it. Way to go. I didn't read all the replies and that is the reason that I made my post. :)

kh

---

### Post by dannyboy79 on 2007-02-28
> **kittyhawk63 said:**
> Still open for suggestions from noobies?

I disconnected my HDD that had Windows XP on it. I set the jumpers on the HDD with Linux to Master. I installed GRUB on that HDD. I set the Windows HDD as Slave. I reconnected the HDD with Windows. At bootup , I get GRUB and am given a choice of what OS I want to start.

Just another suggestion.

kh

You seemed to have left out some critical information!!!!

Yeah this will only happen IF you had your windows drive installed during the Ubuntu installation as grub would have seen your windows install and added windows to your menu.lst file. And if this was the case, you didn't need to rearrange your hard drives which actually can cause even more damage as Ubuntu labels disks according to their position on the ide channel. All you would have had to do was go into your bios and set the ubuntu hard drive to boot instead of the windows one.

OR

if you added your windows drive as a slave after the fact, then you would have had to go into your menu.lst and add an entry for your windows xp hard drive. this get messy as well because you have to update your device.map file etc etc.

**The easiest way to do this is to leave your winxp drive in the system during the install process!!!!! Grub will only overwrite your mbr, not your data!!!!**

---

### Post by kittyhawk63 on 2007-02-28
> **dannyboy79 said:**
> You seemed to have left out some critical information!!!!

Yeah this will only happen IF you had your windows drive installed during the Ubuntu installation as grub would have seen your windows install and added windows to your menu.lst file. And if this was the case, you didn't need to rearrange your hard drives which actually can cause even more damage as Ubuntu labels disks according to their position on the ide channel. All you would have had to do was go into your bios and set the ubuntu hard drive to boot instead of the windows one.

OR

if you added your windows drive as a slave after the fact, then you would have had to go into your menu.lst and add an entry for your windows xp hard drive. this get messy as well because you have to update your device.map file etc etc.

**The easiest way to do this is to leave your winxp drive in the system during the install process!!!!! Grub will only overwrite your mbr, not your data!!!!**



I didn't have to do any of that. I did it just exactly as I stated it. It worked for me. It might not work for others.
kh

---

### Post by Milner_07 on 2007-02-28
> **dannyboy79 said:**
> no, incorrect. Grub doesn't see the drive as "sd" anything, (that's only inside Ubuntu) it's always hd, meaning hard drive. what does your /boot/grub/device.map file show? 

Also, to whoever said that Ubuntu or grub screwed up their mbr, Ubuntu most likely didn't screw up your mbr, you did, when you told it to install grub to it. so then when you wanted to boot to your hard drive, there was no more normal windows mbr which would point to ntldr and ntdetect.com. so all you had to do was use your windows xp cd, boot to the recovery console and type in fixmbr and your mbr would have been back to normal.

NOTE:   Just so people know, when you take out hard drives, then install grub, then put the hard drive back is about the hardest way to install multiple os's and grub. you need to just leave your drives in there and go for it. Of course there is always a slight chance that your data can get lost but that's why you back your important files first.

i know you can us your windows CD but i didn't know my admin password! Stupid i know but ive learnt from that and know i know what it is.


So if i leave my disk in what drive would i need to select for grub to be installed in the correct place to boot Ubuntu off my second hard drive(ide) and Windows off my primary hard drive (Sata)? i guess its some thing like Hda or something?

TM

---

### Post by nick24 on 2007-02-28
Okay I finally get it to work - I wouldn't have done it with out this great forum - YOU GUYS 
Thankyou very much. After plugging my hard drive back up I fire my machine up. Ubuntu panicked for a little bit only because I forgot to set the disk (Which I installed Ubuntu to) as a primary disk. Once I corrected that problem everything is working. Now I have XP MCE and Ubuntu 6.10 on a separate disk plus NTLDR and GRUB are in their respective disks also. Thakns again. Well one more thing - Windows complained about finding a new Hard Drive :lolflag:

---

### Post by Milner_07 on 2007-02-28
dose this mean that grub dose not recognise XP? Do you have to go in to BIOS to boot Xp?
Or dose it right over your MBR any way when the disk is plugged back in?
TM

---

### Post by nick24 on 2007-02-28
> **Milner_07 said:**
> dose this mean that grub dose not recognise XP? Do you have to go in to BIOS to boot Xp?
Or dose it right over your MBR any way when the disk is plugged back in?
TM

Yes that is correct. With this layout GRUB does not recognise XP, so I would have to go to BIOS to boot XP, which I dont mind doing ,since I barely use Windows anymore. To answer your second question GRUB does not write itself in the MBR when I reconnected my HD back up.

---

### Post by Milner_07 on 2007-02-28
Excellent that's just what i want it to do!
Now a question for every one if i set the boot menu to boot the windows disk (that will then be the slave i guess) will it do that so i don't need to fuss about to load windows?

TM

---

### Post by confused57 on 2007-02-28
> **Milner_07 said:**
> Excellent that's just what i want it to do!
Now a question for every one if i set the boot menu to boot the windows disk (that will then be the slave i guess) will it do that so i don't need to fuss about to load windows?

TM
This guide may help explain how I have 2 pc's set up:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by nick24 on 2007-02-28
> **Milner_07 said:**
> Excellent that's just what i want it to do!
Now a question for every one if i set the boot menu to boot the windows disk (that will then be the slave i guess) will it do that so i don't need to fuss about to load windows?

TM

Yes you could boot in to windows with no problem Milner. I just booted in to windows , then ubuntu then windows .......well you get the picture :) just to test it and it worked fine. Sorry for the delay.

---

### Post by Milner_07 on 2007-02-28
Great ill do this tommorow.(i would do it know but im backing up the files on the hard drive i want to instal Ubuntu on)

Thanks nick!!

TM

---

### Post by dannyboy79 on 2007-02-28
> **kittyhawk63 said:**
> I didn't have to do any of that. I did it just exactly as I stated it. It worked for me. It might not work for others.
kh


well there is something you are leaving out, that's impossible for anyone regardless of what hardware or whatever, there is absolutely no way that grub would no that you have a hard drive not connected to the computer and for grub to jsut automatically add a boot line for your os that's on a hard drive that isn't even connected to your computer! Sorry, it's impossible and for you to inform people that that would work for you and possibly not others is just outragious, it's impossible!!! You had to have done a grub-update or some other step that you're forgetting. If you're saying that you only had one hard disk attached to your computer, set as the master, at the time you installed grub, and then attached another hard drive AFTER grub was finished installing, you can't simply boot your master hard drive and expect grub to have 2 choices, it just won't do it, that's impossible!!!! Now you may have choices for other kernels, and maybe a memtest but no other os, not unless you update the menu.lst manually or do a grub-update. You can keep saying that you did it but I want everyone and all newbies especially **THAT IT'S IMPOSSIBLE ** based on the information that you have provided.

---

### Post by dannyboy79 on 2007-02-28
> **nick24 said:**
> Yes that is correct. With this layout GRUB does not recognise XP, so I would have to go to BIOS to boot XP, which I dont mind doing ,since I barely use Windows anymore. To answer your second question GRUB does not write itself in the MBR when I reconnected my HD back up.

WOW, please don't hand out incorrect information!!! If you don't know, don't make anything up or don't just say what you experienced and if you do, inform the other person, that that is your experience only and not based on fact! Grub can to recognize a windows xp install!!!! You can chain load it thru grub! If you want my help, I need to know what hard drives are in your system, what hard drive is being booted from the bios, what your /boot/grub/menu.lst looks like as well as your /boot/grub/device.map. You can install grub onto your mbr of your windows disk or you can install on your mbr of your ubuntu disk. whereever you install grub, that's the disk you will want to boot from in the bios, that's when grub starts, then what it does is it looks for it's config files, which is menu.lst which makes a little menu be displayed for your different os's to boot to. Even if and when you mess up a windows mbr, you can fix it using a win98 boot disk or a winxp cd in the repair console. I would be happy to help, just ask but it appears that people keep giving false information which is really bad for newbie cause they think that they are getting help from people and it still doesn't work, then they just go back to winbloz!!! that's bad for linux! good luck

---

