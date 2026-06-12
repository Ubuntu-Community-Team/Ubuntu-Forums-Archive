---
title: "probem new install 7.1"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by never_retreat on 2008-01-27
Hello All
Let me start this off by saying this is my first non-winblows endeavor.
I'm trying to install 7.1 64 bit on my computer. Here is the problem I cant get the cd to boot. The drive will boot other cd's but not the one that I made from the download. Yes I unzipped it. I can boot to a floppy also. Is there somewhere that I can download a magic ubuntu boot disk from. Bearing in mind I have to do this on a windows system. I don't have anything else running a non windows os.

And in lames terms also, I haven't finisher reading the idiots guide to linux yet.

---

### Post by emarkd on 2008-01-27
Did you get the MD5 hash from Ubuntu's site and make sure the ISO you downloaded wasn't corrupted?

As for getting the ISO's, I always have the best luck with the torrents.  You can get the torrent from Ubuntu's site.

---

### Post by JoshuaRL on 2008-01-27
Yeah.  And you want to burn it to a disk as an ISO file, on the slowest speed possible.  I haven't installed the 64bit system, but I have installed some of the others and I don't think there's any unzipping involved.  As far as other install methods, try the following link.  It has a ton of other ways, including off of an ISO file on a windows partition.  Haven't tried it personally, but if it's in the community documentation you should be able to trust it.

[https://help.ubuntu.com/community/Installation](https://help.ubuntu.com/community/Installation)

---

### Post by never_retreat on 2008-01-28
I did the hash thing The ISO is fine. Any other ideas

---

### Post by emarkd on 2008-01-28
Does it try to boot?  Some hardware is not supported by the CD (usually a video issue) and you have to install using the Alternate CD, which is text-based.

---

### Post by JusCindy on 2008-01-28
I had the same problem and it turns out that the first ISO I downloaded from here wasn't right so I downloaded from another site and it was fine. Make sure you make the cd using the ISO not a zipped file and it should boot ok.

---

### Post by amazingtaters on 2008-01-28
Make sure you are burning the ISO correctly. If you are using something like Nero, you need to make sure you don't choose the option to burn a bootable disc, as those will turn up as duds. I've made that mistake. Could you elaborate on what you are using to burn the live cd and all of that good stuff?

---

### Post by never_retreat on 2008-01-28
I downloaded ubuntu-7.10-desktop-amd64.iso, used win rar to unzip it to a folder, then used nero to make a cd from everything that was in the folder.

---

### Post by emarkd on 2008-01-28
Ah.  The ISO is a CD image.  You don't extract it.  Just use Nero to burn a CD image and select the ISO file.

---

### Post by harrybazeegar on 2008-01-28
what you do is select the "burn image" option in nero ... it comes under the "other " or "misc" heading...

you just select the iso file and nero burns it... no unzipping, no making bootable option.

---

### Post by never_retreat on 2008-01-28
I re did the disk and that fixed it.
But got a new problem.

install froze 
PCI warning cannot find a gap in the 32 bit address range
PCI unassigned devices with 32bit resource registers may break!

any ideas?

---

### Post by never_retreat on 2008-01-28
Hello anyone?

---

### Post by never_retreat on 2008-01-28
Memory problem. Should have known that was going to happen. down to 512 ram, I 'll have to get some more.

---

