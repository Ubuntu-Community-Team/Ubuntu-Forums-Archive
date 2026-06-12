---
title: "Ubuntu 7.10 server can't see RAID 0"
date: 2007-11-02
forum: Absolute Beginner Talk
---

### Post by Dalman on 2007-11-02
My first foray into Linux... I have an IDE RAID 0 (2 hdd) setup with Windows XP already installed on the hdd. I have used Partition Magic 8 to setup a linux partition and swap disk partition on the drive. I then re-booted. I have inserted my Ubuntu 7.10 server "Alternate" disk and it loads up to the installation screen. I then go through all of the motions until I get to Detect Disk part... It can't see any disks so I can't go any further. I have read some threads regarding "fake raid" but for the life of me I can't figure out how to get access to that option?!? 

Any suggestions... (screenshots would be GREAT).. 

thanks everyone.

---

### Post by Jorn.jambers on 2007-11-02
try to install your drivers manually. Is this a PCI card? or integrated in your MB?

---

### Post by PogMoThoin on 2007-11-02
[This]("https://help.ubuntu.com/community/FakeRaidHowto") might help you. Apparently Ubuntu sees through your fake raid array. Had the same problem myself & had to split my raid raptors & install Ubuntu & Vista on seperate hd's

---

### Post by Dalman on 2007-11-03
> **Jorn.jambers said:**
> try to install your drivers manually. Is this a PCI card? or integrated in your MB?

integrated into MB...

I have seen this help section on this site...

 [I][COLOR="Red"]"Install dmraid"
Boot the Ubuntu CD and select Start or Install Ubuntu 

Go to System > Administration > Software Sources and add the universe software repository. 

Go to System > Administration > Synaptic Package Manager and install the dmraid package. 

Go to Applications > Accessories > Terminal and run 

sudo dmraid -ay[/COLOR][/I]

My problem with this is where do I find "Sytem > Administration... etc"

The only thing I get is a set installation. 

I can't see where I would enter text to load any othe options?!

---

### Post by Rangy Bear on 2007-11-03
I think I have a similar problem.  I'm new to Linux in general and even newer to Ubuntu.  I've downloaded the 7.10 live CD to take a look.  Looks really nice. I wanted to install it on a unused drive in my system.  no go.  Ubuntu keeps telling me that I don't have any drives.

I'm running a Gigabyte GA-8KNXP mother board using the built-in RAID controller (IT8212 chipset).  I have two arrays configured: 1- RAID-0 running windows xp and 2- RAID-0 unformatted. I want to install Ubuntu on the second array and be able to dual boot.

When I use the Ubuntu included gpart tool, it says no disk. When I use the Gpart live CD it see all of the drives.  What gives?  Am I missing somethig or is 7.10 missing some driver(s)?

Best Regards,

John

---

### Post by Rangy Bear on 2007-11-07
OK, I've re-read Dalman's reply but I'm unsure which version of 7.10 I should be loading from to do this.  Should I be using the Live CD or the Alternative CD?

Is anyone else having a problem loading Ubuntu on a GigaByte MB?

---

### Post by Rangy Bear on 2007-11-07
I'm a new user to linux and I'd like to be able to dual boot windows and linux on my system until I was satisfied that linux/Ubuntu could meet all my needs.  However, at the present time, Ubuntu and its various offshoots, does not support what is referred to as 'fake raid'.  In my case it is a IT8212 chipset used on a GigaByte mobo, model GA-8KNXP.  Since the GNU GPARTED live CD supports this feature and the GPARTED tool included in Gutsy does not, I must conclude that Ubuntu does not intend to, or is unable to support this chipset and/or 'fake raid'.  This to be further borne out by the lack of response to this thread.  Too bad, I was so looking forward to learning more about linux through Ubuntu. 

Best regards,

John Newton

---

