---
title: "i need GRUB help"
date: 2006-06-30
forum: Absolute Beginner Talk
---

### Post by cara on 2006-06-30
We are dualbooting windows and i cant figure out how to boot into windows. i understand i have to switch the order of hard drives, but im not entirely sure how.
i press E for edit, then switch around the numbers to what i think is the windows drive... but... it comes up with the savedefault chainloader +1 thing, and i have to press the reset button.

Now.. my hard drives are named /hdb (storage)  /hdc (windows) /hdd (ubuntu)    ((in the disks manager))    and i dont think any of them are partitioned.


anyone know what im supposed to change the numbers to?

---

### Post by ovimunt on 2006-06-30
Hi,

What is exactly that you're trying to do? Do you just want to start Windows or are you trying to change the order of your boot options, i.e. make Windows the default boot option?

---

### Post by Jagot on 2006-06-30
[https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]Hi,

What is exactly that you're trying to do? Do you just want to start Windows or are you trying to change the order of your boot options, i.e. make Windows the default boot option?[/QUOTE]

no, i like the fact that my comp boots into ubuntu first, but occasionally there is a few things i need to do in windows (play a game, delete things off the ntfs drive, mostly)

---

### Post by cara on 2006-06-30
[QUOTE=Jagot][https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS](https://help.ubuntu.com/community/GrubHowto/ChangeDefaultOS)[/QUOTE]

so i have to change the boot order entirely?

---

### Post by ovimunt on 2006-06-30
You don't need to change the order of anything.

If Ubuntu and hence GRUB is installed properly you should get a boot menu in text mode when you start your computer. This should give you 3 options for linux (standard, recovery mode, memory test) and one option for Windows. Once in there you just press up and down (the arrow keys) so that you highlight the option you want to start and then just press Enter.

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]You don't need to change the order of anything.

If Ubuntu and hence GRUB is installed properly you should get a boot menu in text mode when you start your computer. This should give you 3 options for linux (standard, recovery mode, memory test) and one option for Windows. Once in there you just press up and down (the arrow keys) so that you highlight the option you want to start and then just press Enter.[/QUOTE]

i did that. it comes up with the savedefault chainloader +1 thing.

maybe my boyfriend installed grub wrong?

---

### Post by ovimunt on 2006-06-30
Umm... can you post the exact error/warning message that you get?

The other option is obviously to go into the boot list file and see what's in there.

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]Umm... can you post the exact error/warning message that you get?

The other option is obviously to go into the boot list file and see what's in there.[/QUOTE]

k i can do that.

---

### Post by ovimunt on 2006-06-30
While you're doing that, try also to go into the boot list file and paste its contents on the forum so we can have a look.

In the Ubuntu terminal (command line) type the following:

> 
gedit /boot/grub/menu.lst


Copy the contents of the file you get there and paste it in here.

---

### Post by cara on 2006-06-30
ok.
when i reboot it has all the ubuntu options, recovery and memtest, at the bottom is windows. i select that one and -

root (hd 1,0)
filesystem type unknown. partition type 0x7
savedeafualt
make active
chainloader +1

then i need to press the reset button on the box.


and i also noticed that i have the ubuntu kernal and the recovery listed twice on the boot menu. odd.


steve@steve-desktop:~$ gedit /boot/grub/menul.lst
ImportError: could not import gtksourceview
Traceback (most recent call last):
  File "/usr/lib/gedit-2/plugins/modelines.py", line 24, in ?
    class ModelinePlugin(gedit.Plugin):
AttributeError: 'module' object has no attribute 'Plugin'

** (gedit:5155): WARNING **: Could not load python module modelines


** (gedit:5155): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5155): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed

** (gedit:5155): CRITICAL **: gedit_plugin_update_ui: assertion `GEDIT_IS_PLUGIN (plugin)' failed



so something is broken! at least - thats what it looks like.

and in the window that opened - ther eisnt anything there.

---

### Post by ovimunt on 2006-06-30
Umm... Try this instead

> nano /boot/grub/menu.lst

This should open the file in text mode.

Also, the reason why you get the Ubuntu kernel option twice is that a kernel update has been done. This is what must have messed up the boot list file. It happens...

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]Umm... Try this instead



This should open the file in text mode.

Also, the reason why you get the Ubuntu kernel option twice is that a kernel update has been done. This is what must have messed up the boot list file. It happens...[/QUOTE]

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
                               [ Read 157 lines ]
^G Get Help  ^O WriteOut  ^R Read File ^Y Prev Page ^K Cut Text  ^C Cur Pos
^X Exit      ^J Justify   ^W Where Is  ^V Next Page ^U UnCut Txt ^T To Spell

---

### Post by ovimunt on 2006-06-30
Right... that's actually not the whole file. The bit that I'm looking for is missing. You'll need to scroll down in that window and get the full contents.

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]Right... that's actually not the whole file. The bit that I'm looking for is missing. You'll need to scroll down in that window and get the full contents.[/QUOTE]


i cant scroll down.

thats all thats there.

---

### Post by ovimunt on 2006-06-30
!Remember, you're in text mode. Use your up/down arrow keys to scroll, the mouse will have no effect... :-|

Plus, since linux does start then there definitely is more in that file than just those lines.

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]!Remember, you're in text mode. Use your up/down arrow keys to scroll, the mouse will have no effect... :-|

Plus, since linux does start then there definitely is more in that file than just those lines.[/QUOTE]


oh haahah /newb
k.


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
# kopt=root=/dev/hdc1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd1,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
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
title           Ubuntu, kernel 2.6.15-25-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-25-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-25-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-25-386 root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-25-386
boot

title           Ubuntu, kernel 2.6.15-23-386
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro quiet splash
initrd          /boot/initrd.img-2.6.15-23-386
savedefault
boot

title           Ubuntu, kernel 2.6.15-23-386 (recovery mode)
root            (hd0,0)
kernel          /boot/vmlinuz-2.6.15-23-386 root=/dev/hdc1 ro single
initrd          /boot/initrd.img-2.6.15-23-386
boot

title           Ubuntu, memtest86+
root            (hd0,0)
kernel          /boot/memtest86+.bin
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title           Windows NT/2000/XP (loader)
root            (hd1,0)
savedefault
makeactive
chainloader     +1



i think thats everything. copying and pasting is hard.

---

### Post by raptros-v76 on 2006-06-30
wait. how many partitions/harddrives do you have?

---

### Post by cara on 2006-06-30
[QUOTE=raptros-v76]wait. how many partitions/harddrives do you have?[/QUOTE]

3 drives.
one for storage, one for windows and one for ubuntu
the ubuntu one is partitioned. i think.

---

### Post by raptros-v76 on 2006-06-30
ok, so in ubuntu, what do you get when you do fdisk -l?

---

### Post by ovimunt on 2006-06-30
Well... it's good news but also bad news...

Good news is that your boot list file is absolutely fine.

Bad news is that there's probably a problem with Windows...

It is normal to get the boot command displayed on the screen at boot (the chainloader +1, etc stuff). Thing is though that if Windows does not start after that it means that it's probably frozen...

In conclusion, I'm afraid you've got a Windows problem. The first thing to try and fix this is to restore the windows MBR on the Windows drive. Here things get complicated and I would advise you not to try it. Windows could mess up your MBR on both drives and then you'd get ONLY Windows starting. To avoid this you need to get inside the computer and physically remove the linux HDD. Only then you can try and restore the Windows MBR and then reconnect the linux drive... In other words you migth want to wait for now and get someone to help you... up to you.

---

### Post by cara on 2006-06-30
[QUOTE=raptros-v76]ok, so in ubuntu, what do you get when you do fdisk -l?[/QUOTE]

uh. nothing comes up.

steve@steve-desktop:~$ fdisk -l
steve@steve-desktop:~$

---

### Post by raptros-v76 on 2006-06-30
*smacks self in face*
im a moron. ignore the thing about fdisk

what do you get when you do 
ls /dev|grep hd
?

---

### Post by ovimunt on 2006-06-30
I have to reiterate, if windows in on your second HDD then your boot list is fine.

Don't play with these things - it's easy to mess it up.

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]Well... it's good news but also bad news...

Good news is that your boot list file is absolutely fine.

Bad news is that there's probably a problem with Windows...

It is normal to get the boot command displayed on the screen at boot (the chainloader +1, etc stuff). Thing is though that if Windows does not start after that it means that it's probably frozen...

In conclusion, I'm afraid you've got a Windows problem. The first thing to try and fix this is to restore the windows MBR on the Windows drive. Here things get complicated and I would advise you not to try it. Windows could mess up your MBR on both drives and then you'd get ONLY Windows starting. To avoid this you need to get inside the computer and physically remove the linux HDD. Only then you can try and restore the Windows MBR and then reconnect the linux drive... In other words you migth want to wait for now and get someone to help you... up to you.[/QUOTE]


i wanted to do this by myeslf without waking my boyfriend up.
i was in windows all day yesterday playing warcraft, so i know its ABLE to be booted into, im just not sure how its done.
knowing my boyfriend, he probably disconnected the drive.
i WAS going to do that but i didnt know if it was possible. 

ill wake him up and see if thats what he did.

glad to hear that the file is ok ;D

thanks for your help :P

---

### Post by cara on 2006-06-30
[QUOTE=raptros-v76]*smacks self in face*
im a moron. ignore the thing about fdisk

what do you get when you do 
ls /dev|grep hd
?[/QUOTE]

hda
hdb
hdb1
hdc
hdc1
hdc2
hdc5
hdd
hdd1
steve@steve-desktop:~$


that looks like a lot of stuff :/

---

### Post by raptros-v76 on 2006-06-30
ovimunt's right, now that i think about it.  i mean, grub looks fine.

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]I have to reiterate, if windows in on your second HDD then your boot list is fine.

Don't play with these things - it's easy to mess it up.[/QUOTE]

where is grub stored? like in the memory?
i was just worried that if i unplugged the ubuntu drive, nothing would boot.

---

### Post by raptros-v76 on 2006-06-30
grub's stored on the harddrive somewhere. i wouldnt recommend unplugging the ubuntu drive

---

### Post by cara on 2006-06-30
[QUOTE=raptros-v76]grub's stored on the harddrive somewhere. i wouldnt recommend unplugging the ubuntu drive[/QUOTE]

ok i woke up the boyfriend, he said to change the BIOS to hard drive d

wooo i get to adventure into the bios now! ive learned so much today, haha

---

### Post by ovimunt on 2006-06-30
Why on Earth does he need to disconnect the drive or change the BIOS settings??? :confused: 

Weird thing to do... Anyway, problem sorted I guess... ;-)

---

### Post by raptros-v76 on 2006-06-30
.....yeah. ok that works.

---

### Post by cara on 2006-06-30
[QUOTE=ovimunt]Why on Earth does he need to disconnect the drive or change the BIOS settings??? :confused: 

Weird thing to do... Anyway, problem sorted I guess... ;-)[/QUOTE]

i'm guessing that since neither of us can figure out how to properly configure grub, chanding the bios is the only way to get it to work.

thanks for the help :)

---

### Post by Arisna on 2006-06-30
Are you saying you plan to make a change in BIOS every time you want to switch between OS's?  If so, don't resign yourself to that just yet.  Check out this link:

[http://www.fedoraforum.org/forum/archive/index.php/t-348.html](http://www.fedoraforum.org/forum/archive/index.php/t-348.html)

I know it's from a Fedora forum and is a bit dated, but the information about the "map" parameter is still valid.  I had to use it to get dual booting to work on a PC recently, and it worked like a charm.  The key is to make Windows think that it is the first drive.  I'm thinking your setup will need to go something like this:

```
title Windows NT/2000/XP (loader)
root (hd1,0)
savedefault
makeactive
[b]map (hd1) (hd0)
map (hd0) (hd1)[/b]
chainloader +1
```

Also note that there may be a recovery partition on (hd1,0), in which case you might need to change that to (hd1,1).  Give that a shot if you boot the above entry and end up in a system recovery console. ;)

---

