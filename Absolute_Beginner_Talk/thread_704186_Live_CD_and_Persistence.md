---
title: "Live CD and Persistence"
date: 2008-02-22
forum: Absolute Beginner Talk
---

### Post by darren-m on 2008-02-22
I have downloaded the latest version of the live CD 7.1 (Gutsy) and was impressed with its look and feel. Internet access worked without any hickups.
Whilst trying out the OS I came across the idea of Persistence with the Live CD.
I follwed the instructions contained here,([https://help.ubuntu.com/community/LiveCDPersistence?highlight=%28persistence%29](https://help.ubuntu.com/community/LiveCDPersistence?highlight=%28persistence%29)) whilst most of it worked , whiping the content of the USB device, formatting it and making it accessible etc The important part of it did not.  No matter what I tried, I could not get any information saved automatically as indicated in the info above.
 I can manually add data to the USB stick no problem but getting persistence to work just didnt seem to happen. Is their something I am missing?
To recap
Determine Which Device Your USB Stick Is     Done (/dev/sdb1)
Partitioning Your USB Stick                              Done
Creating the "casper-rw" File System             Done
Booting the Live CD in Persistent Mode          Done   (added persistent to boot option F6)
Made some changes to the interface background Done
Reboot the Live CD                                         Done   (added persistent to boot option F6)
PC boots up with standard interface ignoring persistent option.

---

### Post by laidback on 2008-02-22
Is this something to do with the Boot sequence set up in your BIOS? Currently your hdd will probably have the 1st priority, USB (if allowed) will be further down the list. 
Either select BOOT options at power up amd then choose USB, or alter in BIOS. Former is better in my view.

---

### Post by darren-m on 2008-02-22
The boot sequence for my PC is CDR and then Hard disk.
If I alter the boot sequence it will bypass the CD rom. 
The problem seems to be, that the persistent option is not working at boot up.i.e it is being ignored.
Am I missing something..I add "persistent" to the end of the boot string. Thanks any way.

---

### Post by laidback on 2008-02-22
Looking through my notes on this I see that Vfat and NTFS formats don't work. Is your USB stick formatted to something else? e.g. ext3

---

### Post by laidback on 2008-02-22
When the live cd menu gets displayed hit <F6> key to enter Other Options. This will display the arguments that the Live CD passes to the kernel. At the end of this list just add a space and the word "persistent". This is meant to instruct the Live CD to maintain and use persistence. That's meant to be all there is to it.

---

### Post by darren-m on 2008-02-22
My usb stick is formatted as ext3. Ok will trythat " persistent" , I only added persistent with no space doh....
Thanks for the help.

---

### Post by laidback on 2008-02-22
I hope it's just the space issue that's missing...really annoying if it is...but still you will get there in the end.

Good luck...post the outcome please.

---

### Post by hrsa on 2008-02-23
I had the same problem and adding a space before "persistent" didn't help :(

---

### Post by laidback on 2008-02-23
For creating the USB file system I have the following note:-

$ sudo mkfs.ext3 -b 4096 -L casper-rw /dev/sda1

replace /dev/sda1 with your own device name. 

Does this help?

---

### Post by hrsa on 2008-02-23
Unfortunately, no. I did the same when i was installing ubuntu on my usb drive... What's more, i can't neither see nor mount the ext2 partition in Ubuntu or Windows

---

### Post by wolfen69 on 2008-02-23
following these [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/) instructions worked great for me. you will need a 2gig drive for it to work good.

---

### Post by hrsa on 2008-02-23
I used the same instructions. Is yours persistent? Can you browse both of the partitions on your usb drive?

---

### Post by laidback on 2008-02-24
Have you used ext2 or ext3, I used ext3, maybe ext2 has a problem.
It's about a year ago that I had a go at this, I used the guide in the book Ubuntu Hacks as my source. However there was a change needed as it refers to casper-cow rather than casper-rw. I believe that casper-cow was dropped in favour of just casper some while ago.
I did get it working though my notes indicate but I dropped it quite quickly in favour of a full install.
There are also some notes somewhere on the web, search for "LiveCDPersistence". I did it with 6.06LTS, maybe v7 has altered things.

Sorry I haven't any more ideas at present.

---

