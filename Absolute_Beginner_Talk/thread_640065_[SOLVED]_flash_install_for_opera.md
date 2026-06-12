---
title: "[SOLVED] flash install for opera"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by blackpit on 2007-12-13
Hello everybody.I've recently installed ubuntu 7.10 and i have spent lots and lots of hours trying to get flash player to work with opera.I've read almost every post i could find on the web and tried everything and failed time after time.By the way flash player works fine with firefox.I have come to the conclusion that the problem lies with the file flashplayer.xpt.It supposed to be in the install_flash_player_9_linux folder but in there exist only these two files: flashplayer-installer and libflashplayer.so.I have searched everywhere but there's nowhere to be found.It's like a ghost or something.Any ideas?

---

### Post by Joe Dinmore on 2007-12-13
Flash works fine in version 9.50beta - not so good in 9.24

---

### Post by SunnyRabbiera on 2007-12-13
hmm, well opera should recognize where firefox puts its plugins as I never had issues with it finding the plugins.
but yes flash is an issue in opera, its more operas fault though

---

### Post by LaRoza on 2007-12-13
I have no problem with Flash with Opera. Just installed it like I would for Firefox.

---

### Post by poisonblack on 2007-12-13
Ensure libflashplayer.so from adobe is your only flash plugin for opera.But even that won't be without problems.From what I have searches,I came to know that flash 9.0.47 works fine with opera 9.24 while the latest version 9.0.64 works only with opera 9.50b

---

### Post by blackpit on 2007-12-14
I finally installed opera 9.50beta and it works fine.Thanks guys

---

### Post by PunkLV on 2007-12-20
Good day, This thread is NOT solved, author did solve the problem, but didnt care to post a reply! 

I have right now exactly the same thing. tar.gz, which had been downloaded from the Adobes main site, contains only 2 (two) files, which are listed above. On the other hand, Installing via Synaptic (flashplugin-nonfree) works swell, except the fact that it also doesnt have flashplayer.xpt file. It creates s-links to them, which are broken. 

I've managed to fix this w/ flash*.so file, but since i just dont have the required flashplayer.xpt i cant get latest Opera 9.25 to work. All I have now, is that i dont get bothered with a msg "pls install flash". 

Therefore. Someone please send it to [email]punk.lv@inbox.lv[/email]
As i see no other options.

---

