---
title: "cpu is maxed out"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by greg m on 2006-08-29
i`m back on line after the update that went south. i did a autoclean, and then it worked. now when ever i have firefox on my cpu has to work a lot harder. is there a program, so i can fine out what program the cpu is working on, or why it is working so hard. i had a windows program i could use (naviscope) but not in linux it needs to be updated,several free windows programs need to be updated and ported to linux. newzprint was another one.
anyway what could be making my cpu maxout.

---

### Post by S1NGH on 2006-08-29
someone had a similar problem, hype. when he was downloading while in with the transfer tab open and XGL, his cpu useage went to the extreme. do you use XGL, were you doing something else while using FireFox?
more information would be helpful.

---

### Post by greg m on 2006-08-29
no i`m not using xgl, at least i don`t think i m i have not installed it.when i`m on the forum it is low, when i go to some web sites, it will max out, as if it is doing more and longer than before the update. i`m wondering if it is uploading while it is doing it. that is why i was wondering if there was a program that would tell.

thank you  greg

---

### Post by chadk on 2006-08-29
check your process list and sort it by CPU.  If you don't know how to do it in the gui just go to shell and type "ps -aux"  Tell us what process name has the most CPU %.  -- I bet it's CUPS

---

### Post by greg m on 2006-08-29
i get 
warning:bad ps syntax,perhaps a bogus `-`

the only thing in the cpu section is
15.6  vsz is 35124  rss is 29748     /usr/bin/x
24.6   vsz is 84360  rss is 36024    /usr/lib/firefox


how can i save a copy of this? i did not see a copy or a send for the entire thing.

thank you  greg

---

### Post by chadk on 2006-08-29
Sorry, I actually meant use "top"
go to terminal and type "top" no quotes.  Then the top couple of lines are your culprit.

With ps -aux you should get something like this:
```

chad     27369  1.0  2.1  68200 22292 ?        Sl   17:02   1:58 skype
chad     28596  2.5  4.9 144184 51288 ?        Sl   17:48   3:52 /usr/lib/amarok/amarokapp
chad     28598  0.0  0.7  25144  8124 ?        Ss   17:48   0:00 kdeinit Running...
chad     28601  0.0  0.6  24456  7076 ?        S    17:48   0:00 dcopserver [kdeinit] --nosid --suicide
chad     28603  0.0  0.8  26084  8884 ?        S    17:48   0:00 klauncher [kdeinit]
chad     28605  0.0  1.0  27280 10852 ?        S    17:48   0:01 kded [kdeinit]
chad     28607  0.0  0.1   2868  1616 ?        S    17:48   0:00 /usr/lib/gamin/gam_server
chad     28624  0.0  0.8  26824  8632 ?        S    17:48   0:00 kio_file [kdeinit] file /tmp/ksocket-chchad     30617 13.8 16.9 269596 175072 ?       Sl   19:05  10:16 klibido

```

This shows that I have a couple processes really kicking my CPU's butt atm.

With top you should see:
```

top - 20:21:16 up 1 day,  5:42,  3 users,  load average: 1.09, 1.39, 1.34
Tasks: 128 total,   1 running, 127 sleeping,   0 stopped,   0 zombie
Cpu(s): 67.3% us,  5.0% sy,  0.0% ni, 25.4% id,  0.7% wa,  0.7% hi,  1.0% si
Mem:   1034652k total,  1019612k used,    15040k free,    20312k buffers
Swap:  1510068k total,    18444k used,  1491624k free,   444332k cached

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND
30617 chad      15   0  263m 170m  15m S 61.3 16.9  10:35.22 klibido
10573 chad      15   0 79676  15m 9308 S  6.0  1.5   0:11.20 gnome-terminal
 4438 root      15   0 94372  68m  12m S  2.7  6.8 184:38.12 Xorg
28596 chad      15   0  140m  50m  24m S  2.7  5.0   3:55.84 amarokapp
 5110 chad      15   0  188m  47m  21m S  0.3  4.7   1:09.27 nautilus
 6229 chad      16   0  2196 1136  856 R  0.3  0.1   0:00.05 top
    1 root      16   0  1564  528  460 S  0.0  0.1   0:01.15 init
    2 root      RT   0     0    0    0 S  0.0  0.0   0:00.00 migration/0

```


Again, showing klibido as a big CPU hog right now becuase I'm.. uh.. reading a lot of news articles on usenet ;)

---

### Post by greg m on 2006-08-30
top is live, and i think it will help. i could not find a working copy paste.how were you able to put the code here?

thank you
greg

---

### Post by S1NGH on 2006-08-30
you can copy and paste the code, you can highlight with the mouse and use the middle mouse button to paste it.

---

### Post by chadk on 2006-08-30
copying and pasting is really irrelevent... the key here is which item(s) are listed on top of the TOP output?  Those are taking the most CPU.

---

### Post by greg m on 2006-08-30
at the top of tops is
4373 root the virt is 72456 cpu is 1.3
5435 oem 1568-115m virt cpu .3
4469 cups 4204 virt cpu .3
i just looked at users and i have 2????

when i instaled ubuntu , it would not install, then i installed the oem version. grub says i have two ubuntu `s on my computer. how can i check? and remove the other one? or should i just reinstall?

---

### Post by annda on 2006-08-30
i suppose you have two kernels, not two ubuntus. please note down the grub entries and post them here (or the appropriate part of your /boot/grub/menu.lst file)

what do you mean by two users? root is fine, some processes, such as init or Xorg, are owned by root. yours are owned by oem.

---

### Post by greg m on 2006-08-30
top-18:57:26 up 16 min,2 users,load average:0.09,0.25,0.27
tasks: 84 total, 1 running,83 sleeping, O stoped, 0 zombie
cpu: 1.3%,0.3% sy,0.0 ni,99.7% id 0.0% wa,0.0% hi,0.0%si
mem: 515012k total,364580k used,150440k free,8600k buffers
swap:851404k total, 0k used,851404k free,189348k cached

this is what top says now, or as fast as i could type.
i`ll have the grub list up soon.how are things in germany? i miss the beer.

thank you greg

---

### Post by AntiFlash on 2006-08-30
are you running off of the live CD or do you have ubuntu installed on your HD?

---

### Post by greg m on 2006-08-30
6 is installed on another computer i had 5 installed, it went easy then 6 came out so i went to a faster computer (800 mhz to 2.5 gig)then the update.
when i started firefox the time my cpu was at 98% . before the update it would not stay blue as long.

thank you greg

---

### Post by greg m on 2006-08-31
when i first start the computer and go to grub i get
gnu grub version 0.97 (639k lower/523200k upper memory)

ubuntu,kernel 2.6.15-26-k7
ubuntu,kernel 2.6.15-26-k7 (recovery mode)
ubuntu,kernel 2.6.15-26-k7
ubuntu,kernel 2.6.15-26-k7 (recovery mode)
ubuntu,memtest86+

the  /boot/grub/menu,1st file is






file:///home/oem/Desktop/menu.lst
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
# groot=(hd0,0)

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

title		Ubuntu, kernel 2.6.15-26-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-26-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-26-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-26-k7 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-26-k7
boot

title		Ubuntu, kernel 2.6.15-23-k7
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hdc1 ro quiet splash
initrd		/boot/initrd.img-2.6.15-23-k7
savedefault
boot

title		Ubuntu, kernel 2.6.15-23-k7 (recovery mode)
root		(hd0,0)
kernel		/boot/vmlinuz-2.6.15-23-k7 root=/dev/hdc1 ro single
initrd		/boot/initrd.img-2.6.15-23-k7
boot

title		Ubuntu, memtest86+
root		(hd0,0)
kernel		/boot/memtest86+.bin 
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

---

### Post by annda on 2006-08-31
the boot menu and the menu.lst are inconsistent, are you sure you've got the menu right? because it says you have two 26 kernels (and i'm not sure if it's at all possible).

the menu.lst shows that you have two kernels, an older (23) and a newer one (26). that's not a bad thing in itself because only one is loaded at boot, so the other one doesn't hog your resources or anything.

i fyou want to free some disk space, you can uninstall the old kernel in synaptic and grub should update the menu automatically.

---

### Post by greg m on 2006-08-31
thank you , i`ll give it a try. i was thinking it was because of the failed install before i was able to install the oem.

---

