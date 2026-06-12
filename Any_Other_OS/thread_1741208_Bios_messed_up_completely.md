---
title: "Bios messed up completely"
date: 2011-04-27
forum: Any Other OS
---

### Post by acid_fall on 2011-04-27
Okay, this is a bit unrelated to Ubuntu, but it is about linux in general, and this seems like a well-educated forum, so I thought I'd post it here since no other forum could solve this problem or me.

I originally had just windows 7 on my desktop computer, but then a few months ago, I decided to get linux mint 10. Being as smart as I am, I put waaaay too much memory on that partition, and a week ago, I was out of memory on my windows partition.

So, I went and deleted the partition, deleted the free space, then put the unallocated space into the windows partition. So, it wasn't until yesterday that I actually had to reboot my computer, and when I did I got an error saying "error: no such partition." Then it gave me a sort of command line that says "grub rescue>" and that's it. There are no commands that work on it either.

So I downloaded Ubuntu and put it on a flash drive so I can boot from that and reinstall the GRUB stuff, but it still gave me the same screen (yes I chose boot from USB).

Then I tried to put my old windows xp recovery disk in, but when I tried to boot from that, the same thing happened. 

And now I am completely clueless on how I can get my machine running again. I would prefer to keep all of my files and not have to delete everything, but if that's not possible, I understand.

P.S. Please remember while posting, that I have no access to any operating system, and even when I have a bootable disk or flash drive, my bios will not let me boot from it.

---

### Post by Yellow Pasque on 2011-04-27
So if you disconnect the drive (just the data cable if you wish) and try to boot from USB/CD, you still have issues?

---

### Post by Perfect Storm on 2011-04-27
Moved to Other OS/Distro Talk.

---

### Post by acid_fall on 2011-04-27
> **Temüjin said:**
> So if you disconnect the drive (just the data cable if you wish) and try to boot from USB/CD, you still have issues?

Well, I just did that. It was successful in booting into the windows recovery disk, but all I got was the blue screen saying "Windows Setup" But then nothing else will com up. My best guess to why this is happening is that when I unplug the hard drive, there is nowhere windows can go.

---

### Post by Yellow Pasque on 2011-04-28
And how about a livecd?

---

### Post by acid_fall on 2011-04-28
> **Temüjin said:**
> And how about a livecd?

An ubuntu one? Not sure. Can't make one, because my only other computer is a netbook without a cd drive.

---

### Post by ventrical on 2011-04-28
> **acid_fall said:**
> Okay, this is a bit unrelated to Ubuntu, but it is about linux in general, and this seems like a well-educated forum, so I thought I'd post it here since no other forum could solve this problem or me.

I originally had just windows 7 on my desktop computer, but then a few months ago, I decided to get linux mint 10. Being as smart as I am, I put waaaay too much memory on that partition, and a week ago, I was out of memory on my windows partition.

So, I went and deleted the partition, deleted the free space, then put the unallocated space into the windows partition. So, it wasn't until yesterday that I actually had to reboot my computer, and when I did I got an error saying "error: no such partition." Then it gave me a sort of command line that says "grub rescue>" and that's it. There are no commands that work on it either.

So I downloaded Ubuntu and put it on a flash drive so I can boot from that and reinstall the GRUB stuff, but it still gave me the same screen (yes I chose boot from USB).

Then I tried to put my old windows xp recovery disk in, but when I tried to boot from that, the same thing happened. 

And now I am completely clueless on how I can get my machine running again. I would prefer to keep all of my files and not have to delete everything, but if that's not possible, I understand.

P.S. Please remember while posting, that I have no access to any operating system, and even when I have a bootable disk or flash drive, my bios will not let me boot from it.

I presume the way to get your boot grub record back is to have Ubuntu *installed* to a USB drive FROM a CD or USB drive. This means that the USB drive that you install Ubuntu on to  will become your psuedo_bootable HD in real time (persistive). I would suggest that you remove the hdd cable first.

After you have INSTALLED Ubuntu do not update yet!! (You can use an 8GB USB flash drive to install Ubuntu onto). After this is all done  turn off your PC and then reconnect your HDD cable .. etc and make sure to BOOT from the installed Ubuntu USB. Then do an update. The updater will search for partitons and append them to the new GRUB boot record.. but I would think that you could only then boot from your Ubuntu USB install.

  I had the same probs with Natty - loosing my boot-record- so I would just wait a few days until the next linux-kernel update, do the update and , voila' ,instant GRUB boot record with lost partitions.

---

### Post by Yellow Pasque on 2011-04-28
> **acid_fall said:**
> An ubuntu one? Not sure. Can't make one, because my only other computer is a netbook without a cd drive.

Make a bootable USB stick: http:/help.ubuntu.com/community/Installation/FromUSBStick

---

### Post by acid_fall on 2011-04-28
> **ventrical said:**
> I presume the way to get your boot grub record back is to have Ubuntu *installed* to a USB drive FROM a CD or USB drive. This means that the USB drive that you install Ubuntu on to  will become your psuedo_bootable HD in real time (persistive). I would suggest that you remove the hdd cable first.

After you have INSTALLED Ubuntu do not update yet!! (You can use an 8GB USB flash drive to install Ubuntu onto). After this is all done  turn off your PC and then reconnect your HDD cable .. etc and make sure to BOOT from the installed Ubuntu USB. Then do an update. The updater will search for partitons and append them to the new GRUB boot record.. but I would think that you could only then boot from your Ubuntu USB install.

  I had the same probs with Natty - loosing my boot-record- so I would just wait a few days until the next linux-kernel update, do the update and , voila' ,instant GRUB boot record with lost partitions.

How do I install it to the flash drive?

---

### Post by acid_fall on 2011-04-28
> **Temüjin said:**
> Make a bootable USB stick: http:/help.ubuntu.com/community/Installation/FromUSBStick

I already have the bootable usb stick, but it say the same error as the windows recovery disk...

---

### Post by ventrical on 2011-04-29
> **acid_fall said:**
> I already have the bootable usb stick, but it say the same error as the windows recovery disk...

You will have to find a friend/family. Go there. Download the Ubuntu .ISO file and burn a copy to CD.

Set to boot from CD in friends PC.

Put USB in and remove hardrive, then boot and go through the installation process > install to the USB drive. It will automatically detect. Do not choose to update during the preinstall. After this is done you may be able to try and boot it from your affected pc but do not update until you reinstall the affected hardrive.

Hope I'm not confusing you. I am sure there are other methods but the method I mentioned has worked for me.

---

### Post by ventrical on 2011-04-29
> **acid_fall said:**
> Well, I just did that. It was successful in booting into the windows recovery disk, but all I got was the blue screen saying "Windows Setup" But then nothing else will com up. My best guess to why this is happening is that when I unplug the hard drive, there is nowhere windows can go.

So you should be able to boot a Maveric ISO and then install to USB. Make sure the harddrive is not  connected to the system

BTW .. what type of PC is it?

If the BIOS is affected or damaged then it may not be possible. If it is an older system then you may need PLOP bootloader.

---

### Post by acid_fall on 2011-04-29
> **ventrical said:**
> So you should be able to boot a Maveric ISO and then install to USB. Make sure the harddrive is not  connected to the system

BTW .. what type of PC is it?

If the BIOS is affected or damaged then it may not be possible. If it is an older system then you may need PLOP bootloader.

It was custom made from 2007, maybe 2008.

---

### Post by acid_fall on 2011-04-29
> **ventrical said:**
> You will have to find a friend/family. Go there. Download the Ubuntu .ISO file and burn a copy to CD.

Set to boot from CD in friends PC.

Put USB in and remove hardrive, then boot and go through the installation process > install to the USB drive. It will automatically detect. Do not choose to update during the preinstall. After this is done you may be able to try and boot it from your affected pc but do not update until you reinstall the affected hardrive.

Hope I'm not confusing you. I am sure there are other methods but the method I mentioned has worked for me.


You know what, I think that may actually work. It may take me a few days to get someone to agree to let me use their computer to do that, but I think it could work. Thanks! I'll try that.

---

