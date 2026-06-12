---
title: "help installing tiny core in virtual box"
date: 2011-03-24
forum: Any Other OS
---

### Post by cain071546 on 2011-03-24
I'm running Mint 8 Helena on a Toshiba laptop
i have Virtual-box 4 installed
Ive been trying to get tiny core installed on it 
but all the threads and posts i found through Google dead end
i cant find a walk-through that works Ive been at it 2 days 
would someone help me

this is as close as i can get 
[http://www.youtube.com/watch?v=RGre8VxSlcY](http://www.youtube.com/watch?v=RGre8VxSlcY)

even that doesn't work
after reboot i get "kernel panic not syncing" error

---

### Post by cain071546 on 2011-03-24
bump

---

### Post by cain071546 on 2011-03-24
bump#2

---

### Post by cain071546 on 2011-03-25
bump#3

---

### Post by highspider on 2011-03-25
tiny core on hard disk; I have no idea what that is but I know that I had to install 
[http://www.virtualbox.org/wiki/Linux_Downloads](http://www.virtualbox.org/wiki/Linux_Downloads)

virtualbox-4.0_4.0.4-70112~Ubuntu~maverick_i386.deb

because synaptic virtualbox-ose didn't have the stuff I needed for what I used mine for.

[COLOR=Red]DO NOT[/COLOR] install the one I posted I only mentioned this for the person that helps you, (who knows tiny core) in case it could be an issue.

---

### Post by ~Plue on 2011-03-25
/nvm

---

### Post by farizluqman on 2011-04-01
In this video
[http://www.youtube.com/watch?v=RGre8VxSlcY](http://www.youtube.com/watch?v=RGre8VxSlcY)

you should see the very specific instruction, you might has been missed:

This is a video cast on how to install Tiny Core in your hard disk. This video cast is using Virtualbox to virtualize . have a hard disk with 1 GB of size.

1. open Appbrowser
2. search for cfdisk.tcz, then click GO button (Go means Install, OK~), then do the same on grub-0.97-splash.tcz
3. if everything is ok, then open terminal
4. type "sudo su"
5. type fdisk -l for
6. type "cfdisk /dev/hda" (hda stands for Your Own Driveletter.)
7. make space
8. when done, type "rebuildfstab" so you can refresh the drive list
9. type "mkfs.ext3 /dev/hda1" where hda1 is your own drive letter. 
10. type "mount /mnt/hda1" where hda1.. urgh...
11. type "mkdir -p /mnt/hda1/boot/grub"
12. type "mount /mnt/hdc" where.. the hdc.. is.. your.. cd rom drive letter. 
13. type "cp -p /mnt/hdc/boot/* /mnt/hda1/boot/"
14. type "mkdir -p /mnt/hda1/tce"
15. type "touch /mnt/hda1/tce/mydata.tgz"
16. type "cp -p /usr/lib/grub/i386-pc/* /mnt/hda1/boot/grub/" to install grub
17. type "vi /mnt/hda1/boot/grub/menu.lst" to make a new grub menu list
18. press "I" key to enter edit mode. then include 

default 0
timeout 10
title tinycore
kernel /boot/bzImage quiet
initrd /boot/tinycore.gz

19. type ": (space)x" to exit and save changes that has been made (this forum turned : x to smiley)
20. type "grub"
21. In the grub prompt, type

root (hd0,0)
setup (hd0)
quit 

21. type umount /mnt/hdc, then eject /dev/hdc
22. reboot then completed!!!!!!!!!!!!!!

---

