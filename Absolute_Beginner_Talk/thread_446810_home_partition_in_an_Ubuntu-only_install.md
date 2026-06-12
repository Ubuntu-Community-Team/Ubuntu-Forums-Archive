---
title: "/home partition in an Ubuntu-only install"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by nvteighen on 2007-05-17
Hi,
I've just read the advantages an /home partition has and I really would like to have one in my soon Ubuntu install. Question: When choosing the "erase entire disk" at the install assistant, does it creates one by default? Or do I have to create it manually using GParted? I **don't** want to keep WinXP nor a dual-boot, that's why I'd prefer do a total reformat.
Thanks!

---

### Post by kebes on 2007-05-17
During the installation, at the partitioning phase, it will have various options. One of them is "erase entire disk" which is the easiest but just creates a single partition.

To have a separate "/home/" partition, you need to select the third option "Manual." Then you get to define what partitions should exist, and where they should be mounted. You need to set a partition for root, /, a partition for home, /home/, and a partition for swap. You can also select what type of filesystem (the default is "swap" for swap and "ext3" for the other ones).

You also need to decide how big to make / and /home/. A default Ubuntu install will use up ~4Gb. So if you make the / partition 10-20 Gb (depending on your disk size) that will be fine, and you can use the rest for /home/. Typically you make the swap about double the size of your current RAM (or maybe just equal to your current RAM if you have alot of RAM).


These are general guidelines, of course. If you have more questions, feel free to ask. You can also see screenshots of the partitioning phases here:
[http://www.psychocats.net/ubuntu/installing](http://www.psychocats.net/ubuntu/installing)

---

### Post by arvevans on 2007-05-17
When you get to the Partition questions area, select "Manual" mode.

Delete all existing partitions.

Create new partitions with the mount points that you need.  Mark all but SWAP for "formating".

[LIST]
[*]Making a separate /boot partition will allow protecting your OS from most outside attempts to corrupt it.
[*]Making a /home partition will allow you to back up your user's information separately from the rest of the system.
[*]making a "/" partition holds all the rest of the stuff, including installed software, configurations data, etc.
[*]Don't forget to make a partition for SWAP, but you cannot and do not need to format this space because swap will dynamically clean and reuse this area as it needs it.
[/LIST]

Since you can only make 4 primary partitions on a HD, this is about all you can do unless you resort to logical partitions.

Hope this helps, and good luck.

Arv
_._

---

### Post by thayerw on 2007-05-17
Like kebes said, it really depends on the size of your hard drive.  If space is tight (15-30GB) I would even consider making the / (root) partition only 6GB and then a swap size equal to the amount of ram in your computer (but at least 512MB) and use the rest for /home.

I install a ton of applications and stuff from the repositories and I have never used more than 4GB on my / (root) partition, so you'll have some breathing room by leaving a couple extra gigs to spare.

If you burn lots of DVD's/CD's and your /tmp directory runs out of space you can always move /tmp over to your /home partition, allowing it to take advantage of the extra space there.

---

### Post by nvteighen on 2007-05-17
Thank you: this was exactly what I asked. But, another question: how should mounting points be written "/home" or "/home/"... or is it unimportant?

I was thinking something like this: my Hard Drive is 80 GB big and have 1 GB RAM (actually, it says to be 0.99 GB... don't know why)

/swap/: 2 GB (I want to be sure... 2+1 GB of memory isn't bad)
/root/: 20 GB
/home/: the rest, 58 GB

---

### Post by nvteighen on 2007-05-17
Oh, didn't see the other two replies... Thank you very much to you too!

---

### Post by tompickles on 2007-05-17
just a thought about the /boot partition. this is where your boot loader is installed right? what advantages are gained by having it as a seperate partition? and how big should it be?

---

### Post by kebes on 2007-05-17
Your partitioning plan looks good. Although, as others have said, you could reduce root to 10-15 Gb without any worries. (I'm using 6Gb after installing lots of software and that includes some hosted websites.)

> **nvteighen said:**
> Thank you: this was exactly what I asked. But, another question: how should mounting points be written "/home" or "/home/"... or is it unimportant?

I think you would write it as "/home" and not "/home/" (I was writing "/home/" previously to emphasize that it is a directory.) In the partitioning phase, you can actually select "/home" from the drop-down list for mount-point ([screenshot]("http://www.psychocats.net/ubuntu/images/feistydual12.png")), which makes it even easier. The installer will know what to do if you select it from the list.

---

### Post by kebes on 2007-05-17
> **tompickles said:**
> just a thought about the /boot partition. this is where your boot loader is installed right? what advantages are gained by having it as a seperate partition? and how big should it be?

The main reason to create a separate boot partition is if you're multi-booting (especially with different versions of Linux). As arvevans mentioned, it also provides some added security, because it becomes more difficult for something to corrupt the boot partition.

I personally don't think it's necessary to have a separate /boot partition.

If you're going to make one, I think 150 Mb is enough. I just checked the size of "/boot/" on three computers that run Ubuntu, and the sizes were: 17 Mb, 34 Mb, 46 Mb.

---

### Post by nvteighen on 2007-05-17
Thanks again.
I'm not going to create a /boot partition. I don't want a multi-boot.
I'll consider reducing the /root partition, I really don't need too much stuff (and that's my primary reason why I'll leave Windows; I want some more liberty). Maybe 15-18 GB (I like 18, because so I can round up the /home partition to 60 GB).

Anyway, thank you all!

---

### Post by tompickles on 2007-05-17
> **kebes said:**
> The main reason to create a separate boot partition is if you're multi-booting (especially with different versions of Linux). As arvevans mentioned, it also provides some added security, because it becomes more difficult for something to corrupt the boot partition.

I personally don't think it's necessary to have a separate /boot partition.

If you're going to make one, I think 150 Mb is enough. I just checked the size of "/boot/" on three computers that run Ubuntu, and the sizes were: 17 Mb, 34 Mb, 46 Mb.

So, if i were to install a 2nd linux distro, i just do the same as i would do in the Ubuntu install, and set the /boot to go the the same partition?

---

### Post by arkanabar on 2007-05-21
[SIZE="3"][FONT="Palatino Linotype"]This looks like the sort of thing I want to know more about.  I'm about to embark on a distro-hopping spree, so the idea of separate partitions for /home, /tmp (to reduce fragmentation), /boot, /swap, and a stack of partitions to serve as root for the different distros I plan to try sounds prudent to me.  (120 GB allows for this sort of thing, particularly as my system is not home to many large files).  But that will come after I've migrated Win2k from my big disk to the 40GB disk.

I've burned myself a copy of Gparted Live w/ Clonezilla just to more easily prepare myself for this.

Any further suggestions?[/FONT][/SIZE]

---

