---
title: "Question about formatting hard drive from NTFS to FAT32"
date: 2006-09-07
forum: Absolute Beginner Talk
---

### Post by emma.meg on 2006-09-07
So, after last night's complete clean install of Linux on my system, I have sound, wireless internet, e-mail, and freedom from Windows with very little stress.

Now, I want to reformat my external hard drive (Maxtor OneTouch III) to go from NTFS to FAT32. I am using Gnome Partition Editor per the suggestion of another forum member, but when I open the program it recognizes two things:

/dev/sda
/dev/sdb

I click on the sdb which is my external HD but no options are available to me other than Unmount and Information. I tried to unmount (just testing it out) and it won't even let me do that. It says could not unmount /dev/sdb1 No such file or directory.

So, I have no idea what to do at this point.

Any suggestions?

Thanks.

---

### Post by aysiu on 2006-09-07
Have you tried this?

1. Plug in your drive.
2. In the terminal, type ```
df -h
``` to see where your drive is (let's just say it's /dev/sdb1)
3. Type ```
sudo umount /dev/sdb1
``` to unmount it
4. Type ```
gksudo gparted
``` to launch the partition editor. See if it can reformat /dev/sdb1 now.

---

### Post by emma.meg on 2006-09-07
That seemed to do the trick except I restarted and when I looked at its Properties, it's FAT32 but it still is read-only. It says it is mounted on /media/usbdisk. Do I need to unmount it to be able to use it? I don't quite understand what the whole mounting thing does...

---

### Post by aysiu on 2006-09-07
FAT32 and read-only? That's weird. Try ejecting it (right-click icon and select **Eject Volume**). Then, turn it off, unplug it, plug it back in again, and then turn it back on again.

Still read-only?

---

### Post by emma.meg on 2006-09-07
I tried what you said. After I clicked Eject, the icon was still there. I right-clicked on it and it still had an Eject plus it also has Mount Volume as an option now. So, I turned it off, did what you said, and when I turned it back on it was still read-only. :/

---

### Post by aysiu on 2006-09-07
That's weird. A FAT32 external hard drive usually mounts read/write. We can force it to mount read/write, but that's kind of weird workaround.

Does it always show up as /dev/sdb1?

---

### Post by emma.meg on 2006-09-07
It shows up as /dev/sdc1...but then again when I did the reformat, it was that name too (I think I might have unplugged it or something, maybe?)...

I did that df command again --

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              54G   20G   32G  39% /
varrun                252M   84K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
udev                  252M  160K  252M   1% /dev
devshm                252M     0  252M   0% /dev/shm
lrm                   252M   19M  234M   8% /lib/modules/2.6.15-26-386/volatile
/dev/sdc1             280G   16K  280G   1% /media/usbdisk

Does that help any? Shoud I just reformat again?

---

### Post by aysiu on 2006-09-08
Can you try this? ```
sudo eject /dev/sdc1
sudo nano -B /etc/fstab
``` Add in this line at the end ```
/dev/sdc1 /media/usbdisk vfat iocharset=utf8,umask=000 0 0
``` Then save (Control-X, Y, Enter) ```
sudo mount -a
``` Is it still read-only?

If not, then... well, that may do for now, but it's sort of a messy workaround, especially if your drive doesn't always show up as /dev/sdc1.

---

### Post by emma.meg on 2006-09-08
It said it couldn't mount it because /media/usbdisk does not exist...grr. 

I appreciate you tryin' to help me out here.

---

### Post by emma.meg on 2006-09-08
I could just return it tomorrow. Any suggestions for an external HD that holds 250-300 GB that's known to work well with Linux?

---

### Post by aysiu on 2006-09-08
Try: ```
sudo mkdir /media/usbdisk
sudo mount -a
``` By the way, I'm not 100% sure it's a compatibility issue. To be honest, it may just be that, for some strange reason, Ubuntu "remembers" your drive is NTFS and keeps mounting it read-only. A reboot may settle that. Who knows?

If it is a compatibility issue, I know for a fact that  my [LaCie external hard drive](http://www.amazon.com/gp/product/B0000DC6B0/102-0869703-2700140?ie=UTF8) works just fine.

---

### Post by emma.meg on 2006-09-08
Okay, I was able to add files to it but it looks like that's something I'll have to do every time I want to use the HD. I was hoping for something a little bit more plug-and-play and less buggy...I think I'm just gonna return it and try another one.

Thanks for all your help!

---

### Post by aysiu on 2006-09-08
> **emma.meg said:**
> Okay, I was able to add files to it but it looks like that's something I'll have to do every time I want to use the HD. I was hoping for something a little bit more plug-and-play and less buggy...I think I'm just gonna return it and try another one.

Thanks for all your help!
No--as long as it keeps showing up as /dev/sdc1, it should be more plug-and-play.

Now, theoretically (and in my experience), it really should be plug-and-play without the /etc/fstab editing. At least try a reboot before you return it. What model is it?

---

### Post by emma.meg on 2006-09-08
It's a Maxtor OneTouch III 300 GB (which from what I've read, really shouldn't be giving me problems). I did try rebooting and it was still acting funky. I bought it from Staples and I remember they were selling some LaCie drives there...I'll give those a try. :)

---

### Post by emma.meg on 2006-09-08
One last question (hopefully, right) -- in my media folder I have the following folders:

cdrom
cdrom0
New Volume
usbdisk

I just want to know if when I plug in my new external HD tomorrow that somehow those folders are going to mess with how it works. Like, I have no idea what New Volume is but it says free space ~ 31 GB. Is that related to the main thing (I'm still thinking in terms of Windows here, so C:)...

---

### Post by aysiu on 2006-09-08
You're right--it really shouldn't be giving you any problems. Truthfully, I'm not much of a mounting expert. Maybe someone can better diagnose what exactly is going wrong here.

---

### Post by boon on 2006-09-08
> **emma.meg said:**
> I could just return it tomorrow. Any suggestions for an external HD that holds 250-300 GB that's known to work well with Linux?

I recently acquired a 300gb seagate external usb hardrive, and described some of my experiences here:

[http://www.ubuntuforums.org/showthread.php?t=249636](http://www.ubuntuforums.org/showthread.php?t=249636)

I can make the following comments:

[LIST]
[*]the drive was preformatted in FAT format and thus read/write out of the box for both windows and ubuntu systems

[*]there seemed to be a problem with the gparted software on the ubuntu cd, so i downloaded and used with success the gparted livecd

[*]you have to adjust permissions on your partitions to make them properly usable
[/LIST]

After a bit of messing about, everything seems to work fine just now.

---

