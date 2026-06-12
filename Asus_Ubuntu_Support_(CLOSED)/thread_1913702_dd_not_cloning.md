---
title: "dd not cloning"
date: 2012-01-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by penguinslide on 2012-01-23
Hi, I am having problems doing a dd clone, this is the first time I have ever had problems with dd, other than being slower than your average clone method, it has never let me down until now.

I have a Asus K52F laptop, running Mint 11, was running Ubuntu until unity, (Mint being based on Ubuntu and using ubuntu 10.4 livecd for dd process, I thought it was acceptable to post here, ubuntu forum is second to none)

Anyway, here's the story: I  filled my 300gb hdd, thought no problem, do a dd to a new 500gb hdd. Didn't boot, so formatted and tried again, came up with a error message, saying one kb not copied, checked the disk, it had got too hot (in the dock while cloning I'm guessing) and had a bad cluster, serves me right for being a tight a$$ and getting a chinese ebay elcheapo I thought to myself.

 So I bought new 500gb hdd, dd again with fan on it, no boot, tried a boot grub fix, it told me it didn't recognise it had an os, looks fine through livecd. So I thought I'd try to install ubuntu 10.4 with it to see if that will give me an option to boot it, it recognised it in install, but on boot went straight to ubuntu. So I wiped, thought maybe dd 300gb to a 500gb maybe causing issues, so I put a 300gb partition on 500gb and did if=/dev/sda1 of=/dev/sdb1 instead of if=/dev/sda of=/dev/sdb, 1kb not copied and will not boot again, won't even mount. So I yield!! WTF am I doing wrong Linux gurus?

---

### Post by carl4926 on 2012-01-23
```
dd if=/dev/sda1 of=/dev/sdb1 bs=4096 conv=noerror
```

Have you tried clonezilla?

---

### Post by penguinslide on 2012-01-23
> **carl4926 said:**
> ```
dd if=/dev/sda1 of=/dev/sdb1 bs=4096 conv=noerror
```Have you tried clonezilla?

Hi, thanks for quick reply, yeah that is the code I gave without a blocksize and whatever conv stands for ( tried stating blocksize in the early days and wouldn't accept the command, perhaps I added a space) will try again using that.

Tried clonezilla and get totally lost with it, probably highlights the things I'm yet to learn about linux

Ok, thank you, will try your code now and let you know.

---

### Post by penguinslide on 2012-01-23
Thanks, DD process running with very solid activity light! how long does it take with that block size?

---

### Post by Grenage on 2012-01-23
That depends on the controller and interface speed.  I usually mirror the whole drive, rather than just a partition - it depends what you're doing.  In this instance, I'd use the same command as carl4926, but I wouldn't refer to partitions.

---

### Post by carl4926 on 2012-01-23
> I wouldn't refer to partitions.
Correct if you want to clone the entire HD

---

### Post by penguinslide on 2012-01-23
> **Grenage said:**
> That depends on the controller and interface speed.  I usually mirror the whole drive, rather than just a partition - it depends what you're doing.  In this instance, I'd use the same command as carl4926, but I wouldn't refer to partitions.


So depends on cpu speed and perhaps ram?   In my case: Intel®  Core&#8482; i3   Processor  370M  :  2.40  GHz 8g ram

Yeah I usually do whole drive, but thought doing just the partition a safer and faster option then resize partition later to make full use of hdd

Just for info sake, what does conv=noerror do?

Gotta go to bed, will let you know what happened in 7 hrs time

---

### Post by Grenage on 2012-01-23
> **penguinslide said:**
> So depends on cpu speed and perhaps ram?   In my case: Intel®  Core&#8482; i3   Processor  370M  :  2.40  GHz 8g ram

Well if both are relatively modern SATA drives, I wouldn't expect it to take too long.  Less than an hour, perhaps - allow for a few.

> **penguinslide said:**
> Just for info sake, what does conv=noerror do?

That parameter means that dd won't stop copying if it encounters an error, it simply fills in the missing bits with zero values.  I *think* it fills in the remainder of the block, so if you are copying 4MB blocks, you can miss out on a lot of data.  That's assuming there are errors, of course.

Edit: null data padding requires the additional parameter "sync".

---

### Post by penguinslide on 2012-01-23
Unfortunately hasn't cloned this morning, won't boot, in my haste I didn't check to see if the terminal had an error message, will try again without partition reference and let you know when I get home from work

---

### Post by sudodus on 2012-01-23
My experience is that dd works, if your two drives have no bad sectors. With bad sectors, dd is no good, use ***ddrescue*** instead. It can be installed with ```
sudo apt-get install ddrescue
``` (or use the ubuntu-rescue-remix). The info page
```
info ddrescue
``` about ddrescue is very well written, so read it (all of it) before starting the job. It saves a lot of trouble.

Always run from another drive, preferably a live CD or USB drive.

---

### Post by penguinslide on 2012-01-24
I'm back from work, rebooted and it works!! I have no idea why the previous dd didn't work, used the same command in terminal as last night, that's all I have time to say right now, just wanted to let you know asap thanks very much for your help, will come back later and try to work out how to mark this as solved

---

### Post by carl4926 on 2012-01-24
Great news
Well done

---

### Post by sudodus on 2012-01-24
Congratulations :KS

Click on **[COLOR="Red"]Thread Tools[/COLOR]** at the top of the page and you get a drop-down menu where you select to mark this thread as SOLVED

---

### Post by penguinslide on 2012-01-24
> **sudodus said:**
> My experience is that dd works, if your two drives have no bad sectors. With bad sectors, dd is no good, use ***ddrescue*** instead. It can be installed with ```
sudo apt-get install ddrescue
``` (or use the ubuntu-rescue-remix). The info page
```
info ddrescue
``` about ddrescue is very well written, so read it (all of it) before starting the job. It saves a lot of trouble.

Always run from another drive, preferably a live CD or USB drive.


Thanks Sudodus, forgot about ddrescue, been a very long time since I researched dd and ddrescue, will try ddrescue on the toasted hdd with the bad sector and see what happens.

---

### Post by learnbash on 2012-02-20
> **penguinslide said:**
> I'm back from work, rebooted and it works!! I have no idea why the previous dd didn't work, used the same command in terminal as last night, that's all I have time to say right now, just wanted to let you know asap thanks very much for your help, will come back later and try to work out how to mark this as solved

I have two hard-drive

one is 400GB
second is 200GB

i want to clone 400GB to another 400GB and same to with 200GB. Please share with me what command you use.

---

### Post by Grenage on 2012-02-20
> **learnbash said:**
> I have two hard-drive

one is 400GB
second is 200GB

i want to clone 400GB to another 400GB and same to with 200GB. Please share with me what command you use.

While this should really have its own thread, it's a quick answer.  After identifying the drives you wish to copy (and you have to be sure), use this command, where sda is the source and sdb is the destination.

```
sudo dd if=/dev/sda of=/dev/sdb bs=4096 conv=noerror
```

---

