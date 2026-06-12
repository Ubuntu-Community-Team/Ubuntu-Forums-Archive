---
title: "Swap problem"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by gentlemanmasher on 2006-11-29
I had an fstab error that i fixed.  then it said swap signature couldn't be found so I followed the following link

[http://www.ubuntuforums.org/showthread.php?t=307009&highlight=swap+signature](http://www.ubuntuforums.org/showthread.php?t=307009&highlight=swap+signature)

I have done everything edited my fstab and reformated the swap on hda5.

Here is what I put in for my fstab
 /dev/hda5   none swap  sw 0   0

When I login I keep getting the login screen I then enter my user name and password and get the nvidia splash screen again.  When I boot in recovery mode I do not get the swap error anymore I just can' login.

Help Please I'm stuck

---

### Post by zgornel on 2006-11-29
Is swap activated on the system? Try this: after a fresh boot, log in, open a teminal or go into one of the consoles (ALT+CTRL+F1), type *free -m* and see if you have some number at the swap field. If you do, I can't help you. If you don't, do this:
1. Check with Gparted so that the swap partition is ok and not of <unknown> type or something like that. 
2. If it is ok, leave gparted. If it's not, format it as swap.
3. Go to a terminal and type : mkswap /dev/<swap partion>. It should generate a UUID, write it down. Then, do a *swapon -a*. Check again *free -m* to see if the swap is used now.
4. Edit you fstab: instead of /dev/hda5 put UUID=<mkswap generated uuid>
5. Edit your /etc/initramfs-tools/conf.d/resume and put in it just : RESUME=UUID=<mkswap generated uuid>
6. Check /boot/grub/menu.lst and remove any resume=<something> kernel parameter.
7. Reboot. Check again after reboot if swap is enabled and do a hibernate test.

---

### Post by gentlemanmasher on 2006-11-29
> **zgornel said:**
> Is swap activated on the system? Try this: after a fresh boot, log in, open a teminal or go into one of the consoles (ALT+CTRL+F1), type *free -m* and see if you have some number at the swap field. If you do, I can't help you. If you don't, do this:
1. Check with Gparted so that the swap partition is ok and not of <unknown> type or something like that. 
2. If it is ok, leave gparted. If it's not, format it as swap.
3. Go to a terminal and type : mkswap /dev/<swap partion>. It should generate a UUID, write it down. Then, do a *swapon -a*. Check again *free -m* to see if the swap is used now.
4. Edit you fstab: instead of /dev/hda5 put UUID=<mkswap generated uuid>
5. Edit your /etc/initramfs-tools/conf.d/resume and put in it just : RESUME=UUID=<mkswap generated uuid>
6. Check /boot/grub/menu.lst and remove any resume=<something> kernel parameter.
7. Reboot. Check again after reboot if swap is enabled and do a hibernate test.

a couple questions.
I can't login at all so everything is done from the recovery login.
  
4.  do I use this UUID=mkswap generated uuid in place of the entire line of /dev/hda5
5.  Not sure how to do this at all
6. How can I do this from the teminal.

Please explain in a bit more detail as I am pretty raw

---

### Post by zgornel on 2006-11-29
the UUID=<mkswap uuid> replaces only "/dev/hda5" part. Leave the rest of the line. If you can't login, do everything from the recovery console: *fdisk -l /dev/hda* to see the list of partitions. Watch for the swap partition to be present then jump to setp 3.

---

### Post by gentlemanmasher on 2006-11-29
what commands would I use for 5 and 6.

---

### Post by zgornel on 2006-11-29
> **gentlemanmasher said:**
> what commands would I use for 5 and 6.

*nano* - text editor; 
*less /boot/grub/menu.lst* - use keys to scroll, *q* to exit

---

### Post by gentlemanmasher on 2006-11-29
so would I use this in the terminal "sudo nano /etc/initramfs-tools/conf.d/resume" to edit.

---

### Post by zgornel on 2006-11-29
Yes.

---

### Post by gentlemanmasher on 2006-11-29
great I will try tonight after work.  Please check back to see if I am good to go.

---

### Post by gentlemanmasher on 2006-11-29
unbelievable.  So after having an fstab error and swap error.  Ended up what i had done did fix it previously, just turns out my drive was to full and wouldn't boot into ubuntu.  I share a partition with windows and moved some files over and filled it up to much.

thanks a million for all of your help.  This is why I stay with ubuntu

---

