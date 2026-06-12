---
title: "Problems booting Ubuntu"
date: 2007-07-29
forum: Absolute Beginner Talk
---

### Post by SeriousName on 2007-07-29
Okay, well, I'm pretty much a Linux newbie, though fairly experienced with computers in general. I've just built a new system and wanted to run Ubuntu on it. I downloaded the 64-bit ISO, because I'm using an Athlon 64 X2 processor, burned it using the recommended InfraRecorder program, and started booting from the CD.

Here's where the problem occurs: when I choose either of the first two options from the CD, my computer simply shuts down. Actually, that's not entirely true; after shutting down once, the second option (the Live CD) worked. From there I installed Ubuntu onto my clean 500GB hard disk.

The installation went without a hitch. However, now when I try to boot up my computer from the hard disk, the Ubuntu loading screen flashes, and then my computer shuts down.

Any ideas? I'm at a complete loss.

---

### Post by SeriousName on 2007-07-29
bump

---

### Post by SeriousName on 2007-07-30
Still haven't figured anything out. :(

---

### Post by Inxsible on 2007-07-30
What speed did you burn the iso at?

Considering that you were able to install it on your 500 GB disk, i dont know how valid that question is?

---

### Post by Inxsible on 2007-07-30
What graphics card do you have? Have you tried it with the Alternate CD?

---

### Post by Rocket2DMn on 2007-07-30
Sounds like it could be a hardware issue.  I've had this problem on computers when the processor just overheated during boot and it was impossible to get the computer to fully boot.
Are you using an older machine?  Specs?

---

### Post by SeriousName on 2007-07-30
I didn't adjust the write speed, so I guess it was at maximum speed. The "Check CD Integrity" function reported no problems, though.

The graphics card is a GeForce 6100, built into the motherboard. I haven't tried the Alternate CD yet because burning discs is a bit of a hassle for me right now (have to take the drive out of the new computer, install it into the old one, write the disc, and then move the drive back into the new computer) but if you really think it could help I'll give it a shot.

---

### Post by Inxsible on 2007-07-30
> **SeriousName said:**
> I didn't adjust the write speed, so I guess it was at maximum speed. The "Check CD Integrity" function reported no problems, though.

The graphics card is a GeForce 6100, built into the motherboard. I haven't tried the Alternate CD yet because burning discs is a bit of a hassle for me right now (have to take the drive out of the new computer, install it into the old one, write the disc, and then move the drive back into the new computer) but if you really think it could help I'll give it a shot.

Recommended burning speeds are 4x or less. Cant say, if that will help for sure, but its worth a try.

your card should not be a problem coz I have seen ppl with 6100 machines being able to install

---

### Post by SeriousName on 2007-07-30
It's a completely new machine, here's the specs:

Athlon 64 X2 5600+
2GB DDR2 800 RAM
500GB Seagate HD
Integrated GeForce 6100

Motherboard is an ECS GeForce6100SM-M if that helps.

I'm pretty sure the processor isn't overheating, when I check it in BIOS it's running at about 50 degrees C.

---

### Post by SeriousName on 2007-07-31
Well, I just finished trying the Alternate CD, this time written at 4x speed. Installation was problem-free again, but upon trying to boot Ubuntu from the hard disk my system still shuts off.

Any more ideas, anyone?

---

### Post by SeriousName on 2007-07-31
bump

---

### Post by vajaria on 2007-07-31
Its been a day since I've tried to install Ubuntu and I think most of it works now (haven't tested wireless graphic card)

Biggest problem I faced was during installation of xserver/xorg. The screen blanked out and I couldn't see what was happening. I assumed it had finished installing and did a hard reboot. *Big Mistake*

This led to the infamous Error 17 message - file not found and I spent 4-5 hours trying fixes for that because I assumed something was wrong with Grub. A premature reboot may also mess up your Windows boot record leading to a HAL.dll file not found error. 

I then gave up and reinstalled Ubuntu... (after fixing my Windows using a recovery CD). This time around I was patient enough for it to complete installation and do a self reboot. 

This time it would show the loading logo but as soon as it came to the login screen - no display. Tried a couple of things... and frankly am not sure which of these brought the display back. There is a some grief involved with display drivers but try this simple trick first -

If you have a laptop/tablet try switching between the monitor and the projection screen (on my tablet its the "function" and "F3" key)
Sounds too simple but I believe this is what worked for me.

Prior to trying this I logged in via text mode and ran init 6. I don't think that this did the trick though.

For those struggling... I feel your pain. I guess we gotta learn to be more patient.
- Good Luck

---

### Post by SeriousName on 2007-07-31
vajaria: I don't think that that has any relevance to my problem. I'm assuming you meant to make a new thread?

---

### Post by SeriousName on 2007-07-31
Bump. I'm really having no luck. :(

---

### Post by Rocket2DMn on 2007-07-31
I still think it could be a heat issue, esp. since you built the box yourself.  You might need a better heatsink/fan setup.
You can try installing the 32-bit version and see what happens.
Remember when you download and burn an image
Check the [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") against the correct [hash]("https://help.ubuntu.com/community/UbuntuHashes")
burn at a slow speed, like 4x or less onto quality media.

---

### Post by SeriousName on 2007-07-31
It could be heat. That's one thing I was concerned with when I was building it, because it's a microATX board and case. However, like I said, the temperatures when I've checked them haven't been high enough to be dangerous.

I guess I'll try a 32-bit version next, then. I know at least that both the 64-bit discs I tried were free of errors, though.

---

### Post by Rocket2DMn on 2007-07-31
It's not necessarily that the temperatures are too high when the computer is running, I've had this problem on my server box during the boot sequence only, maybe because the processor is just really kickin at this time.  I ended up using some thermal paste to replace the cracked and dry pad that was initially there between the processor and heat sink.

---

### Post by SeriousName on 2007-08-03
Well, the 32-bit install worked. I wish I knew why.

So, are there any major advantages to having the 64-bit version? Or should I just leave well enough alone?

---

### Post by kirk427 on 2007-10-18
your problem (and mine) seems to stem from the mother board.  I have the same board you're using.  mind you, I'm using gentoo linux, but the symptoms you describe are the same as mine.  here's what I've done.  I've upgraded the bios (6/12/07) I've found some parameters to pass the kernel at boot to eliminate (or reduce) the power down immediately problem.  I'm currently at 6days running w/o problem...  ok, here's the parms to add to your grub entry:

```

noapic nolapic irqpoll apic=off acpi=noirq

```

I found these in one forum or another, cant remember where.  I've tried eliminating one parameter or another, but they all seem to be necessary.  try giving these a shot.  also, you should add these to the boot cd/dvd so your install will finish w/o a power down.  That is when you boot from the install cd, I think ubuntu will let you add parameters to the kernel.  I'm helping my dad install kubuntu this weekend, so I'll have more knowledge about that soon.  

here's some links that may help:

[http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?CategoryID=1&TypeID=35&DetailID=685&DetailName=Feature&MenuID=1&LanID=9]("http://www.ecs.com.tw/ECSWebSite/Products/ProductsDetail.aspx?CategoryID=1&TypeID=35&DetailID=685&DetailName=Feature&MenuID=1&LanID=9")

error report:

[http://article.gmane.org/gmane.linux.kernel/562836]("http://article.gmane.org/gmane.linux.kernel/562836")

good luck.

---

