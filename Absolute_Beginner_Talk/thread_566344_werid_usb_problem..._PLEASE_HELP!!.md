---
title: "werid usb problem... PLEASE HELP!!"
date: 2007-10-03
forum: Absolute Beginner Talk
---

### Post by markkeng on 2007-10-03
my 1gb, 2gb ad gb usbs arent detected... but my usb printer, memory stick reader and scanner is working? what should i do to fix it? it is soooo irritating please help.

---

### Post by cmnorton on 2007-10-03
Did they ever work, or did they just stop working?

Look at the output of dmesg, and check /var/log/messages to get an idea of what might have happened.

---

### Post by Insightfill on 2007-10-03
I had run into a similar problem - it turns out that USB 2.0 support on my computer (even under WinXP) is flaky, but 1.1 is OK.  This leads to lower-speed devices (such as printers) running OK, but anything shooting for 2.0 to disconnect/reconnect randomly, or not connect at all.

Links:

[http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections](http://ubuntuguide.org/wiki/Ubuntu:Feisty/Hardware#Workaround_for_random_device_disconnections)

[https://help.ubuntu.com/community/UsbFlashDrives](https://help.ubuntu.com/community/UsbFlashDrives)

I knocked my computer to 1.1 only and now my external drive works.

---

### Post by roma.hicks on 2007-10-03
I may or may not know what I am talking about here, just some personal experience with this issue and how I fixed it.

First what is the filesystem on these drives; Ubuntu doesn't like to automount NTFS drives

I would first open terminal and type,
**>cd /media  **
Ubuntu stores most detected drive in this location; these are detected drives but not nessesaily mounted drives. 

If you see your drive, then Ubuntu has detected it just not mounted it; to mount it just type this,
**>sudo mount /media/*[devicename]* /dev/*[devicename]***
that should mount the volume.

If your drive is not there then you might have to probe the USB interface; type,  
**>lsusb**
If it appears there then your system can see the drive; if not, there might be a problem with the device of your USB interface.

next you should type 
**>dmesg | grep -i "SCSI device"**
It should list SCSI table , you need to know if the device is sda, hda, ect.
It should tell you after the word *device*.

Now you can type 
**>sudo mount *[filesystem type]* /dev/*[device]* *[location you want to mount it]***

This is a slightly longer method of mounting it, even though using the GUI does the same thing, but I've some GUI inconsistencies in Ubuntu at time.  

Hopefully this will help, but used this method on Damn Small, still Debian, but I don't know just try it.

---

