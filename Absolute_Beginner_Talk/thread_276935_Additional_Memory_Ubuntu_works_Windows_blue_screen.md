---
title: "Additional Memory Ubuntu works Windows blue screen"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by DOD1951 on 2006-10-13
The other day I added another 512MB DDR memory stick to my desktop. Ubuntu, as usual, dealt with this no problem. When I booted into Windows XP after a period of time, varies, it crashes with blue screen. The only change I made is to the memory. Is it likely that Ubuntu is dealing with possible faulty memory and Windows XP is not? Also am I right is assuming that anything I do on Ubuntu has no affect on Windows XP apart from the grub of course?

---

### Post by meng on 2006-10-13
Wow, Ubuntu wins again! :) You could always run a memtest to see if you have faulty RAM. What you do on Ubuntu shouldn't affect the XP installation, unless of course you wipe a partition or something.

---

### Post by JayTee on 2006-10-13
Windows is VERY unforgiving of memory problems. I'm making some assumptions here. The memory you added EXACTLY matches the existing memory for speed and CAS latency? If you have a dual channel motherboard you might need to change how your memory is arranged. Like the previous post said, you can run the memtest boot option from GRUB and if it doesn't find anything then you most likely have some corruption in Windows. How much RAM did your system have to start with? From a terminal type cat /proc/meminfo then copy and paste the results in a reply posting.

---

### Post by orb9220 on 2006-10-13
If the BSOD code says something like corrupt PFN_List then it is bad ram which memtest will show. Also be sure of Matching ram same size,latency,etc...

---

### Post by DOD1951 on 2006-10-13
Results of cat /proc/meminfo
Total:      1036136 kB
MemFree:        510868 kB
Buffers:         11088 kB
Cached:         307560 kB
SwapCached:          0 kB
Active:         266232 kB
Inactive:       223284 kB
HighTotal:      131056 kB
HighFree:          164 kB
LowTotal:       905080 kB
LowFree:        510704 kB
SwapTotal:     1510068 kB
SwapFree:      1510068 kB
Dirty:             772 kB
Writeback:           0 kB
Mapped:         235732 kB
Slab:            18492 kB
CommitLimit:   2028136 kB
Committed_AS:   638872 kB
PageTables:       1928 kB
VmallocTotal:   114680 kB
VmallocUsed:     11552 kB
VmallocChunk:   102540 kB

Tried memtest 1G and everything blew up :-? Screen went black then I hit ctrl+alt+bkspace but was told desktop already running so quiting which brought back blank screen. So I guess I have either bad memory stick or incompatibility between both sticks. I had 512MB to start with and thought it would be better to have 1GB as most times I only had about 6Mb left when using system with 512Mb memeory. Probably too many things open.

---

### Post by Hairyred on 2006-10-15
I had a similar problem with windoze with my previous pc. Swapping the sticks around solved it for me. I was using slots 1 and 3, so I plugged the slot 1 stick into slot 3 and the 3 stick into slot 1 and away she went. The memory was mismatched, different makes, but that solved it. Not ideal but worth a try.

---

### Post by xpod on 2006-10-15
This thing has 224mb and i recently doubled it up too.It all seemed to show and work fine in both XP and Ubu but about 2 weeks later i started getting strange issues at bootup in ubu..
It would often stick at "Syslog:connot build structure:cannot allocate memory"....
Rebooting would usually work but the niggles persisted so i removed the mem,reinstalled...and i aint had a similar issues since.

When i had that extra stick in i would generally be up in the high 300`s just with FF and essentials running but now im back with just the 224mb i can run FF,Beryl and one or 2 other apps fine and it`s still only at about 150mb with about 50mb of swap being used...:-k 

It`s all gobbildygook to me still:confused:

---

### Post by DOD1951 on 2006-10-15
Well I finally found out I bought a lemon in the additional 512Mb of memory. On running Memtest at bootup time I discovered heaps of errors. So I removed the lemon stick and re-ran memtest and everything was fine on the orginal 512Mb memory. Have to say I am really impressed that Ubuntu handled the bad memory very well but even it started to have problems today i.e self re-booting. I also noticed some very funny file dates in the file browser like the year 2014 which I can only think was caused by the lemon memory. I don't play around with the date and I checked that year is correct.

---

### Post by Delkster on 2006-10-15
> **DOD1951 said:**
> I had 512MB to start with and thought it would be better to have 1GB as most times I only had about 6Mb left when using system with 512Mb memeory. Probably too many things open.

Is that amount of free memory reported by System Monitor in Gnome or something else? Linux eaglerly uses nearly all available memory, harnessing that which isn't used for applications to disk cache and buffers, thus speeding up disk access. It's quite normal to have only a few megs of truely free RAM. However, when applications need more memory, it's quickly freed from disk cache, so you can practically think of that part as free RAM (except that unlike really free memory, it's actually made use of). The Gnome System Monitor takes this into account and shows memory used for buffers and cache as 'free'.

So, if you only have a few megs free according to the aforementioned System Monitor, you're really running out of RAM. If, however, only a few megs of free memory is shown by the KDE Information Center or by the 'free' or 'top' commands in the terminal or something like that, they don't count caches and buffer as free memory, so that alone doesn't mean that you're running out of RAM.

For example I have only 11 MiB of RAM really free right now, but more than 500 megs is in disk cache and 150 in buffers, from which it can be nicely freed on demand.

Edit:
Of course having more RAM helps, though: I have 1 GiB, which is certainly enough for my use, but now that I have it I wouldn't want to go back to a lower amount.

---

### Post by Delkster on 2006-10-15
> **DOD1951 said:**
> Have to say I am really impressed that Ubuntu handled the bad memory very well but even it started to have problems today i.e self re-booting.

No software can really run reliably if the hardware it's running on is unreliable. Of course the memory usage patterns of some software can reveal problems more easily than those of other software, though.

I'd say that it's mostly luck if at first you didn't experience problems with Ubuntu.

---

### Post by DOD1951 on 2006-10-15
Interesting question. System monitor shows:
Usr Memory: 215.b MiB of 503.9 MiB 42.8%
Used swap: 0 bytes of 1.4 GiB 0.0%
The Sysinfo utility shows under Memory Info : total 515Mb Free 4Mb.
So I should go with what System monitor says rather than Sysinfo I suppose?

---

### Post by argie on 2006-10-16
[http://gentoo-wiki.com/FAQ_Linux_Memory_Management](http://gentoo-wiki.com/FAQ_Linux_Memory_Management)

Both actually say the same thing, except Sysinfo includes the memory used for cache as Used, and System Monitor does not.

---

