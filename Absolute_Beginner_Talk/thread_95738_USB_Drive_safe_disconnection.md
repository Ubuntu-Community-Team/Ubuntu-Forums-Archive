---
title: "USB Drive safe disconnection"
date: 2005-11-27
forum: Absolute Beginner Talk
---

### Post by paulozzzz on 2005-11-27
Is there some recommended procedure to detach a USB drive from the system or can I simply unplug it from the USB port?

---

### Post by ssam on 2005-11-27
it is best to right click in it icon on your decktop (or in the computer page of nautilus), and select unmount.

if you just pull it out there is a chance that data might not have finished being writen to it.

---

### Post by paulozzzz on 2005-11-27
[QUOTE=ssam]it is best to right click in it icon on your decktop (or in the computer page of nautilus), and select unmount.

if you just pull it out there is a chance that data might not have finished being writen to it.[/QUOTE]

Oh, the famous unmount... I am always forgetting these details... :oops: Ok.

Thanks.

---

### Post by sicofante on 2007-02-05
I find the need to unmount-before-unplug VERY annoying. If there's any way for the OS to make sure everything is written to the pendrive, it definitely should be used as a default. Pendrives should not need to be unmounted. Natural human tendency is to just unplug them and that's what the OS should expect.

---

### Post by punx45 on 2007-02-05
maybe when they make sockets that won't let go of the drive until it is done read/writing...

---

### Post by paulozzzz on 2007-02-07
Maybe some geek figured out some configuration to disable the disk cache for the usb devices, so one can unplug the unit as soon as the activity light stops flashing.

---

### Post by sicofante on 2007-02-07
Exactly. Or they might just keep pendrive's light on while it's unsafe to unplug it. Much like it used to be with floppies.

---

### Post by Evi1d33d on 2007-02-07
> **paulozzzz said:**
> Maybe some geek figured out some configuration to disable the disk cache for the usb devices, so one can unplug the unit as soon as the activity light stops flashing.

I remember that in Windows(is this word a taboo in here?) there is an option to turn disk cache on or off and the default setting is usually off, so I guess Ubuntu should have disk cache disable on default.

---

### Post by mcduck on 2007-02-07
> **Evi1d33d said:**
> I remember that in Windows(is this word a taboo in here?) there is an option to turn disk cache on or off and the default setting is usually off, so I guess Ubuntu should have disk cache disable on default.
You can't just unplug the drives in Windows either. That can (and in long range WILL) cause loss of data, and in worst case render your flash disk useless (or at least force you to recreate partitioning on the drive).

That's how flash drives are. No use fighting it, after all unmounting them properly is really easy and fast thing to do in Ubuntu at least.

---

### Post by jhenager on 2007-02-07
> **ssam said:**
> it is best to right click in it icon on your decktop (or in the computer page of nautilus), and select unmount.

if you just pull it out there is a chance that data might not have finished being writen to it.

Or Eject, as the option is labeled on my version. It only takes a second.

---

### Post by paulozzzz on 2007-02-07
> **mcduck said:**
> You can't just unplug the drives in Windows either. That can (and in long range WILL) cause loss of data, and in worst case render your flash disk useless (or at least force you to recreate partitioning on the drive).

That's how flash drives are. No use fighting it, after all unmounting them properly is really easy and fast thing to do in Ubuntu at least.

Maybe I am wrong, but... recalling my operating systems classes the professor told me that the problem with the USB drives (or any drive) is the uncommited data in the disk cache. For performance sake, busy systems flush disk caches when the CPU is idle, the wait time can be long enough for a system crash or power failure occur after the issued save command and before the actual data write to the device.  Of course for systems such as those in our homes it rarely is an issue as the cache is almost immediately flushed because the CPU is almost never busy. According to this, disabling disk cache can actually allow one to safely unplug the USB drive as soon as the activity light goes off.

---

### Post by mcduck on 2007-02-07
> **paulozzzz said:**
> Maybe I am wrong, but... recalling my operating systems classes the professor told me that the problem with the USB drives (or any drive) is the uncommited data in the disk cache. For performance sake, busy systems flush disk caches when the CPU is idle, the wait time can be long enough for a system crash or power failure occur after the issued save command and before the actual data write to the device.  Of course for systems such as those in our homes it rarely is an issue as the cache is almost immediately flushed because the CPU is almost never busy. According to this, disabling disk cache can actually allow one to safely unplug the USB drive as soon as the activity light goes off.

That is about right, I was actually responding to the disk cache being turned on by default in Windows. Disk writes work a bit differently in Win/Linux, but unplugging USB drives without unmounting is not safe in either one.

Anyway, there is some option in fstab to make a drive sync immediately, but it's also known to reduce lifetime of flash drives (as they have limited amount of write cycles). So it definitely isn't a good default, and I've never heard anybody actually saying anything good about using it.. (this is also why I find Vista's ability to use flash drives as cache kind of funny)

---

### Post by lyceum on 2007-02-07
> **paulozzzz said:**
> Maybe some geek figured out some configuration to disable the disk cache for the usb devices, so one can unplug the unit as soon as the activity light stops flashing.

On a Mac you just drag it to the trash can. I found that odd at first, but now... it is a nice feature. To bad there isn't an eject button you can add to your gDesklets.

---

### Post by mcduck on 2007-02-07
> **lyceum said:**
> On a Mac you just drag it to the trash can. I found that odd at first, but now... it is a nice feature. To bad there isn't an eject button you can add to your gDesklets.
Well, dragging to trash is just a different way to do the same unmounting ;)

---

### Post by lyceum on 2007-02-07
> **mcduck said:**
> Well, dragging to trash is just a different way to do the same unmounting ;)

Yes, but it is one step

1. drag

or 

1. right click
2. click on eject

so it is meeting half way, and it requires nothing from the hardware vendors :)

---

