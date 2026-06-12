---
title: "Moving to MacBook Pro"
date: 2010-12-31
forum: Apple Hardware Users
---

### Post by josephe on 2010-12-31
Hi all
I currently have a Dell Inspiron 1520 (no real complaints, just want the best laptop I can get ;-) 

I'm running a dual boot system with Lucid on one partition and Windows7 on the other.

Now I'd like to continue as is BUT on the Mac, I know Mac has a product called BootCamp (I think) so I know I can dual boot. But I'd like to just take an image of my Lucid and restore it to the new MacBook... Here my question.... Can I do this and how?

Also, since I really only use windows a little bit, and I'll have itunes on the Mac anyway, do people find they can manage with Windows only in a VM,maybe under Virtual Box?

Thanks 
Joseph

---

### Post by itismike on 2011-01-01
Hi Josephe,
I consider myself a very experienced Linux user who has attempted to upgrade or switch machines several times and am always disappointed with the results. The best suggestion I can think of is to [convert your current home folder into a separate partition]("https://help.ubuntu.com/community/Partitioning/Home/Moving") (assuming it isn't a separate partition already), and then move it to a fresh install of Ubuntu on your Mac. 
When performing the install on the Mac, be sure to choose *Manual* or *Advanced* partitioning which will allow you to create a separate "/home" partition. If you haven't done it before, here are some basic tips:
You'll need three partitions in total: [LIST=1]
[*]"home" - ext4 - will grow with  media downloads, so account for that
[*]"/" - ext4 - your system partition - grows with software installs
[*]"swap" - rule of thumb is to make it 1.5 times the size of your installed memory.
[/LIST]Are you using rEFIt or Bootcamp as your boot manager? With rEFIt, I think you'll want to tell the installer to NOT install grub as that is handled by rEFIt, but I may be mistaken about this.

And yes, Windows will work fine virtualized. I like VirtualBox, but there are many other choices.
Good Luck!

---

