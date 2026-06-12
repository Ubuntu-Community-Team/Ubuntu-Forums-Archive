---
title: "Prevent Loss of Data on Reinstall"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by wagb278 on 2008-04-08
My first post.

I'm in the planning mode for Ubuntu install on new computer.  I want to configure the Hard Disk so extra applications and my data are not lost if I re-install  Ubuntu (or other distro).  Placing /home in a dedicated partition makes sense.  I think Apache and MySQL applicaitons get installed in other directories and MySQL database files end up in /etc/lib/mysql with Web data files placed in /var/www or /srv/www.  I don't want to lose the content of those if I reinstall the OS.  

Is there a commonly used configuration, or scheme, that isolates the OS files from applications and from data?  How does one save even the user accounts if re-installing a new version of Ubuntu; say form 7.10 to 8.4?

I have read many articles and theads recently but I just don't see how to retain the configuration files and settings across a re-install action.  

I think I am asking for confirmation on what directories to allocate to dedicated partitions (without going overboard) such as /var, /svr, and of course /home.

Ideas???  Suggestions???

Thanks

---

### Post by Oldsoldier2003 on 2008-04-08
> **wagb278 said:**
> My first post.

I'm in the planning mode for Ubuntu install on new computer.  I want to configure the Hard Disk so extra applications and my data are not lost if I re-install  Ubuntu (or other distro).  Placing /home in a dedicated partition makes sense.  I think Apache and MySQL applicaitons get installed in other directories and MySQL database files end up in /etc/lib/mysql with Web data files placed in /var/www or /srv/www.  I don't want to lose the content of those if I reinstall the OS.  

Is there a commonly used configuration, or scheme, that isolates the OS files from applications and from data?  How does one save even the user accounts if re-installing a new version of Ubuntu; say form 7.10 to 8.4?

I have read many articles and theads recently but I just don't see how to retain the configuration files and settings across a re-install action.  

I think I am asking for confirmation on what directories to allocate to dedicated partitions (without going overboard) such as /var, /svr, and of course /home.

Ideas???  Suggestions???

Thanks

custom executables should be placed in the /opt directory. If you make this a separate partition you can always reinstall then remove the new /opt and mount the one on a partition by editing your fstab. Having a operate partition for /home covers most data and configuration issues for users. I also like to have a separate partition for data. I call mine /data (yeah im real ingenious with naming  *grins)

---

### Post by Fixman on 2008-04-08
Or you can just make a new partition, put all files there without folders and stop worrying about the bomb.

---

### Post by Oldsoldier2003 on 2008-04-08
> **Fixman said:**
> Or you can just make a new partition, put all files there without folders and stop worrying about the bomb.

since i like to play with different distros and usually run the current beta I've found that the separate data partition is really the way to go separate home is not really that important once you get in the habit of not saving data in the home partition and the separate /opt is  really overkill for me but it may be useful for some people. separate /var is only really useful for mail servers in my opinion.

---

### Post by bodhi.zazen on 2008-04-08
bodhi hands Oldsoldier2003 link :

ln -s /mnt/data/music ~/music
ln -s /mnt/data/pictures ~/pictures
ln -s /mnt/data/stuff ~/stuff

Or

ln -s /mnt/data ~/data

---

### Post by wagb278 on 2008-04-08
links - that is a great idea.

Are there any limitations or restrictions you know of?  I vagely remember some distros have limitations on their use.  Like crossing hard drives.

---

### Post by wagb278 on 2008-04-08
Thanks Fixman and Oldsoldier2003.  I felt that I was making this more complcated than it should be..  Which is why I asked.

---

### Post by Mud.Knee.Havoc on 2008-04-08
I keep /home in its own partition, so I can switch from Ubuntu to Debian or whatever and back and not worry about losing any of my personal files.  This doesn't help for applications, though.  

It does keep your configuration files, though, so all you need to do is reinstall the application and you've got the proper configuration all ready (ie. reinstall conky, your .conkyrc is still in your /home/yourusername folder).

---

### Post by ant2ne on 2008-04-08
I keep home on a separate partition. When I used to dual boot XP, I kept My Documents on a serperate partition too. I also keep my "data" in samba shares on a third partition. If I could just get samba to work right.

---

### Post by ramjet_1953 on 2008-04-08
I also like to fiddle and play with other distros.

However, I approach things from a different angle. Hard drives are cheap these days. so I have three, that I interchange.

That way, I don't have any problem with losing the data in my "working" distro.

For tower systems, you can buy a 'caddy' system, that allows you to plug and unplug a HDD in a few seconds, using a standard 5.25" bay.

For laptops, there is usually just a trapdoor on the bottom and changing the drive only takes a minute or two.

Regards,
Roger :cool:

---

### Post by bodhi.zazen on 2008-04-08
> **wagb278 said:**
> links - that is a great idea.

Are there any limitations or restrictions you know of?  I vagely remember some distros have limitations on their use.  Like crossing hard drives.

There are hard links and soft links.

Hard links can not be on different partitions or hard drives

Soft links can be on different partitions, different hard drives, or network mounts (NFS / samba / sshfs).

---

### Post by ant2ne on 2008-04-09
> **ramjet_1953 said:**
> However, I approach things from a different angle. Hard drives are cheap these days. so I have three, that I interchange. : Right, that is why I have dual 750gigs in a RAID1 array, with three partitions. =-)

---

