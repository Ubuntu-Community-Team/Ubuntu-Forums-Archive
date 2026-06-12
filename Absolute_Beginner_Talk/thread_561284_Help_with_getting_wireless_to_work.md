---
title: "Help with getting wireless to work"
date: 2007-09-27
forum: Absolute Beginner Talk
---

### Post by docinsano on 2007-09-27
I am using a TRENDnet tew-503pi wireless card on my pc running xubuntu. I am new to xubuntu so i have no idea what to do. Ive looked long and hard for drivers but cant find any. Can someone please help me? Thanks in advance.

---

### Post by Seisen on 2007-09-27
Check this link out [http://madwifi.org/wiki/Compatibility/Trendnet]("http://madwifi.org/wiki/Compatibility/Trendnet")

---

### Post by docinsano on 2007-09-27
Thanks for the link, Seisen.
I just have to ask one last thing: how do I install the drivers once i have them?
Thanks again.

---

### Post by jon zendatta on 2007-09-27
how is the drivers packaged you want to install

---

### Post by docinsano on 2007-09-27
its a tar archive (gzip-compressed)

---

### Post by mendingo84 on 2007-09-27
extract the archive and it should have a README in it. follow the steps in there

---

### Post by docinsano on 2007-09-27
I'm not too familiar with terminal and the included readme is a little tough for me to understand. Is there a step by step guide for beginners? Thanks for the help so far.

---

### Post by jon zendatta on 2007-09-27
the drivers will probably be in tar.gz format 
so after you have downloaded try these entries in your terminal

cd ~/Destop
tar -xzvf 'file'.tar.gz
cd 'file'
. /configure
sudo make install

---

### Post by docinsano on 2007-09-27
still not understanding this very well, what exactly am i doing in terminal to install the drivers? What do all these words mean? i'm getting some of the basic terminal lingo but i really dont understand how to use it and do simple things with it. Such as install these damn drivers!

---

### Post by docinsano on 2007-09-28
well i tried some terminal stuff, but with no success. I kind of understand the interface but cant figure out how to get it all to work. Help!

---

### Post by docinsano on 2007-09-29
Alright, so i downloaded the madwifi drivers and followed the how to. However, after i tried to type "make" into terminal, it gives me a bunch of junk like makefile.inc:96 No such file or directory exists, makefile.inc:100 No such file or directory exists, and makefile.inc:159 target invalid.

what does this all mean and how do i get it to work properly?

Edit- Scanning the forums i read that this card is supposed to work out of the box provided that the restricted drivers are installed. I'm not sure if i have these drivers but there is something in the restricted devices manger menu. Anyways i still dont know how to set it up properly.

---

### Post by docinsano on 2007-09-29
bump

---

### Post by docinsano on 2007-10-02
Now that I have the drivers installed, all I need to do is figure out how to connect to the access point. I have a wpa passcode and I'm not completely sure how to get connected yet.

---

