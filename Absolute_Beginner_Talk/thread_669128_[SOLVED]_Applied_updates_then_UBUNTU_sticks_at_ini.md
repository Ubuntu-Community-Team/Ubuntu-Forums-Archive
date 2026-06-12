---
title: "[SOLVED] Applied updates then UBUNTU sticks at initramfs prompt??"
date: 2008-01-16
forum: Absolute Beginner Talk
---

### Post by Sivee on 2008-01-16
Hi,
I am running Ubuntu on a Fit PC. It has been fine for a while then today I was warned that there were updates available. I clicked to obtain the updates and it identified a 111 updates.  I allowed it to perform the updates and it said at the end that they had all been applied and it needed to re-boot. I allowed it to do that and it re-booted.

The Ubunto logo came up and the orange progress bar started to appearand then it just sat with a small amount of progress bar showing.  After about 5 minutes the logo disappeared and I was at a prompt that says (initramfs) and above that it says:

BusyBox v1.1.3 (Debian 1:1.1.3-5ubuntu7) Built in shell (ash)
Enter 'help' for a list of built-in commands.

I am a complete noob with Linux so have not a clue what to do next.
Any help appreciated.

Siv

---

### Post by SOULRiDER on 2008-01-16
Do this. When GRUB appears (what asks you to select what OS you want) select the Ubuntu option but dont press enter, press 'e' instead and in the second of thurd line delete quiet and splash. See if you get any additional errors.

Also, im guessing your kernel got upgraded, try to boot with an older kernel.

Finally, try booting in recovery mode and updating (just in case there are further updates or something was left unconfigured) by using these commands
```
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by Sivee on 2008-01-16
Soulrider,
I don't see the boot options it flashes by too quickly, however I find if I press ALT+F1 I can see the folowing:

booting 'Ubuntu 7.10, kernal 2.6.22-14-generic'

root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=98a7d0ac-5771-4f39-Bef1-cb03b
27184d8 ro quiet splash
    [Linux-bzImage, setup=0x1e00, size=0x1acc58]
initrd /boot/initrd.img-2.6.22-14-generic
    [Linux-initrd @ 0xe4ef000, 0x6e6c30 bytes]

Loading, please wait...
[    15.492122] atkbd,c: Failed to enable keyboard on isa0060/serio0
             check root= bootarg cat /proc/cmdline
             or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/98a7d0ac-5771-4f39-bef1-cb03b27184d8 does not exist. Dropping to a shell!

Then it goes to the mesage I mention in my post.

Can you decipher this stuff??

---

### Post by SOULRiDER on 2008-01-16
Did you change any of your partitions or something?
Im asking that because of
> /dev/disk/by-uuid/98a7d0ac-5771-4f39-bef1-cb03b27184d8 does not exist

Im kinda lost here, im gonna tag your post so others form the Unanswered post team can some help you.

---

### Post by ajmorris on 2008-01-16
> **Sivee said:**
> Soulrider,
I don't see the boot options it flashes by too quickly, however I find if I press ALT+F1 I can see the folowing:

booting 'Ubuntu 7.10, kernal 2.6.22-14-generic'

root (hd0,0)
 Filesystem type is ext2fs, partition type 0x83
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=98a7d0ac-5771-4f39-Bef1-cb03b
27184d8 ro quiet splash
    [Linux-bzImage, setup=0x1e00, size=0x1acc58]
initrd /boot/initrd.img-2.6.22-14-generic
    [Linux-initrd @ 0xe4ef000, 0x6e6c30 bytes]

Loading, please wait...
[    15.492122] atkbd,c: Failed to enable keyboard on isa0060/serio0
             check root= bootarg cat /proc/cmdline
             or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/98a7d0ac-5771-4f39-bef1-cb03b27184d8 does not exist. Dropping to a shell!

Then it goes to the mesage I mention in my post.

Can you decipher this stuff??

hi there,
after the boot fails, could you please log into the terminal (if there is no option to, reboot and go into the recovery option from grub)
it will say type the root password for maintenance, or press ctrl+d to continue. Type in your root password (no characters will show whilst you do this, but rest assured, they are being entered)

now, onto the problem,
from doing these updates, your uuid was changed, IMHO, this debian method of mounting the root partiion via fstab with a uuid is unconventional, i dont see why they do so.. the easiest method, is to remove it.

could you please post the contents of your /etc/fstab file.

If you dont have access to another computer to type out the contents of this file whilst in this recovery mode, you can boot into the ubuntu live cd, and edit the fstab file from your partition in /media.

(you do not need to post the entire contents of your fstab if you are typing it out, just the line that will look somewhat like this:
/dev/sda1 / reiserfs notail,noatime,nodiratime 0 0

(yours will have a UUID=some number entry, and where mine says reiserfs, yours will probably have ext3)

Once you have posted this line, or the whole file... i can walk you through the changes that need to take place to remove the UUID entry

---

### Post by Sivee on 2008-01-16
No, I just applied the updates and re-booted when it said it wanted to re-boot and that was it.

The Fit PC is a slightly strange beast, it runs on custom hardware, so I suspect that the update has assumed I am running more standard i386 hardware and in fact it is a custom.

I have just found the answer in the Fit-PC forums:

1. Restart the PC by doing CTRL+ALT+Del
2. As soon as the PC restarts press Esc, this drops you into the 3 different boot options hit "e" to edit the default boot choice.
3. Locate the line that begins: 
     kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=98a7d0ac-5771-4f39-Bef1-cb03b
4. When on that line press "e" again to edit that line.
5. Change it to:
      kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash
6. Press ENTER to make the change, this takes you back to the list of boot commands.
7. Press "b" to boot and Ubuntu will start.
8. When in Ubuntu in Graphical mode, open a terminal window and type:
     sudo vim /boot/grub/menu.lst
9. You will be asked for your "fit" user password, enter that and you are into the menu.lst file for editing.
10.  Edit the menu.lst file and make the line that looks like the one in 3 above look like the one in 5 above.

I am OK up until line 10 as I don't know what the vim editing commands are, so I am about to do some reading up on vim so that I can complete this process.

If you know the process of how to do this in vim, pleaase post here for noobs like me!

---

### Post by Sivee on 2008-01-16
AJMorris,
Sorry your question must have come in as I was replying to the one from Soulrider.

I am back into Ubuntu after reading the posts I found relating to this on the Fit-PC forums and doing what I said in my previous post here.  The help I need now (I think) is just editing my menu.lst file so that when I next re-boiot the Fit-PC id doesn't go back to the same problem.

I need to understand how vim works.  I tried editing it in the ubuntu text editor, but it wouldn't let me save the file as I do not have permission to change it.

When i tried to make changes in Vim I was clearly not understanding how that editor works as the cursor kept jumping to the bottom of the display and responding like I was trying to do a search for something??

I will understand how you Linux boys think eventually!

---

### Post by SOULRiDER on 2008-01-16
The problem was just what i thought, it was looking for a bad root device.
To edit you dont need vim, you can just use gedit which is way easier.

Press alt +f2 and type
```
gksu gedit /boot/grub/menu.lst
```
You will see something like
```
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=UUID=98a7d0ac-5771-4f39-Bef1-cb03b
27184d8 ro quiet splash

```
Make it look like
```
root (hd0,0)
kernel /boot/vmlinuz-2.6.22-14-generic root=/dev/hda1 ro quiet splash

```
replace hda1 with your root device which i believe is hda1 :P
Save and youre ready to go :) the changes are permanent.

---

### Post by Sivee on 2008-01-16
Yep that works, I can now re-boot and Ubuntu comes up without any problems.

Will I have to go through this stuff again if I am prompted that there are updates?

Also have you any idea why doing an update would have messed the boot files?

(Noob trying to understand).

Cheers for your help.

---

### Post by ajmorris on 2008-01-17
> **Sivee said:**
> Yep that works, I can now re-boot and Ubuntu comes up without any problems.

Will I have to go through this stuff again if I am prompted that there are updates?

Also have you any idea why doing an update would have messed the boot files?

(Noob trying to understand).

Cheers for your help.

just in case you ever have to use vim, to edit the file, you use the insert key.
then to save and exit, you press Esc to get out of edit mode
then use ':wq' which does a write, and then a quit.

But, no, you will not need to go through this again, the UUID entry has been removed from boot, so it will not get this error again. There are many reasons why this code could have changed... but basically a UUID is a Universally Unique Identifier, something in your updates changed the value of this, it happens all the time, but without having a UUID being used to boot, instead of the physical block device from /dev, you wont get this happening again :)

---

### Post by Sivee on 2008-01-17
AJMorris,
Thanks for the advice on using vim. I used vim after finding the vim procedures on the net. I didn't see SoulRider's advice about using GEdit until aftewr I had already done it in vim. 

I have to say I find it very reminiscent of the old "edlin" program that we used to use in the dark days of DOS on the PC. (or maybe edlin was reminiscent of Unix's vi (I don't know which was around first).

I am pleased that the fix will "stay put" now that I have changed the reference to \dev\hda1.

Thanks for all your help.  I have moved forward another step with my understanding of Linux.

---

### Post by SOULRiDER on 2008-01-17
Vim is Vi improved, AFAIK Vi is ancient :P

Also, could you please markt he thread as solved? If you dont know how to do such thing check this out. [https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

---

### Post by Sivee on 2008-01-18
SoulRider,
Sorry, wasn't aware I needed to do that, it is now done!

Thanks again for your help.

---

