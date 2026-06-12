---
title: "Which filesystem for an external? Read + Write for Linux and OS X"
date: 2010-11-30
forum: Apple Hardware Users
---

### Post by kaldor on 2010-11-30
My external hard drive is currently on NTFS. No issues with this for Linux, but on OS X it is read only.

What would be the best filesystem for me to use for read/write on both OS X and Linux distros?

I use Ubuntu, Debian, Fedora and OS X 10.6.5

Thanks :)

---

### Post by DoubleClicker on 2010-12-01
first of all there are no open source solutions that enable any journaled file system to be writable in both OS's.   So you will have to decided, whether open source or journaling is more important to you.     

If you decided you must have open source drivers: the only reliable option is HFS+,  But be aware, that, by turning off journalling, you risk losing data in a crash.  You will also likely have to go through a long fsck, every time you return to OS X, after booting Linux.   


Is you are willing to go with proprietary drivers,  [Paragon]("http://www.paragon-software.com/home/extfs-mac/") makes EXT(2/3/4), HFSPlus, and NTFS drivers for both platforms, which support journaled writes.   I've used the EXTFS driver and it is slow on large partitions, I'm about start testing the HFS+ driver for Linux to see how well it performs.

---

### Post by MisterGaribaldi on 2010-12-01
Or, you could just [go to this web page](http://macntfs-3g.blogspot.com/) and download NTFS read/write support components for Mac OS X and call it good.

---

### Post by kaldor on 2010-12-01
> **MisterGaribaldi said:**
> Or, you could just [go to this web page](http://macntfs-3g.blogspot.com/) and download NTFS read/write support components for Mac OS X and call it good.

Thanks; I will try this out asap.

That's what I thought about HFS+ though. I was going to try it out, but the non-journaling bit bothered me.

---

### Post by MisterGaribaldi on 2010-12-01
It's very frustrating that Apple seems to have these sort of spotty turf war-type problems with others. I really don't understand why that is. Microsoft, the king of being closed and proprietary, has never had a problem with Linux having full read/write support for FAT16 or FAT32, which it's had for so long probably nobody remembers a time when it didn't exist. And a few years ago when the community finally got full read/write support for NTFS, Microsoft never did anything to stop that. And frankly, NTFS was designed mostly with having a secure, UNIX-like privileges management ability (in addition to other things like large file (>2.1GB) support, support for larger partitions, etc.) and Apple can make really none of those claims (well, large file and large partition support yes, but security no) with HFS+ or HFS+ Journaled.

So, what's Apple's excuse really? I have no idea.

---

### Post by conundrumx on 2010-12-02
> **MisterGaribaldi said:**
> It's very frustrating that Apple seems to have these sort of spotty turf war-type problems with others. I really don't understand why that is. Microsoft, the king of being closed and proprietary, has never had a problem with Linux having full read/write support for FAT16 or FAT32, which it's had for so long probably nobody remembers a time when it didn't exist. And a few years ago when the community finally got full read/write support for NTFS, Microsoft never did anything to stop that. And frankly, NTFS was designed mostly with having a secure, UNIX-like privileges management ability (in addition to other things like large file (>2.1GB) support, support for larger partitions, etc.) and Apple can make really none of those claims (well, large file and large partition support yes, but security no) with HFS+ or HFS+ Journaled.

So, what's Apple's excuse really? I have no idea.

What the hell are you talking about?  Apple isn't running around suing and threatening people who make HFS+ drivers.  As far as Microsoft and FAT - [they sued TomTom over Linux's implementation of FAT32 less than two years ago.]("http://en.wikipedia.org/wiki/File_Allocation_Table#Patent_infringement_lawsuits")

---

### Post by MisterGaribaldi on 2010-12-02
conundrumx: whoa, dude, calm down! I never said anything of the kind.

I'm simply saying that Apple has been restrictive and/or not as forthcoming with data to make some things more supported (sound cards on older Macs, HFS+ Journaling, FS access on iPods / iPod Touches / iPhones / etc. And MS sued TomTom? Huh, I didn't know about that.

---

### Post by srs5694 on 2010-12-02
> **MisterGaribaldi said:**
> Or, you could just [go to this web page]("http://macntfs-3g.blogspot.com/") and download NTFS read/write support components for Mac OS X and call it good.

I recommend against this approach. The problem is that, although you can get the read/write support for NTFS in both OS X and Linux, you cannot (AFAIK) get NTFS maintenance tools in either OS. Thus, when (note "when," not "if") your system crashes, the power goes out, or the cat unplugs the external disk from your computer while it's still mounted, it will be left in an unclean state, and it's likely that neither of your OSes will mount it any more. You'll then have to cart the disk over to a Windows system and use it to repair the disk, or boot a Windows emergency disc on the computer to repair the hard disk. Murphy's Law guarantees that this will happen at the least convenient time possible.

HFS+, OTOH, can obviously be checked in OS X. Using the non-journaled variety means that the disk check will most likely take a while, but it will at least be possible. IMHO, for a shared Linux/OS X disk, this makes HFS+ a far superior solution to NTFS.

There are also ext2/3 drivers for OS X, although I don't know much about them. It's possible they aren't reliable enough to trust, but you might want to look into them.

---

### Post by conundrumx on 2010-12-03
> **MisterGaribaldi said:**
> conundrumx: whoa, dude, calm down! I never said anything of the kind.

I'm simply saying that Apple has been restrictive and/or not as forthcoming with data to make some things more supported (sound cards on older Macs, HFS+ Journaling, FS access on iPods / iPod Touches / iPhones / etc. And MS sued TomTom? Huh, I didn't know about that.

Everyone always thinks I'm angry, I have no idea why.  D:  Apple have certainly been bastards about iPod/iPhone syncing, but it's a big source of revenue for them.  As far as open source drivers?  I can't imagine why Apple would devote any energy to documenting or helping in the production of drivers for their hardware for Linux.  OSX is a UNIX, so except for people who are extremely attached to a particular Linux distro there's no practical reason to run Linux on a Mac.  They do write and support Windows drivers for their stuff.

> **srs5694 said:**
> There are also ext2/3 drivers for OS X, although I don't know much about them. It's possible they aren't reliable enough to trust, but you might want to look into them.

ext2 on the Mac works fine, but fuse-ext2 is still 32 bit only.  It can read ext3, but like HFS+ on Linux there's no journaling support.  So the choices are ext2 or HFS+ with no journaling (which is deprecated, IIRC).

---

### Post by logandzwon on 2010-12-03
OP; if you want compatibility use FUSE-3g with NTFS+ for a volume you wanted shared cross platform. Keep in mind performance-wise it'll be the slowest and you will a bunch of features, (specifically NTFS does not support posix permissions, only MS ACLs.) It was designed for a completely foreign on-*NIX OS after all.  See wiki for more; [http://en.wikipedia.org/wiki/NTFS-3G](http://en.wikipedia.org/wiki/NTFS-3G)

Back the on-going flame-war... 
  Historicly MS sued and blocked everyone from NTFS developmental for as long as they could. They held back ANY info about the FS and would make changes every OS and service pack revision to try to prevent reverse assembly. Modern day MS does not seem to really care anymore.
  HFS+ is written by Apple for Mac. It is an FS designed for a UNIX OS. It fully supports both standard posix permissions and extended ACLs, (similar to NTFS.) Apple never really seemed cared one way or the other if anyone reverse engineered it, however there really hasn't been to much movement in the open source camps to do so. There are commercial implementations for it though.

Also, most journaled FSes can be mounted non-journaled, but they will need fsck apoun remount. You probably do not want to fsck every single reboot.

---

### Post by MisterGaribaldi on 2010-12-03
I have no issues with having a 500GB NTFS partition going in Linux, but then again this box is dual-booted with Seven so it presumably does maintenance and I'm just not noticing it.

I'm not really into flame wars and arguing with people on the Internet. You folks want to do that, go right ahead.

---

### Post by srs5694 on 2010-12-06
> **MisterGaribaldi said:**
> I have no issues with having a 500GB NTFS partition going in Linux, but then again this box is dual-booted with Seven so it presumably does maintenance and I'm just not noticing it.

The problem isn't with normal day-to-day operation; it's when something goes wrong -- when you suffer a system crash, a power failure, or some other unexpected shutdown or disconnection of the drive from the computer. When that happens, the filesystem will be in an inconsistent state and will require maintenance. Without maintenance, Linux and OS X will almost certainly refuse to mount the partition. Since neither Linux nor OS X includes any NTFS maintenance tools that can help, the disk will have to be moved to a Windows system, or Windows will have to be booted on the computer in question. (Note that there is a Linux NTFS maintenance tool, but it just does very basic checks and then flags the disk as requiring a full check, which can only be done in Windows.)

Thus, using NTFS on a computer that dual boots Linux and OS X will work, but only until one of those events that necessitates NTFS maintenance occurs. At that time, it'll be a nuissance to get it fixed. If the system triple-boots with Windows, this isn't as much of a problem, but for a Windows-less computer, IMHO, NTFS is a poor choice for a shared filesystem. FAT, HFS, and HFS+ are all better choices (although FAT and HFS are both old and have problems that make them unsuitable for many purposes). Ext2fs or ext3fs might work, too, but I'm not sure of the state of OS X driver support for them.

---

### Post by MisterGaribaldi on 2010-12-07
Yeah, but the problem with that is the drivers for ext2/3 support for Mac OS X are seriously out of date. They were written for Tiger and, afaik, no longer work with Snow Leopard (and may or may not work with Leopard).
 
I understand the issue about getting an inconsistency problem on an NTFS disk, but at least MacFUSE and NTFS 3G support are maintained and current for Tiger - Snow Leopard. That's a far better option, for obvious compatibility reasons, than going with HFS+ or ext2/3.
 
I handle this two ways. First off, most of the media I deal with are FAT32-formatted flash drives. Secondly, I run a private file server in my house where I can move data back and forth between computers (or off-load and then later reload onto the same computer) and I don't have to care what type of FS is on the other end.
 
Filesystems are truly the last hold-out when it comes to true inter-OS-operability. Frankly, the best one can do is the best one can do, and there is no true universal answer to this whole discussion.

---

### Post by pindar on 2010-12-07
> **MisterGaribaldi said:**
> Yeah, but the problem with that is the drivers for ext2/3 support for Mac OS X are seriously out of date. They were written for Tiger and, afaik, no longer work with Snow Leopard (and may or may not work with Leopard).

The fuse-ext2 drivers for macfuse work perfectly under Snow Leopard; I use them quite a lot. With my setup, I only need read access from the other side, so I have never had any trouble with the combination hfs+/ext4. And I find it reassuring that the volume of the other OS are mounted ro; this means they can't be messed up.

---

### Post by srs5694 on 2010-12-07
> **MisterGaribaldi said:**
> I understand the issue about getting an inconsistency problem on an NTFS disk, but at least MacFUSE and NTFS 3G support are maintained and current for Tiger - Snow Leopard. That's a far better option, for obvious compatibility reasons, than going with HFS+ or ext2/3.

I can understand your point with respect to ext2/3, but there's nothing obvious to me about recommending NTFS over HFS+ for a Linux/OS X dual-boot computer. Linux's non-journaled HFS+ support is quite good, and on a Linux/OS X dual-boot computer, you'll at least be able to perform a filesystem check on the disk should the need arise. As I've written, with NTFS, that will be a nuissance at best, which makes NTFS a risky proposition. There's also the fact that HFS+ supports all the usual Unix-style filesystem features (ownership, permissions, symbolic links, etc.), which NTFS does not.

---

### Post by MisterGaribaldi on 2010-12-07
> **srs5694 said:**
> I can understand your point with respect to ext2/3, but there's nothing obvious to me about recommending NTFS over HFS+ for a Linux/OS X dual-boot computer.

Well, sure. But that doesn't necessarily describe the situation for everyone nor necessarily the OP's situation now or at some point in the future.

One ought never to assume there will be adequate support for non-Microsoft filesystems on any random computer you will or might need to use. It's unfortunate and I acknowledge that, but you have to look at things from a more open-ended standpoint. Arbitrary assumptions are what lead to straight-jacket situations down the road. It's bad strategy.

---

### Post by srs5694 on 2010-12-07
We'll just have to agree to disagree, then. You can't make assumptions about support for *Microsoft* filesystems, either. Until recently, Linux's NTFS support was pretty poor. Although NTFS-3g works on several platforms, there's no more guarantee that it'll work on some future OS the OP might need than there is a guarantee that HFS+ will work on such a platform.

*For right now*, IMHO HFS+ is a better choice for the OP, who uses Linux and OS X but not Windows. Could that change in the future? Of course; but data can be transferred to a new filesystem if one's needs change. That's a bit of an inconvenience, not a straight-jacket. In the meantime, IMHO it's appropriate to use the tool that best fits one's *current* needs, and the lack of Linux or OS X tools to deal with NTFS issues makes NTFS a poor choice for use in a Linux/OS X dual-boot environment.

---

