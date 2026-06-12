---
title: "step by step boot for ubuntu only?"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by kujaabi on 2008-03-15
My computer only runs Ubuntu and Kubuntu. After making some networking changes, I can no longer boot my computer!! When it boots it freezes at step *Starting NFS common utilities* which it does not execute. Nothing I've tried gets me past this point. I do NOT want to have to start all over and reinstall Ubuntu from scratch!! [-o<  Is there anyway to boot step by step so that I can skip the NFS utilities start problem?
I'm without my computer until I can get this fixed.  ](*,)
Thanks!

---

### Post by bsharp on 2008-03-15
have you tried booting into recovery mode?  That will boot you into single-user mode (init 1) and you should be able to change your networking settings back.

*note: it will boot you to a command-line interface, and if you need a GUI just
```
startx
```

---

### Post by kujaabi on 2008-03-15
yes I've tried recovery mode but it just went along like before and stopped in the same place. How do I do what you suggested?

---

### Post by kujaabi on 2008-03-15
> **bsharp said:**
> have you tried booting into recovery mode?  That will boot you into single-user mode (init 1) and you should be able to change your networking settings back.

*note: it will boot you to a command-line interface, and if you need a GUI just
```
startx
```

Thanks. I need a bit more info: What is single-user mode like? what does (init) 1 mean? *startx* was not unrecognized and not in the list I found. I'm a bit confused--sorry!

---

### Post by glennric on 2008-03-15
Single user mode is what you are booted to if you select "Recovery mode" from the grub menu.  He is saying to boot to recovery mode and then type "startx" in a terminal if you want a gui.

---

### Post by kujaabi on 2008-03-15
Thanks. Do I choose *c* command line? or *edit* those are the only choices I see.

---

### Post by bsharp on 2008-03-15
Sorry, I should have been more clear.  depending on how many kernels you have installed, pick the second option in your boot menu which should say

Ubuntu-7.10-2.24-generic (Recovery Mode)

or something similar and it will boot you into recovery mode.

---

### Post by kujaabi on 2008-03-15
What do I do from here. *c* or *e* option?

---

### Post by glennric on 2008-03-15
> **kujaabi said:**
> Thanks. Do I choose *c* command line? or *edit* those are the only choices I see.

Where are you that you see these options?

---

### Post by kujaabi on 2008-03-15
when Hightlighted the (recovery mode) before pushing enter. If I simply push enter it begins recovery mode and again stops at the NFS place. Gotta go. Thanks for your help. I hope I can get some help later to continue fixing this.

---

### Post by kujaabi on 2008-03-15
When I start the computer I push <esc>. The screen I then see is:

Ubuntu 7.10, kernel 2.6.22-14-generic
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
Ubuntu 7.10, memtest86+



Use arrow keys to select which entry is highlighted. Press <enter> to boot the selected OS, 'e' to edit the command before booting, or 'c' for command line



------------------------------------

If I press 'e' I see these lines to choose from:

root (hd0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=784a14ba-03ba-4b4d [then an arrow to the right]
initrd /boot/initrd.img-2.6.22-14-generic


Below these three line I have these instructions:

Use arrow keys to select which entry is highlighted. Press 'b' to boot, 'e' to edit selected command in the boot sequence, 'c' for command-line, 'o' to open a new line after ('0' for before) the selected line, 'd' to remove the selected line, or escape to go back to main menu.

-------------------------------------------------------

If I choose 'e' for example I get the following:

[minmal] BASH-like line editing is supported. For the first word, TAB lists possible command completions. Anywhere else TAB lists the possible completions of the device/filename. ESC anytime exits.


grub edit> root (hd0,0)

----------------------------------------

This last screen and menu explanation is similar if I had chosen another line above.

I have no idea where I'm supposed to go or what to do to remove the offending NFS problem.

---

### Post by glennric on 2008-03-15
Have you tried selecting 
Ubuntu 7.10, kernel 2.6.22-14-generic (recovery mode)
and then hitting enter to boot?

---

### Post by kujaabi on 2008-03-15
Yes, and it does its thing and stops at *Starting NFS common utilities* Everything I try ends up there.

---

### Post by glennric on 2008-03-15
Hmm, editing the grub boot parameters won't help you here.  You are probably going to have to boot to a live cd and make some changes.

---

### Post by kujaabi on 2008-03-15
Yes I have a live CD. How should I boot from it to make the changes?

---

### Post by xeth_delta on 2008-03-15
Try also the following: Go to the line describing your regular kernel. Press "e" to edit. Go to the end of the line and add "init 1" or "init S". Press ENTER to save. Press "b" to boot. Let us know what happens.

---

### Post by kujaabi on 2008-03-15
I selected 

Ubuntu 7.10, kernel 2.6.22-14-generic

pressed *e* to edit

then I get another screen. which of these do I add the "init1" or "init S"to?


root (hd0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=784a14ba-03ba-4b4d [then an arrow to the right]
initrd /boot/initrd.img-2.6.22-14-generic

---

### Post by xeth_delta on 2008-03-15
> **kujaabi said:**
> I selected 

Ubuntu 7.10, kernel 2.6.22-14-generic

pressed *e* to edit

then I get another screen. which of these do I add the "init1" or "init S"to?


root (hd0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=784a14ba-03ba-4b4d [then an arrow to the right]
initrd /boot/initrd.img-2.6.22-14-generic

To the kernel line and it is "init 1", be careful. :)

---

### Post by kujaabi on 2008-03-15
Neither 

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=784a14ba-03ba-4b4d-99ec-51b80036bf7c ro quiet splash init 1 nor init S worked.

---

### Post by xeth_delta on 2008-03-15
> **kujaabi said:**
> Neither 

kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=784a14ba-03ba-4b4d-99ec-51b80036bf7c ro quiet splash init 1 nor init S worked.

Same error? I agree with previous posters, you might need tho start from a live cd to correct the problem.

---

### Post by kujaabi on 2008-03-15
I've started it and get the basic desktop (with the install) ico. What do I do and where do I go from there? I can only get onto the new desktop loaded by the CD

---

### Post by xeth_delta on 2008-03-15
Up to this point I am not sure what the error is on your system, but at least I will provide a way to log-in to your installation on a terminal from the livecd.
Open a terminal. Let's assume the partition where Ubuntu is installed is sda1:
```
sudo mkdir /mnt/linux
sudo mount /dev/sda1 /mnt/linux
sudo chroot /mnt/linux /bin/bash
```
Now that terminal will behave as if you were logged in in your computer. I would say try reconfiguring nfs-common, once there. Maybe this will work:
```
sudo dpkg-reconfigure nfs-common
```

---

### Post by glennric on 2008-03-15
First open terminal (Applications->Accessories->Terminal)
Then run the following commands:
```
sudo fdisk -l
```
Find the device name of your root partition.  It is /dev/sd?? or /dev/hd??.  It should be an ext3 partition.  If you have more than one ext3 partition it is probably the first one.  
Then
```
sudo mkdir /media/disk
sudo mount /dev/???? /media/disk
sudo chroot /media/disk
```
Then type "ls" to see if it looks like your root partition.  If there is a "boot" directory it should be the right one.  If not try one of the other /dev/???'s from fdisk.  (type "sudo umount /media/disk", then repeat with other partition)
Now if all that worked then type
```
sudo apt-get remove --purge nfs-server
exit
sudo umount /media/disk
```
Then reboot and see if that helps.

---

### Post by kujaabi on 2008-03-15
ok, I ended up with the following:



* Stopping NFS common utilities
start-stop-daemon: nothing in /proc - no mounted? (success)           [OK]

* Stopping NFS common utilities
start-stop-daemon: nothing in /proc - no mounted? (success)           [OK]



Now what?

---

### Post by kujaabi on 2008-03-15
I rebooted. Same problem it froze. Booting from the live CD only takes me to a completely separate ubuntu desktop etc. like I am a different user. The freezing problem is with my regular setup. Is there any way that I can remove the networking utilities that seems to be freezong up? I don't need the networking right now.

---

### Post by xeth_delta on 2008-03-15
> **kujaabi said:**
> I rebooted. Same problem it froze. Booting from the live CD only takes me to a completely separate ubuntu desktop etc. like I am a different user. The freezing problem is with my regular setup. Is there any way that I can remove the networking utilities that seems to be freezong up? I don't need the networking right now.

Did you try the suggestions glennric and I presented?
Once chroot is done try also:
```
sudo aptitude reinstall nfs-common 
```

---

### Post by kujaabi on 2008-03-16
Thanks for all your help. I have reinstalled Ubuntu and Kubuntu in another partition. I will try to show the problem to a local linux group. I appreciate your assistance!!

---

### Post by xeth_delta on 2008-03-16
> **kujaabi said:**
> Thanks for all your help. I have reinstalled Ubuntu and Kubuntu in another partition. I will try to show the problem to a local linux group. I appreciate your assistance!!

You're welcome! Please let us know what the problem was, once you find out.

---

