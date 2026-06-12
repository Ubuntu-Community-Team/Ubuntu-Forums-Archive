---
title: "Mount my 350D to access raw pix?"
date: 2006-09-02
forum: Absolute Beginner Talk
---

### Post by ehonda on 2006-09-02
I don't even know where to start looking for the right commands to mount my camera. Its a new 350D and has some raw photos on it that I need off. How do I do this?

---

### Post by kidders on 2006-09-03
Hi there,

In theory, plugging your camera in should be all you need to do. Of course, there are endless reasons why things might not happen for you. I'll try to talk you through some of them.

**I - See if your device is even supported**

If you have plugged in your camera since the last boot, reboot your system. This is purely for the sake of keeping these instruction simple.

Open a terminal window and type **dmesg** Lots of text should shoot past. Plug in your cam, wait about 5 seconds and type **dmesg** again. Note any new lines. There should be some messages about (1) a new USB device, (2) maybe some kernel modules loading, (3) filesystems discovered on the device. If the messages go this far, you should notice some reference to /dev entries. (I'll explain, just in case that doesn't mean anything to you.)

**II - Try to access a filesystem**

Especially for USB cameras, Linux tends to view them as "serial" devices. Take a look in /dev for new entries that start with "sd". The handiest way is to type **ls -l /dev/sd*** before and after plugging in your camera. The new additions are your camera. Let's just pretend they're called "/dev/sdb" and "/dev/sdb1".

**sdb** means "Serial Disk B" and **sdb1** means "Serial Disk B, Partition 1". First off, let's see if the camera did actually mount, and is just hiding someplace funny. Assuming you know your camera is "sdb", type **sudo mount | grep sdb** If there is any output, it indicates you're work is done. Navigate to the directory indicated (the output will say something like "/dev/sdb1 on /media/sdb1 type vfat").

On the other hand, perhaps your auto-mounting is not behaving itself. Mount your disk manually by:

[LIST=1]
[*]Creating a place for it to live: **sudo mkdir /mnt/camera**
[*]Performing the mount: **sudo mount /dev/sdb1 /mnt/camera**
[/LIST]

Now you can navigate to /mnt/camera to find your device. **Remember to dismount manually mounted devices** before plugging them out with **sudo umount /mnt/camera**

**III - Things to check**

[LIST=1]
[*]Is your camera in "disk" mode? The various other ways cameras can connect to computers are work for another day.
[*]Does "dmesg" tell you "Device not accepting blah blah"? This is usually bad news.
[*]Does "dmesg" acknowledge the existence of a new device, but show nothing else? This can mean you're having driver-related trouble. Hmmm.
[/LIST]

I hope some of this helps!

---

### Post by ehonda on 2006-09-04
I'm not around the camera and pc right now, but it automatically connects and takes the .jpegs off but won't see the RAW pix. All I did was plug it in with the usb cable and the import wizard starts right up. I'll try the other stuff though tomorrow and see what results I get.

Thanks for the help - Marshall

---

### Post by kidders on 2006-09-04
Ohhh... so you're not having any difficulty getting the cam talking to your computer? In that case, all you need to do is bear in mind that devices like cameras often have several connection "modes" (such as disk mode or PTP mode). Try tinkering with your camera's USB connection settings until you get the result you're after. At least *one* of them is bound to give you direct access to the raw images.

There are plenty of Linux apps that have support for raw image formats ... my advice is to install as many as you can find and try them all out. Of course, if there's a Windows app you like to use, check out Wine and Crossover Office.

My previous post was aimed at diagnosing communications problems with your camera ... you can ignore it :P

---

