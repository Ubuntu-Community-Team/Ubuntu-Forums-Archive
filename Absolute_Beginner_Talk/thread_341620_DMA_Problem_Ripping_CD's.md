---
title: "DMA Problem Ripping CD's"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by l951b951 on 2007-01-18
I feel smart for being able to help myself this far, but now I'm stuck.  I have a problem with ripping CD's.  I had this problem on my linux laptop, and now on my Fedora 6 machine.  I was using Grip but it kept freezing my machine so I switched to Sound Juicer.  It works for the most part, but occasionally it freezes my machine as well.  And by freeze, I mean complete, have to hard reset, freeze.  I feel resourceful for finding my system log, but I need help figuring out how to fix what's broken.  Here is my output.  
> 
Jan 18 21:38:10 linuxbox kernel: hdd: DMA timeout retry
Jan 18 21:38:10 linuxbox kernel: hdd: timeout waiting for DMA
Jan 18 21:52:05 linuxbox kernel: hdd: DMA timeout retry
Jan 18 21:52:05 linuxbox kernel: hdd: timeout waiting for DMA
Jan 18 21:52:06 linuxbox kernel: hdd: status error: status=0x58 { DriveReady SeekComplete DataRequest }
Jan 18 21:52:06 linuxbox kernel: ide: failed opcode was: unknown
Jan 18 21:52:06 linuxbox kernel: hdd: drive not ready for command
Jan 18 21:52:06 linuxbox kernel: hdd: status error: status=0x50 { DriveReady SeekComplete }
Jan 18 21:52:06 linuxbox kernel: ide: failed opcode was: unknown
Jan 18 21:52:06 linuxbox kernel: hdd: status error: status=0x50 { DriveReady SeekComplete }
Jan 18 21:52:06 linuxbox kernel: ide: failed opcode was: unknown
Jan 18 21:52:06 linuxbox kernel: hdd: status error: status=0x50 { DriveReady SeekComplete }
Jan 18 21:52:06 linuxbox kernel: ide: failed opcode was: unknown
Jan 18 21:52:06 linuxbox kernel: hdd: ATAPI reset complete

---

### Post by riven0 on 2007-01-18
Well, do you have DMA enabled? You can check this through you BIOS.

---

### Post by l951b951 on 2007-01-19
I went to my BIOS and there is nothin specifically metioning DMA.  Well, I take that back.  To the best of my memory, it said DMA IRQ1 =PnP.  It repeated this for IRQ1-7.  

I could be mistaken.  I checked it this morning after reading your reply, but didn't write it down, but I'm fairly certain that is what it said.  I know for a fact there was nothin else concerning DMA and the drives.

---

### Post by l951b951 on 2007-06-23
Just to update this with a resolution, it was a drive going bad.  It kept getting worse until eventually the drive would fail to read any discs, quit ejecting, and would lock up the entire computer.  

Swapped drives and everything is working fine.  Finished ripping my CD collection to my NAS.

---

