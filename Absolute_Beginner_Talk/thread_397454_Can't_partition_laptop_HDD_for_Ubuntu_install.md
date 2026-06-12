---
title: "Can't partition laptop HDD for Ubuntu install"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by PaulFXH on 2007-03-30
I already posted on this problem in General Help but the thread seems to have run out of steam without resolving the problem.
So, this is an updated version of my problem.
Having finally convinced my wife to try Ubuntu on her laptop (HP pavilion dv 1000), I'm afraid I fell at the first hurdle when GParted came up with "no devices detected" when I tried to set up the partitions on which to install Ubuntu.
Note that I tried both GParted 0.3.4.5 and GParted 0.3.1 with the same negative result.
In googling around I find that this is not an unknown problem and may be attributable to an as yet unresolved bug. However, no relevant solution seems to be available.
OK, so what alternative partitioning tools, that may have a better chance of actually detecting the HDDs, can be suggested that work as well and (normally) as reliably as GParted?

---

### Post by annda on 2007-03-30
i'd say try the gparted live cd first:
[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

or knoppix (it's renowned for excellent hardware detection)
[http://www.knoppix.net/](http://www.knoppix.net/)

or get any other linux distro like mandriva or fedora, boot into install and reboot after partitioning and saving changes to the partition table, but before installing any actual packages. i did that x times with redhat and mandrake to fix my dual-boot configuration and it saved my disk every time.

---

### Post by PaulFXH on 2007-03-30
Actually, each time I tried GParted was with the Live CD (two versions).
But I have heard good reports of Knoppix Live CD being able to detect hardware that is missed by others whch you seem to be confirming.
So, I've marked this on my agenda for tomorrow.
I'll post back with how I got on.

---

### Post by PaulFXH on 2007-03-31
OK, here's what happened:
I downloaded the Knoppix live CD but when I ran this, I could not find any sign of a partitioning tool nor any means to install Knoppix on my HDD. Indeed, in googling around I see that installing Knoppix on the HDD is actually discouraged.
Then I saw that the install iso for both Fedora and Mandriva consists of very large files (up to 6 CDs) that would cause difficulties with the slow (550 kbps) and somewhat unstable broadband where I am right now.
So, I decided to try the Ubuntu Live CD, and guess what, the partitioning and the install went perfectly.
Now, given that the Ubuntu Live CD uses GParted which is what I tried in a Live CD version, I am very puzzled as to why it worked in one case and not in the other.
So, now my wife has an Ubuntu/XP dual boot system on her laptop and is happy.
Unfortunately, I don't have a logical/scientific explanation for what happened in this case but I can say that, once again, it has been shown that persistence pays off.

---

### Post by jvc26 on 2007-03-31
Bizarre! Well its excellent it worked out for you!
Il

---

