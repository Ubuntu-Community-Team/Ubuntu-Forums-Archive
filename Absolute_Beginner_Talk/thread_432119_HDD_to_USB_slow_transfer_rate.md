---
title: "HDD to USB slow transfer rate??"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by jklslvch on 2007-05-03
hey im copying some music to a usb stick and it starts copying fast (5MB/s) but goes down to transferying by like 500kb/s whats the deal?

---

### Post by steve.horsley on 2007-05-03
I'm guessing that the original burst is as it fills up the in-memory disk cache rather than actually writing to the stick. And when the cache is full, the program's write rate slows down to refilling the cache as fast as it can be emptied into the stick.

Edit: 
Reading other posts, it looks like by guess may be completely wrong.

---

### Post by bozackt on 2007-05-03
I'm having the same problem. I just installed feisty after using dapper for quite a while. The hdd to usb transfer rate was quite fast under dapper, but slow under feisty.

Monitoring disk activity with gkrellm, I see something strange. The hdd read speed shows only about 800 KBps, but the usb drive write speed shows about 5 MBps. When I time how long it takes to copy a large file, the true throughput calculates out to slow 800 KBps number. Something strange is happening here. it's almost like it's throttling back to usb 1 speeds.

By the way, simply reading the hdd or the usb drive shows a sustained access speed of 5 MBps +.

This is really annoying since I back up to the usb drive.

Tom

---

### Post by bozackt on 2007-05-03
Forgot to mention - I have the problem using usb hard drive. I haven't tested it on a flash drive.

Tom

---

### Post by doundounba on 2007-07-28
<bump>

You guys ever solve this?  I'm seeing the exact same thing after upgrading from Edgy to Feisty - all of a sudden backups to external USB drive are super slow.  Same drive, same computer, OS upgrade.  Since I also back up to a USB external drive, this is very annoying...

---

### Post by bozackt on 2007-07-29
The problem is that the default USB mount option in Feisty is set to "synchrous". It may have been different in Edgy. This was apparently done so that if the USB cable is unplugged without unmounting no data will be lost.

To fix this right click on the device icon on the desktop, select "Preferences", select the "Mounting" tab, and uncheck "Synchronous". This setting seems to stick for future mounts of the device.

I don't know how to change the system default for this setting.

---

### Post by zgornel on 2007-08-01
> **bozackt said:**
> The problem is that the default USB mount option in Feisty is set to "synchrous". It may have been different in Edgy. This was apparently done so that if the USB cable is unplugged without unmounting no data will be lost.

To fix this right click on the device icon on the desktop, select "Preferences", select the "Mounting" tab, and uncheck "Synchronous". This setting seems to stick for future mounts of the device.

I don't know how to change the system default for this setting.
It worked on my external USB drive and it bumped the write speed from 7 to 25 MB/s (read speeds remain unchanged ofcourse). Also, (I am using KDE), the unchecked "Synchronous" option remains after dismounting and remounting the drive.

---

### Post by doundounba on 2007-08-01
> **bozackt said:**
> The problem is that the default USB mount option in Feisty is set to "synchrous". [...]

That did the trick!  Thanks bozackt! :cool:

---

