---
title: "Windows doesn't startup!"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by NET WT on 2007-02-16
Hello, I installed Ubuntu the other day. I tried to setup a dual boot. Ubuntu starts up ok, but. Today when my computer was starting up, I chose Windows xp from the Grub menu thing. Windows never started up though. All I got was a black screen which said. 

"Booting 'Microsoft Windows XP Home Edition
Root (hd0,0)
    Filesystem type unknown, partition type 0x7
Save default
Make active
Chainloader +1"

And Windows never started up. 
What does this mean? What should I do?
Thanks for the help.

---

### Post by old_geekster on 2007-02-16
I am fairly new to Ubuntu Edgy myself, but it appears to me that you have installed Ubuntu over the top of XP.

When it says "Filesystem type unknown", that is what happens when XP attempts to access an ext3 partition.

If this is not correct, I am certain that one of the experts here will tell us.

---

### Post by jordanmthomas on 2007-02-16
is XP on your first partition of your first disk?
```
sudo fdisk -l
``` will be of help to find out.

---

### Post by H.E. Pennypacker on 2007-02-16
> "Booting 'Microsoft Windows XP Home Edition
Root (hd0,0)
Filesystem type unknown, partition type 0x7
Save default
Make active
Chainloader +1"

What that means is the following:

1.  The operating system name
2.  Where the operating system is located.  In this case, you've installed it on the very first partition of the first hard drive (there may be only one hard drive).
3.  The filesystem.

The rest is not that important (e.g. the order of the operating systems on the GRUB list).

Please post your full GRUB list, which is located at /boot/grub/menu.list

---

### Post by NET WT on 2007-02-16
Here are the results of "sudo fdisk -l" 


Disk /dev/hda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1       10543    84686616    7  HPFS/NTFS
/dev/hda2           10544       19269    70091595   83  Linux
/dev/hda3           19270       19457     1510110    5  Extended
/dev/hda5           19270       19457     1510078+  82  Linux swap / Solaris


I don't know what a GRUB list is though, or how to get to it.

---

### Post by jordanmthomas on 2007-02-16
type ```
cat /boot/grub/menu.lst
``` to print out the entire file to your terminal; then copy and paste it in here.

BTW your fdisk looks fine and matches the error.

---

### Post by NET WT on 2007-02-16
Here are the results. 



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
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

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
#      password (removed)
# password topsecret

#
# examples
#
# title         Windows 95/98/NT/2000
# root          (hd0,0)
# makeactive
# chainloader   +1
#
# title         Linux
# root          (hd0,1)
# kernel        /vmlinuz root=/dev/hda2 ro
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

title           Ubuntu, kernel 2.6.15-28-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-28-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-28-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-28-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-28-386
boot

title           Ubuntu, kernel 2.6.15-26-386
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-26-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-26-386 (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.15-26-386 root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.15-26-386
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title           Microsoft Windows XP Home Edition
root            (hd0,0)
savedefault
makeactive
chainloader     +1

---

### Post by jordanmthomas on 2007-02-16
In the very last section of that file try changing this line:
```
root (hd0,0)
```
to 
```
rootnoverify (hd0,0)
```

to edit the file, run 
```
gksudo gedit /boot/grub/menu.lst
```

---

### Post by NET WT on 2007-02-16
I did that, now what do I do?

---

### Post by Maestro23 on 2007-02-16
> **NET WT said:**
> I did that, now what do I do?

Did you try to reboot?

---

### Post by jordanmthomas on 2007-02-16
save it, close it, and reboot and see if windows will boot.

---

### Post by NET WT on 2007-02-16
After I saved it and closed it, then I did reboot. I chose windows xp from the list, but after that the black screen came up again. I waited a while, but Windows never boot. 

How long should it take, before Windows starts up?

---

### Post by jordanmthomas on 2007-02-16
It should be instantaneous.

I think I may have found a problem in your menu.lst I didn't see before. 
You'll need to edit it again:

here's the end of what you should have now:
```
### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

You need to comment out a line here, to make it look like this instead:
```

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title Other operating systems:
[COLOR="#ff0000"]#[/COLOR]root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda1
title Microsoft Windows XP Home Edition
rootnoverify (hd0,0)
savedefault
makeactive
chainloader +1
```

save / reboot / pray

---

### Post by NET WT on 2007-02-16
I added the "#" before "root". Was that what I was supposed to do? I saved, then I reboot. Windows didn't startup, I got the black screen again. This is what it said this time:

"Booting 'Microsoft Windows XP Home Edition
Rootnoverify (hd0,0)
Save default
make active
chainloader +1"

---

### Post by jordanmthomas on 2007-02-16
it appears to be a windows error then, since grub did not give you any errors.

Not sure where to go from there.

---

### Post by bulldog on 2007-02-16
> **NET WT said:**
> I added the "#" before "root". Was that what I was supposed to do? I saved, then I reboot. Windows didn't startup, I got the black screen again. This is what it said this time:

"Booting 'Microsoft Windows XP Home Edition
Rootnoverify (hd0,0)
Save default
make active
chainloader +1"

Try to go to the recovery console of a windows instal disk.
[http://www.webtree.ca/windowsxp/repair_xp.htm](http://www.webtree.ca/windowsxp/repair_xp.htm)

If you have found it just type fixboot and fixmbr
Now your windows will boot with a little luck but your ubuntu won't.
You have to reinstall GRUB to make them both work again.
Boot into the live Ubuntu cd. 
When you get to the desktop open a terminal and enter. 
```
sudo grub
```
This will get you a "grub>" prompt 
```
find /boot/grub/stage1
```
This will return a location.Use that location in the next line 
```
root (hd?,?)
```
Next enter the command to install grub to the mbr
```
setup (hd0)
```
Exit the grub shell
```
quit
```

With a little luck you can boot ubuntu an windows from GRUB again.

---

### Post by reabralop on 2007-02-17
I have a very similar issue. I installed Windows and Ubuntu and have been dual booting just fine for over a month now. However, I just tried to restart so I can go into windows and now I can't load either OS. I get the same black screen listed above for windows and Ubuntu says starting in the top corner but nothing as well. It is very crucial that I get into windows so that I may finish my taxes! Will reinstalling Grub fix this also? I don't want to make any mistakes because of the possibility of loosing the info I've done already. Actually the work my wife has done. If this fails and we have to do the taxes all over I may as well kiss Linux goodbye!

---

### Post by pissedoffdude on 2007-02-17
Try using your windows cd to get to the recovery console.  Then type in the command "FIXBOOT" (no quotations).

---

### Post by NET WT on 2007-02-17
I no longer have a problem with Windows xp and dual boot. 

Thanks

---

### Post by H.E. Pennypacker on 2007-02-18
> **NET WT said:**
> I no longer have a problem with Windows xp and dual boot. 

Thanks

Are you going to tell us how your problem was fixed?  Step by step instructions for others who may have the same problem would be very helpful.

---

### Post by reabralop on 2007-02-18
OK, now the problem is serious! I get the same blank screen when I use either the ubuntu cd or windows disk! What now?

---

### Post by NET WT on 2007-02-18
> **H.E. Pennypacker said:**
> Are you going to tell us how your problem was fixed?  Step by step instructions for others who may have the same problem would be very helpful.

Because I was having trouble getting windows to boot up, and since I was unable to fix the problem. I decided to reinstall Ubuntu and not do a dual boot after all. I didn't need Windows for much anyways.

---

### Post by bulldog on 2007-02-18
> **reabralop said:**
> OK, now the problem is serious! I get the same blank screen when I use either the ubuntu cd or windows disk! What now?

Then it could be a hardware problem,like your graphics.
Maybe you can try another if you have one that is.
Or something with the RAM it's very difficult to advice you from here,I'm afraid.

You can try to remove the graphics and put it back again very carefully with all the power down and the cord disconnected from the wall outlet.

---

### Post by reabralop on 2007-02-18
It is a laptop so pulling the graphics card is a no go. I do remember something else though. Before I restarted to go into windows I changed some settings in Beryl. Ubuntu was working fine for the few hours after I made those changes. It wasn't until I restarted that all failed. Does Beryl have that much power to cause this? If so can I do anything from dos? Any thing that will get windows started will be great. At this point I don't care about Ubuntu, I just need to get into the tax software on windows.

---

### Post by reabralop on 2007-02-18
Someone please help!

---

### Post by puyi on 2007-02-24
If all else fails, pull the harddrive, put in some kind of enclosure. Attach your drive to a working Windows machine and copy your files to the working computer. If you have a desktop, install the harddrive in another desktop as a slave drive and copy your files.

This is not the answer you're looking for but you can at least recover your important files this way.

---

### Post by kristalsoldier on 2007-02-24
> **reabralop said:**
> I have a very similar issue. I installed Windows and Ubuntu and have been dual booting just fine for over a month now. However, I just tried to restart so I can go into windows and now I can't load either OS. I get the same black screen listed above for windows and Ubuntu says starting in the top corner but nothing as well. It is very crucial that I get into windows so that I may finish my taxes! Will reinstalling Grub fix this also? I don't want to make any mistakes because of the possibility of loosing the info I've done already. Actually the work my wife has done. If this fails and we have to do the taxes all over I may as well kiss Linux goodbye!

Quick question:

Is this a relatively common occurance? Why does this happen...Especially if the dual boot was working fine for a month?

Thanks!

---

### Post by The Weak Willed Pig on 2007-02-25
> **reabralop said:**
> It is a laptop so pulling the graphics card is a no go. I do remember something else though. Before I restarted to go into windows I changed some settings in Beryl. Ubuntu was working fine for the few hours after I made those changes. It wasn't until I restarted that all failed. Does Beryl have that much power to cause this? If so can I do anything from dos? Any thing that will get windows started will be great. At this point I don't care about Ubuntu, I just need to get into the tax software on windows.

I too am wondering about Beryl.  It was running fine until I restarted Ubuntu then whenever I run Beryl Manager my mouse and keyboard are disabled and I haven't been able to dual boot into XP.
  Anyone else experiencing strange things after running Beryl and restarting?

---

### Post by Fiskal on 2007-02-25
I got the same  problem..... I can't enter to my windows vista!!!!!......

---

