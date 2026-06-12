---
title: "USB stick permissions"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by MichaelSM on 2007-11-01
I have read just about everything I can find on this topic in the Forum, but can't get things straight. I know it's my stupidity, but please help a fool if you can......

Quite simply, I plug in my new 1G USB stick and no desktop icon appears (The stick is formatted fat32)

Places>Computer and there it is. But I can't open it. "Only root can mount /dev/sda1 to /media/sda1"

Fair enough.

How do I 'mount' it as 'root' and then hopefully change something so's I can just plug it in and use it without 'rooting' it?

Thanks in advance (as usual!)

Mike.

---

### Post by jabeez on 2007-11-01
I recently went through quite the debacle with my flash drive. I hadn't used it in awhile, and I went to erase everything and load some music, and thus started permission hell. I didn't have permissions, so I opened a root-mode konqueror (I use Kubuntu) and I STILL couldn't do anything with it. I then took it to my wifes machine and booted into XP, and STILL couldn't do anything. Kept getting "disk protected" errors. I then tried loading the gparted live cd to just completely wipe it, and STILL couldn't do anything. Eventually I just deleted all the files through the drives menu system (luckily it's an mp3/flash drive). I understand the need for security and appreciate what Linux does in this area, but DAMN, things like this can get really ridiculous. I hadn't used the drive for anything other than copying files from my laptop etc., never "protecting" anything (or so I thought), so why the need for such ridiculous security? I had similar problems with adding a hard drive to my bro-in-laws 'puter. Maybe it is a KDE thing, but that was also a debacle, I could enter "administrator" mode but yet couldn't change permissions. So I guess I have nothing to add besides this lil rant......:) good luck though, if I think of anything else I'll post back............

---

### Post by dRock1286 on 2007-11-01
> **MichaelSM said:**
> I have read just about everything I can find on this topic in the Forum, but can't get things straight. I know it's my stupidity, but please help a fool if you can......

Quite simply, I plug in my new 1G USB stick and no desktop icon appears (The stick is formatted fat32)

Places>Computer and there it is. But I can't open it. "Only root can mount /dev/sda1 to /media/sda1"

Fair enough.

How do I 'mount' it as 'root' and then hopefully change something so's I can just plug it in and use it without 'rooting' it?

Thanks in advance (as usual!)

Mike.

I've never had this problem personally, and i don't know if it will work...but...go to your terminal and type
```
sudo nautilus
```
then your password.  see if you can access the computer location and try mounting it that way.  might work, might not...I'm not currently running ubuntu to try it...

---

### Post by dswhite85 on 2007-11-01
I am having the exact same problem and no work around has worked for me yet..

---

### Post by MichaelSM on 2007-11-01
Hello. Nice to know I'm not alone, at least!

So I tried to use my brain .......

michael@michael-desktop:~$ sudo mount /dev/sda1 on /media/sda1
Usage: mount -V                 : print version
       mount -h                 : print this help
       mount                    : list mounted filesystems
       mount -l                 : idem, including volume labels
So far the informational part. Next the mounting.
The command is `mount [-t fstype] something somewhere'.
Details found in /etc/fstab may be omitted.
       mount -a [-t|-O] ...     : mount all stuff from /etc/fstab
       mount device             : mount device at the known place
       mount directory          : mount known device here
       mount -t type dev dir    : ordinary mount command
Note that one does not really mount a device, one mounts
a filesystem (of the given type) found on the device.
One can also mount an already visible directory tree elsewhere:
       mount --bind olddir newdir
or move a subtree:
       mount --move olddir newdir
A device can be given by name, say /dev/hda1 or /dev/cdrom,
or by label, using  -L label  or by uuid, using  -U uuid .
Other options: [-nfFrsvw] [-o options] [-p passwdfd].
For many more details, say  man 8 mount .
michael@michael-desktop:~$ 

Now if someone can interpret THAT for me, maybe we'll be on a winner.

Cheers,

Mike.

---

### Post by anaconda on 2007-11-01
sudo mount /dev/sda1 /media/sda1

Or if you want to specify the type of the partition (usually not needed)

sudo mount -t vfat /dev/sda1 /media/sda1

But actually I would mount it somewhere else, because the /media/sda1 -folder propably doesn't  exist if you haven't created it. 

so you could write (first create the directory, then give everyone rights to it and finally mount the usb-stick)
sudo mkdir /media/usbdisk1
sudo chmod a+rwx /media/usbdisk1
sudo mount /dev/sda1 /media/usbdisk1

---

### Post by MichaelSM on 2007-11-01
Anaconda, that went well at first (I stuck with 'sda1' instead of 'usbdisk1' because that's what the original notification mentioned.) .

So now I have a Desktop icon 'sda1' which I can't write to, copy from,nor change any of the permissions which might enable me to do so, because I'm not 'root' (at Desktop level)

Thanks for the great advice!

Last step to go.

Mike.

---

### Post by anaconda on 2007-11-01
sudo nautilus

would give you file-browser with root rights, and with that you should have read/write rights

but I suspect that you just dont have rw rights to the folder /media/sda1 
This should give you the rights.
sudo chmod a+rwx /media/sda1

---

### Post by MichaelSM on 2007-11-01
Thanks again, Anaconda.

That entry you mentioned, "sudo chmod a+rwx /media/sda1" I had already completed after reading your earlier post.

There must be something wrong with my Edgy file-system; sorry about that. 

After a re-boot and inserting the USB stick, there was no Desktop icon, so to see what was happening, with my limited knowledge, I tried two commands. 1) sudo gedit /dev/sda1 and 2) sudo gedit /media/sda1.

The first command opened an empty folder. The second showed sda1 with a loud comment 'could not open etc.' with red buttons here and there.

I am worried that I'm wasting your time, Anaconda, but ...

Any suggestions greatly appreciated.

Cheers,

Mike.

Late addition: I've done a lot more checking up on this and it appears to be a massive bug so where does that leave us? 

By the way, I just fired up my spare box with Ubuntu Studios on it, plugged in the USB stick, and it was instantly recognised, openable , and writable from Desktop. So it's an Edgy problem....?

---

### Post by MichaelSM on 2007-11-02
Hi. Replying to my own post is about as bad as it can get, but I have one un-answered question.

I have spent hours upon hours getting my Edgy hard-drive up to par. I have followed every thread on EVERY forum, diving into EVERY tiny piece of information and using it as best I can to create a useable and practical operating system which suits my needs, and most of it has worked very well. What our community does keeps me awake at night 'til all hours, and I don't mind it at all. It's brain-food, tiring and refreshing at once. 

I have had a reasonable look at the Ubuntu development sites, and have gained a rough enough idea about the parameters and restrictions required to develop various aspects of an open-source OS.

I have not yet found the development thread which relegated Edgy users to the Neanderthal era vis a vis USB mass storage plugins when the technology was available so many yonks ago. 

It might be well and good for our community perhaps to tell me to upgrade to Feisty/Gutsy/Heron but I've got an elaborate system built upon Edgy which is the ant's pants as far as I'm concerned and I've read enough posts to frighten me off an upgrade as in losing important data.

Maybe this is the focal point of why I am discouraged with my slowly-developing IT work as in getting other people onto Ubuntu Linux. It's not something I make money out of, it's just what I DO in my small town, and I was moments away from having a community meeting to tell all the good news, until I was lucky enough to discover that the USB sticks, which the oldies get from their grand-kids, with all their school-work and  music, can't be accessed on the free Edgy boxes I nearly gave them.

There must be a patch for this. 

Surely I don't have to re-load six or more hard-drives with Feisty just to mount USB sticks.........?

Mike.

---

