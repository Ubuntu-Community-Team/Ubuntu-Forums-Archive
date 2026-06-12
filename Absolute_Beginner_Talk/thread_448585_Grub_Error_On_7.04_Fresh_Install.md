---
title: "Grub Error On 7.04 Fresh Install"
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by LukeCarrier on 2007-05-19
Hello everyone,

I recently decided to format my XP based system and install a copy of Ubuntu 7.04 on my PC, just to see if I liked it. I ran it off the LiveCD with absolutely no problems, it was great.

So I decided to install the OS, completely removing my XP partition. I ran through the installer with no problems. When I clicked the reboot button at the dialog at the end of the install, the BIOS screens passed as they usually do with no problems at all. Then I had this error message when GRUB was executed:

GRUB Loading stage1.5

GRUB loading, please wait...
Error 18.

Does anybody know what this means, and a method of fixing it? I've been scratching my head for ages now with no luck, maybe one of you guys can help me?

Thanks, I look forward to hearing from you.

---

### Post by halitech on 2007-05-19
grub error 18 means it didn't find the boot kernal options. 

seems like there is more help here

[http://www.ubuntuforums.org/showthread.php?t=7051](http://www.ubuntuforums.org/showthread.php?t=7051)

---

### Post by LukeCarrier on 2007-05-19
Thanks halitech, I'll try there first.

---

### Post by halitech on 2007-05-19
hopefully it helps, if not post back and we'll do what we can to help out.

---

### Post by LukeCarrier on 2007-05-19
Thankyou so so much halitech,

After reading through the information in that thread, I've got Ubuntu back up and runnung again, without re-installing. I owe you one!

All I had to do was change my BIOS setup slightly. I simply opened up the BIOS, then selected my HD which is the primary master, and changed the access mode from 'Auto', which I suspect was choosing LBA, to CHS.

Now my system is working, I'll make sure I tell everyone I know to be having this problem to follow these instructions.

Thanks again.

---

### Post by halitech on 2007-05-19
glad to help, I know how frustrating things can be. I recently upgraded my motherboard and hard drive and when setting the boot options, had the wrong drive selected. took me 4 hours to figure it out, felt like a complete idiot :D

---

### Post by LukeCarrier on 2007-05-19
lol sounds pretty annoying, i've left a power cable to a hard disk disconnected and wondered for days why i got a disk boot failiure every time i booted my pc

---

### Post by halitech on 2007-05-19
oh it was ~L~ especially since it was the only computer I had online at the time and couldn't get any help except what I had in my head. and I've done the power cable too but in front of a client which made it even worse :(

---

### Post by LukeCarrier on 2007-05-19
Ouch, I fix computers for people in my area, I'm only 13 and I end up doing all sorts. I haven't quite manages to make a mistake that embarrassing yet though :lolflag:

---

### Post by halitech on 2007-05-19
wait for it, your day is coming ~L~

---

