---
title: "Manual Partition"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by nowatkins on 2007-05-09
I have reloaded UBU 6 times today. Not because I mess up or anything. I just so easy to install, reformat, and reinstall. I have just been learning and experimenting. I have noticed that there is no mount point for /swap. I got an error stating there was no swap. Do I just leave some space free and it will auto create?

---

### Post by alienexplorers on 2007-05-09
When setting up the partitions I use:


> Root     /     (10GB)
HOME     /home      (10GB)
SWAP     swap        (1 GB)

---

### Post by starcraft.man on 2007-05-09
> **nowatkins said:**
> I have reloaded UBU 6 times today. Not because I mess up or anything. I just so easy to install, reformat, and reinstall. I have just been learning and experimenting. I have noticed that there is no mount point for /swap. I got an error stating there was no swap. Do I just leave some space free and it will auto create?

You don't mount the swap, its not a mountable drive. Its only purpose is to serve as buffer space for your OS should your ram run out (or a program specifically uses swap). When you partition your drive, you should have a root file (/) and a second partition that is logical, likely 2 GB and formatted with swap-file format. Ubuntu will know its there, that is all.

Alternatively, when you reformat and install again I suppose for time 7 :p, you may want to consider making a /home partition for data storage so your files are seperate from your OS. This will let you upgrade/reinstall your OS without losing your files. Don't be afraid of the manual partitioner, its not too hard to use. If you make the home partition, you only need about 6-8 GB oh HDD space, rest can be home.

Hope that answers your question. If you do use the autopartitioner, it should make this for you though I don't know the size it picks. Manual is a good experiment for you to do to learn how to partition  :D

---

### Post by jerrylamos on 2007-05-09
In Manual Partitioning, I specifically create a swap space usually just over 512 mb which is my cache size.  You create a partition and select swap as the format.  If you do a dual boot or triple boot or quad boot, you only need one swap; any of the images booted up will use the same swap.

I have had Ubuntu Dapper 6.06, Xubuntu Feisty 7.04, and Kubuntu Feisty 7.04 all on the same system.  You can squeeze them into 4 gb each, 10 gb is more comfortable, and I use 20 gb each because I download iso's onto the desktops.  

It's pretty easy to copy home from one to the other, bookmarks, flashplayer, realplayer, etc.

Note I by far prefer Gnome Partition Editor (Gparted) to the reduced function partitioner that comes with install.  Gparted may be on your System, Administration list or else you can download the package on Applications, Add/Remove or even do a Google search on Gparted and download a standalone one to be burned into its own CD Live.  In particular the manual partitioner on Xubuntu Feisty is broken; it will do edit to change mount point and format and go on to install, but any change in partitions is broken and the install fails.

Cheers, Jerry:)

---

### Post by nowatkins on 2007-05-09
Thanks for you guys help. I just on a crash course. I actually own a IT consulting business. I thought about pushing linux servers instead of the expensive, bloated, and security mess of the Windows 2003 Server.

PS: I not even loading any software or putting any files on the server.

---

### Post by starcraft.man on 2007-05-09
> **nowatkins said:**
> Thanks for you guys help. I just on a crash course. I actually own a IT consulting business. I thought about pushing linux servers instead of the expensive, bloated, and security mess of the Windows 2003 Server.

PS: I not even loading any software or putting any files on the server.

Good man, linux is the way to go :D

You may want to read up on lots of the online info to learn more about configuring. Ubuntu guide in my sig is good, so is [psychocats]("http://www.psychocats.net/ubuntu/index"), not to mention the official wiki which documents lots of extra stuff like hardware support lists (though, those aren't perfectly accurate always).

Have fun with Linux :D

---

### Post by lbelmond on 2008-02-20
[FONT=Georgia][SIZE=2]=^.^=[/SIZE][/FONT][FONT=Georgia][/FONT]

---

