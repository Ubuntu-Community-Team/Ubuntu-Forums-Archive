---
title: "audacity"
date: 2006-10-09
forum: Absolute Beginner Talk
---

### Post by cmaranhao on 2006-10-09
i need help with exporting mp3's with audacity.. it asks me for a file that i don't know where it is (maybe i don't have it installed?))

the file name is libmp3lame.so

(i've set up audacity once and it worked, i can't remember how i did it last time)

---

### Post by foolsh on 2006-10-09
the file you're looking for is in /usr/lib it is called libmp3lame.so.0 
i dont know why the file has that extra 0 behind it but thats the one
so when it asks you where and opens the file browser window go to /usr/lib and add a .0 to the file name then press ok
it will warn you that it was expecting libmp3lame.so and ask if you want to use libmp3lame.so.0 instead click yes
if you dont have libmp3lame.so
sudo apt-get install lame

---

### Post by b_martinez on 2006-10-09
> **cmaranhao said:**
> i need help with exporting mp3's with audacity.. it asks me for a file that i don't know where it is (maybe i don't have it installed?))

the file name is libmp3lame.so

(i've set up audacity once and it worked, i can't remember how i did it last time)

libmp3lame.so is a needed file on your system to encode/decode MP3's. Your system needs it to do what you are attempting. If it's legal to install it where you live/work, then get it and re-try exporting with audcity.
Bill

---

### Post by cmaranhao on 2006-10-09
> maranhao@maranhao:~$ sudo apt-get install lame
Password:
Reading package lists... Done
Building dependency tree... Done
lame is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
maranhao@maranhao:~$


i have the file but when i look in /usr/lib i can't see it there

---

### Post by timnoc1456 on 2006-10-09
cmaranhao! lets learn from each other, I too only little of month old. When you search for the libmp3.so, in the browser window that appears click/enable show hidden files, then under usr/lib you will libmp3.so or libmp3.s.0 or libmp3.so.0.0, whichever it is, all I think is an MP3 encoder and works while encoding audio with audacity. I have tried it and it works.

This is provided you have installed the necessary so called libaries through synaptic packagemanager or easyubuntu.

---

