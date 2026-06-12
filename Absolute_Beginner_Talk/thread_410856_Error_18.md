---
title: "Error 18"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by nicketynick on 2007-04-16
I'm going to post this here, since I'm a novice:
I was  running Dapper, mostly just to run Slimserver. It was working pretty well until:
Wife went to power up a SB last night, and SS crashed. There was some sort of error message in the top part of the right pane of SS, but I couldn't read it all. So I figured a restart was the best idea. While it was shutting down, a warning pop-up came up, but all it had for text was little boxes. I hit the button that would have been OK, and waited for the restart. There were some errors in shut-down process - went by to quick to get them, and here's what I got at restart:

Grub loading...
Error 18

And the drive making funny seeking sounds.
Sound like hardware or software failure?
I've looked up Error 18, being related to partition size, etc. but I don't think I changed anything in that respect!
Unfortunately I don't have a Ubuntu CD handy (I'm going to have to burn one from another machine), but I do have an old version of SlimCD I think I'll throw in to see if the machine will run.
Anybody have any advice to help me out here?
Thanks,
Nick

---

### Post by nicketynick on 2007-04-16
Some more info:
This is not a dual-boot machine - Ubuntu is the only OS
Here is what my fstab looked like immediately prior to the crash:

test@test-desktop:~$ cat /etc/fstab
# /etc/fstab: static file system information.
#
# <file system> <mount point> <type> <options> <dump> <pass>
proc /proc proc defaults 0 0
/dev/hda1 / ext3 defaults,errors=remount-ro 0 1
/dev/hda5 none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/sda1 /media/sda1 ntfs nls=utf8,umask=0222 0 0
/dev/sda5 /media/sda5 vfat iocharset=utf8,umask=000 0 0

hda1 is a tiny drive (8-10GB maybe?). sda1 & sda5 are partitions of about 120GB each on an external drive. Could something be screwed up so that grub is trying to boot from one of the large partitions or something?
I'm stumped - all this is new to me, and I can't understand why if it was working yesterday, and I didn't change anything.....?

---

### Post by dstew on 2007-04-16
Error 18 means that Grub was directed to a partition that was out of range of the BIOS. Usually this is because the linux kernel is on a large disk, past the 8 Gb mark. However, it looks from your fstab that /dev/hda1 is the root directory, and the error doesn't fit with what I see there. That makes me think that something may have happened to the partition table of the drive. If that is the case, you may need to re-format/re-partition your first drive. I do not think simply re-installing grub will work, but you could try that first. You can re-install grub from a live CD (terminal window -- grub -- root (hd0,0) -- setup (hd0)) to see if that helps.

By the way, what exactly did your wife do? I don't understand "SB".

---

### Post by nicketynick on 2007-04-16
Thanks for the response.  I'll have to get myself a LiveCD burnt from another machine - I got this machine with the OS installed already, but no CD :( 
Sorry about the vague references - I just pulled some of the text from posting on another forum. The SB is the Squeezebox3, [www.slimdevices.com](www.slimdevices.com), which is what uses Slimserver. That's all I'm really using the machine for, so I can't figure out how it 'broke'!

---

### Post by nicketynick on 2007-04-24
I'm thinking it is definitely a dead hard-drive. Running the grub commands above seems to have only resulted in a lot of repetitive 'bad' noises from the HD. Guess I'm going to have to take another approach - is there a way I can block off bad sectors on this HD and re-install Ubuntu?

---

