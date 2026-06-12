---
title: "updating repository without any internet (Solved)"
date: 2006-10-15
forum: Absolute Beginner Talk
---

### Post by shifan on 2006-10-15
does any one of you know a way to upgrade the ubuntu repository without having any inter net connection?

---

### Post by shifan on 2006-10-15
does any one of you know a way to upgrade the ubuntu repository without having any inter net connection?

---

### Post by aysiu on 2006-10-15
Do you mean going from Dapper (6.06) to Edgy (6.10)?

You would download (from another computer that *has* an internet connection) an Edgy Alternate CD. The Desktop CD will not do it!

Then you would paste these commands in the terminal: ```
sudo mv /etc/apt/sources.list /etc/apt/sources.list.old
sudo apt-cdrom add
sudo aptitude update
sudo aptitude dist-upgrade
```

---

### Post by shifan on 2006-10-19
im using version 5.10. i like to know is there any particular file or files to copy then update. i can use an internet cafe to download. after adding the repositories its easy with the synaptic to add the software all i have to do is use the "save markings" and use the file in the cafe and download them and use the "add downloaded packeges". ubuntu is great, but im an infant in the subject.

thank you.

---

### Post by aysiu on 2006-10-19
Please specify what you're trying to do.

Do you want to install software or upgrade to Dapper?

If you're trying to upgrade to Dapper, use the instructions in my previous post.

If you're trying to install software, try this:
[https://ubuntuplus.bountysource.com/](https://ubuntuplus.bountysource.com/)

---

### Post by shifan on 2006-10-22
no sir i dont want to upgrade the os because my pc is 800mhz. i only want to install softwares and codecs. sorry for the confusion as i have said im still a infant in the subject. thank you very much for you support. i will try your new suggestion and reply. god bless you

---

### Post by shifan on 2006-10-22
**Yes !**:p aysiu. you have solved my problem now i can play mp3 wich why i usually use the computer for. i have another question but i cant ask here. i searched the forum but couldnt get an answer. thank you very very very much :p

---

