---
title: "Moving files during partitioning"
date: 2007-05-02
forum: Absolute Beginner Talk
---

### Post by jbwick on 2007-05-02
I want to do a dual install of Windows XP and Ubuntu. I've defragged my Windows drive, but I have some files that are separated from the rest of the files, toward the end of the Windows drive. I have a huge gap (probably several gigs) between the end of the main part of my Windows files and these "lost sheep."

My question is, when I partition the hard drive, will those "lost sheep" files be moved closer in on the Windows partition, or will they be lost? 

TIA.
Jerry

---

### Post by jkblacker on 2007-05-02
I had much the same issue, and although I've only booted into xp once (very briefly) since installing, it doesn't in my case seem to have had a disastrous effect. I have heard the advice 'turn off hibernation, turn off page files, turn off anti-virus/anti-spyware etc and then defrag', if you want to be more sure about not losing anything.

In my case, I seem to have been fine. But I stress - in *my* case

---

### Post by jbwick on 2007-05-02
Thanks for the quick response. I understand the computer acronym, YMMV - your mileage may vary. I will go back and shut off my virus software - that may be the files that could not be moved on my hard drive.

---

### Post by jbwick on 2007-05-03
Just thought I'd share my experience with my install. I started by burning a CD of Kubutnu Live of Feisty Fawn and running it. On my Dell Inspiron 1501, the video ran perfectly, as did everything except my wireless card. In the past, I've had problems with the video because the  drivers in Linux tended to be a bit out of date. So I was already impressed.

After my original post here, I downloaded and burned System Rescue CD (available from [http://www.sysresccd.org]("http://www.sysresccd.org")). I used the partition utility there to remove the 'ghost files' from one of the partitions, which I left as a FAT32 partition. 

I reduced the size of the main Windows partition, and it moved files to create the space. As soon as I had finished repartitioning the Windows drive, I rebooted into Windows. The program CHKDSK popped up, saying the file structure was 'dirty.' I let it run, then it booted into Windows, where everything was present and accounted for.

Then I rebooted into the Kubuntu CD and ran the Install. It worked fine, including GRUB for the boot loader. Then I followed the notes at [http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html]("http://ubuntu1501.blogspot.com/2007/01/fixing-wifi-on-dell-1501.html")
to blacklist the generic driver in Linux for my wifi, download a new copy of ndiswrapper and the Windows driver from Dell, and install it. 

Within just a few hours, I entered the world of Kubuntu Linux. I've installed Windows from scratch. This process wasn't bad at all. It was just a matter of following in the footsteps of a lot of people who have come before.

---

