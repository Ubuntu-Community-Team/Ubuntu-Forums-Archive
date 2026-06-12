---
title: "How to create an Ubuntu boot drive, then partition an external HDD, and activate wifi"
date: 2015-08-23
forum: Apple Hardware Users
---

### Post by isa.k on 2015-08-23
I just downloaded the latest Ubuntu Desktop edition 14.04.3, and tried taking it for a spin before installing it.

Actually I am not looking to install a fully working edition of Ubuntu on anything other than a boot drive, if possible. I already downloaded the iso, and ran it on my MBP.

I am trying to shift data from my non-booting MacBook Pro, to an external drive. The MBP has OS X installed, and Win 7 on Boot Camp. All external drives I have that I can potentially use for creating a boot disk/usb are containing data themselves, and need to be consolidated... straight after my bout of procrastination ends.

In the meantime as I mentioned above, I need to create a boot disk/usb that will allow me to perform the simple (oh God I hope it is simple!) function of moving data from the internal drive of my MBP, to the external HDD.

The HDD is 2TB, plugged into a USB 3.0 dock, partitioned into two segments. One NTFS at 1.4 TB, and one OS X Journaled at 600 GB. The NTFS contains data that I would like to keep there. The Mac OS X can be done with as you see fit, as long as I can get the data off of the MBP internal drive, from both partitions there.

Finally, I would like to learn how to activate wifi via Ubuntu.

I pray that I was able to clearly explain what I needed. If not, please ask for further clarification, and I will be much obliged to clarify in any way I can.

**_[SIZE=5][FONT=Arial Black][COLOR="#FF0000"]TLDR;[/COLOR][/FONT][/SIZE]_**
I have a MacBook Pro that has an **internal HDD** sporting a Mac OS X (350 GB) partition and an NTFS Boot Camp (150 GB) partition.

I also have an **external HDD** that is partitioned into NTFS (1.4 TB) and Mac OS X Journaled (**600 GB**)

**I need to transfer the data off of both internal partitions to the external HDD's 600 GB partition.**

How do I create a boot disk that allows me to transfer files across devices... as the Ubuntu disc I am using currently (v.14.04.3 Desktop) is prohibiting me from doing that. I am guessing it requires me to fully install it at first? If possible I do not want to do that... or at worst, how would I install it on the 600 GB partition of the external HDD? . . . and if I did that, would I be able to then transfer files from one device to another?

Thanking you all in advance.

~&#304;sa

---

### Post by howefield on 2015-08-23
Thread moved to the "*Apple Hardware Users*" forum.

---

### Post by crystalocean on 2015-09-01
Hi isa.k,

Let's start with your second question because I think it will help with solving your first question.

> Finally, I would like to learn how to activate wifi via Ubuntu.

Assuming you are able to get Ubuntu running live from a USB, open up the file manager and navigate to two different locations:

First, navigate to **/media/cdrom/pool/main/b/b43-fwcutter** and install what is located there.

Second, navigate to **/media/cdrom/pool/main/d/dkms** and install what is located there, too.

Now, try connecting to the internet again and please report back on whether or not you are successful.

> The HDD is 2TB, plugged into a USB 3.0 dock, partitioned into two  segments. One NTFS at 1.4 TB, and one OS X Journaled at 600 GB. The NTFS  contains data that I would like to keep there. The Mac OS X can be done  with as you see fit, as long as I can get the data off of the MBP  internal drive, from both partitions there.

I believe this can, in fact, be done.

Open up the terminal and run:

```
sudo apt-get install hfsprogs
```

Then try clicking on the MBP internal drive icon on the desktop to mount it--you should be successful now. 

After this, I believe you should now be able read/write from/to the internal MBP drive, at least running as super user.

I have been successful myself doing what you are trying to do so please report back on any problems you encounter and I'll try to figure out where I went wrong in my explanation.

I hope some or all of this helps you (or others) and good luck!

---

