---
title: "Grow Mac os X partition using Linux Ubuntu Gparted"
date: 2010-06-16
forum: Apple Hardware Users
---

### Post by LtPitt on 2010-06-16
Hello there, friends...

I'm reviving my sweet old imac bondi rev b.

This little beast has been overclocked to 300 mhz and has a voodoo2 sitting in it :D

So it deserves living in the 2010 :)
I've installed panther and I'm surprised about how it works...
I'd just need a little more space to this partition but...
How?

There's an application called iPartition but doesn't work on active volumes (any solution for that?)

Then I thought: why not ubuntu?
I've read, here and there, that gparted is able to shrink but not to grow hfs partition.

Then I thought...

That's my situation:

Mac os X 5 gb
Useless 1 gb

If I delete Useless partition from ubuntu and then starting mac os x I grow the disk?
Will I be able to do it?

Any hint or help is really appreciated :)

---

### Post by LtPitt on 2010-06-16
Thinking about it...

Is there any kind of ...

Total backup?

I mean...
I could backup my data to an external disk (any problems if it's ntfs or fat32?) and the format-restore?

---

### Post by linuxopjemac on 2010-06-16
Carbon Copy Cloner

---

### Post by shawnhcorey on 2010-06-16
My advice is to, after you have made backups, of course, is to boot from a LiveCD and use gparted from there.  Trying to change the root partition is dangerous, that is, you could loose the entire system.  By running from CD, it becomes the root partition and you can change your hard disk with one less worry.

And remember, always have a backup!

---

### Post by LtPitt on 2010-06-17
Great, mates!

One last question: with carbon copy cloner can I extract single files from the backup?

Or restore just one single partition?

Thank you

---

### Post by linuxopjemac on 2010-06-17
it runs from within OSX. It copies files one by one. If you put the copy on a firewire drive, you can even boot from that. It can extract the whole OSX partition but you can also only select user files for example.

---

