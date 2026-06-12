---
title: "Need help installing Ubuntu 8.04 on new MacBook Pro"
date: 2008-05-27
forum: Apple Hardware Users
---

### Post by oceanfirehawk on 2008-05-27
Hello everyone. I have been trying to install 8.04 on my MacBook pro without success. i went to: [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro) and did not have much success. Do I have to use bootcamp? When I tried it using bootcamp, i could not get my apple to recognize the partition at startup. and is the refit program safe to use?

---

### Post by cyberdork33 on 2008-05-27
> **oceanfirehawk said:**
> Hello everyone. I have been trying to install 8.04 on my MacBook pro without success. i went to: [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro) and did not have much success. Do I have to use bootcamp? When I tried it using bootcamp, i could not get my apple to recognize the partition at startup. and is the refit program safe to use?
There is more than one MacBook Pro page, you need to make sure you are using the right one for your Mac. How old is it? What version is it?

You do not have to use bootcamp. The basics issue is that you need to resize your OSX partition, to create some free space, then install Ubuntu to the free space.

rEFIt is a great tool. It is safe.

---

### Post by ahdar on 2008-05-27
You need to use rEFIt partition tools to sync GPT/MBR. It'll be good to go. If you prefer Boot Camp's "two-disk" look over the "Apple-Penguin-icon" look in rEFIt, you might be able to remove rEFIt after Ubuntu is installed. Linux and/or windows booting should still be working if the "grub" boot loader is functional. Basically rEFIt and Bootcamp are doing the same two things: BIOS emulation and creating hybrid GPT/MBR table.

---

### Post by cyberdork33 on 2008-05-28
> **ahdar said:**
> You need to use rEFIt partition tools to sync GPT/MBR. It'll be good to go. If you prefer Boot Camp's "two-disk" look over the "Apple-Penguin-icon" look in rEFIt, you might be able to remove rEFIt after Ubuntu is installed. Linux and/or windows booting should still be working if the "grub" boot loader is functional. Basically rEFIt and Bootcamp are doing the same two things: BIOS emulation and creating hybrid GPT/MBR table.You can customize the icons for rEFIt... just replace the existing images with whatever you want. I had an Ubuntu logo for my Linux icon for a long time.

Bootcamp and rEFIt are not the same thing. The Bootcamp assistant is just a GUI partitioning tool. The rest of "bootcamp" is a set of windows drivers. The BIOS/MBR emulation is in the Mac's EFI firmware.

rEFIt is just a menu that displays bootable partitions as the Mac's EFI sees. It is a GUI for your EFI. There are a couple of extra tools included with rEFIt such as the partition sync tool, and the EFI shell access. It does not "create" partition tables, they are already there, it just makes sure that they show the same thing in them and it certainly does not emulate a BIOS.

---

### Post by arcelios on 2008-05-28
> **oceanfirehawk said:**
> Hello everyone. I have been trying to install 8.04 on my MacBook pro without success. i went to: [https://wiki.ubuntu.com/MacBookPro](https://wiki.ubuntu.com/MacBookPro) and did not have much success. Do I have to use bootcamp? When I tried it using bootcamp, i could not get my apple to recognize the partition at startup. and is the refit program safe to use?

I have a fair amount of experience with installing Ubuntu on MacBook. Here's a quick guide:

1. Backup your data. You are going to lose it. When you partition, it wipes your harddrive.
2. Insert your mac installation CD #1, and reboot, while holding down the "c" key. (The second your computer starts to start up again, hold down the "C" key, and don't let go.)
3. Once you see the mac installer, go up to the top of the screen, and click on "Applications", and select "Disk Utility".
4. Click on your harddrive on the left size (not Macintosh HD, but the actual harddrive, which in my case is "74.5 GB ST98823AS Media".)
5. Go under the "Partition" tab.
6. Change the "Volume Scheme" to "2 Partitions", and rename the partitions from "Untitled 1" and "Untitled 2" to "Macintosh HD" and "Ubuntu HD". Then, click on the "Partition" button at the bottom right.
7. Once it is done partitioning, install Mac OS X on one of the partitions.
8. Then restart and it will boot to Mac OS X normally. Then, install rEFIt (I use it-it's very good).
9. Now, pop in your Ubuntu CD, and restart. You will see the rEFIt menu. Use the left and right arrow keys to select the picture of the Linux penguin with a CD behind them, and hit enter.
10. It will boot the Ubuntu LiveCD.
11. Now, click on the "Install" icon, and follow the onscreen instructions. Be sure to set your keyboard for US-Macintosh.
12. When it asks you where you want to install Ubuntu, say for it to use to largest area of continuous space, or something like that. Or, you could do it manually, in which case, you'll see a table of partitions. right click on the partition that is very large (half the size of you harddrive), and has little to no used space (you can tell if Mac is installed on it). Then, once it is deleted, create a new partition on the part that says "Free Space", which should be pretty big, now that you've deleted the big partition.
13. Now, just finish the installation, and you've got it!
14. Every time you startup, Mac OS X will be default on rEFIt, so it will boot automatically after twenty seconds if you don't do anything. Just use the arrow keys to select which OS to boot from.

Well, hope this helps!

-Arc

---

