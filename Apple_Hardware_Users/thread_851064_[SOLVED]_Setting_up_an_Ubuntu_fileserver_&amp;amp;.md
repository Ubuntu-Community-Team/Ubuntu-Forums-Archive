---
title: "[SOLVED] Setting up an Ubuntu fileserver &amp;amp; gateway for use with OS X workstation"
date: 2008-07-06
forum: Apple Hardware Users
---

### Post by NickZA on 2008-07-06
Hi All

The time has come for me to jettison Windows from my life once and for all. Hallelujah.

I'm still pretty new to the OSes I'm now going to be working with - primarily OS X for my workstation (a little Ubuntu too), and Ubuntu for my fileserver.

Questions:

1. Fileserver will really only be accessed from OS X & Ubuntu (Windows is a 3rd class citizen now). So I was thinking to setup the server's RAID-1 as HFS. Can I do this, create a new HFS volume in Ubuntu once I've used mdadm to setup software RAID? (From what I've read, my other option of getting OS X to access EXT3 is not nearly as straightforward)

2. How easy is it to get my OS X and Ubuntu systems talking over an ethernet network (crossover cable)?

3. How easy is it to get:
   a)my OS X system sharing internet with the Ubuntu system as gateway? (presumably the more secure option)
   b)my Ubuntu server sharing internet with the OS X system as gatewat? (my other option)

4. Finally, should I wish to have a Windows partition on my workstation for running games, on those rare occasions I want it to connect to the internet, would it be straightforward using option 3a? (no big deal if not)

5. What is Ubuntu Server, and would it be useful for what I'm trying to do here? (which is to get a stable, fairly secure fileserver up and running quite soon)

Can't wait to get it all running...

:guitar:

-Nick

PS. As an aside, what is LVM (relating to Linux RAID)?

---

### Post by NickZA on 2008-07-06
Hi All 

The time has come for me to jettison Windows from my life once and for all. Hallelujah.

I'm still pretty new to the OSes I'm now going to be working with - primarily OS X for my workstation (a little Ubuntu too), and Ubuntu for my fileserver.

Questions:

1. Fileserver will really only be accessed from OS X & Ubuntu (Windows is a 3rd class citizen now). So I was thinking to setup the server's RAID-1 as HFS. Can I do this, create a new HFS volume in Ubuntu once I've used mdadm to setup software RAID? (From what I've read, my other option of getting OS X to access EXT3 is not nearly as straightforward)

2. How easy is it to get my OS X and Ubuntu systems talking over an ethernet network (crossover cable)?

3. How easy is it to get:
a)my OS X system sharing internet with the Ubuntu system as gateway? (presumably the more secure option)
b)my Ubuntu server sharing internet with the OS X system as gatewat? (my other option)

4. Finally, should I wish to have a Windows partition on my workstation for running games, on those rare occasions I want it to connect to the internet, would it be straightforward using option 3a? (no big deal if not)

5. Would Ubuntu Server Edition be useful for what I'm trying to do here? (which is to get something stable and reasonably secure up and running quite rapidly)

Can't wait to see it all running...

:guitar:

-Nick

PS. As an aside, what is LVM (relating to Linux RAID)?

---

### Post by apswartz on 2008-07-06
1. I don't know about the raid. But OSX will have no problems networking with your Linux box using ext3 since only Linux will actually have to read the ext3. OSX will exchange information via Samba. You will need a Samba server installed on your Linux box.

2. I would get a router that also serves as the gateway to your Internet connection. To use the Linux box as the gateway will require two network cards and setting up iptables to handle and filter the traffic.

3. See 2.

4. No problem with the router/gateway option. If you use your option 3a, your Mac will be cut off from the Internet.

5. Ubuntu server is especially designed to provide various servers. You can run the Samba server (or any other needed server) on a desktop install as needed.

Extra. [LVM Information]("http://www.ibm.com/developerworks/linux/library/l-lvm/").
[http://www.ibm.com/developerworks/linux/library/l-lvm/](http://www.ibm.com/developerworks/linux/library/l-lvm/)

Good luck. 
// Should you fail in your mission the secretary will disavow your actions! // ;-)

---

### Post by werries on 2008-07-06
linux doesn't deal with HFS veery well, FAT32 would actually be the best option.

should be easy to get em talkin over ethernet, and yes, ubuntu would do fine as a gateway. along with windows talking to it. there are network tools built in for this. probably something to do with samba.

As for LVM: [http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux](http://en.wikipedia.org/wiki/Logical_Volume_Manager_(Linux))

server edition is only CLI with no GUI. You would have to know command line proficiently. You can host a server with the normal edition just fine.

---

### Post by NickZA on 2008-07-06
From what I've read, mount -hfsplus gets your HFS+ drives working perfectly (read/write). A lot of people have asked the question about HFS+ and Linux, and as usual when this happens, some guru comes along and makes the answer apparent :)
[http://ubuntuforums.org/showpost.php?p=694291&postcount=1](http://ubuntuforums.org/showpost.php?p=694291&postcount=1)
[http://www.linuxquestions.org/questions/linux-software-2/mounting-hfs-volumes-under-linux-521189/](http://www.linuxquestions.org/questions/linux-software-2/mounting-hfs-volumes-under-linux-521189/)
FAT32 is old, and from what I understand, relatively slow and definitely not secure.

Thanks for the other tips regarding the server, in particular that I should rather go with desktop version. LVM sounds interesting in terms of its ability to resize volumes -- is resizing not a feature of standard software RAID built using mdadm, then?

So I'm still left with the question: Is creating a software RAID HFS+ partition in Ubuntu 8.10 doable?

---

### Post by x0as on 2008-07-06
My fileserver has a raid 5 array formatted ext3 and shared through samba, never had a problem with os x or xp mounting the shares.

---

### Post by bapoumba on 2008-07-06
Threads merged.

---

### Post by NickZA on 2008-07-06
apswartz & x0as: You guys both answered a question I had thought of but had not voiced: "Does OS X need to be able to read the filesystem directly, or is it up to the host system to do translations when talking across the network?" --Excellent.

So I could (using Samba) tocreate my fileserver's RAID as ext3, and not even worry about using HFS+ as I don't intend to use those disks with my OS X workstation directly...

Thank you guys.

---

### Post by cyberdork33 on 2008-07-08
> **NickZA said:**
> So I could (using Samba) tocreate my fileserver's RAID as ext3, and not even worry about using HFS+ as I don't intend to use those disks with my OS X workstation directly....
Exactly, and as already stated, Linux doesn't play nice with HFS+. Any native linux filesystem would be leaps and bounds better.

---

### Post by NickZA on 2008-07-09
Cyberdork :)

Can you elaborate on "doesn't play nice", both what you've read and/or in your own experience?

Reason I ask is that, although I intend to do the above exactly as stated, I will also be running both Ubuntu Studio 8.10 and OS X Leopard on my workstation, and I was actually just about to create an HFS+ partition for common storage purposes when I read your post! Do let me know.

-Nick

---

### Post by cyberdork33 on 2008-07-09
> **NickZA said:**
> Cyberdork :)

Can you elaborate on "doesn't play nice", both what you've read and/or in your own experience?

Reason I ask is that, although I intend to do the above exactly as stated, I will also be running both Ubuntu Studio 8.10 and OS X Leopard on my workstation, and I was actually just about to create an HFS+ partition for common storage purposes when I read your post! Do let me know.

-Nick

HFS+ is an OK filesystem, it is just not well supported under linux. This is a result of having to reverse engineer a lot of it since apple doesn't give out specifics. I am not saying you cannot use HFS+ how you intend, but especially in your previous situation, there are a lot better alternatives.

First, in order to enable write support under linux for HFS+, you have to disable journaling. This in itself almost makes using it pointless.

FAT32 is the optimal choice for a shared partition, with NTFS (under FUSE) following a close second (if you can't deal with the 4GB filesize limit of FAT32). HFS+ support is nice under linux in case you need to access your OSX partition(s), but I would avoid it for other purposes.

If you decide to continue with your choice of HFS+, keep in mind that this filesystem obeys file permissions, thus, files created by your OS X user will be inaccessible to your Ubutnu user (unless you make some changes to your User and Group IDs).

Hopefully, ZFS will be the filesystem of choice once the current issues are worked out.

---

