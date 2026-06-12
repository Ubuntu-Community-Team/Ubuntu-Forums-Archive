---
title: "Firefox 2.0b1 install problems."
date: 2006-07-21
forum: Absolute Beginner Talk
---

### Post by ramcosca on 2006-07-21
I just downloaded and followed the instructions to install Firefox 2.0b1 on my (newly installed :mrgreen: ) dual-boot desktop. I follow the instructions posted on the Mozilla website... ```
Installing Firefox 2 Beta 1

Once you have downloaded Firefox 2 Beta 1, follow these instructions to install:

Linux/GTK2

Extract the tarball and run ./firefox:

tar -xzvf firefox-2.0b1.tar.gz
cd firefox
./firefox 
```

And it works. It extracts from the tar and opens Firefox 2.0b1 (I'm running it right now)... but that's about it.  It won't appear on the Apps menu and it seems that the computer wants to keep using FF 1.5... no way out of that. ](*,) 

So please UbuntuForums users, pimp my Linux. :-|


[Note] Ok, so... it keeps doing it. While I previewed this message, I noticed that the Terminal was still open and decided to close it. Third time I do it today... third time it takes Firefox 2.0b1 with it today. (If I close Terminal it closes Firefox, get it?) What can I do? :(
[Note 2] Hey, Firefox 2.0b1's page recovery thing works! It even kept the text here... lol!

---

### Post by Lord Illidan on 2006-07-21
Just change the GNOME menu icon with alacarte.

Make the firefox command to your firefox executable location.

---

### Post by chickengirl on 2006-07-21
(you've got it installed in your /home, right?)

Change the Firefox launcher on your panel so that it uses the command **~/firefox/firefox** rather than firefox or mozilla-firefox or whatever the default is. Now the launcher will open your installation of Firefox rather than the default ubuntu one.

---

### Post by ramcosca on 2006-07-22
Ok, ok, but... the thing is... it just doesn't add itself to the menus or wherever....

If I close the terminal, it closes Firefox with it... and it just... dissapears. If I were to open 2.0b1 again, I'd have to "untar" again and ***then* ** go to the directory and run the program. It just doesn't save it there or something. ](*,)

> **Lord Illidan said:**
> Just change the GNOME menu icon with alacarte.

Make the firefox command to your firefox executable location.I'll see if this has anything to do with it... I'll just shortcut while it's open, I assume.> **chickengirl said:**
> (you've got it installed in your /home, right?)No idea if it even installed. :-? > **chickengirl said:**
> Change the Firefox launcher on your panel so that it uses the command **~/firefox/firefox** rather than firefox or mozilla-firefox or whatever the default is. Now the launcher will open your installation of Firefox rather than the default ubuntu one.Is this the same thing as Lord Illidan mentioned? (Alacarte Menu Editor).


I'll see if I can get results when I reboot. On XP now... ](*,)

---

### Post by ramcosca on 2006-07-22
Uhm...  got it to work. It did not save when I 'untar-ed' it before... but it may be my computer, after all. It's all shucked up.

Thanks. :D

---

