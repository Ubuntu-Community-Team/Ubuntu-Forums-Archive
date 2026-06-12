---
title: "Can I remove old versions of Ubuntu?"
date: 2006-05-30
forum: Absolute Beginner Talk
---

### Post by harperd on 2006-05-30
I've just upgraded to Dapper Drake and find that I'm running out of hard drive space. I would like to remove earlier versions (I get about 6 options at boot up). Is this a good idea? Can I do it safely? If so, how?

Thanks a lot
David Harper
Madrid Spain

---

### Post by catlett on 2006-05-30
What you will be removing are older kernels. Not ubuntu the whole system. As long as your system is running well on the new kernel it is OK to delete the old ones. Some people think it is a good idea to keep at least one older kernel in case something happens with the one you're running, you can boot with the older version kernel.
The kernels are in synaptic package manager and can be removed by hitting on the entry and choosing to uninstall.
The listing should be linux-386, linux-686 or something like that. There will be a dscription next to it saying it is a kernel.
This is assuming you don't have entire installs of Ubuntu on different partitions. This is assuming you have one install but have gotten new kernels through updates and Grub is offering you the other kernels as options.

---

### Post by harperd on 2006-05-30
Thanks. I removed the oldest kernel but the partition is still nearly 4Gb (I have /home on another partition). Is this a normal size for a basic installation? I've only had the system running for a short time.

---

### Post by catlett on 2006-05-30
What did you install? Just the Dapper Ubuntu? I have Dapper with a seperate partition for home and I have 2.41gb used on my root partition and 515mb used on my home partition.Did you load kde as well?
 I guess now that I look at it I have almost 3gb used. Do you say you have almost 4gb used or that you have a total of 4gb.
The base (root) partition shouldn't grow  much more. That grows from applications added. Home grows from documents, mp3s,dvds etc. You can go through synaptic package manager and see what applications you don't want and remove them to get space. For example Open Office takes up a good bit of space , do you need a full office suit?
Just make sure to read what synaptic says it does and to pay attention when it says other things will be removed. Sometimes something can be attached to something important. 
I would start by browsing synaptic for "fluff" you don't need.

---

### Post by harperd on 2006-05-30
Thanks a lot for your very good advice. Yes I have KDE (in fact Kubuntu) so maybe I have what I should have. I'm using around 3.9Gb on a 4.6Gb partition. In this case I'll just keep an eye on things!

---

### Post by DavidW2 on 2006-06-01
[QUOTE=harperd]I've just upgraded to Dapper Drake and find that I'm running out of hard drive space. I would like to remove earlier versions (I get about 6 options at boot up). Is this a good idea? Can I do it safely? If so, how?

Thanks a lot
David Harper
Madrid Spain[/QUOTE]


You might want to remove the packages that have been downloaded over the time you have been running Ubuntu.  They are in /var/cache/apt/archives.  I know there is a command line to remove them but I don't remember the syntax offhand.  I'm sure someone can answer that.

I ran the 'du -sk' command on my ".../archives" directory and it shows just over 500MBytes of packages.

As a side note... I am using 4GB of a 6.6GB Partition, including my home dir, 3 extra games, 2 extra media players, 2 programming apps and a couple other apps.  This is 6.06RC.

---

### Post by 3rdalbum on 2006-06-01
[QUOTE=DavidW2]You might want to remove the packages that have been downloaded over the time you have been running Ubuntu.  They are in /var/cache/apt/archives.  I know there is a command line to remove them but I don't remember the syntax offhand.  I'm sure someone can answer that.[/QUOTE]

```
sudo apt-get clean
```

---

