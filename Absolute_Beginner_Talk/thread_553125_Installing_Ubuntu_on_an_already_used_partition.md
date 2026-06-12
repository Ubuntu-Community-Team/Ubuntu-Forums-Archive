---
title: "Installing Ubuntu on an already used partition"
date: 2007-09-17
forum: Absolute Beginner Talk
---

### Post by fedja_b on 2007-09-17
Hello every one, 

First I would like to say that I am a complete newbie to Linux and I must I am very excited to start using it. Second, I've searched for this question and haven't come up with a satisfactory answer. The question is: 
Currently I have a Windows box with 3 partitions, all of whom are used. Now, can I install Ubuntu on one of these partitions (particularly the 3rd one, E: which has most free space, around 20 Gb) WITHOUT formatting it so the data that is there remains intact? 

Thanks in advance for your time and your replies!

---

### Post by forestpixie on 2007-09-17
you would need to shrink the partition to free up the space for ubuntu, you would need to format that new partition in order to install. 

Don't really believe you'll be able to install without formatting - they use different file types

---

### Post by Shazaam on 2007-09-17
Yes you can. There are many ways to do it. You can run Ubuntu as a VirtualMachine (using Vmware, VirtualBox, etc), as a live cd (very slow but the best way to test out Linux), or as a multi-boot system by resizing your partitions.
Others have reported success using WUBI....
[http://ubuntuforums.org/forumdisplay.php?f=234](http://ubuntuforums.org/forumdisplay.php?f=234)

---

### Post by slira on 2007-09-17
> **fedja_b said:**
> 
Currently I have a Windows box with 3 partitions, all of whom are used. Now, can I install Ubuntu on one of these partitions (particularly the 3rd one, E: which has most free space, around 20 Gb) WITHOUT formatting it so the data that is there remains intact? 


Hi
the only answer to your last question is NO, sorry...
The installation demands formatting.
What you can do is to save your data, shrink the 3rd partition making 20Gb free, copy data there again - shrinking without saving data first (even after defragment) is a risk...

then use the 20 Gb unallocated to install ubunto; 

during installation, use manual partition and do something like
boot: 100 mb (if you do not have another OS in that hdd; otherwise don't need this partition)
root: 5Gb - ext3
swap: 1,5 x your RAM - swap
home: as big as you can in your remaining disk... - ext3 - this one will be a logical, but it helps using the file system in ubuntu

ubuntu must reformat during installation; I tried once with pre-made partitions (ext2 and ext3 and swap) and got errors... never tried again.

be very careful when deciding mounting points - DO NOT destroy your MicroCrap OS  :lolflag:

after installation, when you reboot you will get a GRUB menu, where you are asked to decide what OS you want to boot from.

booting ubuntu you can change that menu editing menu.lst as root

in a shell cd to /boot/grub

[FONT="Courier New"]cd /boot/grub
[/FONT]

Edit the menu file

[FONT="Courier New"]sudo gedit menu.lst
[/FONT]

2 things I always change:
- timeout
- at the end of the file you can comment [#] the options you do not want in the menu and the name [title] of those you want

You can also change the default OS - the one that boots if you do nothing

be careful not to change critical stuff, or you will not boot again :lolflag:

notice that grub counts hdd and partitions from 0 (1st disk 1st partition is hd (0,0)

Have fun!
slira

---

### Post by fedja_b on 2007-09-18
Thanks for your replies! Yes, I also thought that formatting would be inevitable, but if I srhink my existing partition, will the data there remain safe?

---

### Post by forestpixie on 2007-09-18
It 'should' - but you never know what could happen, ligtning strikes, power cuts, hardware failure - the thing is to make sure that you backup - just in case :) 

Make sure you defrag a couple of times, I turned off the page file before I did it as well. Turn it back on afterwards.

---

### Post by slira on 2007-09-19
> **fedja_b said:**
> , but if I srhink my existing partition, will the data there remain safe?

better safe then sorrow...... I would back-it-up before any shrinking of the partition. If you were shrinking the partition where the OS is, it would be worse... only data, is just a question of time copying it.

best luck, and tell us when your linux is running!
slira

---

### Post by fedja_b on 2007-09-19
Yes, I understand the importance of backup, but this is a partition where my program files are stored, so backing up around 30 gigs of data is not practical to say the least, not to mention not fun :(. I'm installing without a backup, pure test of my luck, and I hope everything goes ok.

---

### Post by slira on 2007-09-20
> **fedja_b said:**
> Yes, I understand the importance of backup, but this is a partition where my program files are stored, so backing up around 30 gigs of data is not practical to say the least, not to mention not fun :(. I'm installing without a backup, pure test of my luck, and I hope everything goes ok.

well, what happened? did you manage? is it working?

---

