---
title: "I'm about to smash something! Please help me. Access and permission."
date: 2006-10-01
forum: Absolute Beginner Talk
---

### Post by switchkill on 2006-10-01
I dont know how to install mplayer. I can't get root access unless i type the sudo commmand. I tried to follow 4 diffrent types of instructions on how to install mplayer taking into account the updated files but it can't find anything i type in. Wehn i try to extract it with the default program it won't let me becaus ei dont have access. I have set the root password twice and have user access, whenever i try to change the permissions it tells me i'm not the owner. I'm going insane. All i want to do is play some Mp3's and access the NTFS partition on my HD. Can someone please point me in the right directions because i'm going to smash something.

---

### Post by 900i on 2006-10-01
sudo apt-get install mplayer

---

### Post by petri on 2006-10-01
No```

sudo aptitude update
sudo aptitude install mplayer
```
Press enter after each line.
Why aptitude? Read this: [http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)


btw why don't you just use Synaptic? Or Adept if you have Kubuntu.

---

### Post by kerry_s on 2006-10-01
Use synaptic, enable the multiverse repo
-> deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse

---

### Post by petri on 2006-10-01
Then you have to install codecs for mp3's. You find a howto here: [https://help.ubuntu.com/community/RestrictedFormats#head-2491078b7f3fdd9ad37ffe23e43eeafdebf4187b](https://help.ubuntu.com/community/RestrictedFormats#head-2491078b7f3fdd9ad37ffe23e43eeafdebf4187b)

Or you can use Automatix or Easybuntu. With Automatix be carefull when it asks you if you want to keep yours sources.lst or replace it with Automatix. You do **want** to keep your original sources.lst 8) 

[http://www.getautomatix.com](http://www.getautomatix.com)
Sorry, I don't use Easybuntu :rolleyes:

---

