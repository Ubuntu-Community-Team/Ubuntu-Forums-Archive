---
title: "[SOLVED] Me hate wireless WPN111"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by edsmaffs on 2007-12-17
OK.
I've installed the ndiswrapper packages.
Done all the instructions.
NO errors at all.
Apart from the suspicious problem that it DOESN'T WORK!!!
My WPN111 adapter has NEVER flashed blue on Ubuntu. Ever.
I've tried reinstalling Ubuntu clean, everything.
I've tried CLI and the graphical version of ndiswrapper.
It doesn't work.
Any ideas? Sorry if I'm being vague, post angry messages if you want me to elaborate.

---

### Post by edsmaffs on 2007-12-17
Anyone?

---

### Post by chamberlain2006 on 2007-12-17
Can you post the output from ndiswrapper -l?

---

### Post by edsmaffs on 2007-12-17
Yep, sure can.

*ndiswrapper -l:*

athwpn : driver installed
        device (1385:5F01) present
netwpn11 : driver installed
        device (1385:5F01) present


Don't know what this means. Is it good or bad? Athwpn and netwpn11 were the names of the .inf files that I installed.

---

### Post by coolbrook on 2007-12-17
Are you using the Win 98 driver?  Try the oldest one if not already installed. 

[http://kbserver.netgear.com/products/WPN111.asp](http://kbserver.netgear.com/products/WPN111.asp)

To remove current drivers
```

sudo ndiswrapper -r athwpn
sudo ndiswrapper -r netwpn11
```

then install the "Initial release."  The oldest version of my driver jives with my WG111v2.

---

### Post by edsmaffs on 2007-12-17
OK I have the setup.exe file from that site, is there a way to extract the driver *.inf 's from it in Ubuntu?

---

### Post by coolbrook on 2007-12-17
Not that I know of.  You'd have to run setup on a Windows machine and then copy the driver from Program Files...Netgear..and the .inf might be there or in a Win 98 sub directory if there are OS folders set up.

---

### Post by edsmaffs on 2007-12-17
:( Don't really want to change my setup on my XP on any way as it works fine...
I'll try looking in TEMP directories first and use that way as a last resort...

---

### Post by coolbrook on 2007-12-17
All it does is provision a driver should you physically install the adapter on your XP machine. If it does have any affect (like on fast user switching) then it won't be adverse.  Just Add/Remove Programs from Control Panel.  You don't have to plug in the adapter on that machine at any point.

---

### Post by edsmaffs on 2007-12-17
OK. All working. However, a couple of problems.

1. There is no icon on ubuntuforums for a man bowing down and praising coolbrook. Thank you very very very much, working fine now!!!

2. XP Wireless mucked up. Oh well...

3. A mod, please can you change the title of this thread to something more appropriate, like "I LOVE UBUNTU!!!" or "LINUX ROCKS!!!!". Thank you.

---

### Post by edsmaffs on 2007-12-17
And XP Wireless working again! All happy now!
Thank you thank you thank you thank you thank you thank you coolbrook.

---

### Post by coolbrook on 2007-12-17
No problem.  Just use Thread Tools to mark this thread as 'Solved'

---

