---
title: "Connect Ubuntu to Win XP????"
date: 2005-10-19
forum: Absolute Beginner Talk
---

### Post by tane_stelzer on 2005-10-19
Hi there,
I am new to linux. I have always wanted to change and now i have. But i have lots of things on my computer at home but would like them on my laptop. The laptop has Ubuntu Breezy and Dektop Win XP. I know i have to use Samba to connect them through network, and i have tried it but i simply don't understand what i have to do. Please explain with detail and tell me what all those commands mean cos i am simply to overwhelmed with all thes new things. 
Thank you very much.
Tane

---

### Post by patrick295767 on 2005-10-19
[QUOTE=tane_stelzer]Hi there,
I am new to linux. I have always wanted to change and now i have. But i have lots of things on my computer at home but would like them on my laptop. The laptop has Ubuntu Breezy and Dektop Win XP. I know i have to use Samba to connect them through network, and i have tried it but i simply don't understand what i have to do. Please explain with detail and tell me what all those commands mean cos i am simply to overwhelmed with all thes new things. 
Thank you very much.
Tane[/QUOTE]

I got same experience than you ... I started about 1-2 months ago.... now it's kind of workign as it was in windows... 
  [http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557)
  [B][U]
If you can[/U][/B], as me, try maybe to use NFS for a first step, then u'll go with samba... I'll look in my records, ... i have some stuffs about samba ... but u'd better have look there : 
[FONT="Arial Black"][SIZE="4"]http://ubuntuguide.org/#sambaserver[/SIZE][/FONT]

Let us know about ur progress !!

Pat'

---

### Post by UbuWu on 2005-10-19
Never tried it myself, but it should be pretty simple: system menu -> administration -> shared folders. Add some folders there and you should be able to access them from your windows pc.

---

### Post by Dr. Nick on 2005-10-19
As above just share a folder, but also look under "general windows sharing settings" by selecting "properties" on a share, make sure the workgroup is the same as the XP box. Then make sure "client for ms networks" and "file/print sharing" is enabled on Xp. Its in the network conrol panel somewhere. Then just open network places and look for your ubuntu. I did it a while ago wihout editng any text files but all gui method

---

### Post by tane_stelzer on 2005-10-20
Okay i will try that once i get home, but a question what is NFS is that another programm like Samba just easier. How doi install it.Do i need to configure anything?
Thanks
Tane

---

### Post by BoyOfDestiny on 2005-10-20
I just want to let you know I had it working out of the box. If your laptop could see your windows box before (i.e you had windows on it, and/or your windows box is sharing), it should be no problem.

I'm not sitting at my laptop right now but, under the Places menu, there should be connect to network. Just browse for your share.

You should see something like windows network, and when you double click, enter your username and pass for your win box.

---

### Post by onesojourner on 2005-10-20
Mine just took about 3 clicks and I was streaming stuff to the xbmc. just read all the check boxes. there is one that will let you browse files on the network. make sure you check-mark that one.

---

