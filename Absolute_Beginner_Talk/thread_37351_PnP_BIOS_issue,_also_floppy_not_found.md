---
title: "PnP BIOS issue, also floppy not found"
date: 2005-05-26
forum: Absolute Beginner Talk
---

### Post by Nopposan on 2005-05-26
The following is an excerpt from what the terminal reads when I type "dmesg," this is a record of what the screen showed when I booted my Presario 700US.

"pnp: PnP ACPI: disabled
PnPBIOS: Scanning system for PnP BIOS support...
PnPBIOS: Found PnP BIOS installation structure at 0xc00f6df0
PnPBIOS: PnP BIOS version 1.0, entry 0xf0000:0x97d8, dseg 0x400
PNPBIOS fault.. attempting recovery.
PnPBIOS: Warning! Your PnP BIOS caused a fatal error. Attempting to continue
PnPBIOS: You may need to reboot with the "pnpbios=off" option to operate stably
PnPBIOS: Check with your vendor for an updated BIOS
PnPBIOS: dev_node_info: unexpected status 0x28
PnPBIOS: Unable to get node info.  Aborting."

However, the computer continues to boot and ultimately runs Ubuntu Linux.  I'm using it right now.  There's a glitch though, I can't use the floppy drive; there's an icon in the "computer" window for the floppy drive, but when I click on this icon I get an error message that says, "Unable to mount selected volume."  When I click on the "more details" option I get a message that says, "mount: special device /dev/fd0 does not exist."

Questions: Is the problem with the PnP BIOS related to the inability to mount the floppy drive?  Where can I find updated BIOS for a Compaq Presario 700 running Linux?

More questions:  O.K., I really don't have a clue here.  When I installed the Ubuntu Linux from CD I told it I was using AMDi386 platform 'cause there's a little decal on my keyboard that says "AMD Duron processor."  Did I configure the install improperly? :|

---

### Post by 23meg on 2005-05-27
can you provide the contents of your /etc/fstab file? i'm not sure your floppy issue is related to the BIOS error, but it seems you may overcome the BIOS trouble by adding pnpbios=off to your kernel launcher line in /boot/grub/menu.lst (i'm not 100% sure this is where it has to be added; can anyone confirm this?).

you can get BIOS updaters from hp.com, but i think you'll need windows to use them.

---

### Post by Nopposan on 2005-05-27
I'll get the fstab information very soon; I went to the hp site and didn't see any BIOS offered for the Presario 700 US model.  'Left a message there for their tech support, but I'll be surprised if they help 'c aue I bought the machine secondhand and I'm not using the OS the model was shipped with.

---

### Post by Nopposan on 2005-05-27
Well, here are the results of what happens when I just type /etc/fstab at the prompt:

"bash: /etc/fstab: Permission denied"

And here are the results of what happens when I try to use the "find" command to find fstab:
"yuko@nopposan:~$ find / -type f -name fstab
/etc/fstab
find: /etc/lvm/archive: Permission denied
find: /etc/lvm/backup: Permission denied
find: /var/lib/cups/certs: Permission denied
find: /var/lib/gdm: Permission denied
find: /var/lib/slocate: Permission denied
find: /var/cache/setup-tool-backends/debug: Permission denied
find: /var/lock/lvm: Permission denied
find: /var/run/fetchmail: Permission denied
find: /var/run/sudo: Permission denied
find: /var/spool/postfix/hold: Permission denied
find: /var/spool/postfix/private: Permission denied
find: /var/spool/postfix/public: Permission denied
find: /var/spool/postfix/incoming: Permission denied
find: /var/spool/postfix/active: Permission denied
find: /var/spool/postfix/bounce: Permission denied
find: /var/spool/postfix/defer: Permission denied
find: /var/spool/postfix/deferred: Permission denied
find: /var/spool/postfix/flush: Permission denied
find: /var/spool/postfix/saved: Permission denied
find: /var/spool/postfix/corrupt: Permission denied
find: /var/spool/postfix/maildrop: Permission denied
find: /var/spool/postfix/trace: Permission denied
find: /var/spool/cron/crontabs: Permission denied
find: /var/spool/cron/atjobs: Permission denied
find: /var/spool/cron/atspool: Permission denied
find: /var/spool/cups: Permission denied
find: /proc/tty/driver: Permission denied
find: /proc/1/task/1/fd: Permission denied
find: /proc/2/task/2/fd: Permission denied
find: /proc/3/task/3/fd: Permission denied
find: /proc/4/task/4/fd: Permission denied
find: /proc/25/task/25/fd: Permission denied
find: /proc/74/task/74/fd: Permission denied
find: /proc/75/task/75/fd: Permission denied
find: /proc/77/task/77/fd: Permission denied
find: /proc/76/task/76/fd: Permission denied
find: /proc/664/task/664/fd: Permission denied
find: /proc/1034/task/1034/fd: Permission denied
find: /proc/1063/task/1063/fd: Permission denied
find: /proc/3723/task/3723/fd: Permission denied
find: /proc/4464/task/4464/fd: Permission denied
find: /proc/4730/task/4730/fd: Permission denied
find: /proc/5086/task/5086/fd: Permission denied
find: /proc/5101/task/5101/fd: Permission denied
find: /proc/5103/task/5103/fd: Permission denied
find: /proc/5132/task/5132/fd: Permission denied
find: /proc/5140/task/5140/fd: Permission denied
find: /proc/5335/task/5335/fd: Permission denied
find: /proc/5347/task/5347/fd: Permission denied
find: /proc/5387/task/5387/fd: Permission denied
find: /proc/5412/task/5412/fd: Permission denied
find: /proc/5429/task/5429/fd: Permission denied
find: /proc/5443/task/5443/fd: Permission denied
find: /proc/5461/task/5461/fd: Permission denied
find: /proc/5586/task/5586/fd: Permission denied
find: /proc/5662/task/5662/fd: Permission denied
find: /proc/5667/task/5667/fd: Permission denied
find: /proc/5668/task/5668/fd: Permission denied
find: /proc/5841/task/5841/fd: Permission denied
find: /proc/5869/task/5869/fd: Permission denied
find: /proc/5880/task/5880/fd: Permission denied
find: /proc/5901/task/5901/fd: Permission denied
find: /proc/5902/task/5902/fd: Permission denied
find: /proc/5903/task/5903/fd: Permission denied
find: /proc/5904/task/5904/fd: Permission denied
find: /proc/5905/task/5905/fd: Permission denied
find: /proc/5906/task/5906/fd: Permission denied
find: /proc/6048/task/6048/fd: Permission denied
find: /proc/6376/task/6376/fd: Permission denied
find: /root/.aptitude: Permission denied
find: /root/.gnome2: Permission denied
find: /root/.gconf: Permission denied
find: /root/.gconfd: Permission denied
find: /root/.gnome2_private: Permission denied
find: /root/.synaptic: Permission denied
yuko@nopposan:~$"

Do you have any suggestions.  I'm a total novice but I just found the "find" command at [http://www.alwanza.com/howto/linux/floppy.html](http://www.alwanza.com/howto/linux/floppy.html).

Thanks.

---

### Post by Nopposan on 2005-05-27
And furthermore:

"yuko@nopposan:~$ /boot/grub/menu.lst
bash: /boot/grub/menu.lst: Permission denied
yuko@nopposan:~$

Why is permission denied??

 :-?

---

### Post by 23meg on 2005-05-27
what you should do is type sudo gedit /etc/fstab at the command prompt. then you can copy and paste the contents of the file here. similarly, you can type sudo gedit /boot/grub/menu.lst to edit the grub menu.

---

### Post by Nopposan on 2005-05-27
Alright!
Here's the results for gedit fstab:
# /etc/fstab: static file system
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
/dev/hda1       /               ext3    defaults,errors=remount-ro 0       1
/dev/hda5       none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 ro,user,noauto  0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

Here's the results for boot grub:
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
default		0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout		3

## hiddenmenu
# Hides the menu by default (press ESC to see the menu)
hiddenmenu

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
## by the debian update-grub script except for the default optons below

## DO NOT UNCOMMENT THEM, Just edit them to your needs

## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specifiv kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
# kopt=root=/dev/hda1 ro

## default grub root device
## e.g. groot=(hd0,0)
# groot=(hd0,0)

## should update-grub create alternative automagic boot options
## e.g. alternative=true
##      alternative=false
# alternative=true

## should update-grub lock alternative automagic boot options
## e.g. lockalternative=true
##      lockalternative=false
# lockalternative=false

## altoption boot targets option
## multiple altoptions lines are allowed
## e.g. altoptions=(extra menu suffix) extra boot options
##      altoptions=(recovery mode) single
# altoptions=(recovery mode) single

## nonaltoption boot targets option
## This option controls options to pass to only the
## primary kernel menu item.
## You can have ONLY one nonaltoptions line
# nonaltoptions=quiet splash

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

## ## End Default Options ##

title		Ubuntu, kernel 2.6.10-5-386 
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel 2.6.10-5-386 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro single
initrd		/boot/initrd.img-2.6.10-5-386
savedefault
boot

title		Ubuntu, kernel memtest86+ 
root		(hd0,0)
kernel		/boot/memtest86+.bin  
savedefault
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

Will this help?

---

### Post by 23meg on 2005-05-28
try the following one by one, and after you perform each step, check if it solves your problem:

first, check that you have a /floppy0 folder under /dev. if not, create one by typing "sudo mkdir /media/floppy0".

go to system/administration/device manager, find your floppy drive in the device list, and in the "advanced" tab check the "block.device" string to ensure that your floppy drive is recognized as /dev/fd0. if not, change the corresponding line in /etc/fstab to whatever the string shows.

if all else fails, try adding "pnobios=off" to your kernel boot line in menu.lst, so that the part corresponding to your kernel looks like this:

```
title Ubuntu, kernel 2.6.10-5-386
root (hd0,0)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/hda1 ro quiet splash pnpbios=off
initrd /boot/initrd.img-2.6.10-5-386
savedefault
boot
```

as i said before, i'm not really sure if pnpbios=off has to be put here, but go ahead and try; you won't break anything.

---

### Post by Nopposan on 2005-05-29
O.K., thanks.  I'm still plugging away though.

1) The directory "floppy0" does exist under /dev.
2) I don't find anything that seems to be a floopy drive in the device list, so I can't follow the instructions as written for checking on the match-up between the device and dev/fd0.
3) Thanks for the code, but how do I use it?  I tried typing it in line by line in the terminal window, but I get errors: "command not found."

I apologize for my ignorance; 'willing to learn though.

Thanks again.

---

### Post by Nopposan on 2005-05-30
'Figured out how to turn the PnP Bios off.  Thanks for the help with that.

However, I still can't access the floppy drive.

---

### Post by Nopposan on 2005-06-02
O.K.

Thank you for all of your help, 23Meg.  I've got the floppy drive working to our satisfaction now; we still have to select "unmount" from a right-click menu to unmount it, but I think that's alright.

All I needed to do was add the word "floppy" to the modules list in the grub boot menu; 'had no idea what was meant by that at first but now I see the light.

'Time to work on the wireless card now.

---

### Post by Coldsnap on 2005-08-27
Hi guys,

Maybe my noob is showing, but Nopposan added the word 'floppy' where, exactly?

Thanks.  Having the same problem, and hoping that his solution will work for me.

- Coldsnap

UPDATE:  Okay, after a bit of searching I found that I can manually mount the floppy drive by using the terminal and typing in "sudo mount -t msdos /dev/fd0 /media/floppy0", and that works fine, but when I try to access the floppy drive through the Floppy Icon in the Computer folder, it gives me the "Unable to mount selected volume error."  As well, trying to UNMOUNT the volume doesn't work, I have to manually unmount in through the terminal.  Help!  Thanks in advance, guys.

---

