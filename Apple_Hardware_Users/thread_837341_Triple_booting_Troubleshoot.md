---
title: "Triple booting Troubleshoot"
date: 2008-06-22
forum: Apple Hardware Users
---

### Post by keylimepie82 on 2008-06-22
Hi,

I've been following the guide below to set up a triple boot on my macbook (not pro)

[https://help.ubuntu.com/community/MacBookPro](https://help.ubuntu.com/community/MacBookPro)

Yeah, I know it says macbookpro, but I couldn't find anything that's for OSX, Hardy Heron, and XP triple boot.

So I went through most of the steps under "Preparing to Install Ubutu alongside OS X & Windows XP (Triple Boot)" without a problem.  But at step 7, it says "After windows is installed, insert your Leopard DVD and it should install all your Apple drivers and stuff."

Yeah, that doesn't seem to happen.  In fact, most of the devices don't seem to be working properly in windows.  (For instance, my wireless...)

I coudn't do the rest of the steps there, so I decided to do them later when I can connect by ethernet.

Then, I started the Linux installation.

I started Disk Utility and tried to create a linux partition on Macintosh HD.  I chose 8 Gb for the new partition and named it "Ubuntu"

It was running for the past 6 hours, stuck on "modifying partition map."  I called the Apple Tech Support and they told me to Force quit the Disk Utility, shut off for a min, then reboot.  

Then, they said I should delete this new partition, reformat, etc.  I opened the disk util again, but no partition was created.

So here is my question:

1. How do I get the devices working properly in the windows side?  (How do I install the Apple drivers?  Inserting the disk didn't seem to do the job...)
2. The guide tells me to disk utility to create a linux partition, but that didn't work the first time.  Do I try again, or should I do something else?
3. Is it possible that my hard drive is f---ed up because of what I described above?

---

### Post by tiagobt on 2008-06-22
> **keylimepie82 said:**
> 1. How do I get the devices working properly in the windows side?  (How do I install the Apple drivers?  Inserting the disk didn't seem to do the job...)

Are you sure you're using the Leopard DVD? I believe older versions don't include the Windows drivers. Using the DVD should work, but if it doesn't, you still have an option. Boot Mac OS and run the Boot Camp utility. It will burn a driver CD for Windows XP or Vista. Stop the utility before it tries to partition your disk.

> **keylimepie82 said:**
> 2. The guide tells me to disk utility to create a linux partition, but that didn't work the first time.  Do I try again, or should I do something else?

Personally, I think Disk Utility is a good partitioning tool. It's easy to use and can handle both MBR and EFI. Considering Disk Utility is behaving weird, you could backup your files, format the entire disk, and then recreate all the partitions you want. To format the disk, go to the Erase tab, choose the entire volume (not one of the partitions) and click on Erase. By the way, what partitioning table are you planning to use?

> **keylimepie82 said:**
> 3. Is it possible that my hard drive is f---ed up because of what I described above?

I don't think so.

---

