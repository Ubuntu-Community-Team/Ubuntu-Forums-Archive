---
title: "African Gremlins"
date: 2006-11-27
forum: Absolute Beginner Talk
---

### Post by nnjond on 2006-11-27
When installing Dapper, things go smoothly until step 5 (of 6); Prepare to partition.  Then, i think 4 options appear, including an automatic sizing. Set at 50/50. On an 80gib disc,this would be ok. But it returns with, -"Not enough space" ?  And i can only go back! But much more often than that, Step 5 reveals only 2 options:

Erase entire disc.

Manually partition. 

if i must manually partition, please could u advise me.

---

### Post by Bachstelze on 2006-11-27
Use an Alternate CD :)

---

### Post by diepruis on 2006-11-27
How much space is in use on the disc?

Did you defrag the disc before trying the installation?

---

### Post by nnjond on 2006-11-27
It's an 80 disc, just formated with Win 2000. almost no other data.

---

### Post by nnjond on 2006-11-27
have tried 3 CDs

---

### Post by diepruis on 2006-11-27
Does the disc use NTFS?

---

### Post by nnjond on 2006-11-27
ntfs. yes.

---

### Post by shaft350x on 2006-11-27
I had problems when I was trying to partition my HD also (120 GB) I had run defrag on it several times, I got a different error, but the solution may be the same.  Try running a chkdsk in windows, or scan disk, or whatever the tool is called to find corrupted files and what not.  Use that then try again.  If you have to do it manually, you will need your windows partition, a swap partition and then your linux partition.  I'm fairly new to this as well, so I can't remember the technical terms, but someone here probably knows.

---

### Post by Sparkl on 2006-11-27
As I know (don't trust me much:-D) Linux only supports FAT32...(my friend told me so...)

---

### Post by diepruis on 2006-11-27
I'd suggest setting up your partitions using the tool on the Live CD, then installing Windows on the partition you created for it. Linux has... issues with NTFS partitions.

Remember to install Ubuntu **after** Windows. Otherwise Windows will hose your bootsector and you won't be able to boot Ubuntu. Ubuntu's installer plays much nicer - at least, that's what I've heard.

---

### Post by diepruis on 2006-11-27
PS: African Gremlins are called "Tokeloshis".

---

### Post by umattu on 2006-11-27
I may be wrong but, I think the issue is that the entire 80gb is one partition that is currently owned by your win2000 install. what you need to create an empty partition, (besure to defrag before doing so, gotta love windows :)) Now when you go to install Ubuntu the installer will see the empty space and you should be able to partition it out however you'd like.

I ran into the same issue when I tried dual booting XP with Ubuntu

---

### Post by diepruis on 2006-11-27
> **umattu said:**
> I may be wrong but, I think the issue is that the entire 80gb is one partition that is currently owned by your win2000 install. what you need to create an empty partition, (besure to defrag before doing so, gotta love windows :)) Now when you go to install Ubuntu the installer will see the empty space and you should be able to partition it out however you'd like.

I don't believe this is the error. My installation was quite happy to resize an existing NTFS partition. It completely broke it as well, of course. :(

I don't know what the error is, so let's avoid it completely. Since the PC is newly installed, that is quite easy to do.

---

### Post by drr422 on 2006-11-27
What i have always done is that since windows by default installs on the whole space you select for it, which may be in your case the 80 gb driv.  So what you may need to do is to use some partitioning software to resize it to your desired size, for example 40 gb, and leave the other space alone.  When you boot up the livecd, then you can choose to install on the partition that is less than 40 gb.  I usually manually edit the partition table like this:
2 GB for /home
10 GB for /
rest for /home/yourname/documents

Sometimes the partition editor in the installation program fails, so if that happens, you can use gparted (on Edgy live cd) and edit the partition table as you see fit.

that way, i can keep my personal preferences when i reinstall and i can keep all of my documents in a seperate partition.  
Thats my two cents anyways...

---

### Post by umattu on 2006-11-27
> **diepruis said:**
> I don't believe this is the error. My installation was quite happy to resize an existing NTFS partition. It completely broke it as well, of course. :(

I don't know what the error is, so let's avoid it completely. Since the PC is newly installed, that is quite easy to do.

Are we on the same thread here? I have yet to read of any errors he is getting, and where does it state it is a fresh system? 

I spoke from experiance, I had this issue. If what you say is true, that the ubuntu partitioner destroyed your NTFS partition then I would suggest that an empty partition is ready and waiting for the Ubuntu install, just so the NTFS is not destroyed. I know that if the first time I tried installing a Linux distro on my box and it broke my NTFS partition I would of been mad as mad can be and I would NOT have tried it again. Thankfully I had issues like hte poster of this thread and I made empty space on my drive via partition Magic and the Linux install was smooth sailing.

---

### Post by diepruis on 2006-11-27
Error:

> **nnjond said:**
> But it returns with, -"Not enough space" ?

Fresh system:

> **nnjond said:**
> It's an 80 disc, just formated with Win 2000. almost no other data.

Futher, I was merely stating that resizing an NTFS partition is dodgy at best. I was trying to convey that doing it all over again is to be preferred.

---

### Post by idrinkwhisky on 2006-11-27
you could boot the windows cd and then partition your hard drive into 2 drives. 1 for windows and 1 for 1 for linux. Leave the linux drive as "raw", i.e. not ntsf/fat32 or anything else for that matter.

then boot from ubuntu live cd and select the raw drive. Let Ubuntu live cd format it in ext3 and install it on that partition.

(i'm sure there is a smarter way, but this method worked for me).

---

### Post by drphilngood on 2006-11-27
> **HymnToLife said:**
> Use an Alternate CD :)

You really should follow HymnToLife´s advice.

---

### Post by CarpKing on 2006-11-27
> **drphilngood said:**
> You really should follow HymnToLife´s advice.

And by Alternate CD, we mean the Alternate Install CD, not merely another copy of the Live CD.

---

