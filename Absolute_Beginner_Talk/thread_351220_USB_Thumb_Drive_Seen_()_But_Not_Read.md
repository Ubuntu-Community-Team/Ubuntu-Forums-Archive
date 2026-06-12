---
title: "USB Thumb Drive Seen (?) But Not Read"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by .plaid on 2007-02-01
Howdy.

I'm more experienced with navigating forums than I am with a non-Windows OS, and I didn't see this question addressed anywhere, so if it has already been answered then that tells you something about my experience with Ubuntu. That said, I'm feelin' good.  

I was recently given a laptop (an old Dell Latitude) with a copy of Win2KPro for which I had neither license nor login, so I decided to format and install Dapper Drake...just last night, now that I think about it. I recognize that I'm in way over my head, but it's a learning process so I'm ok with that.

I'd like to get my (it seems highly fickle) 2011B LAN PC Card to work, so I downloaded a spectrum*.tar.gz and put it on my USB thumb drive. I stuck the drive in the USB slot, and it looks like *lsusb --verbose* detects the drive, but I get no icon - nor does the led on the drive light up.

I'd like to work on the assumption that the port functions correctly; I know the drive works. I've read some that Ubuntu supports 'plug-n-play' but I've not seen this happen yet. **What should I expect to see when I stick a USB drive in the port?** For completeness, I don't see an immediate solution to getting new/more packages until after I get the wireless internet working.

Thanks for your time, and have a great day.

.

---

### Post by glabouni on 2007-02-01
when you plug a usb thumb drive, it should show up on the desktop.
but sometimes it doesn't work as intended, I've seen other thread about similar problem, and I experienced one myself.

you can try to mount it manually using the mount command inside a terminal.

you will need 3 things, a place to mount it, to know what type of filesytem your thumbdrive is, and under what device name your usb thumbdrive is known to the system.

tu get a place to mount it, simply create a directory. the following command will create a directory named "usbthumbdrive" in /media
```
sudo mkdir /media/usbthumbdrive
```

to find which filesystem is on the drive and what's its name to the system, use this command:
```
sudo fidsk -l
```

the output will contain something like this:

```
Disk /dev/sdc: 131 MB, 131072000 bytes
9 heads, 32 sectors/track, 888 cylinders
Units = cylinders of 288 * 512 = 147456 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1         889      127983    6  FAT16
```

find the one corresponding to you usb drive, you'll find its device name under the device column and the filesystem type under the system column.

next you have to mount the filesystem using the mount command
```
sudo mount -t <filesystem> <what> <where>
```
replace <filesystem> by the corresponding filesystem, <what> by the device name, <where> by the place where you want to mount the filesystem

in my case that would be
```

sudo mount -t vfat /dev/sdc1 /media/usbthumbdrive

```

usb thumbdrive content will then be available in /media/usbthumbdrive directory.

---

### Post by .plaid on 2007-02-01
Hi glabouni,

Thanks for your quick reply.

I ran *fdisk -l* (a bit warily with my DOS experience and a lack of *fdisk help*) and it only found my HDD. 

Disk /dev/hda: 12.0 GB, ... bytes
255 heads ...
Units = ...

Device          Boot   Start   ... System
/dev/hda1       *        1      ... Linux
/dev/hda2                1404  ... Extended
/dev/hda5                1404  ... Linux Swap / Solaris

Now, I could convince myself that hda2 is my thumb drive, but I would've expected it to show up as a separate disk, not simply another device under the same disk - unless I don't know how to read this output...?

Am I right in thinknig that there's no real danger to mounting hda2 and finding out what data it contains? I would never think of doing something so cavalier with Windows, but I'm feeling saucy with Linux....

Thanks again,

.

//edit: *info fdisk* worked tho, need to remember that one....

---

### Post by %hMa@?b&lt;C on 2007-02-01
> **.plaid said:**
> Hi glabouni,

Thanks for your quick reply.

I ran *fdisk -l* (a bit warily with my DOS experience and a lack of *fdisk help*) and it only found my HDD. 

Disk /dev/hda: 12.0 GB, ... bytes
255 heads ...
Units = ...

Device          Boot   Start   ... System
/dev/hda1       *        1      ... Linux
/dev/hda2                1404  ... Extended
/dev/hda5                1404  ... Linux Swap / Solaris

Now, I could convince myself that hda2 is my thumb drive, but I would've expected it to show up as a separate disk, not simply another device under the same disk - unless I don't know how to read this output...?

Am I right in thinknig that there's no real danger to mounting hda2 and finding out what data it contains? I would never think of doing something so cavalier with Windows, but I'm feeling saucy with Linux....

Thanks again,

.

//edit: *info fdisk* worked tho, need to remember that one....
man fdisk or fdisk --help will also work. I like fdisk --help, as it just briefs on the command, plus modifies, rather than the enitre manpage

---

### Post by .plaid on 2007-02-01
UPDATE:

In what was a surprise to probably only me, **filesystemtype 'extended'** was not recognized; so it's a device not meant to be mounted I suppose.

---

### Post by .plaid on 2007-02-02
//commence finger-pointing and snickering

I hooked up a friend's digital camera to the usb port and it was instantly recognized, so when I got home I plugged in a different thumbdrive, and *poof* there it was on the desktop. 

On further inspection the problem was 'operator headspace and timing': the housing for the original thumbdrive is too big to mate correctly with the port on the back of the laptop.

So, problem 1 solved, onto problem 2....

Thanks again for all of the insight - at least I got to poke around with the terminal a bit, eh?

.

//end snickering (at least do it more quietly)

---

