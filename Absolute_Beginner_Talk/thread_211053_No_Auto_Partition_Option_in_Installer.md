---
title: "No Auto Partition Option in Installer"
date: 2006-07-07
forum: Absolute Beginner Talk
---

### Post by tonofclay on 2006-07-07
I don't have very much experience with Linux and no partitioning experience, so when I saw that Ubuntu made it easier for less knowledgable people to partition their drives, I thought it would be for me. I have been running off the live cd for a few days now, and after getting my wireless network working with Ubuntu I decided it was time to install. Unfortunately when I got to the partition section of the install, I saw only two options, as opposed to the three I was expecting. I am using the Dapper Drake version. Here is a screenshot of what my install looks like.

---

### Post by dabear on 2006-07-07
Hehe, you would be much better off learning partitioning in the first place. Auto-partitoner [is marked as essential](https://launchpad.net/distros/ubuntu/+spec/ue-partitioning-tool) for the next release, so it will be included in edgy; if you could wait that long :)

---

### Post by tonofclay on 2006-07-07
Hehe yeah you're right, I definately would be better off learning the ins and outs of partitioning, but I just don't understand why installation guides I read all mention this auto-partitioner and even show screenshots of my missing third option. Where could my option have gone?!

EDIT: I found this link as well, which seems to say unless I'm mistaken that the partioning tool is on the LiveCD...

[https://launchpad.net/distros/ubuntu/+spec/ubuntu-express](https://launchpad.net/distros/ubuntu/+spec/ubuntu-express)

EDIT AGAIN: Perhaps my problem is that I need the alternate cd to perform this auto-partion? Quote from this link: [http://mirror.cs.umn.edu/ubuntu-releases/6.06/](http://mirror.cs.umn.edu/ubuntu-releases/6.06/)

"The alternate install CD allows you to perform certain specialist installations of Ubuntu. It provides for the following situations:

    * creating pre-configured OEM systems;
    * setting up automated deployments;
    * upgrading from older installations without network access;
    * LVM and/or RAID partitioning;
    * installing GRUB to a location other than the Master Boot Record;
    * installs on systems with less than about 192MB of RAM."

Does one of the first two options explain why I'm missing the partioning tool on my livecd (which is not the alternate)?

---

### Post by amo310 on 2007-12-23
Unmount the windows partition before opening the installer.

---

