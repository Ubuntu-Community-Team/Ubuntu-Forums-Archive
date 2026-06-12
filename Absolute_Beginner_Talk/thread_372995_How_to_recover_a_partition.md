---
title: "How to recover a partition??"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by makko on 2007-02-28
I was just messing about with my external hard drive just there. I was trying to partition it so I could install ubuntu on it. I magically deleted the main partition on it and now everything is gone... How would I go about getting it back?? I need files on that disk??](*,) 
I am beginning to hate Ubuntu very very quickly after giving it lots of time..what do I do now?

---

### Post by rsambuca on 2007-02-28
What were you using to partition the drive, and what actions were you performing?

---

### Post by makko on 2007-02-28
I was using a mix of the ubunutu installer and the partition editor under administration.. I was adding partitions ext3 and a linux-swap. When I clicked apply it said something about the hard drive being busy.. At the moment I really need to recover that hard drive.

---

### Post by szf on 2007-02-28
Sorry to hear about your fear of lost data. I assume that the application in use was GParted. Have you tried to [google]("http://www.google.com/search?hl=en&client=firefox-a&rls=com.ubuntu%3Aen-US%3Aofficial&hs=DiZ&q=linux+partition+recover+partition+table&btnG=Search") for linux-based tools?

I recall using [TestDisk]("http://www.cgsecurity.org/wiki/TestDisk") once upon a time after I committed a RedHat bootstrap install that overwrote the partition table of a separate hdd.

---

### Post by rsambuca on 2007-02-28
Using a mix of programs to re-partition your drive, and without back-ups!:(

Does anything show up on the drive at all when you view it from the liveCD?

---

### Post by makko on 2007-02-28
TBH I didn't really know what I was doing, I only realised that after I had done it..the drive show up grand when I boot from the live cd.

When I go into the disk manager it says.
Partition List: Partition 1 and free space.
Under free space it says free space not available.

How do I get this back to be mountable in windows..??

---

### Post by makko on 2007-02-28
Ok I've just used testdisk and it says that the structure is ok.
What would be the next step to recover the partition table?

Thanks for the help guys, I really appreciate it..

---

### Post by szf on 2007-02-28
Read the TestDisk documentation, makko... You're the only one that can decide whether the 'advice' (whether software or help/wiki pages) is worth any further risk to your data.

That said, I did recover my $Stuff after accidentally deleting the partition table. It was frightening, yes (I really needed that data back)... and now I don't commit any major operation without a backup first.

Don't kick yourself tho, it's a human thing to not believe the worst case when the information says that 'all will be fine' (caveat: it's truth sourced from software).

---

### Post by makko on 2007-02-28
I've been reading loads just there. Is there a simple guide on how to recover the pratition table?Will Gparted do that for me?

---

### Post by szf on 2007-02-28
This is Open Source - you'll have to go with your gut at some point because you'll never run out of options or information (contradictory, often enough,  if you follow blogs ;)).

Synthesize the info you find, and take your best chance at a full recovery (then share the outcome here).

---

### Post by makko on 2007-02-28
I ran the GParted live cd and right clicked on the partition and said check/repair.. now back in windows and i'm sorted..
I feel like a fool now because someone did say before to GParted and I kinda forgot about it.. When I was in GP a min ago I noticed that it is really easy to creat extra partitions..
Now I'll give it a second shot..
Thanks guys..
BTW this forum is probably the best support forum I have every come across..thanks again!

---

### Post by rsambuca on 2007-03-01
The gParted live CD is really an awesome utility to me.  Let us know if everything works for you.

---

