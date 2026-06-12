---
title: "Erasing a CD-RW"
date: 2006-12-20
forum: Absolute Beginner Talk
---

### Post by saxsux on 2006-12-20
Hi :-)
I've burnt an audio CD-RW and now want to erase it.
How do I do this in Ubuntu?

Thanks

---

### Post by Bachstelze on 2006-12-20
Any decent burning app should let you do this but anyway, I recommend k3b.

---

### Post by Shay Stephens on 2006-12-20
I agree, K3b is the best burner out there.  I have it installed in ubuntu gnome and it works great.  Plus it has data verification, which gnomebaker lacks.  You can erase and format RW disks with it too.

---

### Post by dmjones500 on 2006-12-20
I believe you can blank a CD-RW using cdrdao, which comes with 6.10.  Something similar to the following command might do the trick:

```
cdrdao blank --device /dev/{your-CD-drive}
```

Have a look at the man page.

---

### Post by JRCreations on 2008-03-31
I know this is ages after the fact, but I had the same problem. When I wrote a CD-RW (which is very easy in Gutsy, I should mention), I noticed that one of the steps was 'erasing disc...' so I knew that Gutsy had something pre-installed to erase discs. So I was afraid I was being incredibly obtuse when I couldn't find the option to erase the disc later...
But I found a quick command-line solution that uses cdrdao, thanks to dmjones' lead. Here's the solution, for posterity:
First you need to unmount the drive: ```
umount /media/cdrom0
``` then just erase the disc! ```
cdrdao blank
```
I really think there should be an easier way to do this from within Nautilus just as there is the option to write a CD in the first place.

---

