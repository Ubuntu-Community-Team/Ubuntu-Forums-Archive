---
title: "Which ISO do I need? Confused"
date: 2006-09-21
forum: Absolute Beginner Talk
---

### Post by jamesr316 on 2006-09-21
OK. I have a computer that I built a while ago. The motherboard is an ECS P4M800-M7. The box says it supports LGA 775 CPUs. I believe (its been forever) that there is a 3.0 or 3.2 Ghz cpu w/ 800 Mhz fsb in there. I don't think this is a 64 bit chip, but I honestly have no idea. 

I downloaded the dapper server x86 release, and it took forever to install. Upon restarting, loading of the hardware drivers failed, it continued to load up but ran extremely slow, like windows 3.1 slow. When I retsarted again it gave me an error about no buffer space available. Did I install the right version? Is there a 64 bit version for intel 64 bit chips (if that is what i have)?

Before trying the server release, I tried the regular desktop x86 release, it took a while to load up, and when i tried to use the install wizard on the desktop, the application kept crashing. 

Any help would be appreciated.

James

---

### Post by mbgb14 on 2006-09-21
Thats odd. It shouldn't be a problem. Even if you DO have a 64bit chip, then the 32 bit version will ALWAYS work on it (it falls back).

---

### Post by bodhi.zazen on 2006-09-21
Did you check the obvious ? MD5 sum of download. Check MD5 sum on disk after burn.

---

### Post by jamesr316 on 2006-09-21
Yea, that is what I thought. I never had a problem running windows on this machine before. I wanted to make this an ubuntu box.

---

### Post by jamesr316 on 2006-09-21
I did check the sum. I check on all cds that i download.

---

### Post by wpshooter on 2006-09-21
With that hardware the install should go rip roaring fast.

Something else has to be at play here.

Are you checking the integrity of the burned CD with the verfication process on the initial boot screen menu ?

---

### Post by jamesr316 on 2006-09-21
I checked all cds i the computer i burned them on. When I check the integrity of the cd on the box i want to be an ubunut box, it takes a long time to boot the kernel, and probably shouldn't.

---

### Post by jamesr316 on 2006-09-21
it is still checking...Detecting hardware taking a while, still on 0%. I don;t understand, a decent cpu, 2 GB of RAM, no extra cards just the mobo. Is it possible ubunut doesn't work with this mobo?

---

### Post by wpshooter on 2006-09-21
Was there some previous O/S installed on this computer ?

---

### Post by bodhi.zazen on 2006-09-21
Yes it is possible. I asume you CD is in working order. Do other distro's boot? Try knoppix it has good hardware detection.

---

### Post by jamesr316 on 2006-09-21
wp- there was win2k, winxp, and windows 2k3 server on this machine prior to reformatting. 

i guess i will have to try another distro :/

---

### Post by wpshooter on 2006-09-21
Go to this website and download Killdisk program and WIPE the drive clean and then retry installing Ubuntu.  Make sure the first thing you do when booting to the Ubuntu CD is to run the verification of the CD from the initial boot screen menu.

[http://www.killdisk.com/](http://www.killdisk.com/)

Good luck.

---

### Post by Sentinel83 on 2006-09-21
[FONT="Arial"]Have you tried to boot the livecd or install in safe graphics mode?  I have a pretty powerful machine that took forever to boot up because it would continually pause reading the drives as it booted (my CDRW).  Now sure why booting in safe graphics mode helped, but it sped up the process.  After the install, the machine was back to normal speed...
[/FONT]

---

### Post by NordicRX8 on 2006-09-21
First of all...
Ewwwww! ECS! :-&   I've had more problems with ECS based systems than any other.  Which is probably why I like to peddle ABIT, ASUS and DFI, or the good ole Intel motherboards.

Is your system overclocked/overvolted/undervolted? (CPU, RAM, etc..)

Does this ECS board support more than one "type" of memory (SIMM, DIMM, DDR) and does it have an AGP as well as PCI-X slot?


Sorry for all the questions, but the "obvious" has already been ruled out.  Checksum for the ISO, checksum on the recorded CD, correct iso version... wait actually... 
you mentioned that the downloaded the "server x86" version.   Was there a reason you didn't download the desktop x86 version (by the way, you do NOT have a 64bit CPU)?  Have you tried the "alternate x86" version yet?

If you boot with the desktop version, it shouldn't matter WHAT OS/file systems are on your hard drive (unless there is something terribly screwed up with the partitions), since it's a LIVE CD and everything is being loaded into memory.  

Unfortunately, you could be right regarding your motherboard.  ECS is a "no frills", lower tier manufactured motherboard... it may have enough quirks in its BIOS/design, that may not allow the kernel to load.  Is there a more current BIOS available for your particular model????  Maybe that'll help.

Good Luck

---

