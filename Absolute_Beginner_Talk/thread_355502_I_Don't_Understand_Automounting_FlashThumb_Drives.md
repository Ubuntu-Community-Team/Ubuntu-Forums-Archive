---
title: "I Don't Understand Automounting Flash/Thumb Drives"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by drs305 on 2007-02-07
I am pretty new to Linux and Ubuntu. I have progressed to the point where I am trying to get USB drives (thumb or flash drives) to behave the way I want and am having no success. I tried installing autofs per the instructions at [http://greenfly.org/tips/autofs.html](http://greenfly.org/tips/autofs.html) but am still having lots of problems.

What I want is to be able to plug in a flash drive, have it recognized and mounted by Linux, and when I'm finished simply unplug it without any generating warnings or losing data. I thought that is what autofs was supposed to do but I can't get it to do what I thought it should (see above). 

Additionally, the USB device mount points/folders remain when the device isn't installed, which I would prefer they not.

Here are some specifics that may help you help me.

My fstab contains no reference to usb devices or /dev/sda1 or /dev/sda
When I plug in a flash drive, it automatically mounts in /media/<name of the USB flash drive> and opens a Nautilus window.

When I had autofs installed, the flash drive would still automatically mount as above, opening a new browser window. When I removed the device, I would still get the warning about potential data loss (timeout set to 5 seconds). There were instances when I would get the autofs to halfway work (creating a mount point I specified in the autofs configuration files), but even then it would also mount in /media and give me the data loss warning.

For those of you that read lots of forums, you may have come across a couple of similar posts. I haven't received any help on those thinly read forums and apologize to any who believe this is close to cross-posting.

Thanks for your help.

---

### Post by Maestro23 on 2007-02-07
Did a keyword search(mounting flash drives) and came up with many threads dealing with mounting them.  Did you see this one:

[http://www.ubuntuforums.org/showthread.php?t=319897&highlight=mounting+flash+drives](http://www.ubuntuforums.org/showthread.php?t=319897&highlight=mounting+flash+drives)

Like I said, there are many discussion threads, perhaps you will be able to find one to help you.

---

### Post by dannyboy79 on 2007-02-07
this is an automagic thing in ubuntu (you don't need autofs, this is handled by the hotplug program) but to remove it you can't just remove it, you have to "unmount" it first or yeah, you're gonna possibly screw up your drive. unmounting can be done several ways but if you're coming from windows the easiest way is to right click on it from your desktop and click on unmount. walah, you can remove it without damaging it or the data on it.

---

### Post by matt_risi on 2007-02-07
I always thought this was bull too. Like if Windows can unmount a usb device cleanly, why shouldn't Linux? It's little things like that that make things tough for a new user, not the overall experience/presentation of the OS. I've gotten used to unmounting my drive but it is still a nuisance.

---

### Post by mcduck on 2007-02-07
> **matt_risi said:**
> I always thought this was bull too. Like if Windows can unmount a usb device cleanly, why shouldn't Linux? It's little things like that that make things tough for a new user, not the overall experience/presentation of the OS. I've gotten used to unmounting my drive but it is still a nuisance.
No, Windows can't always unmount USB drives cleanly. That's why you have the 'Safely remove hardware'-thing in systray.

Most of the times there's no problem unplugging USB drives without unmounting, but as disk writes are cached you might loose data if you don't unmount correctly. It's exactly the same thing in windows. (The bigger amount of data you have copied to the flash drive, the more likely all of the data isn't written to the disk instantly)

---

### Post by drs305 on 2007-02-07
Maestro23, and others.

I've done a LOT of reading of threads about auto-mounting and I guess my question really centers on how Ubuntu mounts USB devices.  From what responses indicate so far, this annoyance is something that autofs can't help me with and more experienced users don't think is a problem. If autofs can't do what I'd like if there is another workaround to allow "plug 'n remove' I'd love to hear it.

Thanks for the inputs.

---

### Post by blackhole82 on 2007-02-07
Right clicking on the drive when it comes up on the desktop and selecting unmount always works for me.  I'm new to ubuntu as well, but this doesn't really seem like a complicated issue since it closely resembles the way thumb drives work in windows.

---

### Post by bodhi.zazen on 2007-02-07
> **drs305 said:**
> Maestro23, and others.

I've done a LOT of reading of threads about auto-mounting and I guess my question really centers on how Ubuntu mounts USB devices.  From what responses indicate so far, this annoyance is something that autofs can't help me with and more experienced users don't think is a problem. If autofs can't do what I'd like if there is another workaround to allow "plug 'n remove' I'd love to hear it.

Thanks for the inputs.

There is a work around, mount the device with the sync option.


USB sync
	destroy device: [http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html](http://readlist.com/lists/vger.kernel.org/linux-kernel/22/111748.html)

However, this tends to burn the device out rather fast.

As others have said, as frustrating as it may be to you, this is not now how these devices work, either in Windows or Linux.

Removing your device from windows without unmounting it first is a bad habit, stop it. And yes I have seen data loss and damage to devices removed from windows. Usually you can restore the device, but not always. Just because you can do it most of the time does not make it a good idea :p

---

### Post by bodhi.zazen on 2007-02-07
> **blackhole82 said:**
> Right clicking on the drive when it comes up on the desktop and selecting unmount always works for me.  I'm new to ubuntu as well, but this doesn't really seem like a complicated issue since it closely resembles the way thumb drives work in windows.

Or, for us ubergeeks, umount with the CLI. Easiest way is with an alias ... :p

---

### Post by drs305 on 2007-02-07
> **blackhole82 said:**
> Right clicking on the drive when it comes up on the desktop and selecting unmount always works for me.  I'm new to ubuntu as well, but this doesn't really seem like a complicated issue since it closely resembles the way thumb drives work in windows.

You may be right. I've spend the better part of two days trying to get autofs to work. Perhaps I'm just overthinking this stuff. I'd still like to have the mount directories disappear when the device isn't connected though...  And how do I put a shortcut to the usb mount point on the desktop, especially if someone can tell me how to make the mount point disappear when it's not connected?

I appreciate everyone's inputs.

---

### Post by dannyboy79 on 2007-02-07
> **matt_risi said:**
> I always thought this was bull too. Like if Windows can unmount a usb device cleanly, why shouldn't Linux? It's little things like that that make things tough for a new user, not the overall experience/presentation of the OS. I've gotten used to unmounting my drive but it is still a nuisance.


what???? windows can't automagically unmount your drive either. You have to click on that little icon in the lower right part of the screen and click, safely remove blah blah blah. I THINK there may be a way to disable that so you can just unplug it but that has something to do with indexing or something like that. I forget.

---

