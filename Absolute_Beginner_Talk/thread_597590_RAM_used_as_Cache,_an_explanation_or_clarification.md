---
title: "RAM used as Cache, an explanation or clarification needed"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by Hopworks on 2007-10-30
I'm using Ubuntu 7.04 Server configured as a LAMP with MythTV installed making use of an installed PVR-150.

I have noticed lately, when checking the status of my used RAM, that the remainder of the memory is used as cache. I don't see any performance hits at all, but after I reboot, the result is different.

I don't think I can post images in here, so I'll have to upload them to my host server...
Here is after running for awhile...
[http://hopworks.com/ubuntu_forums/linux_cache_mem_01.jpg]("http://hopworks.com/ubuntu_forums/linux_cache_mem_01.jpg")
[IMG]http://hopworks.com/ubuntu_forums/linux_cache_mem_01.jpg[/IMG]
And after rebooting...
[http://hopworks.com/ubuntu_forums/linux_cache_mem_02.jpg]("http://hopworks.com/ubuntu_forums/linux_cache_mem_02.jpg")
[IMG]http://hopworks.com/ubuntu_forums/linux_cache_mem_02.jpg[/IMG]
What I would like to know is what is USED AS CACHE mean to me, and is there something I should set to change that, or leave it alone? Is it a MythTV using a XFS file system thing?

Hop

EDIT: HUH! I did the image tag, but the links didn't show up. =(
EDIT AGAIN: Live and learn. lol. I used my LAN domain (without the .com) so it didn't work. It's all fixed now.

---

### Post by Lord_Dicranius on 2007-10-30
I was always wondering this too, but was too lazy to post a new thread haha  Thanks for asking Hopworks :)

---

### Post by Hopworks on 2007-10-30
> **Lord_Dicranius said:**
> I was always wondering this too, but was too lazy to post a new thread haha  Thanks for asking Hopworks :)
It's a very active forum, and it will get pushed off in a hurry. I hope someone can enlighten us. =)

Are you running a similarly configured system? I mean using MythTV and a XFS partition also? I suspect those two parameters as the cause since I read by several people, actually a large debate on XFS vs EXT3 or JFS, that XFS is very volatile in the event of a power outage because much of it's performance is RAM related. I've had three power interruption issues and hadn't suffered any data loss btw. Like I said before though, even when I add the two percentages together equaling 100%, I haven't had any problems or performance issues. I HAVE noticed however that a tiny portion of my swap file was used. That should never happen with 1.5 gigs of ram installed, in my system anyway.

---

### Post by sloggerkhan on 2007-10-30
Every Ubuntu I've ever used has always had the 'cache' expand to fill most of the unused RAM as it's running. Still very little swap usage and quick running, though. Not sure what it means.

---

### Post by Lord_Dicranius on 2007-10-30
Nope.  Just a basic Ubuntu desktop install (or was it when I was using Kubuntu... :-\ ), and ext2 (that's the default file system, right? haha).

I found this a few mins ago: [Memory, Swap Management](http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/).  I'm not on my Ubuntu system right now though, so I can't try out that "free -m" command to see what's going on (I've never heard of the "free" command neither, hmm).

---

### Post by Hopworks on 2007-10-30
> **Lord_Dicranius said:**
> Nope.  Just a basic Ubuntu desktop install (or was it when I was using Kubuntu... :-\ ), and ext2 (that's the default file system, right? haha).

I found this a few mins ago: [Memory, Swap Management](http://ubuntu.wordpress.com/2005/10/07/memory-swap-management/).  I'm not on my Ubuntu system right now though, so I can't try out that "free -m" command to see what's going on (I've never heard of the "free" command neither, hmm).

```
root@hopworks:~# free -m
             total       used       free     shared    buffers     cached
Mem:          1519       1486         32          0          2       1179
-/+ buffers/cache:        304       1214
Swap:         4447          0       4447

```Total 1519, used 1486!!!! free 32!!!!!!!!

Gotta know what this means

---

### Post by schorsch on 2007-10-30
Every linux system uses the available free memory for file system caching to improve performance. So after a reboot the cache ratio will be low and increase to the maximum when starting applications. If memory is needed by applications file system caching will be reduced so: works as designed!
When using the "free -m" the command the relevant line for  memory in use is the one starting with "-/+" as this shows memory usage without file system caching.

---

