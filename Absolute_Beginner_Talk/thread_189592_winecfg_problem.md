---
title: "winecfg problem"
date: 2006-06-05
forum: Absolute Beginner Talk
---

### Post by hotbrainz on 2006-06-05
After installing wine, it is instructed to do winecfg before you start installing anything. So i did it and i get:

 /home/username/.wine not found

I dont understand. Do i have to create a directory .wine in  /home/username

Could someone please elucidate?

Thanks for the help in advance..

---

### Post by ash211 on 2006-06-06
When I installed wine and ran winecfg, I don't remember getting that error message.  I think the purpose of winecfg is to create that folder and get the basic structure of wine setup.

Could you please post the exact error message you're getting and the command you're running?  Maybe that could help us a little.

Also, how did you install wine?

---

### Post by hotbrainz on 2006-06-06
yaay, finally i got an answer :) thanks for responding

I did: sudo apt-get install wine

and the directory for wine is found in:

/usr/lib/wine

I thought that this was the way it should be. I wanted to install something using wine. Reading instructions, i typed in 

winecfg

and i get the message:

> /home/username/.wine not found


---

