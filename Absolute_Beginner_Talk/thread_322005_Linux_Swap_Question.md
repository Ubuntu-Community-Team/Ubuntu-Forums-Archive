---
title: "Linux Swap Question"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by steveOW on 2006-12-19
Hello All, I'm very new to Ubuntu but have used HPUX and Sun Solaris in the past. I'm tired of Windows and am venturing out to Linux on the PC!!

Ok So here's my story. Booted up using the 6.06 LTS 64-bit disk(I have AMDX2-64) and was installing to a 20GB Partition I made special at the end of a 320 SATA Slave drive. I have 3 physical drives in the machine. C: is a 30GB for Windows OS Only, D: is an 80GB for Program Files E: WAS the 320GB used for data storage, pictures and movies...

During the end of the install Ubuntu asked me for partition info. I made the root (/) the 20gb as planned. It then asked me for Linux Swap. Well I pointed to the rest of the E: drive. 

Did I just wipe out the 100GB of movies and family photos by makeing the remainder of this drive swap???

When booting back into Windows I dont even see the E:drive at all anymore. Partition Magic sees it as Linux Swap. Oh Help!!??

Thanks...........Steve

---

### Post by macogw on 2006-12-19
Yeah, I think that's what you did.  There are tools to recover lost data, though.  I can't name them, but Google can.

By the way, swap is virtual memory for when your ram just isn't enough.  You can have between 1 and 3 times the amount of memory you have.  I have 1gb of ram, so I have 2gb of swap.  It would be another partition that you add in to the end of the drive.

---

### Post by scrooge_74 on 2006-12-19
Sad to hear what you did , windows won't see any linux or swap partitions made under linux (windows don't like to play and share)

i hope you can recover the data or had some kind of backup

---

### Post by taurus on 2006-12-19
XP can access your ext2/ext3 with [http://www.fs-driver.org/](http://www.fs-driver.org/)...

---

### Post by steveOW on 2006-12-19
Thanks for the super quick responses!! 

Taurus! Thank you so much. Its all back with a click of a button!! 

Might be time to back-up me data!

Steve

---

### Post by scrooge_74 on 2006-12-19
> **taurus said:**
> XP can access your ext2/ext3 with [http://www.fs-driver.org/](http://www.fs-driver.org/)...

I just learn something new today :D

---

### Post by macogw on 2006-12-19
me too

I thought it would've formatted the swap and erased everything

---

### Post by lemonsCC on 2006-12-19
I think you need to tell it to erase all data...thats not the default as far as i know.

Lucky you....time to backup?

---

