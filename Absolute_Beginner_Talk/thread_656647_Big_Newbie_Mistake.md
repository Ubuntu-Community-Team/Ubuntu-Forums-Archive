---
title: "Big Newbie Mistake"
date: 2008-01-02
forum: Absolute Beginner Talk
---

### Post by squier on 2008-01-02
i have previously had ubuntu on an old comp.  i went thru the installation fine and i knew that i needed to partition to run with windows.  i just got a new laptop with windows vista (not too fond of it but as i am still in school i need it for some things), but anyways i went to install ubuntu.  it seemed like everything worked but once i restarted it would load to the screen with  grub 1.5  and just stop.  its the screen rite before where you choose which one to boot.  so i put the cd back in and tried to start over.  i guess i went to fast and missed the partitioning part.  so now i think i have wiped out windows.  so i guess my main question is windows totally gone now and if not how would i go about getting it back.  my computer is from acer and i did not receive a windows cd with it.  
also if i am just screwed and have to buy windows again what do i need to do to set up a dial up connection on ubuntu.  maybe i'm looking in the wrong place but i can't seem to figure it out.  i go to the network and enter the info but i do not see anywhere to actually connect once i do that.  
thanks for any help or tips on getting this figured out

---

### Post by eolson on 2008-01-02
To most of that,  I don't know.  Somebody will be along who can help I am sure.  As to the no cd,  I'd call Acer and tell them you didn['t receive one and need it.  Any excuse.  Not providing cd's is getting to be a BAD habit with vendors.  It's absolutely nuts.  I think it's probably due to pressure from MicroSoft but don't know that to be true.  A stupid CD only costs a few cents in bulk.  Sorry for the rant.

---

### Post by sumguy231 on 2008-01-02
If you used the default 'use the entire hard disk' install option, it's gone. To make sure, do a 'sudo fdisk -l' in a terminal and see if it lists a Windows partition there. The filesystem type will be listed as NTFS.

I don't know anything about dial-up so I can't help you there. But you might try searching the Ubuntu Wiki:
[https://wiki.ubuntu.com/](https://wiki.ubuntu.com/)

---

### Post by philinux on 2008-01-02
boot the live cd.

Open terminal Apps>Accesories>terminal

Post the output of the command 

sudo fdisk -l

that's a letter L but small case

This will show whats happened to your disk. Maybe windows is still there and ubuntu is there too.

---

### Post by dstew on 2008-01-02
Boot the LiveCD, open a terminal window and enter the command```
fdisk -l
```That should tell you if you have really wiped out WIndows or not.

---

### Post by Saint Angeles on 2008-01-02
IFyou've removed vista and you have no disc, you should still have a key or something on the bottom of your laptop right?

you could technically find someone with the CD and use your legal key that you purchased with your friend's disc.

but you might have to reinstall Ubuntu afterwards (carefully this time) because windows has a tendency to erase "foreign" partitions when it feels like it.

---

### Post by squier on 2008-01-02
thanks everyone.  the product key is on the bottom i wasn't thinking about that.  i'm going to give that a try soon.  if i did lose it atleast i didn't have any info saved to it yet.  i guess i'll pay a lil closer attention to what i'm doing next time.  but thanks again for the quick responses

---

### Post by Enginirical on 2008-01-02
Laptops don't come with windows disks but recovery disks. They are the same thing only it includes necessary drivers for your laptop. Normally you need to resize partitions, and windows recovery disks for some laptops wont let you install on a partition but only on the entire hard disk, if thats the case format it with recovery disk, then use gParted to resize the windows partition and carry on from there...

---

