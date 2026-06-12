---
title: "defrag"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by troughton on 2006-08-29
can some one tell me how i can defrag my drives on linux please ??

---

### Post by aran384 on 2006-08-29
u mean defraging linux hdd??? or a windows one??? cause i dont think linux hdds need defraging far as i know anyways

---

### Post by troughton on 2006-08-29
i meen linux hda i dont have windows anymore and yes my linux drive need defraging i have just run a system check and it said it needed defraging

---

### Post by xyz on 2006-08-29
No need to defrag; think about all the time you'll save!
It's just that GNU/Linux puts things back where they belong right away therefore no need to defrag to put things back in order.
For more read [b]ajgreeny's Avatar  	
ajgreeny[/b] here:
[http://www.ubuntuforums.org/showthread.php?t=218495](http://www.ubuntuforums.org/showthread.php?t=218495)

---

### Post by jdong on 2006-08-29
Linux filesystems do not need to be , nor do they benefit from, defragmenting.

---

### Post by justin whitaker on 2006-08-29
> **troughton said:**
> can some one tell me how i can defrag my drives on linux please ??

On windows, the system gets fragmented because the storage routine is crap. On Linux, you do not have that issue: the system is journaled, and the storage routine is optimized.

You may be thinking that you can save space, or increase performance, by defragging your system. 

For that, hdparm will allow you to change how your system uses your HD, cruft will get rid of everything that deborphan cannot, and make sure that you have DMA on.

---

### Post by Metacarpal on 2006-08-29
> **troughton said:**
> i meen linux hda i dont have windows anymore and yes my linux drive need defraging i have just run a system check and it said it needed defraging

What system check did you run, and what was the exact message that told you that you needed to defrag?

Also, are you doing bittorrent downloads?  If so, that might be the fragmentation your system is detecting.

---

### Post by jdong on 2006-08-29
I should add, to my previous statement, an exception, now that metacarpal reminded me. The default Ubuntu filesystem ("ext3") will fragment large (>1GB), slowly-growing files (<1MB/s) . Such files include torrents or huge downloads. You may notice it when trying to burn the files onto a DVD, when the burn process has to slow down because it cannot read the file fast enough to keep up. However, the rest of your system will **not** be affected by these fragmented files (for example, Openoffice won't start slower because you have a fragmented DVD ISO on the drive).

For the most part, this is not enough to bother people, but if you are a heavy torrenter/downloader, it could be enough to bug you. If that's the case, you can first try turning on your torrenting program's "preallocation" feature, which quickly creates an empty file the size of your torrent. This will cut down greatly on fragmentation. If that's not enough, you may want to consider using a different filesystem. XFS is the king of performance in this regards, but because of its aggressiveness you'd want to make sure you don't suffer from too many improper shutdowns/resets.

---

### Post by kinematic on 2006-08-29
if linux filesystems don't need to be defragged jdong then why did you create a linux defragger ;) 
[http://www.ubuntuforums.org/showthread.php?t=169551&highlight=pyfragtools](http://www.ubuntuforums.org/showthread.php?t=169551&highlight=pyfragtools)

---

### Post by jdong on 2006-08-29
It was an experiment, designed to address the bittorrent issue I described above. The theory was, by recreating the file quickly, the filesystem would find better locations and optimize the placement of such files.

The results? I'd say pyfragtools is an overall **failed** experiment, and I do **not recommend** people to use it.


True, it is capable of defragging those large fragmented files, but in the process it stresses the filesystem so much that it makes future write performance suffer even more!

---

### Post by justin whitaker on 2006-08-29
On Freshmeat today:

[http://vleu.net/shake/](http://vleu.net/shake/)

This is not an endorsement, of course. ;)

---

### Post by jdong on 2006-08-29
shake's defragmentation algorithm is virtually identical to pyfragtools/xfs_fsr/defrag.... Again, the same warning I gave above applies -- unless you're using XFS, you'll probably degrade performance. And, if you're using XFS, you'd feel safer running xfs_fsr.

---

### Post by kinematic on 2006-08-29
well yeah i knew it wouldn't help much if any but others may not so maybe it's better to delete that post and prevent n00bs from d'loading it ;)

---

### Post by 3rdalbum on 2006-08-29
I was wondering what happened to pyfragtools... lucky I never ran it on my old machine, it already suffers bad enough performance!

---

### Post by jdong on 2006-08-29
To supplement my previous statements about torrenting performance, here's some non-scientific anecdotal data. Of course, it's not useful for an apple-to-apple comparison but comparing an apple to an orange can still lead to some level of insight :)


Between yesterday and today, I torrented two files on the same system, using the same software setup, same hard drive. Yesterday was a Ubuntu Dapper DVD. Today was a FC6T2 DVD. Both are roughly the same size. Between the two downloads, I switched from ext3 to XFS, by rsyncing the drive to a 2nd computer and rsyncing it back, so again, identical setup. pyfragtools and k3b were used to collect statistical data.

Initial fragmentation:

Ubuntu ISO on ext3: 15.5frags/MB
Fedora ISO on XFS: 2.47frags/MB


Average burn speed to DVD via k3b, speed set at 16x:

Ubuntu ISO on ext3: 5.33x (HD constantly grinding, light constantly on)
Fedora ISO on XFS: 8.50x (HD not grinding, light blinking about once per second)



In this case, there was a clear difference between how ext3 and XFS stored the files on the hard drive. In fact, ext3 fragmented this file enough that I saw the effects in burning the ISO, though it was bearable and not fatal by any means. I had plenty (50GB) of free space left on the drive in both cases. Note that my burner is not exactly the best of the breed, and does not attain the 16x (it starts at 2x, then jumps to 8x, then jumps to 10x, and so on), but my observation is that ext3 was a bottleneck in burning this ISO.

Just more anecdotal info, pyfragtools was able to defragment the ext3 ISO to <.50frags/MB after about 5 passes, after which the file read back at abundant speed (reboot in between to clear disk cache, of course). xfs_fsr reduced the file to no excess fragments after one pass.

---

### Post by shanepardue on 2006-08-29
> you can first try turning on your torrenting program's "preallocation" feature

any idea what this is called in azureus? i wasn't able to find that feature.

---

### Post by Metacarpal on 2006-08-30
Quick question regarding torrents and fragmentation:

If one downloaded a file via bittorrent (for sake of arguement, onto a ext3-formatted drive), and it became fragmented, then they made a COPY of the same file (presuming one has space), then DELETED the original, would that not solve the fragmentation without need for an external defragmentation program?

Then, of course, turning on preallocation would prevent it from happening in the future. ;)

---

### Post by jdong on 2006-08-30
> **Metacarpal said:**
> Quick question regarding torrents and fragmentation:

If one downloaded a file via bittorrent (for sake of arguement, onto a ext3-formatted drive), and it became fragmented, then they made a COPY of the same file (presuming one has space), then DELETED the original, would that not solve the fragmentation without need for an external defragmentation program?


That is exactly how these "external defragmentation" programs work, but they automate the process. Sometimes it takes quite a few copies to unfragment them. Note that, as warned earlier, you could fragment your freespace if you do this enough that it actually degrades future performance.

---

### Post by LKRaider on 2006-08-30
A way to defrag the whole drive is to tar the filesystem to another partition, delete the original and restore the tar back.

---

### Post by Metacarpal on 2006-08-30
> **jdong said:**
> That is exactly how these "external defragmentation" programs work, but they automate the process. Sometimes it takes quite a few copies to unfragment them. Note that, as warned earlier, you could fragment your freespace if you do this enough that it actually degrades future performance.

Not that I really have much to worry about there anyway... with the [wireless torrent freeze-up bug]("https://launchpad.net/distros/ubuntu/+bug/46845"), I pretty much stay off the torrents anyway.

---

### Post by troughton on 2006-08-30
so in answer to my question i dont need to defrag is what you are saying i think can you tell me how to force check my system insted of wating every thiry mounts to do it as my computer is only swiched off once a month or so

---

### Post by jdong on 2006-08-30
**shutdown -F -r now** will force the check on next reboot, then reboot your system.

---

### Post by tribaal on 2006-08-30
**EDIT:** Dont' use this method, it's really a dirty hack. :)

Being a big torrent downloader (nobody's perfect, heh?), I had to come up with a solution for my fragmentation problem (shutdown -fr now showed me over 50% on my storage partition).

What I did was the following:
Got to your local used hardware store, and get a used HDD (something like 20 gigs, theses come very cheap in Switzerland, I guess it's the same everywhere).

Plug it in you PC, format to ext3 and mount.

Then during the night (the process is slow), turn off bittorrent for a change, and run a script that will copy all of your fragmented torrents to you "new" disk, delete the original, and then copy back the file to where it was.

It's slow, but it works great. After such a run, my defrag comes down from over 50% to less than 2%. And 2% is really really not noticeable. :)

The whole process cost me a whole 15CHF (around 10 dollars), and I'm not even sure it's really slower than "traditional" defrag :)

- trib'

---

### Post by jdong on 2006-08-30
Why not install XFS on that torrenting drive?

---

### Post by tribaal on 2006-08-30
> Why not install XFS on that torrenting drive?

Two honest answers:

1. Because I didn't think before I bought that cheap drive
2. Because I like doing things in a suboptimal way

Nah, because I didn't think of it at the time, really. :)
Edit: and now my drive is too full to change the filesystem without loosing data in the process (don't have a temporary storage space large enough, and I'm too lazy to free up some space, resize, change the filesystem, put the data back in, and repeat) :)

- trib'

---

### Post by Sef on 2006-08-30
Reifersfs does not have this problem.  Ext3 will set an initial limit and if the file goes over it will fragment the file. Reifers will simply expand the file size.

---

### Post by jdong on 2006-08-30
> **Sef said:**
> Reifersfs does not have this problem.  Ext3 will set an initial limit and if the file goes over it will fragment the file. Reifers will simply expand the file size.

My gripes with reiserfs are:

(1) It fragments even worse than ext3 on large files... That's one of the key observations I made while writing pyfragtools (our 3 dev laptops were xfs, ext3, and reiserfs, all rsynced with identical data)

(2) during periods of heavy metadata activity, it brings the rest of the system to a standstill. This really hurts multitasking responsiveness

(3) Performance degrades over time. When you start with a fresh reiserfs setup, it feels snappy and great. A few months later, it'll slow down to the point that you feel the difference by reformatting and restoring the data.

(4) the reiserfsck tool is utterly useless. If bad luck ever strikes you, don't expect the repair tool to help you out in any fashion.

---

### Post by Toxicity999 on 2006-08-30
Semi-Off topic... there have actually been some commercial Linux Defragging programs... it was funny to watch them spin down the hole :). Atleast as far as I remember I saw an article about some mainly windows corp. coming up with one... idiotic if you ask me. Theres not much use unless you manually screw with how the storage routines run. I still stick by the idea that windows allows all this stuff to stay around just for the huge market in windows repairing apps. ;)

---

