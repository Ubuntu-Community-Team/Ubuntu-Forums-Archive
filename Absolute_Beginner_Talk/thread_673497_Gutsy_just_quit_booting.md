---
title: "Gutsy just quit booting"
date: 2008-01-20
forum: Absolute Beginner Talk
---

### Post by rfurman24 on 2008-01-20
Gutsy just quit booting. No changes were made. The problem has been intermittent since I installed Gutsy. I just got rid of fiesty on a second drive because I thought I had the bugs worked out of Gutsy. Today it would just hang on a blinking cursor when it should have been starting X. I tried alt f1 and control alt f1 with no luck. I tried all 3 kernels no luck. After many resets and trying different things know it just hangs on or shortly after "running /scripts/init-bottom" I have know idea what to do or try. I installed arch on the other disc and it is nowhere near ready. Need help asap. Thanks.

---

### Post by rfurman24 on 2008-01-20
I just noticed while snooping around with the live disk that I have no fstab. Only a fstab.pre-uuid. Could that have something to do with it? I tried coping the file and renaming it fstab but it did nothing. I really need my computer back.

---

### Post by rfurman24 on 2008-01-21
fsck returned clean and did not help the problem.  Anyone?

---

### Post by dstew on 2008-01-21
> I just got rid of fiesty on a second driveHow did you do this? It might help us to figure out how your system went wrong.> I just noticed while snooping around with the live disk that I have no fstab. Only a fstab.pre-uuid.Are you sure you were looking at the fstab on your hard disk? You have to mount it to your LiveCD file system. Maybe you were looking at the fstab on the LiveCD.

---

### Post by rfurman24 on 2008-01-21
Thank God for someone trying to help. I installed arch on the second disc. Everything went normal. When I got tired of messing with arch and went to boot to Gutsy it would not boot. At first I thought it was doing the thing it had been doing intermittently with not loading X but alt f1 and alt control f1 did nothing when I rebooted into recovery it hangs just after "running /init-bottom... done" I have run fsck from live disk and no errors were found. I ran it a few more times to be sure and then errors were found and repaired but it still will not boot. I have no clue where to start? What logs to check? I seriously do not want to format.

---

### Post by rfurman24 on 2008-01-21
Yes. It was the Gutsy /etc folder I was in. I made sure by checking the arch folder as well.

---

### Post by apostate on 2008-01-21
Do you get a GRUB menu?

---

### Post by dstew on 2008-01-21
> it hangs just after "running /init-bottom... doneCan you get a command line in recovery mode? If not, you might need to try some kernel boot parameters to get a system loaded. Or maybe reinstall...
EDIT: It might be [this bug]("https://bugs.launchpad.net/ubuntu/+source/busybox/+bug/131961"). You can boot a LiveCD, mount your Ubuntu root partition onto the LiveCD system, and examine the file /var/log/kern.log for clues.

---

### Post by rfurman24 on 2008-01-21
I do get the grub screen. I can choose any of the three kernels and their recovery modes. None will boot. They just hang so I get no command line. It is hanging in the boot process. I really do not want to reinstall. Gutsy was a pain in the a$$ to fix all the bugs. I do not think I want to do it again.

---

### Post by rfurman24 on 2008-01-21
I had already seen that bug. From what I read it seems the segfault does not prohibit the boot process, just an annoyance. I do not get the segfault anyway.

---

### Post by dstew on 2008-01-21
Look in /var/log/kern.log for clues to your particular problem. You have to mount your Ubuntu hard disk system to your LiveCD system to see it.

---

### Post by apostate on 2008-01-21
Ok,

RE: your  fstab, I buy that it was not the arch filesystem, but unless you chroot to the harddrive, the so called root filesystem of your live CD session is actually the CD!

RE: GRUB, If you get no feedback on any kind of error at all, just a blank screen with a cursor, this is my conjecture. Your grub config is jacked up, and it is unable to find a bootable image of any Ubuntu OS. This might actually be Arch's fault, I'd need to know way more to say for sure. I'm betting a glance at your grub .ini file and menu file will reveal that the strings telling grub where to go to find each kernel are now wrong.  Can you post your hardware, with the linux volume designators (sda1, hda1, ect....) and also your grub.ini?  You will need to use the chroot command from a live session to select the hard drive as the root filesystem, and then grab the grub.ini file.

---

### Post by rfurman24 on 2008-01-21
I do not see anything that really means anything to me. It just looks like normal boot messages and then they quit.

---

### Post by rfurman24 on 2008-01-21
> **apostate said:**
> Ok,

RE: your  fstab, I buy that it was not the arch filesystem, but unless you chroot to the harddrive, the so called root filesystem of your live CD session is actually the CD!

RE: GRUB, If you get no feedback on any kind of error at all, just a blank screen with a cursor, this is my conjecture. Your grub config is jacked up, and it is unable to find a bootable image of any Ubuntu OS. This might actually be Arch's fault, I'd need to know way more to say for sure. I'm betting a glance at your grub .ini file and menu file will reveal that the strings telling grub where to go to find each kernel are now wrong.  Can you post your hardware, with the linux volume designators (sda1, hda1, ect....) and also your grub.ini?  You will need to use the chroot command from a live session to select the hard drive as the root filesystem, and then grab the grub.ini file.

Not sure where to start so here goes. I put arch grub in the mbr and chainloaded to the grub on the gutsy drive (sdb). When the arch grub loads I select the gutsy drive(which I manually entered) then it takes me to the Gutsy grub which is where I pick the kernel I want to boot. About the fstab I mount my /sdb2 (root) partion from the live cd and looked in the /etc file their is no fstab only a fstab.uuid. I have two 250gb satas the arch is sda gutsy sdb rest of computer is in sig. After reading this if you still think its grub I will post the .ini. Thanks.

---

### Post by apostate on 2008-01-21
Is the gutsy volume on a different physical drive than the MBR for Arch?

---

### Post by rfurman24 on 2008-01-21
Yes it is. Arch is on sda(hdo) and gutsy is on sdb(hd1) gutsy has its own grub and is chainloaded from the arch drive.

---

### Post by apostate on 2008-01-21
Was there an hda0 before you installed Arch?

---

### Post by rfurman24 on 2008-01-21
I do not understand your question. I have had two drives in the computer since I built it. I had Fiesty on hdo(sda) and Gutsy on hd1(sdb). After I got Gutsy to where I thought it was good to go(apparently it was not) I installed arch over Fiesty to play with it. That is when this started but the arch install should not have affected it since it did not touch the sdb drive with Gutsy on it.

---

### Post by apostate on 2008-01-22
But Ubuntu worked prior to the Arch install?

I'd say if was almost certainly your bootloader. If you were having issues at the kernel level, you would be getting boot messages from Gutsy.  The fact that you get a black screen for any of the kernels on that drive sounds very suspiciously like a mismatch in the actual volume numbers, and the ones that grub is trying to use. Did you at any point during this period change which drive was the slave, and which the master?

---

### Post by rfurman24 on 2008-01-22
They are sata drives. I did try to change which boot first. but realized that when I switched the boot order that it changed the drive number system and confused grub due to the hdo vs hd1 so I switched it back but it booted once after that and then that was it. Here I am.

---

### Post by rfurman24 on 2008-01-27
I gave up. I found other files missing besides the fstab the X11 folder was gone who knows what else. I installed mint and one drive and debian on the other. Thanks for the help.

---

