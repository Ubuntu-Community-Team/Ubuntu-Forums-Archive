---
title: "Problems with parallel port printing"
date: 2007-05-05
forum: Absolute Beginner Talk
---

### Post by scott.todd on 2007-05-05
The subject sums it up, and I am at a loss, looking for some insight...
    
Here is some background, take what you need & ignore the rest.  Let me know if I have left anything out that is useful.
   
My older computer stopped working and rather than troubleshoot it, I got an old computer (newer than mine) from work that they were keeping for spare parts and put in a new hard drive.  Then I installed Ubuntu (goodbye windows, on this pc anyway) and away we go (I am now on version 7.04) but I haven't been able to get my Lexmark 3200 to print.  On my old pc, redhat was able to print to the printer so I don't think it is a linux issue.  I believe I checked the BIOS (as in I don't really know what I am doing there) and I think that the parallel port is enabled but to be honest I am not sure.  I tried "cat something.txt > /dev/lp0" and it says permission denied.  I tried "ls -l /dev/lp0" and it says that root and lp have permission but I don't know how to add my users to the lp group.  I am not even sure if that will work, I don't know how to test if my parallel port is even working....
   
I have had enough for a little while, if anybody has some ideas that I can try, I will appreciate anything at this point...

---

### Post by gradedcheese on 2007-05-05
To add yourself to the lp group, edit (with sudo) the file /etc/group and find the line:

```

lp:x:7:cupsys

```

and change it to say:

```

lp:x:7:cupsys,your_user_name

```

The BIOS setting should be for bidirectional mode, I believe.  What does the BIOS say about the LPT port?

---

### Post by Sef on 2007-05-05
Read [LinuxPrinting]("http://www.linuxprinting.org/show_printer.cgi?recnum=Lexmark-3200").

Lexmark in general does not work well with Linux, unless it is from their Optera line which is made for businesses.  However, your computer will mostly work.

---

### Post by scott.todd on 2007-05-06
I just checked, my user is already on the line in /etc/group.

> **gradedcheese said:**
> The BIOS setting should be for bidirectional mode, I believe.  What does the BIOS say about the LPT port?

It was on EPP, I set it to bi-directional with no luck.

Here is what my BIOS says re: my parallel port:
Parallel Port                         [Enabled]
   Mode                                 [EPP]   <-- I changed this to Bi-Directional
   Base I/O Address              [398]
   Interrupt                            [IRQ 7]

---

