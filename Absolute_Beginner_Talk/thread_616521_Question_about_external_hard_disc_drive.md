---
title: "Question about external hard disc drive"
date: 2007-11-18
forum: Absolute Beginner Talk
---

### Post by PakelisViniu on 2007-11-18
Hello, i installed ubuntu today. Soon i encountered several problems.
1.I have downloaded winrar for linux. I made this because i got important rar. file.I wanted to extract it. But there wasn't such option. And if i try open with that linux rar programe it shows error.

zip: stdin: not in gzip format
tar: Child returned status 1
tar: Error exit delayed from previous errors
 
At first it was named .rar but i changed to tar.gz willing it will work. How i should extract them?

2. When i connect my external hard disc drive it runs for a few seconds and then craches.What is the cause? It says smthng that Nautilus can't read or smthn. Its really annoying because i back-up my data from windows :films,music etc.

Please help me :] And try to explain in plain english :]

---

### Post by bluepowder7 on 2007-11-18
for unzipping stuff, i stumbled across a program called ALZip.  seems to work really well for all sorts of formats.  it's free, so you should be able to download it easily.  the .exe file i have is 6.5megs.

as for the external HDD, no idea.  i assume it's formatted in NTSF instead of the traditional old FAT32?

---

### Post by PakelisViniu on 2007-11-18
So the only way is to Format everything? :confused: i can't do that. All treasure is there :/

---

### Post by skyjacker on 2007-11-18
> **PakelisViniu said:**
> 

2. When i connect my external hard disc drive it runs for a few seconds and then craches.What is the cause? It says smthng that Nautilus can't read or smthn. Its really annoying because i back-up my data from windows :films,music etc.

Please help me :] And try to explain in plain english :] YTou might try this and see if it helps. Worked for me.> I clicked 'storage media' in the left column in Dolphin File Manager.
I right-clicked the Disk (it showed up here in dolphin, but not in Konqueror?)
I choose 'properties' > 'mounting'
I unchecked 'mount as user'

---

### Post by PakelisViniu on 2007-11-18
Where is that Storage media? :D sorry for stupid question but i couldnt get :D i use ubuntu 7.10

---

### Post by bluepowder7 on 2007-11-18
did you instlal ubuntu 7.04 or 7.10 ?  if you installed 7.04, then you might need to install some additional stuff to be able to read NTSF (windows 2000 and windows xp) hard drives.  if you installed 7.10 then the problem is somewhere else.

no, don't format anything.  i made that mistake once when i was using one of those external hard drive cases - it turns out that the case had bad electronics, but i ended up formatting my entire drive because i though the hard drive itself was damaged.

---

### Post by PakelisViniu on 2007-11-18
Yes i got 7.10 and as i saw ALZip is for windows , tried and it didn't worked.


Any other suggestions?

---

