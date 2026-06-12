---
title: "Help for a newbie, please?"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by Kyleth on 2007-01-10
Right, I'm thinking of dual boothing Ubuntu 6.06 with Mac os X on my macbook.

As it appears fellow 15 year olds and most of my ICT teachers don't even know what Ubuntu is (terrible I know) I thought I'd come here...

I was just wondering, Which version should I download as I have the new Intel Core 2 Duo chip?

Also, how well would my airport express card and my Netgear DG834Gv3 Router work with Ubuntu?

And finally How easily can Ubuntu be uninstalled, incase I decide to rid myself of it for whatever reason.

Sorry for all the questions. I don't want to come across as a bother if at all possible.

Thanks in advance :]

---

### Post by riven0 on 2007-01-10
Normally, I would recommend Edgy as it is the latest release and most people don't have problems with it. 

But since you have a wireless card, it may be safer just to go for Dapper. A lot of the wireless cards in Edgy are experimental, and some take a lot of fumbling around before you can get it working. So I definitely recommend Dapper.

As for uninstalling Ubuntu, the LiveCD comes with it's own partitioner where you can manually delete and resize any partition on your laptop. So it can be done through there.

Good luck! :KS

---

### Post by kebes on 2007-01-10
> **Kyleth said:**
> Right, I'm thinking of dual boothing Ubuntu 6.06 with Mac os X on my macbook.

As it appears fellow 15 year olds and most of my ICT teachers don't even know what Ubuntu is (terrible I know) I thought I'd come here...

Well you're in the right place!


> I was just wondering, Which version should I download as I have the new Intel Core 2 Duo chip?

Also, how well would my airport express card and my Netgear DG834Gv3 Router work with Ubuntu?

I have a macbook pro (1st gen, which has a core duo chip) and it boots the standard Ubuntu (x86 architecture) LiveCD just fine. Wireless is detected out of the box, no configuration or mucking about. (Edit: works with Dapper, have not tried Edgy.)

So what you want is the same Ubuntu version that all x86 intel chips use.


> And finally How easily can Ubuntu be uninstalled, incase I decide to rid myself of it for whatever reason.


Uninstallation is of course possible. There are tools on the disk to resize partitions. (I know it works with fat32 and NTFS, not sure about HFS+.) So in theory if you don't like it, you can just delete it and format the free space so that Mac OS X can use it.

(Of course, always back up your data before attempting things like that!)

You should certainly burn a LiveCD and try booting that first. It will give you a good idea what Ubuntu is like (except that the LiveCD runs much slower than a real install), so that you'll know whether you want to install it.


> Sorry for all the questions. I don't want to come across as a bother if at all possible.

Dont' be sorry! That's what the forums are here for. If you run into any problems in your installation (or un-installation), let us know. Post again if you have other questions.


EDIT: With regard to uninstalling: It appears that [gparted]("http://gparted.sourceforge.net/features.php") can shrink, but not grow, HFS partitions. Thus if you uninstall Ubuntu, you'll be left with a small HFS partition and empty space. You would then have to decide between formatting the empty space as a new partition for Mac OS X, or reinstalling Mac OS X to reclaim the space.

---

### Post by meborc on 2007-01-10
> **riven0 said:**
> ...But since you have a wireless card, it may be safer just to go for Dapper. A lot of the wireless cards in Edgy are experimental, and some take a lot of fumbling around before you can get it working. So I definitely recommend Dapper...

i would say the opposite - edgy is newer, therefore it has better wifi support... no way is edgy worse then dapper!

---

### Post by Kyleth on 2007-01-10
I heard these forums were very helpful. It is indeed true. :]

Thanks for the help guys, I'm downloading it now. I hope it's the LiveCD. As stupid as it sounds, I'm not sure if it is or not...

EDIT: Yeah, uninstalling sounds okay, that won't be too hard. I've already reinstalled OS X once since I've had this Macbook. :P

---

### Post by Modernity on 2007-01-10
For sake purposes, Edgy is cool and all, but I still think Dapper would give you less problems. 

The install is the same as the LiveCD. They are both on the ISO. Don't feel bad though, because all of us has been noobs at some point in time and we wish more ppl would at least give Ubuntu or other distro's of Linux a chance.

Good luck with your install and if you need further help, feel free to ask. (AND THEN, go back and tell your IT teacher to catch up with the rest of the world and to pull their noses out of the DOS screen!)

---

### Post by Kyleth on 2007-01-10
Ahh thanks :]

Sorry to cause any confusion but I'm now downloading 6.10 instead.
Someone from another forum who has used Ubuntu before said it would be better.
Well I guess there's only one way to find out...

---

### Post by mustang on 2007-01-10
Actually I believe there were a lot of kernel fixes targeting the macbook that went into edgy so I would try edgy before dapper. 

I have edgy running on a white macbook(core duo). Everything is fine except suspend. That's really the dealbreaker for me :/

---

### Post by Kyleth on 2007-01-10
Pardon me here for being such a n00b, what is Suspend may I ask?

---

### Post by jvc26 on 2007-01-10
Suspend is sort of like hibernate, except one stores your RAM information on the HDD and the other, if i remember rightly just holds it in the RAM. I'm pretty sure that is the difference. Basically its putting the computer to sleep mode rather than turning off I think,
Il

---

### Post by Kyleth on 2007-01-10
Ahhh that does sound useful, but I think I could live without it.

Just about...

---

