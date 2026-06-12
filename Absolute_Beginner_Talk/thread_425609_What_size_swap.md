---
title: "What size swap?"
date: 2007-04-27
forum: Absolute Beginner Talk
---

### Post by Blofeld on 2007-04-27
How large should the swap partition be on a machine with 256 MB RAM and 30 GB HDD?  And why?  Thanks.:-k

---

### Post by jiminycricket on 2007-04-27
I think it should be double the size of your RAM in your case (although that can be a myth these days), so if you hibernate then everything has room to fit inside of it.

---

### Post by linux_kid on 2007-04-27
400-600 with one OS
200-400 with two OS's

See above post, correct about myth, depends on computing needs...

---

### Post by Duck2006 on 2007-04-27
The swap partition sould be twice the ram size. When the ram is full it dumps the info in the ram to the hard drive, so the system will run smoth, (or we hope so). With that said you can make larger if you wish. Any ram over 512Mb there is realy not much need for swap and there sould be enough ram to run the system in that but i use 1Gb for swap, and it works quite well with that.

---

### Post by ViRMiN on 2007-04-27
Linux_kid where'd you get that info from?  Isn't it a bad idea to share swap partitions between distros?

---

### Post by linux_kid on 2007-04-27
> **ViRMiN said:**
> Linux_kid where'd you get that info from?  Isn't it a bad idea to share swap partitions between distros?

I ment If he was running windows alongside ubuntu, sorry if that was misconceived.

---

### Post by ViRMiN on 2007-04-27
No worries, Linux swap is totally independant of Windows swapfiles.

---

### Post by Blofeld on 2007-04-27
Why does every distro need its own swap file?

---

### Post by Duck2006 on 2007-04-27
> Why does every distro need its own swap file

No they don't they can share the same swap file (linux distro's that is)

---

### Post by Najand on 2007-04-27
How can someone run windows alongside ubuntu, on such an old computer?

---

### Post by louieb on 2007-04-27
> **Najand said:**
> How can someone run windows alongside ubuntu, on such an old computer?
**Slowly! **  With 256MB memory its not bad. I have a P1 200 128MB ram and a 4 gig hard drive. Put Ubuntu on it just for grins. It is functional but slow.    

Since I don't have a lot of applications running at the same time I find 512MB swap works pretty well no matter how much memory the machine has. Probably could get by with  256MB. Never seen more that 100MB used. 

The only exception to that is on the Laptop. I believe the hibernate and suspend use swap when I put the PC to sleep. In that case I'm using memory X 1.5 for swap. 

I don't know about the rest of you, but when I have multiple Linux distros on the same machine they all share the same swap partition. Its just temporary storage for whatever distro is running at the time.

---

### Post by Blofeld on 2007-04-28
"With 256MB memory its not bad." 

Thanks for sticking up for us frugal users.  I mean, of course it's nice to have plenty of space and power, but for the bread-and-butter tasks of writing letters, e-mailing and surfing the internet no-one really needs multiple CPU cores and Gigs of RAM.  My current computer cost me 50 bucks. \\:D/ 

The only thing that bothers me about my machine is that larger WMV videos occasionally skip.

I don't have a parallel Windows-Linux install, BTW, but a parallel Linux-Linux install.

---

### Post by red_five on 2007-05-03
My laptop currently has only 256MB, but my swap is 2GB. I'm getting ready to max out the RAM to 1GB, and I always use the swap = physical X 2 rule-of-thumb. In this case, I recently reinstalled the OS, so I planned ahead. Any time I install Windoze, I set it to use 2x physical; I do NOT allow Windows to manage the setting itself, because sometimes it will use whatever space you have left on your hard drive, and your system WILL grind to a halt while it expands the pagefile. No thank you, Uncle Bill.

I am not sure where the 2x rule came from, but I know that it's older than Linux, and probably older than Windows and Macintosh. Every time I've used it, it works great. Highly recommended.

---

