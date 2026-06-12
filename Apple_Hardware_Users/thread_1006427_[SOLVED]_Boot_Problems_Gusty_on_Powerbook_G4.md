---
title: "[SOLVED] Boot Problems Gusty on Powerbook G4"
date: 2008-12-09
forum: Apple Hardware Users
---

### Post by mattppcintel on 2008-12-09
I recently got Gusty installed on an old Powerbook G4 that was given to me and have been experiencing a strange problem.  Sometimes when the computer is rebooted it fails to boot and opens some built in console.  It displays an error stating that "device /dev/hd3 does not exist".  I haven't quite figured out what the magic trick is to get it to boot but here is what i did the most recent time:

1. after it booted to built in console typed command "resume /dev/hd3"
2. returned error saying no device at location, doing normal boot
3. nothing happened so i typed "reboot"
4. the began to reboot
5. I gave the computer a love tap (not too hard)
6. The system booted normally

I don't know if I messed something up or installing updates did it but I would really like this thing to boot reliably.  Any ideas on what might be amiss would be greatly appreciated.

If you want info on the powerbook:
Powerbook Titanium G4 (Gigabit Ethernet) 550mhz
radeon video

Thanks in advance!
512 meg ram

---

### Post by tiresia on 2008-12-09
> **mattppcintel said:**
> 
5. I gave the computer a love tap (not too hard)
6. The system booted normally

A love tap? Well, maybe, your computer needs more love to boot reliably :)
Can you please post your file /etc/yaboot.conf (you need to use 'sudo')

---

### Post by mattppcintel on 2008-12-09
Wow, thanks for the quick response.  The yaboot.conf pasted below.  One thing I well add, the last time I edited it I didn't update the system (ybin -v) so I don't know if that could have caused the problem.  I don't want to reboot again cause I'm scared it won't start again.

boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot

image=/boot/vmlinux
        label=Linux
        read-only
        initrd=/boot/initrd.img
        append="quiet nosplash video=radeonfb:1152x768-24@60"

image=/boot/vmlinux.old
        label=old
        read-only
        initrd=/boot/initrd.img.old
        append="quiet splash video=ofonly"

There you go!:p

---

### Post by tiresia on 2008-12-09
> **mattppcintel said:**
>  One thing I well add, the last time I edited it I didn't update the system (ybin -v) so I don't know if that could have caused the problem.  I don't want to reboot again cause I'm scared it won't start again.

boot=/dev/hda2
device=/pci@f2000000/mac-io@17/ata-4@1f000/disk@0:
partition=3
root=/dev/hda3
timeout=50
install=/usr/lib/yaboot/yaboot
magicboot=/usr/lib/yaboot/ofboot
enablecdboot


I already thought that there was a similar problem, because the computer is asking for a /dev/hd3 instead it should be /dev/hd**a**3 (or you tipped it wrong in the first post?)
Anyway, yes you need to run 'ybin -v' and don't be afraid to restart your computer.

---

### Post by mattppcintel on 2008-12-09
So do you think the problem arose because I did not run the ybin -v before rebooting?  If so, a brief explanation of what issues that causes would be great.  The only changes made to yaboot that were not updated was adding "quiet nosplash" to the append line.  It took me ages to get this thing up and I will keep it up indefinitely if I think booting will be a problem.

Thanks again!

---

### Post by tiresia on 2008-12-09
I made a short 'how to' about yaboot 
[http://ubuntuforums.org/showthread.php?t=994882](http://ubuntuforums.org/showthread.php?t=994882)

The file /etc/yaboot.conf is the configuration file for the installation of the ppc bootloader (yaboot), which is on the Bootstrap Partition (/dev/hda2 in your case). It means that yaboot will be installed in the Bootstrap Partition according to the parameters in yaboot.conf
If you change this configuration without reinstalling yaboot - and ybin does right this, yaboot will boot just ignoring your changes.

It's a bit strange, what you say. Because yaboot is looking for the root on /dev/hd3 - and there is no such partition. It even wonders me that you can start with nosplash if you did not run ybin.
Anyway, make a backup of /etc/yaboot.conf (and of /etc/X11/xorg.conf), it's always safer. Then run 'ybin -v'. 
Restart your computer, and let's see, if it works - without 'love tap' :)

---

### Post by mattppcintel on 2008-12-09
Well I rebooted and it booted up fine.  I don't understand why it wasn't booting before though.  I was adding the arguments that were updated at the 2nd stage bootloader (Linux quiet nosplash) so it should still have been using them, it may not have been using the "video=radeon..." portion but it booted without that when I was setting it up, just got a flashy screen.  The only difference between when it wouldn't start and when it would is that at the debian console I typed reload /dev/hd3 and "tapped" it.  I'll take better notes if it has a problem again (I hope it doesn't) and maybe shed a little more light on it.  It may have been reporting /dev/hda3 and I was just misreading.  I'm kinda wondering if the hard drive is getting flakey.  

Anyways, for now I'd say this is solved until I have the problem again.  I'll have better info if it happens again though.

Thanks for the link too.  It's very helpful for a newbie like me!!!

---

### Post by tiresia on 2008-12-09
Good! You shouldn't have anymore problems - at least like this.
Please, mark this thread as solved, if you see that your computer boots up reably

---

