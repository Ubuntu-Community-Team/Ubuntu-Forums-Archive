---
title: "[SOLVED] frustrated with new upgrade.  assistance appreciated!"
date: 2008-04-04
forum: Absolute Beginner Talk
---

### Post by kavmac on 2008-04-04
So, I went and bought that computer on Monday ([see here]("http://ubuntuforums.org/showthread.php?t=740363&highlight=radeon+x1200"))...  everything is great!  Until I went to do some updates yesterday and it told me it was having issues connecting. Fine.  I was also having issues with Mercury installing.  Fine.  So I had decided to do a fresh install of Gutsy.  Fine.  Need to backup my files I've transferred from my external hd.  Fine.  It's fine until I get to the last folder (which happens to be season 3 of Battle Star Galactica) - it hangs on Episode 19 of 20, and then freezes my whole computer!  So I did a hard reboot.  It freezes every time I try moving that folder completely.  It even froze last night when I was checking my email in firefox and transferring stuff.  Which I understood because my processor was busy with the file transfer.  So I left it over night transferring files... only to wake up this morning to have it tell me that there was 2+ hours left in the transfer - that was only to have taken 1hr max when I went to sleep!  And yes, it started to hang on Episode 19!  So I tried cancelling and it froze.  SO, with all this frustration, I decided to move the folder episode by episode, eventually going 2 at a time because I was tired of wasting 20 minutes on one folder.  It didn't freeze!  Also at one point last night I was checking my computer stats, and it told me that I only have 1.7GB of RAM, when I should have 2, and that my harddrive space is 288.4GB, when in reality I have a 320GB HDD.  I understand that root takes up 5%, but if my math serves me correctly, that should only be what, 16GB??  I want to do a memory check, and understand that I need to do the one with the live cd, but are there any other ones I should attempt?  I want to know whether this is a hardware issue, or just a crappy install on my part, since I only have about 10 days left before I'm stuck with this computer for good (gotta love the 14 day return policy).

So to recap incase I've confused anyone... What other suggestions for memory tests do you have?  And, any suggestions on where the rest of my harddrive space has gone to?

Computer specs as per Futureshop's website (because I can't remember how to check in terminal - mind blank):
Processor Type AMD Athlon 64 X2 4400+
Processor Speed 2.3GHz
RAM 2GB DDR2
Hard Drive 320GB SATA 7200RPM
Optical Drives 16X Dual-Layer DVD Burner
Graphics Card ATI Radeon X1200 Integrated
Available Expansion Bays 3 x 3.5", 1 x 5.25"
Available Expansion Slots PCI E x 16, PCI X1, 2 x 2 PCI 2.2
Cache 2 x 512KB L2
I/O Ports 8 x USB, VGA, FireWire (IEEE 1394)
Sound Card High Definition Audio

Thanks in advance!

---

### Post by mikewhatever on 2008-04-04
Can you please post the outputs of the following:
<free -t>
<df -h>

---

### Post by kavmac on 2008-04-04
```
kris@thebeast:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          1773        483       1289          0          7        223
-/+ buffers/cache:        252       1520
Swap:         5192          0       5192

```

and 

```
kris@thebeast:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             289G   94G  181G  35% /
varrun                887M   92K  887M   1% /var/run
varlock               887M     0  887M   0% /var/lock
udev                  887M  100K  887M   1% /dev
devshm                887M   16K  887M   1% /dev/shm
lrm                   887M   34M  853M   4% /lib/modules/2.6.22-14-generic/volatile

```

---

### Post by Teber on 2008-04-04
not sure about most of your problems.

however after formatting i would expect the capacity of your hard disk to be approx. 298 gb. total hard disk space would make sense then. the figure for ram may mean the amount of unused ram? the gurus could answer that one i'm sure.

for everything else: it could be hardware not really supporting ubuntu? or maybe something wrong with your file system? the experts are sure to give some hints.

edit: unsurprisingly an expert is already at it!

---

### Post by PantsMan on 2008-04-04
> **kavmac said:**
> So to recap incase I've confused anyone... What other suggestions for memory tests do you have?  And, any suggestions on where the rest of my harddrive space has gone to?

For memory testing, I always use Memtest86+ (Google will find it...) because it's information is nice and accurate, and it seems to be a little faster than Memtest86 (from which it was branched)

As for HD space, don't forget that HD manufacturers very rarely use binary bytes when quoting drive space, they all work to "decimal", 1,000 bytes=1KB, 1,000KB=1MB etc... In actuality, a 320GiB (GibiByte in drive manufacturer speak) drive will be equivalent to only 298GB, and the overheads of formatting on top can easily "lose" you the remaining space.

---

### Post by mikewhatever on 2008-04-04
Strange. It only sees 1773 MB of RAM and 289+5 GB of disk space.

---

### Post by kavmac on 2008-04-04
> **PantsMan said:**
> As for HD space, don't forget that HD manufacturers very rarely use binary bytes when quoting drive space, they all work to "decimal", 1,000 bytes=1KB, 1,000KB=1MB etc... In actuality, a 320GiB (GibiByte in drive manufacturer speak) drive will be equivalent to only 298GB, and the overheads of formatting on top can easily "lose" you the remaining space.

I figured something along those lines would happen... darn HD manufacturers!  So I guess that solves that *issue*...

---

### Post by kavmac on 2008-04-04
i downloaded Memtest86+ and just burned it onto CD... I'll run that... if I have time before I head off to work I'll let you know the results.  Thanks for the assistance so far!

---

### Post by mikewhatever on 2008-04-04
> **kavmac said:**
> i downloaded Memtest86+ and just burned it onto CD... I'll run that... if I have time before I head off to work I'll let you know the results.  Thanks for the assistance so far!

Memtest is on Ubuntu live cd, usually the third boot option.

---

### Post by PantsMan on 2008-04-04
> **mikewhatever said:**
> Memtest is on Ubuntu live cd, usually the third boot option.

If it's the same Memtest, I found it didn't detect recent hardware correctly... Anywho, they all do much the same thing - pop the disk in your CD drive, boot the machine and wait an hour or so... :)

---

### Post by kavmac on 2008-04-04
test went fine... but still only showing 1773 MB of RAM... so i'm gonna call it quits on this computer for the time being and talk to the crazy people at Futureshop while I still have time left to return it to them...  I'm not normally a quitter, but it's not the first time I've had computer issues with purchases from Futureshop... so if they can't figure out why I'm not getting my full 2GB worth, I'll just ask for my cash back and go to canadacomputers and build myself a better one.  Which is what I should've done in the first place... but I have to wait about a month before I can get down to one of their stores to take a look at some of their stuff...

Thanks for the help everyone!

---

### Post by PantsMan on 2008-04-04
> **kavmac said:**
> test went fine... but still only showing 1773 MB of RAM...

Memtest said you had 1,773MB as well? Duff chip on one of your sticks by the sound of it, and properly duff enough that it's not getting used at all (I've seen it on sticks I've bought for work... No memory errors but you're not getting as much as you should because one chip on a stick is "not there")

---

