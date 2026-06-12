---
title: "where did that empty partition space go?"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by GabeForPrez on 2007-12-17
it might have been a poor decision, but i didnt know at the time.

i was dual-booting linux and windows for a while,
but i decided to uninstall the ubuntu distro [why? cuz i wasn't using it, and it was taking up room]

so, from the live cd's gparted I simply deleted the partition. i was attempting to extend the windows partition to fill up the remaining space, but it refused. so i went ahead and deleted the partition and left some empty space to extend the windows partition later.

so after restarting the live cd, it now says that the current windows partition does indeed hold all the free space, but it is not any larger than before.

to illustrate,  the windows partition is 100gb, the full size of the hard drive is 160gb.
gparted says that the windows partition has 6gb free, with 94gb used space.

where did that missing gb go?

---

### Post by lgambett on 2007-12-17
You have to extend the Windows partition again using gparted. If gparted gives you errors try to defrag **and** chkdsk Windows partition, then try again using gparted.

---

### Post by Pumalite on 2007-12-17
> **GabeForPrez said:**
> it might have been a poor decision, but i didnt know at the time.

i was dual-booting linux and windows for a while,
but i decided to uninstall the ubuntu distro [why? cuz i wasn't using it, and it was taking up room]

so, from the live cd's gparted I simply deleted the partition. i was attempting to extend the windows partition to fill up the remaining space, but it refused. so i went ahead and deleted the partition and left some empty space to extend the windows partition later.

so after restarting the live cd, it now says that the current windows partition does indeed hold all the free space, but it is not any larger than before.

to illustrate,  the windows partition is 100gb, the full size of the hard drive is 160gb.
gparted says that the windows partition has 6gb free, with 94gb used space.

where did that missing gb go?

If Vista, you have to allocate space for Ubuntu from WITHIN Vista first. Then you use Gparted Live CD. You boot from it and in the freed space you make the following partitions:
10 GB for '/'
2x RAM, up to 1 GB for /swap (except laptop, where /swap=RAM)
The rest for /home
Then install Ubuntu going Manual and use the partitions already made.

---

### Post by GabeForPrez on 2007-12-17
alright, i will try gparted again.
right now.

i did attempt gparted before though, and its not that it gives me an error, its that there is no room to extend the windows partition, it just fills up the entire bar.

it says there's 6gb remaining on the drive, but i know for a fact that it has 94gb used, not 154gb.

i'll return with a screenshot to clear this up.

---

### Post by Pumalite on 2007-12-17
> **GabeForPrez said:**
> alright, i will try gparted again.
right now.

i did attempt gparted before though, and its not that it gives me an error, its that there is no room to extend the windows partition, it just fills up the entire bar.

it says there's 6gb remaining on the drive, but i know for a fact that it has 94gb used, not 154gb.

i'll return with a screenshot to clear this up.
If you have XP, defrag several times, erase all temp files, get rid of all data that can be backed up, turn Page File to 0 (turn it back to original later). Boot from Gparted again. (Gparted in Live CD is different from what I'm talking about)

---

### Post by GabeForPrez on 2007-12-17
thanks to lgambett for responding.
but wow, thank you very much pumalite. 
your answers are concise and would fix my problem quite well.
but that wasn't the problem.
instead i just had to check in with the gparted live cd [instead of gparted from the ubuntu live cd] which read the free space correctly this time, and all is well now.

your [very quick] support, pumalite, is greatly appreciated.

---

### Post by Pumalite on 2007-12-17
> **GabeForPrez said:**
> thanks to lgambett for responding.
but wow, thank you very much pumalite. 
your answers are concise and would fix my problem quite well.
but that wasn't the problem.
instead i just had to check in with the gparted live cd [instead of gparted from the ubuntu live cd] which read the free space correctly this time, and all is well now.

your [very quick] support, pumalite, is greatly appreciated.

You are quite welcome. Good luck.

---

