---
title: "Grub Error Messages and help"
date: 2007-04-26
forum: Absolute Beginner Talk
---

### Post by kbarron on 2007-04-26
Grub Error Messages 16/17/18 

--------------------------------------------------------------------------------

I installed Ubuntu about 3 months ago. Havent really used it that much. Today when I turned on my laptop it froze after the 

Grub Loading Stage 1.5
Error message 16/17/18

I have tried rebooting it a dozen times and the error messages switch back and forth between 16,17, and 18. One time I got it too give me the option of selecting my OS since it was a dual boot but after selecting Windows it froze again.

I tried downloading the super grub disk however when i chose to boot from the cd rom via the bios its still going straight to grub loading etc and not reading the cd rom boot disks.

i also tried a windows boot disk and the ubuntu live cd and it wouldnt load that either in the bootup from the cdrom

i really have no idea on what I need to do to fix things. I had 2 40 gig hd's and partioned Ubuntu onto about 10 gigs. 

Nothing new has been installed recently either and the last time i even went into Ubuntu was like 3 weeks 
ago.

I dont have any idea how to get things working again. I dont know why it wont read from the cd rom either. Is there anything I can do via the F2 setup menu.

I really need to get this thing fixed and any info/help would be greatly appreciated.


any help and or direction would be great. even just to get me back to windows


kyle

---

### Post by igknighted on 2007-04-26
Yikes... i would boot the live CD (or any live CD) and run fsck on both drives... sounds like a HD might be failing.

If it checks out OK, put in your winXP cd, boot it to the recovery console, and type fixmbr.  That should restore the windows bootloader.  If you want to keep Ubuntu put the ubuntu liveCD in and follow these directions: [https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by dubrict on 2007-04-26
[http://www.uruk.org/orig-grub/errors.html]("http://www.uruk.org/orig-grub/errors.html")

Yeah, so 16 and 17 indicate that your /boot/grub/menu.list file may be corrupted

and 18 says your kernel is not executable!

You didn't recently drop this laptop, did you?

---

### Post by kbarron on 2007-04-26
The laptop did actually drop about 2 weeks ago but I had been using it full time since then.

I have tried the ubuntu live cd, ultimate book disk, and the super grub disk and I cant get any of the three to boot. It still goes straight to the grub loading message upon turning it on. 

the only thing I can do is enter the phoenixbios screen however it seems that my options are kinda limited there as far as what I can change.

Is this something I need to take into a repair shop as I need to get this working ASAP.

---

### Post by Seisen on 2007-04-26
Sounds to me that your Bios got corrupted somehow, then again I could be wrong. You can check your motherboard manufactuer and see if they have an update for you bios or a way to flash it to change it back the way it was.

---

### Post by kbarron on 2007-04-26
I guess I am lost as to how to run anything as far as a fix goes if I am not able to access any of the boot disks I have downloaded because the cd rom is not being read when I change it the boot up order to first.


Would the bios screen load and the grub loading screen still come up if the HD failed?

If I need to have this repaired would this be a costly repair if its a failed HD? I doubt there is any warranty left on this as its about 3 years old. The mother board was replaced about 2 years ago.

---

### Post by Sef on 2007-04-26
> If I need to have this repaired would this be a costly repair if its a failed HD?

If it is a hard drive, it would depend on how easy it is to remove.   My Dell Inspiron is easy to remove.   What kind of laptop do you have?  You might be able to take it out yourself, but more likely your motherboard or some  other part was damaged by the fall.

---

### Post by kbarron on 2007-04-26
For some reason the Cd rom wants to work now and I am able to boot from it.

I was able to get into the ubuntu live cd as well as the super grub disk. 

any ideas how I go about the fix now if its possible.

---

### Post by igknighted on 2007-04-26
see the link i posted in the original reply for how to repair grub.  Also, run fsck to ensure that your filesystems are ok

---

### Post by dubrict on 2007-04-26
It sounds like a clear-cut case of a faulty hard drive.  I've seen them where they don't fail until a week or two after they're dropped, and then sometimes work fine.

---

### Post by rillip on 2007-04-26
It sounds to me like your CD drives are none to reliable either.  Once you get it working, I'd strongly recommend a backup, as your laptop may not have much time left in this world...

---

### Post by Yellowbelly on 2007-04-26
I'd just like to add that I had a similar problem with grub. I was just running ubuntu as normal and started up my jacked up amarok program to see if it'd work but it doesn't. It's frozen so I needed to restart and boot up in windows. I got impatient so just hit the reboot button instead of letting the system shut down and i had a grub error that freaked me out. Rebooted but it loaded up and everything's ok now. Kinda weird I think.

---

