---
title: "New to Ubuntu - Random Video Bugs/Crashes after Install."
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Dev0205 on 2007-05-18
Hi all. I'd appreciate any support you can throw my way. I've really been having some fun the past few days trying to get Ubuntu to work correctly on my system. You see, The install "v7 I believe" went well and I had no problem customizing things. However, the system randomly locks up pretty bad "Can see the GUI and move mouse..just no interaction". Other times, the monitor makes a clicking sound and the video will go out. Both issues I can usually get out of by pressing Ctrl-Alt-Backspace and relogging in. 

I have an ATI9200 video card installed and believe it is what is causing all the fuss. I've read a few posts on the subject and even tried to install fglrx "forgive me if I'm not correct" but ended up messing up my xorg file..and having to reload Ubuntu all over again.

Any ideas? Aside from the system locking up or video going out..I'm absolutely loving Linux.

P/S-I'm about 3 days into switching and am pretty new to the lengo. 

Thank you,
Devin

---

### Post by vtel57 on 2007-05-18
Hi Devin,

WELCOME to the wonderful world of GNU/LInux. It gets easier once you know everything. ;)

This may or may not be video hardware related. There is a simple command that you can use within the Terminal that will help you properly configure your X (the windows system used by Ubuntu). Type this command into your Terminal:

```
 $ sudo dpkg-reconfigure xserver-xorg
```

Read and follow the steps. A mis-configured xorg.conf file could cause the problems you're experieincing. However, other hardware related issues could also be guilty. What are your basic system specs? CPU and speed, RAM, etc.

---

### Post by Dev0205 on 2007-05-18
vtel57,

Does the command $ sudo dpkg-reconfigure xserver-xorg work as a means of resetting X...in the event that I go and mess something up "I've already had to reinstall once"? On a side note..After the reinstall, things seem to be working correctly..not sure If it was something I installed like Beryl. 

About my system : I'm on a A7N8X Delux Mobo, with AMD Athlon XP 1800+, ATI 9200 Video Card, 512 of ram. Thank you for your help.

Devin

---

### Post by vtel57 on 2007-05-19
Absolutely! dpkg-reconfigure can save your rear end should you crash your X by tweaking xorg.conf. If you can boot to the command line, this command will save you. You can also manually fix xorg.conf using your Live CD.

Hopefully, you're reinstall fixed whatever bugaboo you were having. 

Have FUN with it... that's what it's all about! :)

Later...

---

