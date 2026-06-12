---
title: "No choosing partion size in Ubuntu Install?"
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by Aiello on 2007-08-23
I am preparing to install Ubuntu along side Windows XP for a duel booting computer. This is a family computer, so I only want to give Ubuntu 13gb or so.
Now, I am using this tutorial for the install: [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
It says there is an option in the Ubuntu installer for it to create a new partion of a specified size. I only get these options in my installer: Guided- use entire disk, Guided- use the largest continues free space, and Manuel.:confused:

Any help? (Basically I want to make a 13gb partion for Ubuntu)
-Thanks!

---

### Post by wolfen69 on 2007-08-23
you want to pick manual.

---

### Post by Aiello on 2007-08-23
Well, I am a little... erm... ify about picking manual. I know absolutely NOTHING when it comes to partioning, or anything hardware related for that matter...
Would it be safe to manually start messing around with the HDD, especially when I am a total newb?

---

### Post by Aesir09 on 2007-08-23
**use wubi, the windows based ubuntu installer, i did it and its awesome, easy to install, so so easy!**

:guitar:

---

### Post by klytu on 2007-08-23
> **Aiello said:**
> I am preparing to install Ubuntu along side Windows XP for a duel booting computer. This is a family computer, so I only want to give Ubuntu 13gb or so.
Now, I am using this tutorial for the install: [http://www.psychocats.net/ubuntu/installing]("http://www.psychocats.net/ubuntu/installing")
It says there is an option in the Ubuntu installer for it to create a new partion of a specified size. I only get these options in my installer: Guided- use entire disk, Guided- use the largest continues free space, and Manuel.:confused:

Any help? (Basically I want to make a 13gb partion for Ubuntu)
-Thanks!

If all of your drive is currently partitioned, you want to use the manual option in order to resize your existing Windows partition to free up at least 13GB of space in which to install Ubuntu. If you haven't partitioned a hard disk before and are unsure of what to do, you might want to consider installing Ubuntu on a totally separate hard drive rather than alongside Windows on the same drive.  Whenever you resize an existing partition there is some risk that if something goes wrong you will lose all your data on the drive, so make sure you have important stuff backed up first. On the bright side, I have done this MANY times and have been lucky in that I haven't yet lost any data.

EDIT: I noticed your last response stating that you know nothing about partitioning. On second thought I think you should choose the guided partitioning method and let the Ubuntu installer walk you through it if you want to install Ubuntu on the same hard drive as Windows. This should work OK for you, but even better would be to just install Ubuntu on a separate spare hard dirve.

---

### Post by Aiello on 2007-08-23
Well, I don't have another HDD laying around and I really don't have the money to go out in buy one...
I would really hate for me not to be able to use Ubuntu fully just because of the partioning thing.:( Oh, well. I guess I will due some more research tomorrow. 
If any one can give me a run down on how to manually partion, it would be much appreciated. 
-Thanks!

---

### Post by Aiello on 2007-08-24
Well, for some reason or another, I am getting the option for Ubuntu to automatically resize and create a new partition. I just have one quick question:
The option for the automatic resize is called Guided- resize SCSI1 (0,0,0), partition #2 (sda) and use freed space. I then have bar that is labeled New Partition Size. Will the size I select on the bar be the size of the Windows partition, or of the Ubuntu partition?

-Thanks!

---

### Post by Aiello on 2007-08-24
Any help? Penny for your thoughts?

---

### Post by eapache on 2007-08-24
That will be the ubuntu partition size.

---

### Post by Aiello on 2007-08-24
Thanks. But... the smallest partition I can create is a bit over 40gb. I only want a partition of about 13gb. Does this mean I will have to go manual any ways?:confused:

---

### Post by eapache on 2007-08-24
Please select manual and then take a screenshot, and I will write a step-by-step for you.

---

### Post by dptxp on 2007-08-24
The partitioning and formatting do not start till a couple of steps after you select your partitions, so it is safe to manually configure and proceed only if all looks fine and safe.

Choose manual partition. If you have see only one partition, do not proceed without defragmenting in Windows first.
Next select the partition and resize to original size minus 13 GB you want to give to Ubuntu. Resize
from start and make sure later that FORMAT is disabled.

You can do it to any partition if it got 13 GB free.
Now you got 13 GB unused space.
Resize it to 6 GB, mount as /, ext3 format.
Resize rest 7 GB to 6 GB, mount as /home, ext3 format or FAT32 format.
Set last 1 GB as SWAP.

You can have total 4 Primary partitions maxm, rest can be logical.

Try to understand first, you will feel more at ease.

---

### Post by Aiello on 2007-08-24
> **eapache said:**
> Please select manual and then take a screenshot, and I will write a step-by-step for you.
file:///home/ubuntu/Desktop/Screenshot.png
Here is the screen shot. I hope it uploaded okay.

EDIT: Okay, it didn't. How can I upload it. I don't see an option for file upload.

---

### Post by eapache on 2007-08-24
Please attach it through the "Manage Attachments" under "Additional Options".

I'm afraid I have to leave now, but I will revisit this thread when I log back on and continue to help. Please be patient.

---

### Post by Aiello on 2007-08-24
There we go.

---

### Post by eapache on 2007-08-24
OK, this is what you have to do.

1. Run the Windows defragment utility several times to clean up your partition and make it easier for the installer.

2. Shrink the ntfs partition by right-clicking and selecting re-size. Remove 13Gb (or however much you want to give ubuntu).

3. Create the ubuntu swap partition by right-clicking on the free space, and selecting new partition. Give this partition only 2x your ram amount (1000Mb should be fine if you don't know your ram amount). Put it at the beginning of the free space, and make it of type linux-swap.

4. Now create another partition using all of the remaining free space. Make it ext3, and set the mount point to /.

Your table should now look something like this:
Device------Type-----Mount Point---------Size
/dev/sda1---fat32-----/media/sda1---------41 MB
/dev/sda2---ntfs------/media/sda2-----66000 MB
/dev/sda3---swap----none---------------1000 MB
/dev/sda4---ext3-----/--------------------13000 MB

---

### Post by Aiello on 2007-08-24
Thanks for the info. I will try this out tomorrow. 
I have 2 quick questions though:
1. My RAM is 1.5GB. Should I give the Ubuntu swap partition 3GB?
2. Will I still be able to save data in Windows?

-Thanks again!

---

### Post by eapache on 2007-08-25
Give the Ubuntu swap just 1.5 GB. As a 32bit OS, it can't use more than 3GB or so of combined ram & swap anyways.

Yes you will be able to read and write to your windows C: from ubuntu. There is some software you need to install to enable it, but it is all graphical and quite simple.

I have also edited my previous post to make it a little simpler.

---

