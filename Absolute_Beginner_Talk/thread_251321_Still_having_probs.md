---
title: "Still having probs"
date: 2006-09-05
forum: Absolute Beginner Talk
---

### Post by bigstick on 2006-09-05
some success I thought, managed to get my 2nd hd back on windows,also managed to get Ubuntu to go through a complete installation by using the IRQPOLL switch and install in server mode.
It also reckonised that I had windows on the other hd and installed the grub in the root of the windows drive. 
But when it asked to reboot the system , it went back to windows
I tried to check if the installation took but windows cant read the drive, its there and it can see it but thats all.
I have went through various methods but still no success.
If I try and istall as a desktop it cant see the dvd drives it will not install unless I use IRQPOLL, I go through guided partioning and it seems to complete an instillation and even put the grub in. WHERE AM I GOING WRONG? 
Please can someone help as my wife wants to put me in a rubber room.

IT WILL NOT BEAT ME!!

---

### Post by bigstick on 2006-09-05
Update- I had another think about it and because its ASUS mobo I used the bios to boot the 2nd hd and its booting into the grub and gives the option to what system I want.
Now what I get next is it ask,s for a username and password which is ok but then Im left with a command prompt, where do I go from here? the commands in linux are totally alien to me. any help guy,s/gal,s

---

### Post by taurus on 2006-09-05
Did you use the server CD or the desktop CD?  Let's see if you have X installed on your machine or not.  At the prompt, type this command and describe what happens (with error message if there is one)!

```
startx
```

---

### Post by bigstick on 2006-09-05
major new developement, cant get grub to load gats so far the error repeats as follows.

[4294777.680000]hda:cdrom_pc_intr:the drive appears confused(ireason=0x01) any ideas.
thanks

---

### Post by bigstick on 2006-09-05
new developement,on last try ubuntu did boot to a command prompt, I tried the startx command here is what I got.

-bash:startx:command not found
jim@ubuntuhal2000~$
I think it means that startx is not installed, and the rest is a command prompt waiting on the user?
I think I may have a bit of a system but nothing that I can work with not knowing the language, any help with this please, is there a step by step how to about installing and setting up ?
I seem to be making progress but still havnt got a working system.

Thanks

---

### Post by taurus on 2006-09-05
So, looks like you are using the server version.  At the prompt, run

```

sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start

```

---

### Post by bigstick on 2006-09-05
Hi dude
 you must know what your doing, but here is the next prob.
 keyed in what you said and lots of scrit going on, and then it froze here is the error message.

92% [working] [4295402 300000]hda:drive not ready for command

does this make sence, I thought you had cracked it, but yet another hill to climb but I still have hope! 

Thanks for your help and advice

Jim

---

### Post by taurus on 2006-09-05
There is something wrong with your first harddrive, /dev/hda!!!  Perhaps you are running out of space on it!  What is the output of this command then?

```
df -h
```

---

### Post by bigstick on 2006-09-07
Tried what you said but it did not know the command, what I have done is stared from fresh again, I have wiped hd1,hd0 has windows on it.
hd1 is unallocated free space, I ran the ubuntu dvd and it starts asking to install or run the live cd. I tried to install in safe graphics mode and still using the IRQPOLL option. it gets as far as checking hardware and tells me it cant mount the cdrom, I dont understand if it can read the dvd why cant it install from it?
Both hd,s are maxtor 200ghz so there was no porblem about space, both are working correctly and windows see,s both drives and will write to them, if I try and install without using IRQPOLL I get the same error as my previous attempts(hda:cdrom-intr drive is confused disable IRQ217)this may not be exact its just what I remember.
This is quite frustrating as my son who has quite an old system has installed it and is up and running,maybe I should get him to try it on my system?

Thanks again for any help

---

