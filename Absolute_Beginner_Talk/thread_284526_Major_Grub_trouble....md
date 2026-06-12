---
title: "Major Grub trouble..."
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by Oldmate on 2006-10-25
I've recently had a friend upload some Ubuntu 6.06 updates, and when I've gone to reboot my laptop, my grub to login to Ubuntu or Win XP has changed and I cannot boot in at all. (He's not sure how to fix it either).

Am an absolute novice on this, so can anyone describe in detail how to fix the grub so that I can resume normal operation to boot into Ubuntu or Windows from grub?

Any help much appreciated.

Thanks, Mark.

---

### Post by Old Pink on 2006-10-25
Rightio, I'll help you on this one. :) 

What error are you getting? Can you see your OS list, or do you just get error 22?

---

### Post by louieb on 2006-10-25
Check the link in my signature. The post it points to is a good description of the steps you need to go through to fix Grub. Hope it helps.

---

### Post by Old Pink on 2006-10-25
Woah hold the phone! Who says he needs to reinstall grub? 

My GRUB used to update wrong, so every option pointed to (hd0,1) instead of (hd0,0) and hda2 instead of hda1. 

Of course, I only had to change the defaults and now it updates fine. If this person's friend messed with menu.lst, it could be as simple as editing a few lines. 

Think before re-installing GRUB. ;)

---

### Post by louieb on 2006-10-26
> Old Pink  	Woah hold the phone! Who says he needs to reinstall grub? 
That is true we don't know just what or where the problem is.
So Oldmate a couple of questions.
When you boot does the grub menu get dispayed?
If you don't get to the menu then something along the lines of
```
grub error ##
```
should be displayed. What grub error number got displayed?
If you got the menu but after making the selection it failed to boot the operating system please describe as best you can what messages if any it displayed. Try and let us know what the last two said.

---

### Post by Oldmate on 2006-10-28
Hi Louieb,
Here is the screen message when powering up my laptop:

Booting 'Ubuntu, kernel 2.615-27-386

root (hd0,0)
 Filesystem type unknown, partition typr 0x7
kernel /boot/vmlinuz-2.6.15-27-386 root=/dev/sda1 ro quiet splash

Error 17: Cannot mount selected partition

Press any key to continue... 

** When I press any key, the grub comes up with:

Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernel 2.6.15-27-386 (recovery mode)
Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernel 2.6.15-27-386 (recovery mode)
Ubuntu, kernel 2.6.15-27-386
Ubuntu, kernel 2.6.15-27-386 (recovery mode)
Ubuntu, memtest86+

** When I click on any of the above, the first error message comes up - Any Ideas?

---

### Post by confused57 on 2006-10-29
You might want to boot up with the desktop live cd, open a terminal, and post the output of:
```
sudo fdisk -l
```
The -l is a small "L".

You can reinstall grub with the live cd:
[http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351)

---

### Post by louieb on 2006-11-02
Did you get it working?
[LIST]
[*]Do I have this right. The laptop was dual booting XP and Linux.
[*]You applied some updates.
[*]Now Ubuntu won't boot and the XP option is gone. 
[*]Congratulations you have just been screwed by the Debian grub updater.
[/LIST]You have a couple of options.
[LIST]
[*]1. Reinstall everything. Oh you don't want to do that.
[*]2. Use a live CD and edit your /boot/grub/menu.lst file. Most live CD's are somewhat of a pain to use because you have umount and mount the partition with write access. It's not hard but there are quite a few steps you need to do and can get frustrating. 
[*]If you go this route I suggest you get the Puppy Linux live CD. It has a GUI for mounting and un-mounting partitions and a nice text editor.   
[*]I'm not going to describe what your menu.lst file should look like because it depends on how your PC is setup. There are quite a few post here that describe the process.
[*]3. Reinstall grub and hope it alters your menu.lst correctly. Look for post by a guy named Bulldog he describes how to do it quite well.
[/LIST]

---

