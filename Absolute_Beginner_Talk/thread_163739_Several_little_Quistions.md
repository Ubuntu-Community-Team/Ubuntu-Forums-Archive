---
title: "Several little Quistions"
date: 2006-04-21
forum: Absolute Beginner Talk
---

### Post by wesireal on 2006-04-21
Well, there are no reliable 64 bit  codecs for audio and video, so;

Can a 32bit Ubuntu be installed on amd64 bit processor?

On 64bit  dual-core?

If so, will all the 32bit apps including wine work?:-D

One more.

Can ubuntu be installed on a ntfs partition or does it have to be fat32? If ubuntu is the ONLY os on the pc then what format the hdd be? I ask this because on fat 32 there is a limitation of 4000mb to one dvd. Ntfs can go to 4460mb. Quite a difference and i do a lot of video work.

---

### Post by nanotube on 2006-04-21
yes, you can install 32bit ubuntu on 64bit proc.
you can even install 32bit dual-core kernel on your 64bit dual core processor, i think.

---

### Post by Randomskk on 2006-04-21
Don't format the drive in linux, but the filesystem will mostly be ext3.
While reading/writing FAT32 and reading NTFS are both supported, neither are actual linux file systems - linux uses ext2 and ext3, and reiserfs generally speaking.

Using the normal CD installer, if you tell it to automatically partition the drive it will do all you need for you as far as formats go.

---

### Post by VoiceOvGod on 2006-04-21
If you are using 32-bit, then Wine should work just fine.

Basically, its just like 64bit processor running 32bit windoze. It is tricked into thinking it is 32 bit.

---

### Post by wesireal on 2006-04-21
[QUOTE=Randomskk]Don't format the drive in linux, but the filesystem will mostly be ext3.
While reading/writing FAT32 and reading NTFS are both supported, neither are actual linux file systems - linux uses ext2 and ext3, and reiserfs generally speaking.

Using the normal CD installer, if you tell it to automatically partition the drive it will do all you need for you as far as formats go.[/QUOTE]

Thank you. Are there any video size problems/limitations as between fat32 and ntfs?  Anyone know the maximum video size that can be burned onto a dvd in ubuntu/linux? Please.:-k

---

### Post by Randomskk on 2006-04-21
Same as in windows. The DVD is a maximum capacity, both linux and windows can full it up. As far as FAT32 and NTFS go, it's the same limits as windows but remember - linux CANNOT (safely) write to NTFS, only to FAT32 (it can read both, however).

EDIT: sorry, I just noticed I said "Don't format the drive in linux, but.." - what I meant to say was don't format it from windows, as windows cannot format the disk to the filesystem type linux needs. Ooops ><

---

### Post by wesireal on 2006-04-21
ok;however;

Fat32=4000mb maximum-----Ntfs=4460mb maximum.
In linux----ext2=?   ext3=? and reiserf=? in mb,offcourse. Please

---

### Post by Randomskk on 2006-04-21
You might find this page useful:
[http://en.wikipedia.org/wiki/File_system_comparison](http://en.wikipedia.org/wiki/File_system_comparison)

---

### Post by nanotube on 2006-04-21
[QUOTE=Randomskk]You might find this page useful:
[http://en.wikipedia.org/wiki/File_system_comparison](http://en.wikipedia.org/wiki/File_system_comparison)[/QUOTE]

heh yea, that's the link i was going to post before i saw your post. :)

but to summarize, essentially, if ubuntu is the only os on the computer, just go with ext3 (the default filesystem) or reiserfs, and you will not be running into any file size limits (maximum size is in terabytes). don't worry about considering fat32 or ntfs at all.

---

### Post by wesireal on 2006-04-22
nanotube, thank you.

You have answered my real quistion. No limits on size; I assume it also means no limits to how much can be burned onto disk> wow

Does this also remove the 2000mb limit of divx files(Burning onyo disk) as well? Anyone with experience of video conversion etc? Please.

---

### Post by nalmeth on 2006-04-22
If you'd like to stick with the 64-bit kernel, you can create a 32-bit chroot environment to run whatever 32-bit stuff u need. The howto is in Customization Tips and Tricks I think!
As for divx/avi
I've never felt the need to rip to anything greater than 1 Gig, but I see no reason why you could not rip to as high as 2 gig's.

Check out acidrip. Most people would recommend dvd::rip, but acidrip done good for me!

---

### Post by wesireal on 2006-04-22
[QUOTE=nalmeth]If you'd like to stick with the 64-bit kernel, you can create a 32-bit chroot environment to run whatever 32-bit stuff u need. The howto is in Customization Tips and Tricks I think!
As for divx/avi
I've never felt the need to rip to anything greater than 1 Gig, but I see no reason why you could not rip to as high as 2 gig's.

Check out acidrip. Most people would recommend dvd::rip, but acidrip done good for me![/QUOTE]

Your suggestion raises an interesting quistion;

Due to lack of 64bit audio video codecs one shall have to install in the cheroot! Then, would it be possible to stream the video from the cheroot(!) to my tv, which will be the second monitor on the system?:twisted:

---

### Post by nanotube on 2006-04-22
[QUOTE=wesireal]nanotube, thank you.

You have answered my real quistion. No limits on size; I assume it also means no limits to how much can be burned onto disk> wow

Does this also remove the 2000mb limit of divx files(Burning onyo disk) as well? Anyone with experience of video conversion etc? Please.[/QUOTE]

you can burn on a disk as much as the disk will hold. most dvd-r disks are 4.7 gigs, so that would be your limit. if you have dual layer disks they are 9 gigs.
you would not be subject to the 2000mb limit for divx files.

---

