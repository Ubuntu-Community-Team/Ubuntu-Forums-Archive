---
title: "Dual Boot Crappy Attempt"
date: 2006-07-29
forum: Absolute Beginner Talk
---

### Post by EminNew on 2006-07-29
I've been trying to set up dual boot system and this is what my drive looks like now:

[[IMG]http://img93.imageshack.us/img93/8384/sshot1od0.png[/IMG]](http://imageshack.us)
[http://img93.imageshack.us/my.php?image=sshot1od0.png](http://img93.imageshack.us/my.php?image=sshot1od0.png)

9.32 Gb unknown is Ubuntu (Hoarry Hedgehog)
H: is WinXP (currently the only bootable)
1.44 Gb unknown is the swap
C: is another XP (supposed to be without network, not bootable now)

Any ideas how to make all this work? I could sacrifice the other Xp, if neccessary.

---

### Post by catlett on 2006-07-29
If they are all installed correctly and the issue is getting them to boot, you might want to try GAG. It is a boot loader than can handle windows and linux. The download is small and you can burn the iso to a cd and boot into gag rigth away.
If not grub can work but it will take a bit of editing.
Try gag first [http://gag.sourceforge.net/](http://gag.sourceforge.net/)

---

### Post by dave_567 on 2006-07-30
a link to read...

[http://www.futuredesktop.net/ubuntu6.06.html](http://www.futuredesktop.net/ubuntu6.06.html)

dave

---

### Post by confused57 on 2006-07-30
Very nice link, Dave.

EminNew,  could you give us a little more background of how you managed to set up your partition table this way...i.e. in what order were the operating systems installed, etc?  Is there any way you can get a copy of Dapper or at least Breezy?  One problem is that Windows pretty much has to be the first OS on a single hard drive, thank MS for that.
There's probably several options to get your dualboot working, but more info would definitely help.  Would reinstalling XP on the 1st partition be feasible for you?  If not, there are other possible options.  Whatever method, be sure to back up any important data.

---

### Post by EminNew on 2006-07-30
OK, this is going to be fun.

First I installed two XPs, first one on the larger, and the second on the remaining 10 Gb partition.

Then I formated the first one and installed Ubuntu, but because of a minor glitch I reinstalled it, this time dividing the first partition in two parts, first part being 10 Gb, second remaining empty, followed by a 1.5 Gb swap. Another 10 Gb XP was last.

I put Ubuntu on the first partition and it worked, although I could not boot into remaining XP.

Since I could not go online (having a USB ADSL modem not supported by Ubuntu), I proceeded to reinstall XP. I reasoned that maybe somehow I'd be able to choose OS now, and if not, at least I could go online to look for help.

So here I am. 

I'm a bit confused by conflicting information, as some people claim XP has to be first, while others claim Ubuntu does.

---

### Post by EminNew on 2006-07-30
And, yes, I can get my hands on Dapper Drake. I plan to download it this very night.

---

### Post by EminNew on 2006-07-30
And, yes, I'm prepared to reinstall everything.

I'm set to get it all working if it takes all night (again).

---

### Post by confused57 on 2006-07-30
> **EminNew said:**
> OK, this is going to be fun.

So here I am. 

I'm a bit confused by conflicting information, as some people claim XP has to be first, while others claim Ubuntu does.

I don't know anything about dual booting 2 Windows OS, but experiences of other posters indicate Windows must be in a partition located in front of Ubuntu when dual booting the 2 OS.
Good luck.

---

### Post by EminNew on 2006-07-30
Thank you all. 

I'm going to study the material I've gathered on the net (including here), and then I'll probably be reinstalling OS's for quite a bit.

I'll let you know if it worked, and promise to help other beginners here, once I get a better grip o things.

---

### Post by confused57 on 2006-07-30
You shouldn't have any problems, doesn't hurt to do a little research and planning beforehand.
You have the right attitude...that's what makes this such a great forum community.

---

### Post by tehnad on 2006-07-30
I am not sure why everyone thinks Windows has to be first.  This very laptop I am posting with has Windows second, just like my other PC setting beside me.  You simply have to put GRUB back into the MBR and modify the menu.lst file to point to the Windows partition.  If you are reinstalling both Operating systems then I would repartition your HD into two partitions. Format one as ext3 and the other as FAT 32.  Windows will see the FAT and want to go there. Install Windows allowing it to take over the MBR.  After Windows is installed, install Ubuntu allowing GRUB to take the MBR over.  6.06 does so well that you donot have to modify the menu.lst file.  It generates one automatically thats works nicely.

---

### Post by confused57 on 2006-07-30
> **tehnad said:**
> I am not sure why everyone thinks Windows has to be first.  This very laptop I am posting with has Windows second, just like my other PC setting beside me.  You simply have to put GRUB back into the MBR and modify the menu.lst file to point to the Windows partition.  If you are reinstalling both Operating systems then I would repartition your HD into two partitions. Format one as ext2 and the other as FAT 32.  Windows will see the FAT and want to go there. Install Windows allowing it to take over the MBR.  After Windows is installed, install Ubuntu allowing GRUB to take the MBR over.  6.06 does so well that you donot have to modify the menu.lst file.  It generates one automatically thats works nicely.
That's good to know, you're the first person I've seen able to install Windows on a partition after the Ubuntu partition with a dual boot. If I may ask, what is the grub menu.lst Window's entry?  Thanks for the "HowTo"...

---

### Post by tehnad on 2006-07-30
Ubuntu provides an example in the default menu.lst type:
sudo less /boot/grub/menu.lst
Look at the example they have listed to get the idea of it all.  If you want to edit then replace "less" with "nano".

---

### Post by catlett on 2006-07-30
> **tehnad said:**
> Ubuntu provides an example in the default menu.lst type:
sudo less /boot/grub/menu.lst
Look at the example they have listed to get the idea of it all.  If you want to edit then replace "less" with "nano".

Would you mind posting your list for us? The example in the grub menu is when windows is on the second hard drive. We are curious about how your list works. With windows on a partition behind ubuntu's on the same disk.

---

### Post by tehnad on 2006-07-30
1

---

### Post by tehnad on 2006-07-30
# menu.lst - See: grub(8), info grub, update-grub(8)
#            grub-install(8), grub-floppy(8),
#            grub-md5-crypt, /usr/share/doc/grub
#            and /usr/share/doc/grub-doc/.

## default num
# Set the default entry to the entry number NUM. Numbering starts from 0, and
# the entry number 0 is the default if the command is not used.
#
# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout

# This is the grub splash image
splashimage (hd0,0)/boot/dragon.xpm.gz

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
#hiddenmenu

# Pretty colours
#color cyan/blue white/blue

## password ['--md5'] passwd
# If used in the first section of a menu file, disable all interactive editing
# control (menu entry editor and command-line)  and entries protected by the
# command 'lock'
# e.g. password topsecret
# password topsecret

#
# examples
#
# title		Windows 95/98/NT/2000
# root		(hd0,0)
# makeactive
# chainloader	+1
#
# title		Linux
# root		(hd0,1)
# kernel	/vmlinuz root=/dev/hda2 ro
#

#
# Put static boot stanzas before and/or after AUTOMAGIC KERNEL LIST

### BEGIN AUTOMAGIC KERNELS LIST
## lines between the AUTOMAGIC KERNELS LIST markers will be modified
## by the debian update-grub script except for the default options below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
##      kopt_2_6_8=root=/dev/hdc1 ro
##      kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=/dev/hda2 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,1)

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

title		Ubuntu, kernel 2.6.15-26-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, kernel 2.6.15-23-386
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.15-23-386
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
#title		Other operating systems:
#root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda2
title		Windows XP.
root		(hd0,1)
savedefault
makeactive
chainloader	+1

This is it minus my md5-sum hash.  -Tehnad-

---

### Post by tehnad on 2006-07-30
My fault, after looking at this again I realize that you are right and windows is on the first partition of this HD.  I need to grab the menu.lst from my other computer that has it definitely on the second.  I put it on after ubuntu

---

### Post by catlett on 2006-07-30
It's as simple as that.:D  That is why you shouldn't take anything for granted. Since I have gotten involved with linux everyone says windows should be the first partition. I never second guessed it because I knew nothing of linux and dual booting.
Now that I see your entry, windows can be booted from any partition just like any other distro.
Thanks for posting. I always wondered but windows was already there.

Maybe we'll turn this into a post on how to enter different grub entries.

Just so everyone sees that you never stop learning here is my list with windows on the first partition, even though it didn't need to be 


```
## ## End Default Options ##

title           Ubuntu, kernel 2.6.15-26-686
root            (hd0,0)
kernel          /vmlinuz-2.6.15-26-686 root=/dev/hda5 ro quiet splash
initrd          /initrd.img-2.6.15-26-686
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-686 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.15-26-686 root=/dev/hda5 ro single
initrd          /initrd.img-2.6.15-26-686
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,0)
kernel          /vmlinuz-2.6.15-26-386 root=/dev/hda5 ro quiet splash
initrd          /initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,0)
kernel          /vmlinuz-2.6.15-26-386 root=/dev/hda5 ro single
initrd          /initrd.img-2.6.15-26-386
boot


title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title           Debian GNU/Linux, kernel 2.6.12 Default (on /dev/hda2)
root            (hd0,1)
kernel          /boot/vmlinuz root=/dev/hda2 ro ramdisk_size=100000 lang=us apm=power-off nomce vga=791
initrd          /boot/initrd.img
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title           Debian GNU/Linux, kernel 2.6.12 (on /dev/hda2)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.12 root=/dev/hda2 ro ramdisk_size=100000 lang=us apm=power-off nomce vga=791
initrd          /boot/initrd.img-2.6.12
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
title           Debian GNU/Linux, kernel memtest86 (on /dev/hda2)
root            (hd0,1)
kernel          /boot/memtest86.bin
savedefault
boot


# This entry automatically added by the Debian installer for an existing
# linux installation on /dev/hda2.
#title          Debian GNU/Linux, kernel memtest86+ (on /dev/hda2)
#root           (hd0,1)
#kernel         /boot/memtest86+.bin
#savedefault
#boot


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdb1
title           Microsoft Windows XP Professional
root            (hd1,0)
savedefault
makeactive
map             (hd0) (hd1)
map             (hd1) (hd0)
chainloader     +1

#This entry is for the PC-BSD install on hdb4
title        PC-BSD
rootnoverify (hd1,3)
chainloader  +1
boot

#This entry chainloads to Puppy's Grub
title        Puppy Linux
rootnoverify (hd0,10)
chainloader  +1
boot

```


[COLOR="Red"]EDIT[/COLOR]I just saw your post but don't bother. I believe your point. Like I said I never questioned it and windows was already first. So I never experimented. I just asked because it is a comman thing to hear people say 'keep windows first'. I wanted to make sure when I correct people I can link to your list and say "see, tehnad has windows second. it can be done."

---

### Post by confused57 on 2006-07-30
> **tehnad said:**
> My fault, after looking at this again I realize that you are right and windows is on the first partition of this HD.  I need to grab the menu.lst from my other computer that has it definitely on the second.  I put it on after ubuntu

No, you were right...root (hd0,1) is the 2nd partition.
I've bookmarked this page for future reference, learn something new every day.

---

### Post by tehnad on 2006-07-30
The file that I just replaced is what it looks like with it on the second partition.  I just modified it to save room.  The reason people say to put Windows on first is because they do not know how to reinstall grub in the MBR(master boot record).  That is the only trick you need to get it to work right.  To do this you need a live disk like Knoppix that has grub on it.  It does work just fine though. The reason that this laptop had Windows first is because of the rescue disk for this laptop.  It formats the entire drive taking everything over.  My other machine is home built and has Linux first.

---

### Post by catlett on 2006-07-30
> **tehnad said:**
> The file that I just replaced is what it looks like with it on the second partition.  I just modified it to save room.  The reason people say to put Windows on first is because they do not know how to reinstall grub in the MBR(master boot record).  That is the only trick you need to get it to work right.  To do this you need a live disk like Knoppix that has grub on it.  It does work just fine though.
Since we are having the conversation [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by tehnad on 2006-07-30
You know that is wild.  When I had to re-install grub I tried the Ubuntu disk and it told me that grub was not found.  Maybe it is because I never tried sudo ("Ubuntu is secure in many ways") anything.  I just assumed it was like many of the other live distros that I have used where root was wide open for use.

---

### Post by tehnad on 2006-07-30
Catlet you should tell me how to make a scroller like you did with your menu.lst.  I feel bad posting such a large page taking up so much room when there is a better way.  I haven't made many posts anywhere because I never wanted to be the idiot everyone boo'd off the stage.  Now that I am more proficient at Linux and have been programming in C++ for the last two semsters I would like to learn a little better posting habbit

---

### Post by catlett on 2006-07-30
> **tehnad said:**
> Catlet you should tell me how to make a scroller like you did with your menu.lst.  I feel bad posting such a large page taking up so much room when there is a better way.  I haven't made many posts anywhere because I never wanted to be the idiot everyone boo'd off the stage.  Now that I am more proficient at Linux and have been programming in C++ for the last two semsters I would like to learn a little better posting habbit

When you post there are options at the top of the window. When you highlight an area of text you can then go to one of the options. I always use the "wrap in code" option but there is a wrap in quotes option.
The code option is this one #  So you would paste in your list. Highlight the text like you were going to copy/paste and without loosing the highlight, click on the # symbol.
There are many options on the post window. They all work with highlighting. You can use it to create a hyperlink to a word or set of words, italicise, change color etc.
I use wrap in code instead of wrap in quotes because the quote option removes spaces between letters. Why I don't know. 
Later I'll pm you on how to post an image like this.:D 
[IMG]http://i80.photobucket.com/albums/j180/brthomas503/post.jpg[/IMG]

---

### Post by tehnad on 2006-07-30
Cool. I didn't relize that wrap in code made the scroller.  I thought it just changed your text to a different font to simulate code. Good to know.  I would assume that the images that you posted are sreen shots with the one of your GUI being modified to only show the top.  Close?

---

### Post by catlett on 2006-07-31
When you use the code wrap it will put a long entry in the scroll bar format. I think it happens because it doesn't change the format i.e. spaces and line changes. It posts it exactly so to keep it inside the area given it has to use scroll bars. I don't believe it does it in the quote mode. I stopped using the quote wrap when it removed the spaces between entries on the saame line. It was hard toi show someone a line from /etc/fstab (for example)
The image is not very hard but takes a few steps. In Applications<Accessories there is a "Take a screnshot" entry. This takes a screenshot of your desktop.
The pain in the neck part is it is saved in png format. You have to change the format to upload the image. To do this you rigth-click on the image and choose "open with". Then select gimp. When it opens in gimp go to the top menu and select file and then select "save as".
When the save box appears, you want to select "browse for extension types". When the list of extensions appears select "jpeg" and then hit save.
Now go to an image hosting site, I use photobucket 
[http://photobucket.com/](http://photobucket.com/) When you upload the picture to photobucket, it will give you 3 urls for the image. You want the image url. The one that is listed as "img".
Just copy/paste the img url right into the post/reply box. That is it. The url comes with [img] tags already so you do not need to use a menu option.
When you post the reply, the image will be there.
I hope I didn't make it make it sound complicated.
Basically you need to use gimp to change the image to jpeg before you can up[load the image to  a hosting site. After you upload just copy/paste the image url into the text box of the forum reply window.
Have fun. I hope you post more. It appears you have alot to offer.

---

### Post by EminNew on 2006-08-06
Well, I did it.

I can now dual boot Ubuntu and Xp, with FAT32 partition both can access.

I learned how to mount the FAT32, and enable it on boot.

I managed to set up broadband, although it doesn't work again after some upgrades. But I'll sort it out too.

Also, I'm fighting some issues with mp3's, as only a handfull are recognized as playable.

All in all, it may be some time before I master all the ropes of Linux, but I quite enjoy the process of learning. Thank you all.

---

### Post by richbarna on 2006-08-06
> **EminNew said:**
> Well, I did it.

I can now dual boot Ubuntu and Xp, with FAT32 partition both can access.

I learned how to mount the FAT32, and enable it on boot.

I managed to set up broadband, although it doesn't work again after some upgrades. But I'll sort it out too.

Also, I'm fighting some issues with mp3's, as only a handfull are recognized as playable.

All in all, it may be some time before I master all the ropes of Linux, but I quite enjoy the process of learning. Thank you all.

EminNew you are an example to all new-users, I had the same enthusiasm and optimistic outlook as you when I first started.

I hope other new-users read your post.

Have fun :)

Rich

---

### Post by catlett on 2006-08-06
For mp3 capabilities and dvd etc, you can take the easy route and get Automatix. It is a script that installs everything you need. [http://ubuntuforums.org/showthread.php?t=223087](http://ubuntuforums.org/showthread.php?t=223087)
If you want to get into your system a little more, you can follow the Dapper Guide and install the packages your self. (just make sure you change your repository list when the guide says to [http://doc.gwos.org/index.php/DapperGuide](http://doc.gwos.org/index.php/DapperGuide)
If you use the guide, make sure to install win32codecs. Get instructions from the "restricted formats" section [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by EminNew on 2006-08-07
Yup, did that and it works.

Although, I used EasyUbuntu instead of Automatix.

I have to warn people when following links to EasyUbuntu, 'cause an older link could make you download older version.

I happened to wget a version that was outdated by just .01 version increment, and could not install Flash and Java support (a bug corrected in latest edition).

So make sure you check at their official web page.

I'm still having trouble with broadband, but I'll post it in a new thread.

---

