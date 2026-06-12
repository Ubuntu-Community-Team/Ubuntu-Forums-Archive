---
title: "Problem with partitions"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by secallen on 2006-07-19
Hi, 

I'm new to Ubunutu so please accept my apologies if this problem is really obvious.

I intalled Dapper Drake as a dual boot with XP on the C partition of my drive. In the Ubunutu installer I created an ext3 partition for Ubuntu, a swap partition of about 512 MB and a FAT32 partition for what I hoped would be shared files. When I booted into XP I could see the shared folder but it told me it was not formatted. Foolishly I chose to format it there and now when I click on it in Ubuntu it says that it cannot be "mounted". Do I have to start again? 

Also, if it is possible to have a shared drive for files, should I designate it as /home when installing Ubunutu? Can I do this retrospectively if my system is OK?

Thank you.:KS

---

### Post by Crosbie on 2006-07-19
It's certainly possible to have a shared drive.  Ubuntu sees my Windows data partitions (Fat32) and reads/writes to them fine.  You'll need more competent advice as to how to get there from where you are: I designated mine on install (being very careful to tell Ubuntu *not *to format them.)

I also chose to keep my /home partition from a previous Mandrake install, telling Ubuntu not to format.  This caused me permissions problems at first, but I managed to work around that.

---

### Post by secallen on 2006-07-19
Yes, my ubuntu install reads and writes to the (Fat32) XP partition fine. Do you think I should set up two Fat32 partitions in XP and leave enough undefined disk space for ubuntu to make its system and swap partitions?

---

### Post by Crosbie on 2006-07-19
> **secallen said:**
> Yes, my ubuntu install reads and writes to the (Fat32) XP partition fine. Do you think I should set up two Fat32 partitions in XP and leave enough undefined disk space for ubuntu to make its system and swap partitions?

That sounds sensible to me.  Ubuntu is designed to play nicely with Windows XP.  Windows XP is designed to exclude and trample over all competition. ;)

Re the /home partition: You don't have to designate a data partition as /home.  I'm not sure I'd want Windows to see my Linux /home, where I store settings for my system.  (See sarky comment above.)  But I may just be being paranoid about this.

---

### Post by secallen on 2006-07-19
Thanks for you help, I'll give it a try.
Fergus

---

### Post by OU812 on 2006-07-20
I'm worried - you said you formatted the partition using winxp. Winxp can only format in ntfs - except for partitions of up to 32 gigs (I think). You'd be better off - if this is the case - formatting the partition from within linux. If ubuntu works the same as slackware try launching cfdisk from a terminal

sudo cfdisk

john

---

