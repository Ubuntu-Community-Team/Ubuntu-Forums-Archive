---
title: "Unable to boot CD on laptop after failed attempt"
date: 2006-07-25
forum: Absolute Beginner Talk
---

### Post by genedoc on 2006-07-25
Hey folks, trying to install Dapper Drake on Toshiba M45-S351 laptop with 100GB HD and WinXP Home.  Was able to boot from CD ROM initially and ran install.  Got to screen where partitioning could be done.  Forgot verbage, but chose first option of three choices on how to partition.  Second option was a full erase and third was manual configuration.  Anyway, I clicked on the first and then pressed <NEXT>.  I let the machine sit there with the three item screen still showing, but no progress bar suggestion partitioning was happening for 15 minutes or so, but couldn't wait any longer.  Real Life got in the way and I needed to pack up, so I cancelled the install.  Yeah, duh, how else can I make things go badly?  Anyway, the Dapper Drake install program didn't seem to be acting as though it was doing any partitioning, so it didn't seem to be a terrible thing to quit.

Anyway, my XP still runs fine and shows the disk size as though no space was consumed in an alternate partition.  The problem is that I am unable to boot to the CD any longer (regardless of BIOS changes with the CD first), so presumably something happened with the boot sector.  I tested the CD in another system and can boot to it without a problem, so I know (as I expected) that the CD is fine.  Any thoughts on how to rescue the system?  I usually "clean" my laptop on a semi-annual basis with a full hard drive format and figure that's what I'm looking at to deal with the problem of not being able to boot to the CD.  Any thoughts?

---

### Post by wombat20 on 2006-07-25
Very odd.  Can you boot from any other CDs?  Like Partition Magic or similar?  

Does the CD drive still work alright in Windows?

---

### Post by genedoc on 2006-07-25
I can access the CD drive, and even the Ubuntu preview, from XP.  No obvious problems there.  I cannot, however, CD-ROM boot from a Win 2000 CD or the Toshiba recovery CD.

So, I will need to change pace and ask about how to rebuild (e.g. Ubuntu or XP first?), but I'll use another thread for that after I've hunted through documentation online.

---

### Post by genedoc on 2006-07-28
Found a solution.  Figured it was a boot record problem.  Very nice web site for fixing Win XP problems:  [http://www.webtree.ca/windowsxp/repair_xp.htm]("http://www.webtree.ca/windowsxp/repair_xp.htm").

Anyway, using the XP Pro disc, I went into the repair mode.  Using c:\FIXMBR and c:\FIXBOOT, I fixed the boot record.  I was able to boot to CD's after doing these two fixes.

---

### Post by KI4DFH on 2006-11-06
.

---

