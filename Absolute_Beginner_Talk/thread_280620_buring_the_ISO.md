---
title: "buring the ISO"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by huviduc on 2006-10-19
i was just wondering what i am doing wrong. i have the ubuntu 6.06 iso file burned to CD but it does not seem to work. it tells me that there is no operating sytem found. what am i doing wrong? thanks alot for any help

---

### Post by Sef on 2006-10-19
What operating system are you using to burn the .iso?

---

### Post by aysiu on 2006-10-19
How did you burn it?

Like this?
[http://www.psychocats.net/ubuntu/iso](http://www.psychocats.net/ubuntu/iso)

---

### Post by localuser on 2006-10-19
Its possible that you burned the image at too high a speed.  If all else was done correctly, you might want to re-burn it at a slower rate.

~lu

---

### Post by huviduc on 2006-10-19
i just burned the iso with windows XP using a program called CDBurnerXP Pro 3 and just simply burned it using the default values


i just read threw those directions on the link cause i didnt notice hte link the first time and i am going to try that and let you guys know

---

### Post by barkej on 2006-10-19
If you open the disc in windows what files do you have on the disc?

---

### Post by Sef on 2006-10-19
Free [ISO Burner]("http://isorecorder.alexfeinman.com/isorecorder.htm") for Windows.

Directions for [burning an iso]("http://www.petri.co.il/how_to_write_iso_files_to_cd.htm") in Windows XP.

---

### Post by localuser on 2006-10-19
> **huviduc said:**
> i just burned the iso with windows XP using a program called CDBurnerXP Pro 3 and just simply burned it using the default values

The correct approach would be to double check the MD5SUMS to ensure you got a complete download.  The link which aysiu posted explains how to do that.  If the download was complete, then you could try to re-burn the CD at a slower rate.

If you are new to this, and you don't know how to check the MD5SUMS, and you don't want to deal with it, and you don't mind wasting a CD, then you can try to re-burn at a slower rate and hope for the best.

---

### Post by huviduc on 2006-10-19
i just used md5 and i got one error but it says the file is 100%, i am going to try buring at a slower speed

---

### Post by aktiwers on 2006-10-19
Then you should download a new one.. 
But for me it sounds like you forgot to burn the file as an image. When you are done burning, there should NOT be only an .iso file. Burn as Image :)

---

### Post by huviduc on 2006-10-19
ok, now the cd works, but when i go to gnome partition editor to make my partitins for the dual boot. it freezes while scanning devices. anyone know a possible cause for this. its happened twice in a row

---

### Post by Sef on 2006-10-19
If you are using the Desktop CD, then wait a few minutes. Sometimes it just needs some time.  If you still have the problem, then download the alternate CD. It is text-based, but pretty simple to follow.

---

### Post by huviduc on 2006-10-19
i have two hard drives in the computer, would it help if i removed one for the time being?

---

### Post by localuser on 2006-10-19
> **huviduc said:**
> ok, now the cd works

For future reference, it may be helpful for others doing searches to know what fixed the problem.  Did you have to re-download?  Or did you burn the image incorrectly?

~lu

---

### Post by aysiu on 2006-10-19
> **huviduc said:**
> ok, now the cd works, but when i go to gnome partition editor to make my partitins for the dual boot. it freezes while scanning devices. anyone know a possible cause for this. its happened twice in a row
How much RAM do you have?

---

### Post by Mission 10 on 2006-10-19
If you're talking about resizing partions via the installer then it sometimes takes a long time. I have a 2.8ghz 512mg ram system with a small 80gig hard drive and it took over 20 minutes.

---

### Post by huviduc on 2006-10-19
ok, that makes sense. to fix the problem i had to burn the cd differently. i think the reason is that i was to fast. i tried reburning slower and it worked fine. this program usually makes *.iso files work just by buring them, atleast it did for my formatting disks, but anyway, i burned as from an iso at a slower speed as directed by the very helpful link i was provided with. From there i had problems getting the cd to run the partitioner, i disconnected the secondary drive and it worked perfectly. i think it was just to much for the system running of of cd with the amount of resources the comp has(it was free and has limited RAM and processor). i thank you guys so much for your help, i have never had such fast responses with actual good info and no criticism on any forum i have ever been on. i will def be a returning user considering i registered today. thank you very much.

P.S. this is my first time really dealing with linux, and this has been an extrmeley good experience. i give my first thumbs up for the system and its helpful users

---

