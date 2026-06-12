---
title: "[SOLVED] Totally Killed My Computer!"
date: 2008-02-13
forum: Absolute Beginner Talk
---

### Post by ThePinkWitch on 2008-02-13
Ubuntu won't load at all even with startup disk. It tried to rescue my system and it  totally had a fit. thats the only way to describe it. It said "can't initialize installation  something something...I have tried restarting it without disk and with disk. The last message was on a black screen saying.. Kernel panic- not syncing:VFS: Unable to mount root fs on unknown block  What does that mean?? :confused: I've been trying for a week and a half to get the network going now this :cry:

---

### Post by SunnyRabbiera on 2008-02-13
a kernel panic is not a good thing let me tell you...
what did you do excactly?

---

### Post by emarkd on 2008-02-13
Did you edit your menu.lst file?  This sounds like Grub is looking for Ubuntu on the wrong partition.  Either that or a bad disk...

---

### Post by seventhc on 2008-02-13
the *live cd* should still boot, (I am assuming this is what was meant by start up disk.)

---

### Post by ThePinkWitch on 2008-02-13
I put new RAM in and it booted ok first time. Then I shut it down a couple of times to change the RAM around because the old RAM I left in seemed to not be working and I took it out. I restarted the machine a few times then because it wouldn't load Ubuntu. it loaded once and I heard the startup music but it was completely black. When I restarted it wouldn't load at all. I tried the system rescue but it couldn't load the keyboard then just put this weird pattern up and stopped WHAT DID I DO??? AHHHHHHH won't even reinstall the OS.

---

### Post by SunnyRabbiera on 2008-02-13
Might be a bad harddisk as previously suggested... not good.

---

### Post by ThePinkWitch on 2008-02-13
> **emarkd said:**
> Did you edit your menu.lst file?  This sounds like Grub is looking for Ubuntu on the wrong partition.  Either that or a bad disk...

No I didn't edit anything

---

### Post by ThePinkWitch on 2008-02-13
> **seventhc said:**
> the *live cd* should still boot, (I am assuming this is what was meant by start up disk.)

Yes I used the install CD it won't work :(

---

### Post by seventhc on 2008-02-13
It is possible that you roasted some hardware if you didn't ground yourself  while switching ram.
I'm not saying you did, but it is possible.
More likely in a dry climate than in a humid climate.

---

### Post by emarkd on 2008-02-13
If you think it's a RAM problem, you can run MemTest from the Grub menu to test it.  May take a while, though, so go make some coffee :)

A hardware problem is about the only thing I can think of that would effect both the installed OS and the Live CD.

---

### Post by BrentMlady on 2008-02-13
Try and make sure that you have the CD drive as the first boot option in the bios.  Then if you can you want to try and fix the Grub menu with this, if you know the drive you installed it on.

[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

If not try and do a reinstall on the system.

:)

---

### Post by ThePinkWitch on 2008-02-13
> **seventhc said:**
> It is possible that you roasted some hardware if you didn't ground yourself  while switching ram.
I'm not saying you did, but it is possible.
More likely in a dry climate than in a humid climate.

OMG I hope not! I was trying to be careful I touched the case first.

---

### Post by ThePinkWitch on 2008-02-13
> **BrentMlady said:**
> Try and make sure that you have the CD drive as the first boot option in the bios.  Then if you can you want to try and fix the Grub menu with this, if you know the drive you installed it on.

[http://ubuntuforums.org/archive/index.php/t-24113.html]("http://ubuntuforums.org/archive/index.php/t-24113.html")

If not try and do a reinstall on the system.

:)

I did that. I went to the BIOS and got it to boot from CD Rom. How do you mean reinstall on the system?

---

### Post by BrentMlady on 2008-02-13
if you got it to boot from the live CD you should be able to do the commands from the website I provided and try and fix the boot menu.

If you want to do a clean reinstall just run the setup again and tell it to over right the last ubuntu you installed.

---

### Post by mgranet on 2008-02-13
You might try switching back to the old ram and see if it boots. Your new stick might be bad.

---

### Post by seventhc on 2008-02-13
> **ThePinkWitch said:**
> OMG I hope not! I was trying to be careful I touched the case first.
Good, it probably isn't from that then, provided the part of the case you touched was metal and not plastic lol

---

### Post by ThePinkWitch on 2008-02-13
> **emarkd said:**
> If you think it's a RAM problem, you can run MemTest from the Grub menu to test it.  May take a while, though, so go make some coffee :)

A hardware problem is about the only thing I can think of that would effect both the installed OS and the Live CD.

No It won't boot at all now. It just beeps at me. I've totally killed it :(

---

### Post by ThePinkWitch on 2008-02-13
Thanks everyone for your input and help. It won't even boot up at all now. I guess I did fry something. I think the HD is shot. It just beeps and clunks and won't start up. I'm beginning to think I just wasn't meant to have Ubuntu. I've had nothing but angst since putting it on a week and a half ago. Now the computer is dead. Anyway thanks again for your help.

---

### Post by gsiliceo on 2008-02-13
Beepings are errors send by the BIOS indicating some hardware is bad installed or damaged. Depending on the number and duration of beeps you can diagnose whats wrong.
Yeah, try switching the ram, then the hard disk, the videocards might be wrong to and the rest of the cards, at last the PSU.

---

### Post by seventhc on 2008-02-13
The ram may not be seated properly, make sure its in all the way.

---

### Post by BrentMlady on 2008-02-13
if it is beeping at you then it has to be a hardware problem.  try and make sure everything is in the correct location and that the new ram is compatible with your motherboard model.

---

### Post by ThePinkWitch on 2008-02-14
> **BrentMlady said:**
> if it is beeping at you then it has to be a hardware problem.  try and make sure everything is in the correct location and that the new ram is compatible with your motherboard model.

just loading dead computer in the car to see PC doctor. Thanks I think yu guys are right..it's gotta be hardware and I did it! LOL Thanks guys .

---

### Post by ThePinkWitch on 2008-02-14
Hopefully it can be revived. Byeeeeeeee

---

### Post by seventhc on 2008-02-14
It might not be from anything that you did, I had a times where something went bad at the same time as I was doing something major. I eventually solved the problem, but it was much more difficult to solve since I kept looking at what I had been doing. As it turned out, the problem was totally unrelated, but a huge coincidence that it happened when it did.
Once I started looking elsewhere for the problem it was solved very easily, I had only been concentrating on the things I had done, and not where the actual problem was.

---

### Post by ThePinkWitch on 2008-02-14
> **seventhc said:**
> It might not be from anything that you did, I had a times where something went bad at the same time as I was doing something major. I eventually solved the problem, but it was much more difficult to solve since I kept looking at what I had been doing. As it turned out, the problem was totally unrelated, but a huge coincidence that it happened when it did.
Once I started looking elsewhere for the problem it was solved very easily, I had only been concentrating on the things I had done, and not where the actual problem was.

You're absolutely right. I took it to computer shop and it turns out it was the Motherboard. And it wasn't anything I did. he showed me the capacitators (Is that how you spell it?) and they were corroded and even had rust LOL. It was jst a coincidence and the RAM was ok. Anyway he's putting a new board in and upgrading it for me so thats cool. I just need an better second hand graphics card and I'm cruisin' lol :guitar: Lucky I still have my main machine or I'd go nuts with out a computer :biggrin:

THANKYOU EVERYONE WHO REPLIED. You guys are great!

---

### Post by ThePinkWitch on 2008-02-15
WARNING! I"LL BE BACK!!!!! :lolflag:

---

### Post by seventhc on 2008-02-15
Welcome back then ;)

---

