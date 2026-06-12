---
title: "Ubuntu on MBP 4.1"
date: 2009-01-27
forum: Apple Hardware Users
---

### Post by MasterCylinder on 2009-01-27
I've spent the last couple of days trying to get Ubuntu on my computer with no avail. I downloaded and burnt a live CD of Ibex (8.10). But the only blank I had was somewhat scratched, when I check the disk integrity it reported that the disk was in fact corrupt.

But, I do have two copies of 7.04 (pressed copies, not burned)... I already have made a partition in Bootcamp (~15 gigs), and I have refit worked out also.

So heres the deal, when ever I to boot from the Fiesty disk(s) that i have i get the following error message:

/bin/sh: can't access tty: job control turned off...

help?

---

### Post by MasterCylinder on 2009-01-28
Update:

I've successfully installed Ubuntu 8.04 (Hardy Heron)

After refit loads and I select the Linux partition, it hangs. Like its just Tux on the screen...

If someone would read this and could offer me some advice that would be awesome

---

### Post by hyperboloid on 2009-01-28
You probably need to sync the MBR (or did you already do that?) 

See here: [https://help.ubuntu.com/community/MacBookPro4-1/Intrepid]("https://help.ubuntu.com/community/MacBookPro4-1/Intrepid") and look at the installation instructions for the installer bug.

By the way, I would strongly recommend running 8.10 on your hardware since the hardware will be much better supported in 8.10.

---

### Post by MikeTheC on 2009-01-28
> **hyperboloid said:**
> You probably need to sync the MBR (or did you already do that?) 

See here: [https://help.ubuntu.com/community/MacBookPro4-1/Intrepid]("https://help.ubuntu.com/community/MacBookPro4-1/Intrepid") and look at the installation instructions for the installer bug.

By the way, I would strongly recommend running 8.10 on your hardware since the hardware will be much better supported in 8.10.

+1 to that. Plus, you should probably already be seeing the prompt for an available distro upgrade.

---

### Post by cyberdork33 on 2009-01-28
> **hyperboloid said:**
> You probably need to sync the MBR (or did you already do that?) 

See here: [https://help.ubuntu.com/community/MacBookPro4-1/Intrepid](https://help.ubuntu.com/community/MacBookPro4-1/Intrepid) and look at the installation instructions for the installer bug.
This sometimes happens even with the partition tables synced... For some, it works if you just completely turn off your Mac, then start it up again (maybe twice). If not then, you may need to reinstall GRUB. More details are in the FAQ stickied at the top of the forum.

---

### Post by MasterCylinder on 2009-01-28
Thankyou for all the help!

I am up and running on 8.10! It boots like a charm!

When refit loaded I went into the partition manager and refreshed the MBR?

Now everything works great, just going to iron out some tweaks

thanks once again

---

