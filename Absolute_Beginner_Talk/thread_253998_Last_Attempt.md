---
title: "Last Attempt"
date: 2006-09-09
forum: Absolute Beginner Talk
---

### Post by bigstick on 2006-09-09
I am ready to give up Ive been trying for a week now to install UBUNTU but no joy, It gets as far as detecting hardware and the error is cannot mount cdrom, if it can read it to get that far what is the problem. Ive tried various how to,s and read just about every post with a similar problem, I have just downloaded the alternate version hoping to find some tool to over come this ,but no joy.
Is there anybody that has had a similar prob and found an answer?
Please help me Im going nuts.

---

### Post by seshomaru samma on 2006-09-09
I had a similar experience when Dapper just came out on a machine at work. I gave up . It turns out there was some hardware problem that was not detected properly by Windows. It was like a PCMIA device or something similar.  A technician is supposed to fix it next week, maybe I will have more details then
Is it a Windows machine ? do you get any hardware errors on Windows? like 'Windows detected an unknown hardware' or somehing similar?

---

### Post by xyz on 2006-09-09
Hi...well try and hang in there!
I'm pretty sure you already did all this but just in case:
Did you: 
1. check install CD's integrity
2. md5 sum?
3. check if you've got HW (hd) problems?

I must admit that in order for me to upgrade to Dapper, I had to install Breezy Badger first! Don't ask why and how...I just don't know but it's worked ever since! Knock on wood.

Good luck to you and keep us posted.

---

### Post by ieee488 on 2006-09-09
Do you have another CD drive you can try?

---

### Post by bigstick on 2006-09-11
Ok Guys 
        A big Thanks for all your support and help.
Here is where Im at at the moment!
Looked at the problem again and Googled IRQ217 which seems to be a recurring error, and found someone with a similar problem its to do with a AVER TV card which I have installed on this machine and yes its a Windows machine I had hoped to duel boot.
So I removed the card this morning and Ubuntu installed straight off the dvd SUCCESS!!
BUT and there is always a but I have a new problem.
By the way Windows is still working ok thats what Im using to write this,
I have copied the whole message to give someone with more know how a chance to figure it out.

Booting Ubuntu Kernal 2,6,15-23 686
Root(hd1,0)
Filesystem type is EXT2FS,partion type 0x83
Kernal/boot/vmlinuz-2,6,15-23-686 root=/dev/sdb1 ro quite splash
[linux-bzimage,setup=0x1c00,size=0x16e65c]
initrd/boot/initrd.img-2,6,15-23-686
[linux-initrd@0x1f94c000,0x6a3cb9 bytes] save default.
boot.
uncompressing linux...ok.
booting kernal.
alert!/dev/sdb1 does not exist. dropping to a shell
Busybox v1.01(debian 1:1.07-4 ubuntu3)
builtin shell (ash)
enter help for a list of builtin commands.
/bin/sh: cant access tty: job controll turned off.
#
# 


Thats where Im at the moment, any Idea,s

Thanks again Guys.

---

### Post by bigstick on 2006-09-14
Hi Everybody
              Still hanging on, no futher progress than my last post.
I dont know if this has anything to do with it but I carried out my usual anti-virus scan today and found that AVG scanned my 2nd hd and listed all the Linux files then moved on to windows on the 1st hd everythig was clear.
The Grub still ask,s what op sys to boot, but still same error hdb does not exist.
My previous post has the full error.
 
If anybody has any Idea,s please help.

Thanks

---

### Post by Iowan on 2006-09-14
> **bigstick said:**
> ...
The Grub still ask,s what op sys to boot, but still same error hdb does not exist.

hdb or sdb? BTW, what kind of hard drive?

---

### Post by bigstick on 2006-09-15
Hi Everybody
              I dont know what happen this morning but I thought Iwould have another round with Ubuntu, and to my suprise it booted up to the desk top AT LAST SUCCESS.
(it may have been the size of the hammer I used this time!!)So now I have something to work with, I am very impressed with the desk top and the preinstalled app,s.
Im busy downloading Linux Drivers for all my bits and bob,s and cant wait to get my feet wet.
A BIG THANKS for all your help and support.
Ill keep you posted thanks again

---

### Post by Najand on 2006-09-15
Sounds great... congradulations...

---

