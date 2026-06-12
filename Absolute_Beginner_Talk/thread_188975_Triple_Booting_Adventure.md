---
title: "Triple Booting Adventure"
date: 2006-06-04
forum: Absolute Beginner Talk
---

### Post by Merlin Whitewolf on 2006-06-04
Don't laugh too hard, please. Just help, if you can.

I'm new to computers. :)  I got my first one about a year and 8 months ago. I began finding references to Linux a few months later. (I was teaching myself how to use the computer, surf the web, etc.) Some of you may find it funny, but prior to getting my own computer, I had thought that 'windows' was just a word for the OS installed when the computer was made. I thought each manufacturer had their own. I learned better in a matter of minutes. 
The next illusion that was shattered was that w95 could be easily made 'safe'. LOL That first computer was destroyed when someone tried to hack in. So I got another. ](*,)  I'm stubborn. :D  
I started finding references to linux in many places, so I started looking for it. At first, all I found were sites that were selling support with CDs to install. For me, the price was prohibitive. Then a friend sent me a set of fedora core 4 CDs. Being very new to linux, as well as relatively new to computers, I'm sure I made many mistakes. I crashed that install. 
A day or so after that FC 5 came out. I downloaded and burned the ISOs to CD, installed it, and then I couldn't boot windows at all. LOL I had come across references to the ubuntu family of OSes, so I looked the site over and chose to download Kubuntu. After I installed it, I could boot Fedora and windows, also. I was on top of the world! I had created a triple boot system. 
I used that for a bit, but when the new version of Ubuntu came out, I thought I'd try it. I surfed a bit with the live CD and discovered that I liked it. So I installed it. I intended for it to replace the Kubuntu install in my triple boot system. But there is a problem.
Ubuntu and windows boot fine, but fedora isn't even on the list. I can't boot fedora at all. I'm sure it's still there as I chose to install Ubuntu to the partition that I'd installed Kubuntu on. 

How can I fix this?

---

### Post by joshrobinson on 2006-06-04
well you would have to do some configuration editing.. mainly your /boot/grub/menu.lst

do you really need fedora core5? ubuntu is way better in my eyes, so i think you shouldnt worry about it and just stick with windows/ubuntu dual boot

ubuntu is very easy to install software and get how you want it, with fedora core you are going to be installing dependencies and rpm files all day long to get things you want on it

---

### Post by Merlin Whitewolf on 2006-06-04
[QUOTE=joshrobinson]well you would have to do some configuration editing.. mainly your /boot/grub/menu.lst

do you really need fedora core 5?[/QUOTE]

How do I do some configuration editing? :confused:  Please. You'll probably need to give instructions as a step by step process. I'm really not very knowledgable.

I do want to keep FC 5. I have it set up and am working on some projects with it. :D

---

### Post by catlett on 2006-06-04
This isn't that hard as long as you know what partition FC5 is on. Open the terminal and enter```
 sudo fdisk -l
``` That will list your partitions. Now you have to figure out which one fc5 is on. HOPEFULLY FC% is installed on a "reiserfs" type of filesystem., So it will be in the partition with reiserfs next to it.
Once you find that you just make an entry in grub. First run fdisk and post the results. Then I'll make up the entry for you and you just enter it in grub.

P.S. this is my list. As you can see we're going to make an entry like I did for FC5.
```


## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda7 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,6)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## additional options to use with the default boot option, but not with the
## alternatives
## e.g. defoptions=vga=791 resume=/dev/hda5
# defoptions=quiet splash

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## controls how many kernels should be put into the menu.lst
## only counts the first occurence of a kernel, not the
## alternative kernel options
## e.g. howmany=all
##      howmany=7
# howmany=all

## should update-grub create memtest86 boot option
## e.g. memtest86=true
##      memtest86=false
# memtest86=true

## should update-grub adjust the value of the default booted system
## can be true or false
# updatedefaultentry=false

## ## End Default Options ##

title		Ubuntu, kernel 2.6.15-23-686
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-686
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-686 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-686 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-23-686
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,6)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda7 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,6)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

title          Debian GNU/Linux
rootnoverify   (hd0,8)
chainloader    +1

title          Fedora Core 5
rootnoverify   (hd0,10)
chainloader    +1

```

---

### Post by Merlin Whitewolf on 2006-06-05
[QUOTE=catlett]This isn't that hard as long as you know what partition FC5 is on. Open the terminal and enter```
 sudo fdisk -l
``` That will list your partitions. Now you have to figure out which one fc5 is on. HOPEFULLY FC% is installed on a "reiserfs" type of filesystem., So it will be in the partition with reiserfs next to it.
Once you find that you just make an entry in grub. First run fdisk and post the results. Then I'll make up the entry for you and you just enter it in
[/CODE][/QUOTE]

This is my hard drive layout -
/dev/sda1  '/' for Ubuntu  5GB  ext3
/dev/sda2  winxp    45GB  ntfs
/dev/sda3  Extended
/dev/sda5 Fedora 49GB ext3
/dev/sda6  swap 2GB
/dev/sda7  '/boot'  Ubuntu  49GB  ext3

As you can see, all Linux partitions are ext3. Is the the problem? 

I tried reinstalling fedora and told it to not install a bootloader. I then reinstalled Ubuntu and added '/dev/sda5' to the list of other OSes to be booted. Fedora is now on the menu, but it still won't boot. 
How do I edit the grub menu to boot fedora? Oh, and how do I find the grub menu to edit it?:roll:  I need to learn more, don't I?

---

### Post by catlett on 2006-06-05
To edit the grub menu you enter this ```
sudo gedit /boot/grub/menu.lst
``` When it opens you can press enter a couple of times to make a space between the last entry and enter a new option.
You can add a generic entry to grub that will boot another os. You need to make a title, so you can see it when it comes up. Then you tell grub where the OSs root is and finally tell it to load. 
If fedora was on /dev/sda5 it would have booted when you added it. But for an example "IF" fedora was on /dev/sda5 then the entry to grub would be this 
```
title         Fedora Core 5
rootnoverify  (hdo,4)
chainloader   +1
``` This is a generic entry. You could get technical and enter the kernel and initrd image but this will work.
Just to make sure we know where fedora is, enter ```
sudo fdisk -l
``` This will show where fedora is and then you can check the menu. We can also mount the fedora partition and you can open fedora's grub menu and get the exact listing for fedora and put that in.
First thing first, reply with fdisk -l

---

### Post by Merlin Whitewolf on 2006-06-05
[QUOTE=catlett]To edit the grub menu you enter this ```
sudo gedit /boot/grub/menu.lst
``` When it opens you can press enter a couple of times to make a space between the last entry and enter a new option.
You can add a generic entry to grub that will boot another os. You need to make a title, so you can see it when it comes up. Then you tell grub where the OSs root is and finally tell it to load. 
If fedora was on /dev/sda5 it would have booted when you added it. But for an example "IF" fedora was on /dev/sda5 then the entry to grub would be this 
```
title         Fedora Core 5
rootnoverify  (hdo,4)
chainloader   +1
``` This is a generic entry. You could get technical and enter the kernel and initrd image but this will work.
Just to make sure we know where fedora is, enter ```
sudo fdisk -l
``` This will show where fedora is and then you can check the menu. We can also mount the fedora partition and you can open fedora's grub menu and get the exact listing for fedora and put that in.
First thing first, reply with fdisk -l[/QUOTE]

From fdidk --

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
units = cylinders of 16065 * 512 = 8225280 bytes

Device      Boot   Start     End        Blocks            Id     System
/dev/sda1            1           682        5478133+     83    Linux
/dev/sda2     *      683      6451      46339492+   7      HPFS/NTFS
/dev/sda3             6452   19457     104470695    5      Extended
/dev/sda5             6452   12830     51239286      83    Linux
/dev/sda6             12831  13079    2000061        82    Linux swap / Solaris
/dev/sda7             13080  19457    51231253      83    Linux

That's what it lists. There's no /dev/sda4. I don't know why.

I looked at the grub menu by following your directions. The entry for Fedora is --

title  Fedora Core release 5 (Bordeaux)  (on /dev/sda5)
root  (hd0,4)
kernel  /boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/sda5
savedefault
boot

This doesn't really resemble what you wrote, does it?

When I installed Fedora, I didn't install its bootloader. I thought the bootloader in Ubuntu would do the job. Was I wrong? Is it needed? :confused:

---

### Post by catlett on 2006-06-05
Grub identifies 0 as a place, so it's numbering is 1 behind what you would think. Meaning the 5th partition to grub is 4 (0,1,2,3,4). Grub doesn't need to be installed by the fedora install. I only mentioned it becaus if grub was installed there before, we could mounty the p[artition amd look at the entry for FC5 in it's grub.
Anyways I'm surprised that Fedora isn't booting with that entry. What we can do is try my entry and see if we get lucky.
Open the list up again. Put a # infront of each line of the old entry. This will tell the computer to "ignore" the text that follows #. Plus it keeps the entry there in case you want it back. (all you do is delete the # )
Then add my earlier entry to the list. Save and reboot. Choose the fedora entry and hopefuly it boots.
You new menu should look like this (plus the other ubuntu entries of course)
```
#title Fedora Core release 5 (Bordeaux) (on /dev/sda5)
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/sda5
#savedefault
#boot

title         Fedora Core 5
rootnoverify  (hdo,4)
chainloader   +1
```

---

### Post by Merlin Whitewolf on 2006-06-06
[QUOTE=catlett]Grub identifies 0 as a place, so it's numbering is 1 behind what you would think. Meaning the 5th partition to grub is 4 (0,1,2,3,4). Grub doesn't need to be installed by the fedora install. I only mentioned it becaus if grub was installed there before, we could mounty the p[artition amd look at the entry for FC5 in it's grub.
Anyways I'm surprised that Fedora isn't booting with that entry. What we can do is try my entry and see if we get lucky.
Open the list up again. Put a # infront of each line of the old entry. This will tell the computer to "ignore" the text that follows #. Plus it keeps the entry there in case you want it back. (all you do is delete the # )
Then add my earlier entry to the list. Save and reboot. Choose the fedora entry and hopefuly it boots.
You new menu should look like this (plus the other ubuntu entries of course)
```
#title Fedora Core release 5 (Bordeaux) (on /dev/sda5)
#root (hd0,4)
#kernel /boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/sda5
#savedefault
#boot

title         Fedora Core 5
rootnoverify  (hdo,4)
chainloader   +1
```[/QUOTE]

I get this message when trying to boot Fedora after making the changes --

'Error 13: Invalid or unsupported format'

](*,)  I'm the stubborn kind of person, so I'll keep plugging away at this. But I'll admit to being confused as to why this didn't work.

---

### Post by catlett on 2006-06-06
It doesn't make sense but there is one last thing I can think of. If the grub your using is from ubuntu, you can run an update. Grub will search for any new kernels. Hopefully it will recognise fedora and make an entry, but I doubt it.
This command is good if you added a kernel to Ubuntu, Since grub didn't see fedora the first time I doubt it'll see it now. But there's nothing to loose and everything to gain ```
sudo update-grub
```

---

### Post by Merlin Whitewolf on 2006-06-06
[QUOTE=catlett]It doesn't make sense but there is one last thing I can think of. If the grub your using is from ubuntu, you can run an update. Grub will search for any new kernels. Hopefully it will recognise fedora and make an entry, but I doubt it.
This command is good if you added a kernel to Ubuntu, Since grub didn't see fedora the first time I doubt it'll see it now. But there's nothing to loose and everything to gain ```
sudo update-grub
```[/QUOTE]

Thanks. I'll try that.

---

### Post by Merlin Whitewolf on 2006-06-06
That didn't do it either. 
My router and modem had to be reset this morning. It's a pain when something like that happens when you're needing to post to a forum.
-Merlin

---

### Post by steve.horsley on 2006-06-06
What bootloader did Fedora use? If it was grub, you should be able to mount the fedora partition, have a look in /media/sda5/boot/grub/menu.lst and find how Fedora configures grub to boot itself. If Fedora uses LILO then obviously that's no help.

---

### Post by sanjose on 2006-06-06
```

title Fedora Core release 5 (Bordeaux)  (on /dev/sda5)
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/sda5 rhgb quiet
initrd /boot/initrd-2.6.15-1.2054_FC5.img

```

---

### Post by cotcot on 2006-06-06
[QUOTE=Merlin Whitewolf]From fdidk --

That's what it lists. There's no /dev/sda4. I don't know why.

[/QUOTE]

Not having /dev/sda4 is normal because your partitions /dev/sda5 and above are 'logical' partitions made in the 'extended' partition /dev/sda3. Logical partition start numbering from 5 regardless if you have 1, 2, 3 or 4 'primary' partitions.There are max 4 'primary' partitions of which 1 or more can be 'extended'. These have the numbers 1 to 4. You have 2 primary partitions and 1 extended. You do not have the 4th primary partition installed thus also not numbered.

So your fedora is on /dev/sda5. 
I have a comparable problem since the reinstall of Breezy (3 weeks ago). I did not care because I do not use FC5, but I will check my menu.lst and post the result if I can make FC5 bootable again.

---

### Post by catlett on 2006-06-06
[QUOTE=steve.horsley]What bootloader did Fedora use? If it was grub, you should be able to mount the fedora partition, have a look in /media/sda5/boot/grub/menu.lst and find how Fedora configures grub to boot itself. If Fedora uses LILO then obviously that's no help.[/QUOTE]
He didn't use Grub > When I installed Fedora, I didn't install its bootloader. I thought the bootloader in Ubuntu would do the job. Was I wrong? Is it needed?
But I was thinking that he could still get into fedoras boot folder and get the kernel number and initrd. Couldn't he? There may not be a grub folder but there should be a boot folder with the kernel and boot. Right or wrong? I'm asking because if we can get his kernel version and initrd we can make an exact path to it in the grub menu. Hopefully? But Cotcot might have the answer.

> I did not care because I do not use FC5, but I will check my menu.lst and post the result if I can make FC5 bootable again.Cotcot, do you have fedoras partition mounted in Ubuntu? If so can you open the folder (or desktop icon however you have the mounting of the partition set up) and go into the boot folder. Then open the grub folder. And finally open menu.lst. This will be your fedora'a grub menu. With a little luck you and Merlin will have the same kernel version and we can use your entry but change the root to (hd0,4)

---

### Post by cotcot on 2006-06-06
I have checked a couple of thinks.
As a good father I had kept my menu.lst from before the breezy reinstall and compared its content for booting FC5 to what the ubuntu installer did. I then # marked the entry that the ubuntu installer made and added the entry from my old menu.lst. I could again boot FC5 (although i do not need it anymore). My menu.lst for FC 5 is now :

# title		Fedora Core release 5 (Bordeaux) (on /dev/hda5)
# root		(hd0,4)
# kernel		/boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/hda5 
# savedefault
# boot

title		Fedora Core5
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd-2.6.15-1.2054_FC5.img
savedefault
boot

As you see i have FC5 on partition /dev/hda5 (remember that the grub annotation starts with 0 , so grubs hd0,4 is /dev/hda5). So the difference is that the ubuntu installer did not add ' ro quiet splash' and the line with 'initrd'. 

You could backup your menu.lst (give it the name menuold.lst). Put a hash (#) in front of the lines in menu.lst about FC5 and put lines in as above (without the hash). Check the files vmlinuz and initrd in /boot/grub for the exact syntax. 

Merlin Whitewolf : Congratulations for exploring linux. Please do not hesitate to come back with questions if you feel unconfortable with the replies. There are no stupid questions. I was in your situation about 2 years ago. 

Catlett : i will check your question here after.

---

### Post by cotcot on 2006-06-06
[QUOTE=catlett]He didn't use Grub 

Cotcot, do you have fedoras partition mounted in Ubuntu? If so can you open the folder (or desktop icon however you have the mounting of the partition set up) and go into the boot folder. Then open the grub folder. And finally open menu.lst. This will be your fedora'a grub menu. With a little luck you and Merlin will have the same kernel version and we can use your entry but change the root to (hd0,4)[/QUOTE]

Catlett : I think my previous post included a reply on your suggestion. Let us see what this gives.

---

### Post by catlett on 2006-06-06
Yes your reply is exactly what I was hoping for. It doesn't get better than that for an entry. Even down to the same number partition.
Back to you Merlin, Cotcot did and said it all. If anything is going to work it is what he just posted.


P.S. I would go with his entire entry first and if it doesn't work then you can mount Fedora and look for the vmlinus and initrd specific to your install. But I think they are going to be the same. I don't think FC5 got a new kernel since you guys installed and put uibuntu in. The only thing to change for now is [COLOR="Red"]/dev/hda5[/COLOR] after FC5 root= in the third line. Make it [COLOR="Red"]/dev/sda5[/COLOR] in your entry. Save it and reboot. Hopefully that is it.

---

### Post by Merlin Whitewolf on 2006-06-07
[QUOTE=cotcot]I have checked a couple of thinks.
As a good father I had kept my menu.lst from before the breezy reinstall and compared its content for booting FC5 to what the ubuntu installer did. I then # marked the entry that the ubuntu installer made and added the entry from my old menu.lst. I could again boot FC5 (although i do not need it anymore). My menu.lst for FC 5 is now :

# title		Fedora Core release 5 (Bordeaux) (on /dev/hda5)
# root		(hd0,4)
# kernel		/boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/hda5 
# savedefault
# boot

title		Fedora Core5
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/hda5 ro quiet splash
initrd		/boot/initrd-2.6.15-1.2054_FC5.img
savedefault
boot

As you see i have FC5 on partition /dev/hda5 (remember that the grub annotation starts with 0 , so grubs hd0,4 is /dev/hda5). So the difference is that the ubuntu installer did not add ' ro quiet splash' and the line with 'initrd'. 

You could backup your menu.lst (give it the name menuold.lst). Put a hash (#) in front of the lines in menu.lst about FC5 and put lines in as above (without the hash). Check the files vmlinuz and initrd in /boot/grub for the exact syntax. 

Merlin Whitewolf : Congratulations for exploring linux. Please do not hesitate to come back with questions if you feel unconfortable with the replies. There are no stupid questions. I was in your situation about 2 years ago. 

Catlett : i will check your question here after.[/QUOTE]

Wow! Thank you! It worked perfectly! I just booted into Fedora and it worked fine. I rebooted and I'm back in Ubuntu. Hoozah! :D :-D 

Thank You,
Merlin

"Learning is easy; it's understanding what you've learned that's hard."

---

### Post by Merlin Whitewolf on 2006-06-07
[QUOTE=catlett]Yes your reply is exactly what I was hoping for. It doesn't get better than that for an entry. Even down to the same number partition.
Back to you Merlin, Cotcot did and said it all. If anything is going to work it is what he just posted.


P.S. I would go with his entire entry first and if it doesn't work then you can mount Fedora and look for the vmlinus and initrd specific to your install. But I think they are going to be the same. I don't think FC5 got a new kernel since you guys installed and put uibuntu in. The only thing to change for now is [COLOR="Red"]/dev/hda5[/COLOR] after FC5 root= in the third line. Make it [COLOR="Red"]/dev/sda5[/COLOR] in your entry. Save it and reboot. Hopefully that is it.[/QUOTE]


Thank you very much for all the work you put into helping me. You and Cotcot got me through this. :-D :D 
I have a couple more questions though, what is the 'Color="Red"' entry about? I didn't enter it yet and am wondering what it is for. Do I replace everything after 'FC5 root=' in line 3, or do I insert it between that and 'ro quiet splash'?

Thank You,
Merlin

"If you're still learning, you're still alive."

---

### Post by cotcot on 2006-06-07
[QUOTE=Merlin Whitewolf]Thank you very much for all the work you put into helping me. You and Cotcot got me through this. :-D :D 
I have a couple more questions though, what is the 'Color="Red"' entry about? I didn't enter it yet and am wondering what it is for. Do I replace everything after 'FC5 root=' in line 3, or do I insert it between that and 'ro quiet splash'?

Thank You,
Merlin

"If you're still learning, you're still alive."[/QUOTE]

Because you can boot now you do not have to change anything. Because it works your  FC5 entry in menu.lst should look like this :

title Fedora Core5
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/sda5 ro quiet splash
initrd /boot/initrd-2.6.15-1.2054_FC5.img
savedefault
boot


The comment of catlett was to only replace hda5 by sda5. I have another type of hard disk drive than you have. Because you have a SATA drive your partition is called /dev/sda5 whereas I have a ATA drive and my partition is called /dev/hda5. SATA is a newer type of hard disk drive (better access time etc).

---

### Post by catlett on 2006-06-07
Cotcot explained it.(Just a labeling issue about the type of hard drive, I thought it may be an issue for grub but it appears it isn't)  Don't change anything if it's working. I appreciate the thank you but Cotcot is the one who came through with th correct entry. Glad the problem is solved. See you around the forum.

---

### Post by Merlin Whitewolf on 2006-06-07
[QUOTE=cotcot]Because you can boot now you do not have to change anything. Because it works your  FC5 entry in menu.lst should look like this :

title Fedora Core5
root (hd0,4)
kernel /boot/vmlinuz-2.6.15-1.2054_FC5 root=/dev/sda5 ro quiet splash
initrd /boot/initrd-2.6.15-1.2054_FC5.img
savedefault
boot


The comment of catlett was to only replace hda5 by sda5. I have another type of hard disk drive than you have. Because you have a SATA drive your partition is called /dev/sda5 whereas I have a ATA drive and my partition is called /dev/hda5. SATA is a newer type of hard disk drive (better access time etc).[/QUOTE]

Thank you. I realized that after I had clicked 'submit'. LOL 
I appreciate all of your help.
I tried responding earlier, but for some reason I couldn't connect to the forums. 
Ah! The wonders of the internet -- when the servers are cooperative, that is. =D> 

-Merlin

---

### Post by Merlin Whitewolf on 2006-06-07
[QUOTE=catlett]Cotcot explained it.(Just a labeling issue about the type of hard drive, I thought it may be an issue for grub but it appears it isn't)  Don't change anything if it's working. I appreciate the thank you but Cotcot is the one who came through with th correct entry. Glad the problem is solved. See you around the forum.[/QUOTE]

Catlett,
Yes, Cotcot did provide the solution and I do appreciate that! But you spent a good bit of time and effort in trying to solve my problem. I do very much appreciate that.

Regards the hard drive, I typed it in as sda rather than hda. I had noticed in my researches that the 2 were different; I'm not completely sure what the difference is, but at least I know there's a difference. :grin:  
You've helped me in several other ways, too. I know more about using the terminal and gedit now than ever before. That's from following your instructions. If you ever write a book, I'll find a way to buy it.:D 

See you around the forum!
Thanks,
Merlin

---

