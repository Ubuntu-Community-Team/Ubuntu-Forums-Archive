---
title: "boot help and mounting issues"
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by tommyrock on 2008-01-14
Running newest Gubuntu on IBM ThinkPad T41.

I'm completely new to Linux as of this weekend and have been having a bunch of problems, but I really want to keep on with it. To begin with, I can only boot from the CD, and even then it just re-installs. If I select "Boot from Disk" or without the disk in the drive, all I get is a screen full of "99 99 99 99 99..." and it doesn't do anything. I'm not sure how to stop this.

As far as mounting, I feel like there's something I don't understand. If I plug in my 3rd gen iPod Nano to the USB port my iPod recognizes for a second it's connected and then disconnects, with my computer showing no recognition. I can't search for it and nothing changes. I also cannot eject the disk out of the CD-ROM, but I'm assuming this is related to the first part as my laptop is running off of the CD.

Any help is majorlymajorlymajorly appreciated -- I've never felt so clueless before!

---

### Post by Cypher on 2008-01-14
How old is the laptop? Does the installation complete fully or are there any errors? Does the GRUB menu show up if you boot the laptop without the CD?

While booted into the CD, it's unwise to eject the CD, but I'm sure you can force it if you really wanted to..

As far as the iPod goes, while booted into the LiveCD, go to Applications->Accessories->Terminal and then type "dmesg | tail -n 25" this will print the last 25 lines. Now plug the iPod in and redo "dmesg | tail -n25" and you should see new messages about the iPod, get us what it says and we can help you further..

---

