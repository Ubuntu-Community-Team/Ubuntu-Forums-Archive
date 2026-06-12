---
title: "Installing on an external hard drive?"
date: 2007-09-06
forum: Absolute Beginner Talk
---

### Post by Hope for Chaos on 2007-09-06
So I've been messing with Ubuntu off the live cd for a week or so and I think I'm ready to install it.  My first plan was to add a second internal hard drive and install it on that since I didn't wana partition my vista drive or lose any of that space.  After looking into that it was a lot more work since dell discourages the second hard drive....its kind of a pain to get the parts for it.  So now I'm looking at partitioning my 160gb My Book and running it off that but really don't know where to begin and if its even possible.  I was just curious if the process was similar to installing it on an internal drive and if the performance would suffer too much.  Thanks for any help.

---

### Post by eph1973 on 2007-09-06
I run Ubuntu off my external HD on my laptop, and I feel it runs fine.  I didn't have any problems at all with Ubuntu seeing it (I use a Seagate Free Agent Desktop 500GB external USB HD).

---

### Post by Hope for Chaos on 2007-09-07
That's good to know it works and it works well.  Do I just go about installing it the same way?  I've heard it can be hard to distinguish between the internal and external drives.  Also how does partitioning work?  Does it do it during the install or will i need to do that before?  Thanks for any help.

---

### Post by eph1973 on 2007-09-07
For me, it worked just fine just using the normal install program, I didn't have to do anything extra over what you would do for a normal internal HD.  You can even boot from the external drive after you have installed (i.e. if you have Windows on your internal drive, you can boot onto the Linux installed on your external USB drive without having to do anything with your internal drive, assuming your BIOS allows such things).  

This is what I did was during the install: 
I used the install program to partition, using the manual partition option.  My existing HD was recognized as hda1 with a ntfs file system.  My external drive was recognized as sda1.  I manually configured my partitions using the install program so I had a swap partition (I used a 3GB swap, which is probably bigger than it really needs to be, but it's a 500GB HD, so I figured in case I ever moved my HD to a machine with more memory than my laptop currently has, I would still have a sufficiently sized swap partition), an ext3 partition, that I mounted at / which is where I installed Linux, and a FAT32 partition mounted at /windows so that if I wanted to, I could place files there both with Linux and with Windows, giving me the ability to easier swap files between Windows and Linux.  Some people also recommend a small partition mounted at /home (ext3, most likely), but that's up to you, it's not necessary.  The only partition that you NEED is the one mounted at / and it's highly recommended that you make a swap partition with a suggested size of 1.5 to 2 times the amount of the memory you have.

Just make sure that after everything is configured, if you want to keep Windows for a dual boot setup, then the existing partition(s) with your ntfs file system(s) (hda1, hda2, or whatever the install program recognizes them as), are NOT listed on the list of partitions that the install program is going to make to install Linux on the last screen before it actually begins the install (that is the last screen where you can still go back and change whatever to your liking).

It really is a piece of cake, and pretty intuitive.  Good Luck.

---

### Post by Jon Walker on 2007-09-16
If I have the feisty fawn iso on a cd, can I use the cd to install onto my external HD or do I need to download the ISO and put it on my external HD. I want to boot and run linux from the external HD like you are.

---

### Post by eph1973 on 2007-09-16
You can install it from the CD, you might also want to take a look at [http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu](http://apcmag.com/6101/dualboot_windows_xp_and_ubuntu)
It has a walkthrough to install if you want to dual boot.

---

### Post by Jon Walker on 2007-09-16
Thanks I am doing it right now :)

---

### Post by Jon Walker on 2007-09-16
It is installing to the harddrive as I type this. Hopefully it works... Is there anything special I need to do to make it work with a power pc Ibook?

---

### Post by eph1973 on 2007-09-16
Not sure, you might want to try to Google.  However, I would recommend that you just wait to see how it works out before you start asking questions, because it is easier to figure out what is going on than what might happen.

---

### Post by Jon Walker on 2007-09-16
I don't think it worked right. I know the linux files are all installed on my HD but I haven't tried booting from the USB yet. 

I did somehow manage to kill my desktop that was already running ubuntu. It will no longer boot at all. I guess I have to reinstall ubuntu to fix it. I suck at this technical stuff.:confused:

Thanks again for all the help.

---

### Post by eph1973 on 2007-09-16
What do you mean you killed the desktop that was running Ubuntu?  And have you tried booting from your external drive yet?  This page may be helpful to you:
[https://wiki.ubuntu.com/PowerPCFAQ](https://wiki.ubuntu.com/PowerPCFAQ)
I don't know if there is anything that you will be able to use there, but there's a bit about yaboot.  Also, I made the mistake of assuming you were running some sort of IBM PC type machine, vice an Apple.  There is a different way to go about installing it on an apple, so you might want to make sure you pay close attention to those differences (i.e. if you are reading a web page about it, make sure it is addressing and iBook, and not some sort of Windows based machine).  I'm afraid I don't have any experience with apple computers (well since the apple IIe, and that's not going to help anyone).  Good luck.

---

### Post by Jon Walker on 2007-09-16
I have ubuntu working again on my desktop. I was using my desktop to run the live cd to install ubuntu onto my external HD, something went wrong and messed up my ubuntu desktops OS and it wouldn't boot. I fixed it by doing a new ubuntu reinstall. I have yet to test to see if the hard drive will boot from USB because my laptop that is an apple is not nearby. I am going to test it more tomorrow after I get some sleep.

At this point in time I am just happy nothing cuaght on fire or blew up :)

---

### Post by eph1973 on 2007-09-16
Ahh, I think I understand what you are doing now.  You are going to want to check your bios on your ibook to make sure it can A) boot from a USB device, and B) check your CD-ROM, your USB, THEN your internal HD, or you will find that you won't be able to boot up Linux.  Hope it works out for you, good luck.

---

