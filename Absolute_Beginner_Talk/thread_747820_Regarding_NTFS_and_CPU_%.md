---
title: "Regarding NTFS and CPU %"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by azurepancake on 2008-04-06
I'm quite new to Linux, so please excuse my ignorance. I've been trying to get my feet wet with Ubuntu and have been fiddling around, learning UNIX commands etc. 

So I typed into terminal "top" to try out the top program and see all my processes in real-time. Top outputted with no problem, very cleanly. I then noticed at the top of the list of processes, something called "mount.ntfs" using 3.7% of the CPU.

This made me wonder why mounting a NTFS partition requires CPU and so much of it at that. Would using a format like EXT3 or EXT2 change the story? 

If anyone can clear this up for me I'd be very grateful. Please, feel free to be as detailed as you like, I'm trying to learn as much as possible about this wonderful OS. 

Thanks

---

### Post by DariusS on 2008-04-06
I'm only guessing here, but I believe it's due to the program ntfs-3g or similar running in the background, ready to read or write to an ntfs partition. the current cpu usage may be due to an actual ntfs read or write, even though none has been explicitly been done by you.
someone correct me if I am way off mark, but that's my initial impression.

---

### Post by azurepancake on 2008-04-06
That would make much sense, since I am actually using the NTFS partition for storing my media and my torrent client is accessing it currently. I'll have to monitor it when I close my torrent client to see if the CPU % drops at all. Thanks!

---

### Post by kbless7 on 2008-04-07
Thats interesting. I was playing with my windows partition (ntfs) and the program never showed up in my list of apps running. I guess its different for everyone.

---

### Post by azurepancake on 2008-04-07
Yeah, that is interesting. I just reboot my computer and now I am not seeing any ntfs-mount process when I run the top command. I wonder why?

---

### Post by Datz on 2008-06-22
I am having a similar problem, but my mount.ntfs processes are using alot more cpu.  My cpu usage will go to 100% periodically.  Just now when I checked, there were two mount.ntfs processes running, and they were both using 42% cpu.
 I am using Ubuntu (hardy) and my system has a 2.66GHz P4.
Any help is greatly appreciated.

Another thing to consider is the mount.ntfs process seems to go into high usage when my apache server is running.
thanks 
Datz

---

### Post by Datz on 2008-06-22
I moved my web site directory from my storage drive to my OS drive, and the problem seems to have vanished.

Is there some bug here?
I would think that having a web directory on another HD would be something that should not cause problems.

---

