---
title: "After installation reboot, comp hangs on black screen"
date: 2007-07-08
forum: Absolute Beginner Talk
---

### Post by snwbord2456 on 2007-07-08
First off I am pretty new to Ubuntu. Secondly I recently re-installed Ubuntu after trying to install a cursor scheme that cause Ubuntu to hang on a black screen with the loading cursor.

Thread here:
[http://ubuntuforums.org/showthread.php?t=495236](http://ubuntuforums.org/showthread.php?t=495236)

Because of this I decided to reinstall Ubuntu.
Now after reinstalling Ubuntu when the computer reboots from the installation I get the

Starting Up...

then it hangs on a black screen. I have an ATI card and used the text installer but I havent been able to add the drivers or anything like that because I can only get to a black screen.

Edit: if I restart and hold down the buttons to get the virtual terminal I can get that, and while it did take much longer than normal to reach the command prompt after doing so I got the menu.lst. I had to type it up because this post is ebing done from my desktop and I'm installing on my laptop.

defauly num

default 0

timeout sec
timeout 3

hiddenmenu
hiddenmenu

Pretty Colours
color cyan/blue white/blue

password
password topsecret

examples

title Windows 95/98/NT/2000
root (hd0,0)
makeactive
chainloader +1

title Linux
root (hd0,1)
kernel /vmlinuz root=/dev/hda2 ro

Start Default Options
defualt kernel options
e.g. kopt=root=/dev/hda1 ro
kopt_2_6_8=root=/dev/hdc1 ro
kopt_2_6_8_2_686=root=/dev/hdc2 ro
kopt=root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439f47e8 ro

Setup crashdump menu entries
e.g. crashdump=1
crashdump=0

default grub root device
e.g. groot=(hd0,0)
groot=(hd0,0)

should update-grub create alternative automagic boot options
e.g. alternative=true
alternative=false
alternative true

should update-grub lock alterbnative automagic boot options
e.g. lockalternative=true
lockalternative=false
lockalternative=false

additional options to use with the default boot option, but not with the alternatives
e.g. defoptions=vga=791 resume=/dev/hda5
defoptions=quiet splash

should update-grub lock old automagic boot options
e.g. lockhold=false
lockhold=true
lockhold=false

Xen hypervisor options to use with the default Xen boot option
xenhopt=

Xen Linux kernel options to use with the default Xen boot option
xenkopt=console=tty0

altoption boot targets option
multiple altoptions lines are allowed
e.g. altoptions=(extra menu suffix) extra boot options
altoptions=(recovery) single
altoptions=(recover mode) single

controls how many kernels should be put into the menu.lst
only counts the first occurence of a kernel, not the alternative kernel options
e.g. howmany=all
howmany=7
howmany=all

should update-grub create memtest86 boot option
e.g. memtest86=true
memtest86=false
memtest86=true

should update-grub adjust the value of the default booted system can be true or false
updatedefaultentry=false

End Default options

title Ubuntu, kernel 2.6.20-15-generic
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439f47e8 ro quiet splash
initrd /boot/initrd.img-2.6.20-15-generic
quiet
savedefault

title Ubuntu, kernel 2.6.20-15-generic (recovery mode)
root (hd0,0)
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=a86b2426-7c84-4b5e-8bca-4ff1439447e8 ro single
initrd /boot/initrd.img-2.6.20-15-generic

title Ubuntu, memtest86+
root (hd0,0)
kernel /boot/memtest86+.bin
quiet

---

### Post by snwbord2456 on 2007-07-08
I tried to do apt-get update (without the sudo) and I got

E: Could not open lock file /var/lib/apt/lists/lock - open (13 permission denied)
E: Unable to lock the list directory

Is this a root conflict or shoudl I do something else with the menu.lst, I saw a couple things that sould should update next to them, should I do that or should I just install the ATI drivers like I did last time?

---

