---
title: "Should I store files on my windows partition?"
date: 2005-09-11
forum: Absolute Beginner Talk
---

### Post by Steve Smith on 2005-09-11
I'm dualbooting Ubuntu & Win XP for now, untill I get everything I need working in Ubuntu.  I have a blank partition ready to format to use as my home directory, which I need to be able to read in XP.

- Can you mount a Linux partition in XP?
- Is there any benefit in formatting it as a Linux partition over having it as a win fat32 partition?
- Is there any risk of loss of data if it's a win partition?

Thanks!

---

### Post by aysiu on 2005-09-11
[QUOTE=happysteve]
- Can you mount a Linux partition in XP?[/quote] It's difficult, but I think theoretically it can be done with some third-party software.
> 
- Is there any benefit in formatting it as a Linux partition over having it as a win fat32 partition? FAT32 can share files between Linux and Windows.
> 
- Is there any risk of loss of data if it's a win partition? No.

Just so you know, though, /home partitions cannot be FAT32. You need a native Linux format for a /home partition.

---

### Post by Steve Smith on 2005-09-11
Thanks, that's cleared a could of things up for me.

[QUOTE=aysiu]Just so you know, though, /home partitions cannot be FAT32. You need a native Linux format for a /home partition.[/QUOTE]

... and that's changed my plans a bit! :)

---

### Post by aysiu on 2005-09-11
Well, if you have a huge partition that is clean, I'd divide it into two partitions--one very small and one very large. The very large should be the FAT32 partition with all of the files you want to share between Windows and Linux. The very small one should be EXT3 and /home (where all of your settings and preferences should go--they don't take up that much space).

---

### Post by Nequeo on 2005-09-12
[QUOTE=aysiu]Well, if you have a huge partition that is clean, I'd divide it into two partitions--one very small and one very large. The very large should be the FAT32 partition with all of the files you want to share between Windows and Linux. The very small one should be EXT3 and /home (where all of your settings and preferences should go--they don't take up that much space).[/QUOTE]
 Just to follow up on what Aysiu said, just because your home partition can't be FAT32 doesn't mean you can't mount a FAT32 partition inside your home directory.

For example, I have a 40GB FAT32 partition mounted as /home/sger/Shared in Linux, and as 'F' drive in Windows XP. 

Cheers,

---

### Post by Steve Smith on 2005-09-12
Thanks for the ideas, both of you!  Making it all fat32 and mounting it inside my home directory sounds like a good compromise for me :)

---

### Post by aysiu on 2005-09-12
[QUOTE=happysteve]Thanks for the ideas, both of you!  Making it all fat32 and mounting it inside my home directory sounds like a good compromise for me :)[/QUOTE] I'd highly suggest splitting it into two partitions--a large FAT32 and a small EXT3 (for /home). Having a separate /home partition is really important, especially for a new user. It means you can keep reinstalling the OS or install a new version of the same OS numerous times without losing your settings and preferences. The /home partition doesn't have to be big--maybe 1 GB or even less.

---

### Post by Steve Smith on 2005-09-13
[QUOTE=aysiu]I'd highly suggest splitting it into two partitions--a large FAT32 and a small EXT3 (for /home). Having a separate /home partition is really important, especially for a new user. It means you can keep reinstalling the OS or install a new version of the same OS numerous times without losing your settings and preferences. The /home partition doesn't have to be big--maybe 1 GB or even less.[/QUOTE]
 Er, thanks, just read that one too late (my fault!) and lost my Gaim settings, favourites... :-P  Going to reformat the whole thing to start again in a minute anyway, Linux newbiie getting in a mess, going to take you up on your suggestion! :)

---

### Post by aysiu on 2005-09-13
[QUOTE=happysteve]Er, thanks, just read that one too late (my fault!) and lost my Gaim settings, favourites... :-P  Going to reformat the whole thing to start again in a minute anyway, Linux newbiie getting in a mess, going to take you up on your suggestion! :)[/QUOTE] The first time you've got that partition set up, select the partition to be formatted as ext3 and mounted as /home.

In subsequent installs, select that partition to be mounted as /home, but *do not* select it to be formatted. Make sure it says "do not format."

---

### Post by Steve Smith on 2005-09-13
[QUOTE=aysiu]The first time you've got that partition set up, select the partition to be formatted as ext3 and mounted as /home.

In subsequent installs, select that partition to be mounted as /home, but *do not* select it to be formatted. Make sure it says "do not format."[/QUOTE]
 Thanks for your help, that'll make things much easier :)

---

