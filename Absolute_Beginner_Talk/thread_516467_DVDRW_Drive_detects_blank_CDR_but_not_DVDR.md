---
title: "DVDRW Drive detects blank CDR but not DVDR"
date: 2007-08-03
forum: Absolute Beginner Talk
---

### Post by Eastisle on 2007-08-03
Hi, I originally posted this in the General Help forum but had no success. Hopefully someone here will be able to help me :)

I was trying to burn some media to a DVD-R using my DVDRW drive but it wont recognize/detect the blank DVD.
I can hear the drive reading the DVD but it never shows on the desktop as a blank DVD-R.
It is as if there was no DVD in the drive in the first place. I dont get any error messages or anything of that matter.

I know my drive works since I have burned many CD-Rs without a problem. When blank CD-Rs are inserted Ubuntu recognizes them immediately and I get prompted with options to make a Audio or Data CD. Audio CDs are also recognized and I play them with no problems.

I have tested out different DVD-R brands(Memorex, Dynex, etc.) to see if that would be a factor but none have been detected. I have tested commercial DVD movies as well but they also aren't recognized.

My Drive brand: HL-DT-ST
Model: DVD+-RW GWA4164B

In case this is a factor:
I have a dual drive and my Sony DVD-ROM DDU1615 has no problems playing DVDs of any sort.

Anyone know why this is? Any solution? Thanks in advance.


When trying to burn through the terminal:> ea@agent:~$ makedvd -burn "/home/ea/OUT_PREFIX"
--------------------------------
makedvd
A script to create a DVD-Video file structure and burn it to DVD
Part of the tovid suite, version 0.30
[http://www.tovid.org](http://www.tovid.org)
--------------------------------
================================================== =======
Please insert a blank DVD+/-R(W) disc into your DVD-recorder
(/dev/dvdrw) if you have not already done so.
expr: syntax error
(standard_in) 1: parse error
================================================== =======
Found no disc in /dev/dvdrw. Cannot burn to this disc!
Found no disc. Please insert a usable DVD into /dev/dvdrw.
Trying again in 1 seconds...
Looking for usable media...
expr: syntax error
(standard_in) 1: parse error
Found no disc. Please insert a usable DVD into /dev/dvdrw.
Trying again in 1 seconds...
Looking for usable media...
expr: syntax error

---

### Post by shearn89 on 2007-08-03
the "syntax error" bit looks like there's a problem with either the way you're giving the command, or the script itself... Try using one of the add/remove disc burning programs?

---

### Post by Eastisle on 2007-08-03
Thanks for the response shearn89. I installed Gnomebaker and gave it a try, but no luck.
The DVD-R is still not detected and prompts me to enter a blank DVDR.

Can it some how be driver related?
Again, thanks for the effort.

[IMG]http://i117.photobucket.com/albums/o63/eastisle/Screenshot-1.jpg[/IMG]

---

### Post by shearn89 on 2007-08-04
It looks like it. Check the Ubuntu Document Storage Facility ([UDSF]("http://doc.gwos.org/index.php/Main_Page")) to see if you're drive is listed under the Hardware Incompatability section, and maybe trawl some google results. Are you able to burn DVD-RWs?

---

### Post by Eastisle on 2007-08-04
Thanks again for the help. No I'm not able to use DVDRW. From my trials, reading anything DVD related is non-existent. I will look through the incompatibility list and search some more on the issue.  Any more ideas are welcomed. I appreciate the help.

---

