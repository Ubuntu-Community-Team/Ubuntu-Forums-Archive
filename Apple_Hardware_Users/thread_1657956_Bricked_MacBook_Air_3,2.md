---
title: "Bricked MacBook Air 3,2"
date: 2011-01-01
forum: Apple Hardware Users
---

### Post by eyerouge on 2011-01-01
**Problem**
When powering up my Air-brick it instantly shows a white/grey screen of emptiness, at the same time as I hear the oh so loud chime. 


**What I had**
[LIST]
[*]Original and functional OS X that came with the crap
[*]Had installed a perfectly(?) working Ubuntu 10.10 (64) as well
[*]rEFIt was also installed and functional, allowing me to (auto)boot Ubuntu
[/LIST]


**What I have tried**
[LIST]
[*]Any and all key-combos when powering on the system seem to do exactly nothing. (I might have "forgotten" about some of them, please enlighten me.)
[*]Booting from the recovery USB stick that came with the Air seems to be impossible as nothing happens when I press the keys.
[*]Same goes for me to boot anything else or do anything on it.
[*]Resetting the SMC ([http://support.apple.com/kb/HT3964?viewlocale=en_US](http://support.apple.com/kb/HT3964?viewlocale=en_US)) did nothing.
[*]Supposedly resetting the two different RAMs also did nothing except make the annoying chime sound here on and ever after whenever I reboot the machine.
[/LIST]

**What to do..?**
This machine, all pimped up, costs a minor fortune. It's also my first Apple experience. Something tells me warranty won't help me if I tell the Apple-pluckers that I had Linux running on it and/or created a partition somewhere on the HD.

I also *refuse *to pay hundreds of Euros for troubleshooting and "repair" to some third party tech support (apple itself has no presence in my country) for stuff I could do on my own granted I had and could give relevant info. 

If anyone here comes up with anything that actually lets me do something that in the end allows me to do one or more of the following: 

a) boot what I had on it (osx or ubuntu)

b) reinstall osx from the USB stick that came with the Air 

c) do a clean install of Ubuntu

d) use clonezilla to restore the full hd with partitions and all (yes, a week ago I cloned it and have it tucked away in an external HD. I used clonezilla iso + apple external cdrom + external crap hd to create it)

e) make rEFIt and/or the built-in OSX(?) and/or EFI boot menu upon powering up the frakking thing appear

...I would be very grateful and buy you a jug of coffee given you take paypal.
 


**What seems to have caused this**
[LIST]
[*]From within Ubuntu I created a new partition (FAT32) by using GParted. I used only un-allocated space and didn't touch any existing partition in any way - no resizing, no nothing. Partitioning went fine (or so Ubuntu said.. I guess my brick says something else..)
[*]I, from within Ubuntu, dd'd Clonezilla stable to this new FAT32 partition.
[*]My intent was to be able to run Clonezilla from the computer by selecting it for booting in rEFIt, without using the external cdrom or USB. 
[/LIST]

---

### Post by wersdaluv on 2011-01-01
for the boot key combos that you might have forgotten, have you tried booting while holding "alt" with the Ubuntu CD and/or the Air recovery drive?

---

### Post by tgalati4 on 2011-01-01
That "unused" partition space may have in fact stored backup-partition table or boot information or other apple-proprietary stuff that gparted didn't recognize.

The fact that the emergency usb drive didn't work indicates perhaps some other issue--perhaps hardware-related.

If you didn't pay for apple-care, then you don't have much choice.  When you descend into the apple kingdom, you must be prepared to pay for your continued computing experience.

---

### Post by eyerouge on 2011-01-01
> **wersdaluv said:**
> for the boot key combos that you might have forgotten, have you tried booting while holding "alt" with the Ubuntu CD and/or the Air recovery drive?

Sadly, yes. :P 

I have tried ALT and also C with both CDROM (Ubuntu/Clonezilla) and also the rescue USB sent along with the Air.

---

### Post by beringse on 2011-01-02
[http://support.apple.com/kb/ht1343](http://support.apple.com/kb/ht1343) gives you a few more keyboard shortcuts for troubleshooting the start up. I suppose you don't have a superdrive/OSX install cd as you didn't mention it...

---

### Post by arabis on 2011-01-02
A few days ago, I had a similar experience but with a Imac 11,2.
Also, the problem was that my Imac suddenly shutdown an after didn't respond at all with the power-on button. It was 30 days after I bought my Imac. So I just went back to the AppleStore and tell them that my Imac suddenly shutdown and I was not able to put it on. The apple guy tried himself to put it on without success. I simply got on the spot a new Imac. But in my case, it was obvious that the problem was a hardware one.

---

### Post by sha.goyjo on 2011-01-03
At the risk of sounding immoral, feign ignorance. It is highly unlikely that your tech will care enough to yank the solid state drive out of system and examine it on a side cable. Especially not on an air, due to the absolute bitchiness of the disassembly process. But that's the route I usually take when I void my warranty with Linux: pretend you don't know cpu from a case from a monitor and make big doe eyes.

---

### Post by _mario_ on 2011-01-03
Hi,

some years ago, I had a similar problem: my MacBook Pro 4,1 (with rEFIt) refused to recognize the partition table and, hence, only presented a grey screen at bootup. no USB drives, no CD drives. nothing. although the drive physically worked. 

the problem was: while installing FreeBSD, I managed to create an MBR partition table inside a GPT partition (that was there to partition the whole disk). but as of the EFI specification (which also defines the GPT), nesting of partition tables is forbidden. hence, I conclude, that Apple's firmware just crashed/hung somehow.

the only solution was to put the disk into an external case attached to another machine via USB and erase the whole offending partition. since, you 'played' with partitions, you might have created a similar setup.

ciao,
Mario

---

### Post by srs5694 on 2011-01-03
I'm afraid I don't have any easy solution for the original poster; however, I do have some comments, and one not-so-easy suggestion....

> **tgalati4 said:**
> That "unused" partition space may have in fact stored backup-partition table or boot information or other apple-proprietary stuff that gparted didn't recognize.

That's unlikely. GParted is fully GPT-aware, so it wouldn't be abusing a GPT disk in this way, at least not unless a rather severe bug was involved. To the best of my knowledge, Apple doesn't store stuff in unallocated disk space on GPT disks, although their [Tech Note TN2166](http://developer.apple.com/library/mac/#technotes/tn2006/tn2166.html) implies they reserve the right to do so on a *temporary* basis (for disk partitioning tools to use when moving/resizing partitions, say).

[quote=sha.goyjo]But that's the route I usually take when I void my warranty with Linux:  pretend you don't know cpu from a case from a monitor and make big doe  eyes.[/quote]

There was a thread here a few months ago about Apple's warranty and Linux. As I recall from that discussion, there's nothing in the warranty terms that forbids installing Linux on a Mac. Thus, in theory there's no need for the doe eyes. In practice, of course, you could run into some jerk at the store who refuses to honor the warranty, and it's even conceivable that Apple would back up such an employee.

[quote=_mario_]the problem was: while installing FreeBSD, I managed to create an MBR  partition table inside a GPT partition (that was there to partition the  whole disk). but as of the EFI specification (which also defines the  GPT), nesting of partition tables is forbidden. hence, I conclude, that  Apple's firmware just crashed/hung somehow.[/quote]

It's entirely believable that Mac's EFI implementation is broken in such a way as to do as you report; however, the EFI spec does *not* forbid nesting an MBR partition table inside a GPT partition. It *does* forbid nesting a GUID Partition Table within a GPT partition, though. In fact, there's a GUID code ("MBR Partition Scheme", 024DEE41-33E7-11D3-9D69-0008C781F39F) expressly for nesting MBR data in this way. There's also a proposal to use this as a workaround for booting GPT-unaware OSes on GPT disks; use a modified boot loader to point the OS at the sector of the hard disk where the MBR data begins and away you go. (To the best of my knowledge, nobody's written a working boot loader that uses this system.)

Now, to my suggestion: If the problem is in fact due to partition table damage of some sort, it should be possible to repair it by removing the disk from the computer and fixing it using another computer -- say, a regular PC running Ubuntu or some emergency Linux system. You could use GParted or gdisk to examine the data structures and fix anything that's damaged. The trouble would be in removing the disk from the computer -- and that probably *would* void the warranty, if it's still in place.

---

### Post by dcow90 on 2011-01-06
I have pretty much the exact same problem.  Also, I would like to note that srs5694 is correct on all three points. 

I have ruined my partition tables in such a way that Apple's EFI is not able to load anything.. not even boot from a CD.  Similar things happen on boot however, I am able to get to a "No-Sign" logo when booting into the OSX partiton.  When I boot into Windows, it just hangs black.  It does not recognize my Linux partitions -- which is to be expected considering what I did.  However, I have rEFIt installed which loads fine (sort-of).  

My question is, is there any way I can repair the partition table using the EFI shell which I CAN load from rEFIt?  I'm using a Macbook 5,1 so pulling the HDD is not a problem, it's just I do not have to proper tools with me to connect it to a PC right now.  

Also, if anyone can help me figure out what exactly when wrong I would love to learn.  If you're willing to help I can explain in more detail.. it's pretty crazy..

dcow

---

