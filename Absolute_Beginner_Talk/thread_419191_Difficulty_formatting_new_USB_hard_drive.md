---
title: "Difficulty formatting new USB hard drive"
date: 2007-04-22
forum: Absolute Beginner Talk
---

### Post by infrarad on 2007-04-22
I got a new 300gig external hard drive. It will only be used with linux machines, so I attempted to format it in ext3 using gparted. I started the process, and left the computer for 2-3 hours, and when I came back it was still working on it. I cancelled the process because that seemed like an awfully long time, my browser crashed and I couldn't reopen it, and generally things were not working well until I rebooted from the tower.

I dunno what to do next. Do I start suspecting that the hard drive is bad and return it, or is there a next step in terms of software solutions?

Thanks!

---

### Post by mhansen on 2007-04-22
You can try the old-fashioned way...


run sudo fdisk /dev/whatever-it-is and partition as you like.  Make the partition(s) of type 83
then run sudo mkfs.ext3 /dev/whatever-it-is


and that should be that...



Regards,
Mike

---

### Post by infrarad on 2007-04-22
"...and partition as you like. Make the partition(s) of type 83..."

I'm afraid I don't understand what that means. Does fdisk take an argument of some sort? This is basically the first thing (beyond ls, cd, and rm) that I've done from the command line =)

---

### Post by mhansen on 2007-04-22
ok, I assume you know which device your usb drive is.  If not, plug it in, and then type fdisk -l  and look for your USB drive and make note of which device it is.  For example, mine is /dev/sdh, so I'll use that for these examples.  Then type sudo fdisk /dev/sdh  You'll get output like this:

Disk /dev/sdh: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       19457   156288321   83  Linux

Command (m for help):

at that prompt, type p to list the partitions on that drive.  There's probably just one so hit d to delete it, then n to make a new partition, type p to make it primary, and then make it partition number 1.  When it asks for the starting cylinder, hit enter, and hit enter when it asks for the end cylinder (you're using the defaults and using the entire disk for one partition)  then type t to change the partition's system id.  You'll enter 83 when it asks for the hex code, then type w and  you're done with that.

Then run sudo mkfs.ext3 /dev/sdh1

Remember, /dev/sdh is an EXAMPLE.  Edit accordingly.


Regards,
Mike


P.S.  Or you could just wait for someone else to come along and give you a more "Ubuntu-friendly" answer.  :)  I'm admittedly a bit old-school.

---

### Post by szf on 2007-04-22
> **infrarad said:**
> I got a new 300gig external hard drive. It will only be used with linux machines, so I attempted to format it in ext3 using gparted. I started the process, and left the computer for 2-3 hours, and when I came back it was still working on it. 
I've seen Ubuntu 'remount' drives and/or partitiions when you attempt to commit an operation with gparted. There may be a failure message from the app when its' mounted beforehand - was there any click-thru  error message from gparted app?

---

### Post by infrarad on 2007-04-22
'Or you could just wait for someone else to come along and give you a more "Ubuntu-friendly" answer.  I'm admittedly a bit old-school.'

Perhaps, but your highly detailed answer helped =)

I did not get a clickthru error from gparted. However, having run Mike's suggestion, the terminal currently reads 

```
Writing inode tables:  141/2385
```

and, after initially incrementing through some values in that first number, shows no sign of continuing past 141. That can't be good...

---

### Post by mhansen on 2007-04-22
Well, I Googled and Googled, and just couldn't find anything, and this is one I've never seen before.  I admit, I'm stumped on this one.  I'm sorry we couldn't get you going...




Regards,
Mike

---

### Post by infrarad on 2007-04-22
It's alright--I get "Your computer is broken in an entirely novel way" a lot, for some reason.

---

### Post by Defrector on 2007-12-27
I know this is a dusty thread, but for documentation purposes:

I had the same experience formatting a USB drive to EXT3. It would get to something along the lines of:
```
Writing Inode Tables: 50/916
```

...and would stop at 50 for what would appear to be forever. Maybe it's just REALLY slow. I don't know.

However, I tried mkfs.ext2 instead of .ext3 and it seems to be getting through the job without snagging on any tables. Try it.

If anyone has any ideas why this difference would be, please post.

---

