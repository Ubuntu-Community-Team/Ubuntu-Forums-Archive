---
title: "Unable to boot from liveCD (MBP)"
date: 2010-09-21
forum: Apple Hardware Users
---

### Post by khronoslynx on 2010-09-21
Hello all.
I have a MacBook Pro 6,2 that try as I might refuses to boot from live CDs. I have rEFIt installed, and _both_ of the liveCDs I've burnt for 10.10 (32 and 64 bit) do not show up either in rEFIt or when I hold down "option" as my mac boots.

Both CDs will run perfectly as either liveCDs or Installations in Parallels, but I'm looking to (hopefully) someday replace Mac OS entirely with Ubuntu. Being completely unable to see these liveCDs presents a bit of a problem though..

Anybody have any advice at all, or ideas on what I may be doing wrong?

Thanks!

---

### Post by NoBugs! on 2010-09-22
It's probably related to [this problem]("http://ubuntuforums.org/showthread.php?t=1090160"), sometimes the only way to boot from cd is to go into the startup settings in mac os :(

---

### Post by khronoslynx on 2010-09-22
That worked like a charm, thank you very much!
Currently replying from my brand new Ubuntu installation haha.

---

### Post by cliffordstoll on 2010-09-23
Hi No bug.... Thanks for the solution... I had the same problem and was just going to make a thread... but you just solved my problem here...:)

---

### Post by NoBugs! on 2010-09-24
Someone should try to find what settings Mac OS is setting to make it boot from the cd. What if Mac OS was deleted from the disk, how would you boot a livecd? It would be great to have this ability in refit or some other tool...

---

### Post by cpsquire on 2010-12-01
The startup disk fix doesn't work for me (Macbook 4,1). The CD shows as bootable and spins up, returning a "Missing operating system" error and a cursor as the CD spins down again. The CD boots on a PC, so I am sure that it is a bootable disk. rEFIt and the Apple startup manager return the same error.

---

