---
title: "After Gutsy, CPU running at MAX"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by TeoK on 2007-10-24
Is anyone having the same problem?

I just upgraded..the CPU runs at 80-100 percent capacity. versus %0-10 in Feisty. why?

---

### Post by n3tfury on 2007-10-24
if you JUST installed gutsy, it's probably trackerd indexing your HDD.  take a look at System>Administration>System Monitor>prcesses and see what's gnawing at your CPU.  by the way, that's normal until the indexing is finished.

---

### Post by TeoK on 2007-10-24
yes, trackerd and xorg are v active. but the numbers dont add up this high.
i'll try to update later on.
Thanks though for easing my mind!

---

### Post by n3tfury on 2007-10-24
no problem.

---

### Post by arthur_kalm on 2007-10-25
I actually have a question about this CPU usage. Why is Xorg taking up so much bloody CPU? When switching desktops, moving windows about or even making a new tab in firefox, xorg usage jumps to 15+%. What gives? It really slows down the system (it's the worst when using Opera). None of the other releases of Ubuntu were anywhere near this slow. I'm not running Compiz Fusion...

---

### Post by Jim Danner on 2007-10-25
This is a big problem for me, too. The fan is raging every few minutes, System Monitor tells me CPU is at 100% almost continuously, but in the Processes screen the most intensive processes are gnome-system-monitor itself at 10% and firefox-bin around 7% (trackerd is at 1%). What's making up the other 80 or so percent?

By the way, I'm not sure this is new with Gutsy. I never checked in System Monitor, but the roaring fan happened with Feisty as well, sometimes. Any thoughts?

---

### Post by macogw on 2007-10-25
> **Jim Danner said:**
> This is a big problem for me, too. The fan is raging every few minutes, System Monitor tells me CPU is at 100% almost continuously, but in the Processes screen the most intensive processes are gnome-system-monitor itself at 10% and firefox-bin around 7% (trackerd is at 1%). What's making up the other 80 or so percent?

By the way, I'm not sure this is new with Gutsy. I never checked in System Monitor, but the roaring fan happened with Feisty as well, sometimes. Any thoughts?

That's probably to do with ACPI and your CPU throttling

---

### Post by sloarch07 on 2007-10-27
I have having similar problems after upgrading to Kubuntu Gutsy.  Moving windows, scrolling, drop down menus, etc. are painfully slow.  I don't see any processes using over 5% however my CPU is maxs out anytime a window is displaying a lot of text!  Trying to read man pages is like wading through a pool of molasses..... it's so slow.  The one place I don't have this problem is in Firefox.  Menus and scrolling are very responsive in Firefox.  Does firefox use a different engine for rendering menus and scrolling?  How do I get the rest of KDE back to normal speeds?

---

### Post by Jim Danner on 2007-10-28
> **macogw said:**
> That's probably to do with ACPI and your CPU throttling

You mean that ACPI wrongly reports the CPU utilization at 100% while it's actually around 20%, and ACPI also misreports CPU temperature so that Power Management decides to speed up the fan?

I don't think that's likely to be the problem; wouldn't the same thing happen when Windows runs on that computer? It doesn't happen then...

---

