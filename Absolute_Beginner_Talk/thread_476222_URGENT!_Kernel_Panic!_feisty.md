---
title: "URGENT! Kernel Panic! feisty"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by ucsblaw on 2007-06-17
Hi people...im calling on anyone who can try and lend a hand. I'm in a panic myself!

I have a sony vaio s580. 2 gigs of ram and 100gig sata HDD. 

I installed feisty using wubi... i managed to get everything up and running but then i got cocky.

I tried to fix the hibernation/ suspend problem using a guide i found on this forum



In terminal put:

> sudo apt-get install uswsusp

it gave me some blue box that said that i cant install uswsusp (i think that's what it said) and then i pressed ok. Since Im an idiot...I then decided i should remove what i just tried to install so I typed

> sudo aptitude remove uswsusp

i then restarted my computer and got this

> wubi/boot/initrd.img-2.6.20-16 low latency
[Linux-initrd @ 0x1f9af000, 0x640000 bytes]
boot
[16.297381] RAMDISK: ran out of compressed data
[16.297448] invalid compressed format (err=1)
[16.298258] Kernel panic - not syncing: VFS: Unable to mount root fs on unknown block (8,3)
[16.298323] 

then....i cant do anything...my computer is completely dead...I cant even power off...I HAD TO REMOVE THE BATTERY


IM DYING HERE....I spent 2 months getting everything working correctly,,,and customizing my entire desktop and now its gone. 

respectfully yours

---

### Post by candtalan on 2007-06-17
Hi ucsblaw
Does it boot up ok with a live CD I wonder? If so, there maybe ways to see what has happened and repair. A live CD such as knoppix will give immediate access to things, it is useful as a toolkit. If you have the ubuntu live CD at least try this? you can do simiar things as knoppix with a bit more work though.

Others here may be able to help more.

---

### Post by Gimpy_Rob on 2007-06-17
Ok, don't panic like kernel did...  Like candtalan said, many things can be fixed with live CDs, that's why they are so great.  

But I must say, the number or people that are pulling their bios batteries is STAGGERING...  I have never pulled out mine on my desktop or server boxes, and I can only imagine doing it in EXTREME situations like bios not responding, or lost bios passwords.  If you have bios level hard drive security, this can cause loss of data.  You can 99% of the time shut down a computer by holding power button for 5 seconds (sometimes they seem like really long seconds) or by pushing  restart button first, then powering off during bios (but usualy best to let it finish POST (self test))

Anyways, back to your problem, data recovery will be easy enough, with live CD, if it comes to that.  I personally don't know enough about these systems to give advice on getting the computer booting again.  I'll check back and if you need to backup data, can help with that.

---

### Post by ucsblaw on 2007-06-17
im grateful for your responses. I do have a live CD but I wouldnt know what to do once i booted up with the live CD. Im a novice with linux and the only reason i got everything working on ubuntu was diligence and the help of this forum and wiki's. 

I don't even know what i did...I know i can boot to the grub menu...does that help at all?

Also, I dont think its a HDD or memory problem because my XP boots up fine.

---

### Post by kleeman on 2007-06-17
If you can see the grub menu then try the option that says "recovery mode". If that boots then do this at the command line:

apt-get install linux-image-2.6.20-16-generic

reboot using

shutdown -r now

and select the generic kernel in the grub menu (looks like you are using a low latency kernel at present)

If that works go to synaptic and reinstall your old kernel

---

### Post by ucsblaw on 2007-06-17
thanks for the input...i tried what you said but i cant find 'recovery mode'...when i get into the grub menu this is all i see.

> GRUB4DOS

**find /wubi/boot/grub/menu.lst    **     (this just boots up to the kernel panic error)
**find /menu.lst     **                              (this gives me  'error 17 file not found')
**find /boot/grub/menu.lst    **              (this gives me  'error 17 file not found'...fallback 2...etc)
**find /grub/menu.lst  **                        (this gives me 'fallback 3...etc)
**commandline     **                               (this gives me 'grub>' with limited bash like editing)
**reboot  **                                            (just reboots)
**halt     **                                              (this just shutsdown my computer)    

---

### Post by ucsblaw on 2007-06-17
would this have anything to do with how i messed around with the uswsusp? This happened right after i removed the uswsusp.

I had updated to ubuntustudio the previous day and i know that it changed the kernel to a low-latency kernel but i didnt have any problems...and now im baffled. i dont know what to do. SHould i reinstall?

---

### Post by jonward0690 on 2007-06-17
I am not shure if uswsusp has something to do with it or not it proboly does I instaled it and it fixed my computer to where I can hibernate it ,you will proboly have to recover all your data with a live cd and do a reinstall,there might be someone who can help you though.

---

### Post by ucsblaw on 2007-06-17
so i've been reading up on this kernel panic and ramdisk stuff...since i updated to studio and installed the new low latency kernel i have apparently a small boot partition which ran out of disk space. The problem could be fixed by removing some older kernel versions left over from previous kernel updates but how would i do this? I dont know how to do anything under the grub commandline. I cant get into recoverymode  and i cant boot up to ubuntu at all. All i can do it boot to grub command line and there i have "limited bash like editing" which i dont know how to use.

---

