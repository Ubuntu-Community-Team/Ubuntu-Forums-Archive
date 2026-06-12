---
title: "Adding 2nd HDD for Dual Boot"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by JNasci7906 on 2006-05-30
ok, sorry if this is a double post, but ive searched and i cant find anything that helps in my adventure. My question is as follows: next week I'm going to get a 2nd hard drive for my machine, i currently have an 80 gig thats formatted entirely for linux, i did NO partitions when i set up breezy badger. Is it possible to add a 2nd HDD, format it for windows, and install XP on the 2nd drive so i can play my games without messing with wine (too difficult for me to understand and get working correctly). Also, after installing XP onto that HDD will i be able to easily select which HDD to boot from at inital boot?

Thanks for your help all

Nash

---

### Post by Stew2 on 2006-05-30
Not too sure how this works with Ubuntu installed first, but I had a similiar setup with windows installed on one drive and ubuntu on another. It was very easy to set up but I had windows installed first. Grub is very intuitive at detecting other operating systems, and will set up the bootloader for windows and ubuntu. This gives you a menu at boot up that defaults to ubuntu but lets you select windows if you so desire. Some one with more knowledge than me probably knows how to install windows after ubuntu, I would personally install windows first and then reinstall ubuntu and let grub set up the dual boot for you. As I said though, I'm definitely not an expert on this and someone else probably knows exactly how to add windows afterwards. Just thought I would post to let you know how I had it set up. Hope this helps. 

Regards,
Stew2

---

### Post by catlett on 2006-05-30
This is a little tricky but not impossible. The issue is Windows won't recognise or boot to Linux. It will overwrite the MBR with windows bootloader and you will not have an option for linux at boot. What you can do is this.
Remove the linux drive (or just unplug the cable) Put your new hard drive in as the master and run the xp install. Let XP do everything it wants, including the mbr.
Now put your linux drive in as the master and make the windows drive as slave.
When you boot up grub will only have linux and no windows, but we can put an entry in grub for windows.
Open the terminal and enter```
 sudo gedit /boot/grub/menu.lst
``` This is your grub menu. Hit enter a couple of times to make a space between the last line of text and this entry. Enter this 
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

This entry is used when windows is the slave to a linux master. Windows likes to be on the first partition of the first hard drive. This mapping will "trick" the windows install into thinking it is the master on the first drive.  Save the entry by hitting "save" at the top of the gedit window. Reboot your computer and you will see the windows entry. Choose the entry and grub will send you to windows.
Just make sure your jumper settings are right when you switch evrything around. Google for the settings or go to the web site of the drive maker and they will have a diagram.
To recap. Unplug/rermove linux drive. Put new drive in and run XP install. Choose all the defaults. Let windows do what it wants. Move the windows drive to slave and put the linux drive in as master. Boot into linux and change your grub menu. Reboot to your new grub menu.:-D  Post if you have any questions or problems.

---

### Post by JNasci7906 on 2006-05-30
hey thanks i really appreciate the help, easy to follow post and everything a noob needs. Thanks Again!!!!!!!!:D :D :D :D :D :D 


Nash

---

### Post by Stew2 on 2006-05-30
[QUOTE=catlett]This is a little tricky but not impossible. The issue is Windows won't recognise or boot to Linux. It will overwrite the MBR with windows bootloader and you will not have an option for linux at boot. What you can do is this.
Remove the linux partition (or just unplug the cable) Put your new hard drive in as the master and run the xp install. Let XP do everything it wants, including the mbr.
Now put your linux drive in as the master and make the windows drive as slave.
When you boot up grub will only have linux and no windows, but we can put an entry in grub for windows.
Open the terminal and enter```
 sudo gedit /boot/grub/menu.lst
``` This is your grub menu. Hit enter a couple of times to make a space between the last line of text and this entry. Enter this 
```
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1
```

This entry is used when windows is the slave to a linux master. Windows likes to be on the first partition of the first hard drive. This mapping will "trick" the windows install into thinking it is the master on the first drive.  Save the entry by hitting "save" at the top of the gedit window. Reboot your computer and you will see the windows entry. Choose the entry and grub will send you to windows.
Just make sure your jumper settings are right when you switch evrything around. Google for the settings or go to the web site of the drive maker and they will have a diagram.
To recap. Unplug/rermove linux drive. Put new drive in and run XP install. Choose all the defaults. Let windows do what it wants. Move the windows drive to slave and put the linux drive in as master. Boot into linux and change your grub menu. Reboot to your new grub menu.:-D  Post if you have any questions or problems.[/QUOTE]

Ummm... what he said :D See? I told you someone else would know how to do it! Catlett's method sounds good to me, and you can usually find the master/slave HDD jumper settings on a label on the drive itself. :)

---

### Post by sir_cheats_a_lot on 2006-05-30
hmm...that is a good one.  I assume they would both be 80Gb.
here is how i did it:
   i have a 160Gb and a 20Gb hard drive. on the 160 i had windows xp pro. i took out the 160Gb drive plugged in the 20Gb(on the slave plug of the primary IDE ribbon(the one towards the middle of the one the original Harddrive is attatched to)  and installed Ubuntu on it, then i plugged the 160Gb back into the primary IDE ribbon. 
Also i'm sure i had also gone into BIOS and changed boot priority to boot from the second (ubuntu )Drive first.

I imagine you could do this in much the same way.  if you don't mind changing your Ubuntu drive as a slave(or the cable select setting, this should be the default setting if you bought the PC, instead of building it yourself...at least this was the case with my old HP).   once you have the bios settings changed and you boot your PC grub should detect your Windows install and should list it on its menu.  you shouldn't have to edit the menus.lst file for it to work this way.  

   Good luck!

---

### Post by confused57 on 2006-05-31
Here's how I have my system set up:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)

---

### Post by catlett on 2006-06-01
[QUOTE=confused57]Here's how I have my system set up:

[http://www.ubuntuforums.org/showthread.php?t=179902](http://www.ubuntuforums.org/showthread.php?t=179902)[/QUOTE]
When did you make that how to thread? Nice job, I'll have to post the link in replies to threads about configuring dual boots with sata, a 2nd hard drive and even dual boot without touching windows mbr.
I was thinking about putting together a grub floppy how to from the link you got me before but my floppy wasn't configured ( a had to edit /etc.fstab myself) so I don't know if everyone's floppy will mount like mine. I simplified the process but I don't know if my floppy commands are the default.
See you around.

---

### Post by confused57 on 2006-06-01
Thanks, I thought it'd be much easier to refer someone to that thread rather than typing out the instructions each time; even now, I'm hesitant to install grub to the windows mbr(always a "chance" of a problem)...a grub boot floppy "howto" would be nice.

---

### Post by Terry Jones on 2007-06-24
title           Windows
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

What does each one of these lines mean? 
Please in the response if possible explain each line. 
My Windows  partiton is on the slave  drive . 
It is the second partition not the first.
The first partition is an HP recovery partition. 
Grub is installed to the master drive.
I can boot the slave drive with the bios.

---

### Post by confused57 on 2007-06-24
Your entry to boot Windows would need to point to the 2nd partition:
```
title Windows
root (hd1,1)
savedefault
makeactive
map (hd0) (hd1)
map (hd1) (hd0)
chainloader +1
```


title Windows <---you can name it anything you want
root (hd1,1)   <---hd1 is the 2nd hard drive(slave),1 is the 2nd partition
savedefault    <---You don't really need this, this is just to boot WinXP if it was booted last & grub set up for
makeactive     <---This sets your Window's partition as active
map (hd0) (hd1)  <---These map commands "fools" Windows into thinking it is the first hard drive to boot
map (hd1) (hd0)
chainloader +1  <---This hands off the boot process to the Window's bootloader

This site explains grub, other booting utilities, mounting filesystems, etc quite well:
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)

---

### Post by Terry Jones on 2007-06-25
I followed the instructions to the letter. It did not work. On the master drive the second partition contains XP Pro and  the other partitions contain Fedora Core 6 , Gentoo 2006.1, and  Ubuntu 6.06. I am using the grub menu of Ubuntu to do the edititng . When I select XP Pro from the Ubuntu's grub menu it brings up the NT bootloader. By editing the boot ini file of XP Pro I can boot XP Home. When  I try to select the entry of XP Home from  Ubuntu's grub menu I  get the following errors under the following conditions.
 
1.Follwing the instuctins of the reply to my  eariler post. Grub error 11 or error 12.

2  Setting  the XP Home entry to match that of XP Pro as following.

title Microsoft Windows XP Professional -Master
rootnovarify(0,1)
chainload+1
  

title Microsoft Windows XP Home -Slave
rootnovarify(1,1)
chainload+1

When I used the entry for XP Home as typed above. I saw the entry as typed on the computer's  screen with the following  words listed below : press any key to reboot.When I reboot I see Ubuntu's  grub menu screen.

---

