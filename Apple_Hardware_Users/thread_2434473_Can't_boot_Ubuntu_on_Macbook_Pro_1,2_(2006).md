---
title: "Can't boot Ubuntu on Macbook Pro 1,2 (2006)"
date: 2020-01-06
forum: Apple Hardware Users
---

### Post by sergio-rondan on 2020-01-06
Hi all! Im new in this forum.

Im from Argentina, my english is very poor, so excuse me for that. I cant understand all that i read but my writing is awful.

Here is my problem.

I bought recently a Macbook pro 1,2 core duo and i want to install Lubuntu 18.04. Im already a user of linux, i used it since 10 years ago.

I write the lubuntu iso to a pendrive, but i cant boot it. When i reboot the macbook pro and press the Option Key, there's no option to boot from usb, only to boot from hard drive. I tried to burn a dvd with the iso, and the problem is the same. I cant see nothing to boot. I tried various solutions that i found in internet but nothing works, i think because all of that solutions are for others models of macbook.

can someone help me? its was more easy to install lubuntu 16.04 on a powerbook g4 with powerpc !

many thanks!

---

### Post by eight-quarter-bit on 2020-01-10
I'm reaching waaaay back in the memory banks for this one, but if I recall correctly certain old models of Intel-based Macs had very limited boot pickers that didn't support many distros. Check out [rEFInd]("http://www.rodsbooks.com/refind/") as a replacement boot picker with better Linux support.

---

### Post by vashxp on 2020-01-17
Hi Sergio, do you solved the problem ?
I guess rEFInd its the soluction for for you.

---

### Post by sergio-rondan on 2020-01-21
Im gonna try rEFInd boot manager and see whats happend

---

### Post by sergio-rondan on 2020-01-21
well, in writing this post in the macbook pro 1,2 with lubuntu 18.04, thanks¡¡¡

i have two problems more, i cant get the sound working. I see the chanells unmuted on the alsamixer, and i see the chanells working, but still no sound. in the powerpc, i have to add the sound module to etc/module, i have to do that?
another thing is the webcam, ¿i need to install some special package?

many thanksssss!!!!!!!!!!!

EDIT: the webcam is working, only the audio is not working

---

### Post by gsahli on 2020-01-22
I can only recommend this OLD info:
[https://help.ubuntu.com/community/MacBook1-1/Hardy](https://help.ubuntu.com/community/MacBook1-1/Hardy)

---

### Post by sergio-rondan on 2020-01-22
that post didnt work, but this [https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/289674](https://answers.launchpad.net/ubuntu/+source/alsa-driver/+question/289674) works

thanks!!!!

---

