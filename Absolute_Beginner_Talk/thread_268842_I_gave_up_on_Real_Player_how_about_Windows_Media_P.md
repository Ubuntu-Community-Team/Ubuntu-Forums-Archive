---
title: "I gave up on Real Player how about Windows Media Player"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by Tobster on 2006-09-30
For a month now I been trying to install Real Player and really need to give up now.

Is there some way to install Windows Media player codec.

Just to give you an idea of my Linux ability,  I installed Xine DVD player to get Quick Time Codec, then I realised that it really was an amazing DVD player.

If there an easy way of getting them it be fab...  I already done Easy Ubuntu

Thanks 

Toby

---

### Post by easyease on 2006-09-30
wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb

---

### Post by Sef on 2006-09-30
Have you followed the directions in [Restricted Formats?]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by easyease on 2006-09-30
> **Sef said:**
> Have you followed the directions in [Restricted Formats?]("https://help.ubuntu.com/community/RestrictedFormats")lol thats the page every newbie should read......

---

### Post by K.Mandla on 2006-09-30
Hmm. There used to be a link to a realplayer 10 .deb file on that page. I wonder what happened to it.

I still have the deb at home. I'll have to put it online somewhere, if that's not taboo.

---

### Post by K.Mandla on 2006-09-30
> **easyease said:**
> wget -c [http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb](http://packages.freecontrib.org/ubuntu/plf/pool/dapper/non-free/w32codecs_20060611-1plf1_i386.deb)
sudo dpkg -i w32codecs_20060611-1plf1_i386.deb
Is there a real media codec in that package? That might be easier than the player.

---

### Post by easyease on 2006-09-30
Im not too sure, I dont think there is though. think its just wma/ wmv codecs in that package. one more reason to praise the genius of vlc.....

---

### Post by Kilz on 2006-09-30
> **K.Mandla said:**
> Is there a real media codec in that package? That might be easier than the player.

It should have a real codec if its the mplayer codec pack. Then install mplayer and your home free. ```
sudo apt-get install mplayer
```

---

