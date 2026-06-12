---
title: "Done with XP but a few little problems"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by mactruc on 2006-08-22
After YEARS of trying to find a distro that would start me off easy in the linux world and not just dump me, I have found it. I have tried Redhat as far back as version 5.something and Mandrake and 10.1 and I always felt like the learning curve was too high. Now thanks to a roommate who discoverd ubuntu on digg.com, I have made the swtich. Sadly, he wont leave XP himself, but im working on that. Now, enough with my background, onto the questions/concerns.

1.) First and formost, I gotta play some World of Warcraft and I DO have it running... but the frame rate sucks. Granted, Im not on a power house at all, 1ghz athlon, 1gig of ram and GeForce FX 5200 512meg. With XP i could get ~ 25-30 fps. Now im having a hell of time reaching 20. Is this due to opengl vs direct3d? I assume so and i have already used the -opengl and have turned all options down to the min running at 800x600 and have installed the Nvidia drivers. Yes, Im sure the install worked cause my screen savers went from what seemed to be 3fps to much higher. That is the first concern

2.) My logitech mx518 is having problems. The "extra" buttons dont work. Period. I have come across a few posts on how to get them to work, but that always crashes out x and i have to bring back the old config file. While I can live without the extra buttons, my mouse wheel does not scroll all the time, its hit and miss from reboot to reboot. That is a PITA i never noticed how much i used it till it was gone.

3.) Dual booting is XP NOT working. Only reason for this is WoW, when I try from the grub loader, XP is listed,  it says disk read error some something similar, but i can mount it in ubuntu. I have tried adding a common line, the exact line im not sure, but that still doesnt; load same error. Any insight would wondeful.

3,) This is big, almost as big as the WoW issue. I cant burn and Audio CD from MP3 files. I have tried Serpentine, K3b (I know its for KDE), and Gnomebaker. Gnomebaker says i dont have the decoder installed, k3b same problem and Serpentine says, after installing decoder, says I dont have enough free cache space. I can burn CD images and DVD images no problem w/ Gnomebaker.

4.) Samba networking, cant get it working with the other computers on the network or the XBOX this is also of major importance to me as I stream many divx files to the XBOX. Along with that any replacment for xboxconnet, the software to stream media from your PC to the XBOX360? i have not had any luck finding any soild information on that front.

So thats it, if you guys can help me fix the 4 problems, I can finally give up XP and convert friends and family. Im sure you guys will need some posting of the config files for at least one of my problems, and I would post them, if I knew which ones you need. ](*,)  
Thanks
J

---

### Post by beameup on 2006-08-22
#3. There are a couple of gstrteamer 8 plugins you need to install to enable that.


From this page [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

To add mp3 support to GnomeBaker, install gstreamer0.8-mad and gstreamer0.8-misc. You ca also add the gstreamer0.8-vorbis and gstreamer0.8-flac plugins

[http://www.ubuntuforums.org/showthread.php?t=168290](http://www.ubuntuforums.org/showthread.php?t=168290)

---

### Post by TFX360 on 2006-08-22
J,


Read between the lines,

After YEARS of trying to find a distro that would start me off easy in the linux world and not just dump me, I have found it. I have tried Redhat as far back as version 5.something and Mandrake and 10.1 and I always felt like the learning curve was too high. Now thanks to a roommate who discoverd ubuntu on digg.com, I have made the swtich. Sadly, he wont leave XP himself, but im working on that. Now, enough with my background, onto the questions/concerns.

1.) First and formost, I gotta play some World of Warcraft and I DO have it running... but the frame rate sucks. Granted, Im not on a power house at all, 1ghz athlon, 1gig of ram and GeForce FX 5200 512meg. With XP i could get ~ 25-30 fps. Now im having a hell of time reaching 20. Is this due to opengl vs direct3d? I assume so and i have already used the -opengl and have turned all options down to the min running at 800x600 and have installed the Nvidia drivers. Yes, Im sure the install worked cause my screen savers went from what seemed to be 3fps to much higher. That is the first concern.

Can't really help you here. You could try to compile you own driver. That would probably be faster. I've done so for my ATI drivers for Xgl (see Wikipedia on THAT!)

2.) My logitech mx518 is having problems. The "extra" buttons dont work. Period. I have come across a few posts on how to get them to work, but that always crashes out x and i have to bring back the old config file. While I can live without the extra buttons, my mouse wheel does not scroll all the time, its hit and miss from reboot to reboot. That is a PITA i never noticed how much i used it till it was gone.

Well this is specific also. Can't help here... but you could try [HTML]http://my.opera.com/Mr%20Green/blog/show.dml/140616[/HTML]

3.) Dual booting is XP NOT working. Only reason for this is WoW, when I try from the grub loader, XP is listed,  it says disk read error some something similar, but i can mount it in ubuntu. I have tried adding a common line, the exact line im not sure, but that still doesnt; load same error. Any insight would wondeful.

Gimme the insides of /boot/grub/menu.list

3,) This is big, almost as big as the WoW issue. I cant burn and Audio CD from MP3 files. I have tried Serpentine, K3b (I know its for KDE), and Gnomebaker. Gnomebaker says i dont have the decoder installed, k3b same problem and Serpentine says, after installing decoder, says I dont have enough free cache space. I can burn CD images and DVD images no problem w/ Gnomebaker.

[HTML]http://members.chello.nl/w.hellinga/[/HTML]

4.) Samba networking, cant get it working with the other computers on the network or the XBOX this is also of major importance to me as I stream many divx files to the XBOX. Along with that any replacment for xboxconnet, the software to stream media from your PC to the XBOX360? i have not had any luck finding any soild information on that front.

Nuff samba on this forum, try and find some.

So thats it, if you guys can help me fix the 4 problems, I can finally give up XP and convert friends and family. Im sure you guys will need some posting of the config files for at least one of my problems, and I would post them, if I knew which ones you need.



Thanks
J

---

### Post by deadgobby on 2006-08-22
You could install Automatix, it will get all the codecs in one sweep. Please read before installing. 
[http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix](http://ubuntuforums.org/showthread.php?t=177646&highlight=Automatix)
 If you want to rip your audio cd to mp3
[http://www.ubuntuforums.org/showthread.php?t=227417](http://www.ubuntuforums.org/showthread.php?t=227417)

Gobby

---

### Post by Josh_b on 2006-08-22
#3 (The first one)

I had a similar problem to this. What version of Ubuntu are you using? If it isn't Dapper, then I suggest you upgrade. That's how I fixed it.

Josh

---

### Post by mactruc on 2006-08-22
Thanks for the crazy amount of feedback in 20 minutes. I am using Dapper, sorry to leave that info out my /boot/grub/menuthingy says

```
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
timeout		10

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
#      password --md5 $1$gLhU0/$aW78kHK1QfV3P2b2znUoe/
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
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-386
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd		/boot/initrd.img-2.6.15-26-386
boot

title		Ubuntu, memtest86+
root		(hd0,1)
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
rootnoverify	(hd0,0)
savedefault
makeactive
chainloader	+1


```

I gave it all to you, the rootnoverify line seems to point to the correct drive and partion. Maybe im being drunk and dumb but im 99.9% sure is correct. 

And about the smb, is it really that much  pita, all the posts i have seen and tried havent worked. Im not made of money and DVDs are $$ in my poor world of retail paychecks](*,)

---

