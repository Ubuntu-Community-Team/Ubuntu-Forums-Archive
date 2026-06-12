---
title: "De-Fragment Drive?"
date: 2007-06-16
forum: Absolute Beginner Talk
---

### Post by RichPicker on 2007-06-16
Last week I had a major file system crash, and couldn't boot. I had to rebuild my system. I tried to do it with dual-boot, but it wouldn't partition - I waited 30 or 40 minutes - but the little clock just kept spinning. I've read here that some folks need to de-frag their windows machine before loading Ubuntu in a partition.

Should I de-frag my drive now, or regularly, in case I encounter the same problem again?

If so, how can I do that? I've read a few things on the wiki about partitioning windows before installing Ubuntu. But have not yet found how to do that with an Ubuntu system.

Or am I way off the path of understanding?

---

### Post by floke on 2007-06-16
Before installing Ubuntu - defrag windows and run a scandisc check.
Then install. You can set up the partitions prioir to installing if you like, or you can do it during the install process itself.

---

### Post by RichPicker on 2007-06-16
I'm already running Ubuntu. I was running Ubuntu when the file system error occurred. And when trying to re-install Feisty, it would not partition.

---

### Post by floke on 2007-06-16
How did you try to partition? I would use the alternative installer since IMO it works the best.

---

### Post by RichPicker on 2007-06-16
I inserted the CD, which I burned some moths ago from the iso. And I selected to install it on a partition on the drive, but it would not do it. I had to wipe the disk to install it.

---

### Post by floke on 2007-06-16
That could be due to a number of reasons. So now you only have ubuntu on your drive. Is that right? If so, no need to worry about defragging.

---

### Post by RichPicker on 2007-06-16
Yes, I only have Feisty on my drive. But that is all I had when the file system error happened. And when I had to completely reinstall with the CD, it would not install on a drive partition. I'm trying to know what to do if/when that happens again.

---

### Post by floke on 2007-06-16
Ah now I'm with you. In that case I'm out of answers. Actually had a similar incident last week. From a fsck failure I couldn't boot into gnome (KDE was fine) or gnome apps. Since I have a separate home partition it was quicker to reinstall the OS than to search for a solution to the problem. All good within the hour. Best practice really is to set up a separate home if you haven't already done so. As for the rest - ??

---

### Post by RichPicker on 2007-06-16
Yeah. That's what I had --  fsck error.
What is this? "Best practice really is to set up a separate home if you haven't already done so."
Maybe too complex to explain here?

---

### Post by floke on 2007-06-16
Well its quite simple. You set up a partition on your drive and use it as your /home partition; then, if the OS gets borked for any reason you just reinstall the system files from the cd - tell the /etc/fstab to use the partition (eg sda2) for home - and you're back where you were.

Just create a new partition on your disc for all your docs - lets say this is sda2. Format it as ext3.

Then edit your fstab - 'sudo gedit /etc/fstab' and tell it to use the partition for /home

e.g. my fstab entry is this

# mounting sda6 as Feisty home
/dev/sda6       /home   ext3    nodev,nosuid    0       2

(this is pretty standard for setting up a home directory - the nodev etc. stuff is all about the security settings etc. for it I think)

Then - when you restart, ubuntu will use - in this case - sda6 as /home

Don't forget to copy over all the files in your /home/username directory to the new partition first - especially the hidden config. files.

---

### Post by RichPicker on 2007-06-16
Thanks, That's beyond my current knowledge of Ubuntu. I will study your instructions, learn what I can, and ask more questions here when I get them.
Thank you.

---

### Post by floke on 2007-06-16
You should also have a look at this:

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

This is a *must* for Linux IMO. Couldn't live without it. It saves so much time.
If time to solve serious system problem is >1 hour then solution = reinstall.

---

### Post by RichPicker on 2007-06-16
I just glanced at the URL. It looks excellent. Thanks.

This Dell Inspiron 1300 takes me a few days to reconfigure. I have to jump through all the hoops.
Screen Resolution
Touchpad
Microphone 
Alsa Drivers
Codecs
Mozilla Addons
Webcam Driver
etc.

That's why it's especially important for me to protect against a crash from happening again. I have experimented with the Simple Backup Config. I'm thinking of buying a large-storage USB device and backing up to it regularly. Even after creating a separate /home partition think I should still backup everything regularly to some external location?

---

### Post by floke on 2007-06-16
Absolutely - I do. Came across this today also but haven't tried it yet.

[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

The main things I have are config files for OOo, Firefox, and beryl.
Upgraded a spare partition to Gutsy today and just coped over the relevant config files from my feisty /home partition - and, bang! Got all my configs exactly the way they were in feisty, with no mucking about.

---

### Post by RichPicker on 2007-06-16
No kidding. How is Gutsy?
While I'm asking. . .  is Feisty a modification of Dapper And is Gutsy a modification of Edgy? Am I asking that question clearly?
This is now off the original topic.

You've given me MUCH food for thought and learning.

---

### Post by floke on 2007-06-16
The release map has been: Hoary-Breezy-Dapper-Edgy-Feisty-[Gutsy]
Each version was, yes, a modification of the former - incorporating new improvements etc.
At the moment Gutsy is stable enough for me. No real difference from Feisty to be honest. Maybe the fonts look a bit sharper (perhaps). The kernel has better power management, enabling longer battery life and lower running temperatures - but I'm not sure if I see it really. 

Anyway, the fun will begin when they start pumping in the big stuff like the new Xorg etc.

But as long as I have my home directory on a different partition I couldn't care less if the OS breaks, since I can have it all back up and running the way it was within 30-60 mins ;)

---

