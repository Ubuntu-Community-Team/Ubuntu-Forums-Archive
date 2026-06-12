---
title: "Boot Process"
date: 2006-10-30
forum: Absolute Beginner Talk
---

### Post by Derek3131 on 2006-10-30
When Ubuntu is trying to launch it scans for my hard drive and the boot partition on it, it always starts with hda, scans it a few times, finds nothing and then starts the scan on hdb and repeats a few times... 

My HD is on hde... is there a file i can edit to make the boot process start with hde and skip all the others so it finds the boot partition and ultimately boots up faster?

please post a link if you know of one, my searches have been coming back it everything but my problem.

Thanks in advance.

---

### Post by Derek3131 on 2006-10-30
So  when my PC boots up it does the following

**hda** ... scanning (doesn't find anything)
hda ... scanning (doesn't find anything again)
hda ... scanning (repeat)
hda ... scanning (repeat)
**hdb**... scanning (doesn't find anything)
hdb ... scanning (doesn't find anything again)
hdb ... scanning (doesn't find anything again)
hdb ... scanning (doesn't find anything again)
**hdc** FINDS CDROM
**hde** Finds hard drive and boot partition and boots up. 


I am trying to cut out the scans for hda and hdb... any ideas?

---

