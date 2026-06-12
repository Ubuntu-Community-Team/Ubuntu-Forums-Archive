---
title: "installation problem"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by BaronVonSTFU on 2007-04-03
Hi, Im trying to install ubuntu and every time the bar gets to 87% (setting up the clock) it freezes.  I know the cd works because i used it to install on my friends computer.  What gives?

---

### Post by ndefontenay on 2007-04-04
Hi.

Can you give a little more detail?

Which bar are we talking about rith now?

At what time does it fail> (during installation or when getting in KDE/Gnome?)

How far have you been?

---

### Post by BaronVonSTFU on 2007-04-04
The install bar.  After it installs the language packs it goes to something that says "setting up the clock"  and it just freezes.  I cant even move my mouse.  I tried installing in the safe mode, non safemode, i tried synching the clock when i was picking my time zone.  Nothing has worked.  Its driving me insane.

---

### Post by Wilton Speziali Caldas on 2007-04-11
Hi. 
I have the same installation problem with a notebook toshiba satellite a40-s161.
Did you find a solution?

---

### Post by BaronVonSTFU on 2007-04-11
I did not.  I assume it was my cd so I just bought one online instead.  They are taking their sweet time sending it though so I haven't actually been able to test out my theory.

---

### Post by BaronVonSTFU on 2007-04-12
Alright I finally got the cd mailed to me and it STILL froze at 87 percent.  How can setting up a clock make a whole installation freeze?  Im assuming no one has an answer.  I guess its back to windows for me.:( :( :confused:

---

### Post by zvacet on 2007-04-12
If you can install to another comp,but not at yours,maybe is hardware issue.If you can be more specific about your hardware,maybe somebody can help you to solve problem.

---

### Post by BaronVonSTFU on 2007-04-12
Well Im not entirely sure what I have.  I got this computer about 5 years ago.  I have a 1.4ghz athlon processor.  im not exactly sure what kind of motherboard I have.  All I can say is its 5 years old.  I have an agp radeon 9600 video card.  Thats really about all I know.  Pretty sparse

---

### Post by guinra on 2007-04-12
Have you tried running memtest?  You can do so when the CD boots, just select "Memory Test".   If the memory checks out OK, and you've tried different discs, try using a different CD-ROM drive and if that fails, a different hard drive.

---

### Post by BaronVonSTFU on 2007-04-12
I tried the memory test and it checked out ok.  I dont really have any other hds to use.   I also tried something where i typed in some command /casper/vmlinuz noapic nolapic.  I dont exactly know what that was for but it didnt seem to help.  I tried to make my own partitions with a bigger swap partition too but that didnt work either.

---

### Post by scottdizzle on 2007-04-14
Same problem.. I encountered it and searched google for:

'ubuntu setting up the clock 87%'

and this is where it took me. The computer I'm trying to do this with is set up the following:

40gb hard drive:

20gb = Windows 2000
20gb = ubuntu
   512 mb = swap
   the rest = /

Hardware is:
Athlon 1.1ghz
RAM = 320 mb SDRam
AGP ATI Rage card
40gb WD
Some cd burner
Intel 36905b NIC

Everything loads fine you know getting into Gnome to start the installer... but as you probably guessed.. freezes at 87%. Mouse moves but progress bar does not. I also can't interact with anything on the screen. Just move the mouse around.

[Is there a way to get to the text based installer as seen on this video?]("http://video.google.com/videoplay?docid=-6104490811311898236&q=ubuntu+windows+dual+boot")

**edit:** I'm trying to install now with the safe mode start up.. like option #2 in the list when you boot the cd. I'll report back

---

### Post by scottdizzle on 2007-04-14
Okay.. using option #2 for safe mode boot seemed to work. Everything installed properly this time. Try that *BaronVonSTFU*

---

