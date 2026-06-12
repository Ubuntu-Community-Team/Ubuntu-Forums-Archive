---
title: "Help with multiple hd and partitions"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by Crash-n-Burn on 2007-07-10
Hey guys,

I tried searching but was not able to find a situation close enough to mine.

I'm going to set up Ubuntu FF to be the main OS on my media center computer. My question is I have 3 HD's that I can't figure out how to partition correctly. I want them all to be able to read files too and from windows (other computers on network), and I want Ubuntu to be on a 40gb partition by itself.

When I tried setting it up myself it keeps asking for a different mount point for each hd and I was not sure which file system and mount points to use on each hd/partition to use. I had ubuntu set as a ext3 and all of the others jfs (don't know why). I believe ext3 is the best for ubuntu and the main partition should be mounted to /.

Should I just pop in a windows cd and format the rest NTFS? Or should I try doing it through linux and use its file systems?

Thanks in advance!

Jason

---

### Post by mikesignguy on 2007-07-10
many question...i will try and lead you to the answers but we need to know what u want to accomplish

like why would you want NTFS drives if your main OS is linux?

use this for mounting windows  drives:

[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

---

### Post by mr_byte on 2007-07-10
> **Crash-n-Burn said:**
> Hey guys,

I tried searching but was not able to find a situation close enough to mine.

I'm going to set up Ubuntu FF to be the main OS on my media center computer. My question is I have 3 HD's that I can't figure out how to partition correctly. I want them all to be able to read files too and from windows (other computers on network), and I want Ubuntu to be on a 40gb partition by itself.

When I tried setting it up myself it keeps asking for a different mount point for each hd and I was not sure which file system and mount points to use on each hd/partition to use. I had ubuntu set as a ext3 and all of the others jfs (don't know why). I believe ext3 is the best for ubuntu and the main partition should be mounted to /.

Should I just pop in a windows cd and format the rest NTFS? Or should I try doing it through linux and use its file systems?

Thanks in advance!

Jason

Well, as for your mount points, if you're not going to access the drives from Ubuntu, then I think you can just blank out the mount points the installer supplies for those drives, don't touch them at all, and just nuke and load on the 40gb partition.

If you want to format them as ext2/3 partitions, and access them from windows you will need *ext2ifs* from [http://www.fs-driver.org](http://www.fs-driver.org). I use to share "My Documents" on a 6gb ext3 partition between XP and Ubuntu.

I don't know anything about jfs, other than it's a journaling filesystem.

Jeff

---

### Post by Crash-n-Burn on 2007-07-10
Sorry guys,

Let me try to clear myself up. I am not going to be running windows on this computer. My other computer is going to be running windows and I want my linux computer (this one) to be able to read files from my windows machine.

I'm trying to figure out the best way to partition my other 2 hds. After reading the fourms my first hd is 40gbs is mounted to / and ext3, and 70gbs is ext3 and mounted to /home (for saving files I believe?) I don't know how to partition/format my other 2 hds.

My question is how do I format my other 2 hds and how do I mount them. I can't use / or /home mounting anymore since they are already being used, so I don't know how to do it. I want them to always be mounted since I am not going to run windows. Should they be ext3 and where should I mount them too? 

I just want my other 2 hds to be there for saving media files.

Is that any better?

Thanks again

---

### Post by Inxsible on 2007-07-10
Pop in your LiveCD and use GParted on it to format the 2 drives. You can choose to format it to anything either NTFS or EXT3, although since this comp is Ubuntu only, I would go for EXT3.
 
To have your Windows machine access these drives, you will need to install Samba on the Ubuntu machine to set up a virtual network and also install  fs-driver on the windows machine to access ext3 drives. 
 
If you are going to format the drives to NTFS, then you will need to install ntfs-3G on the Ubuntu machine to be able to write to the NTFS drives.

---

### Post by insomniacpyro on 2007-07-10
[http://www.fs-driver.org/](http://www.fs-driver.org/)

You can also use Ex2 IFS if you want Windows to handle Ext3 file systems. Yes, the name is Ext2, but it works with Ext3's. I'm not sure if you will be able to see/access the drives over the network, as I don't have experience with that. From what I've used, you should be able to share the drive like any other, but any computer will need this to access them.

Also, on these other two drives, is there data on them? If you do have some on them, you should leave them as they are until you can backup and restore the data after formating.

---

### Post by Crash-n-Burn on 2007-07-10
> **insomniacpyro said:**
> [http://www.fs-driver.org/](http://www.fs-driver.org/)

You can also use Ex2 IFS if you want Windows to handle Ext3 file systems. Yes, the name is Ext2, but it works with Ext3's. I'm not sure if you will be able to see/access the drives over the network, as I don't have experience with that. From what I've used, you should be able to share the drive like any other, but any computer will need this to access them.

Also, on these other two drives, is there data on them? If you do have some on them, you should leave them as they are until you can backup and restore the data after formating.

That did it!

I created the hd's as Media/Stuff and so on and they came up that way after I re-formated. 

My other question is, is it normal to require sudo in order to create folder in my other hard drives? I am not able to drap and drop or create folder in either of my other hds.

---

