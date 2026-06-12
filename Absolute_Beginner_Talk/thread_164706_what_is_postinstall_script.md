---
title: "what is postinstall script?"
date: 2006-04-23
forum: Absolute Beginner Talk
---

### Post by rajsarkar on 2006-04-23
I am trying to install msttcore fonts. I have downloaded the mstt fonts in a folder following a guide in the forum. However I don't understand the next step ie to use postinstall script to install the fonts. Pls help. TIA.

regards,

Raj

---

### Post by Nikusan on 2006-04-23
[QUOTE=rajsarkar]I am trying to install msttcore fonts. I have downloaded the mstt fonts in a folder following a guide in the forum. However I don't understand the next step ie to use postinstall script to install the fonts. Pls help. TIA.

regards,

Raj[/QUOTE]

```
sudo apt-get install msttcorefonts
```

---

### Post by rajsarkar on 2006-04-24
I already tried with apt-get. But the repository seems not working. Thats why I had been trying to install the fonts by installing them from other sources. When I searched the forum I found solution for similar problem, but the post talks about using postinstall script which I could not understand. 

Raj

---

### Post by Nikusan on 2006-04-24
[QUOTE=rajsarkar]I already tried with apt-get. But the repository seems not working. Thats why I had been trying to install the fonts by installing them from other sources. When I searched the forum I found solution for similar problem, but the post talks about using postinstall script which I could not understand. 

Raj[/QUOTE]

What is the error message when you try installing with apt-get?
What is the contents of your /etc/apt/sources.list file?

---

### Post by revaldo on 2007-02-07
postinstall script for msttcorefonts can be found in /usr/sbin/ directory.It can be edited
   with g-edit as root.

   If you want to install msttcorefonts open a terminal and type 
              sudo /usr/sbin/update-ms-fonts /tmp/mstt(where mstt is a directory you have 
    created and you have put all your *exe fonts)-thanks to an earlier thread

---

