---
title: "Flash movies"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by salvatordarling on 2007-12-28
Hey everyone,
so, I have the Gnash SWF player installed on my machine, but when I go to view flash movies (YouTube, IMDB trailers, animations etc) it either works very badly - the audio and video go out of sync - or not at all - it leaves wierd patterns all over the movie player screen. 
Any thoughts on what I can do?  I'm not super good at commands and stuff, so the simpler the better...

Thanks

---

### Post by n00blar on 2007-12-28
I have the same issue, and still trying to find a fix for it.
I followed the instructions from [here,]("http://www.psychocats.net/ubuntu/flashubuntu") but all Flash related content just looks bad, and it appears to put a lot of load on my CPU.

---

### Post by harlan on 2007-12-28
I think gnash is a beta release and you'll need the flashplugin
$sudo aptitude install flashplugin-nonfree

---

### Post by billgoldberg on 2007-12-28
Gnash is a good idea but in reality it sucks.

I would use it if it worked as good as the flash player, but it doesn't.

Using adobes flash player will solve the issue.

1. Go [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&Lang=Dutch") and download the .tar.gz file to your desktop.

2. Right-click the file and choose “extract here”.

3. Double click the folder and double click the installer.

4. Run it in terminal.

5. Follow the text installer and make sure you choose to install it for firefox.

6. Done (reboot firefox)

---

### Post by salvatordarling on 2007-12-28
> **billgoldberg said:**
> Gnash is a good idea but in reality it sucks.

I would use it if it worked as good as the flash player, but it doesn't.

Using adobes flash player will solve the issue.

1. Go [here]("http://www.adobe.com/shockwave/download/download.cgi?P1_Prod_Version=ShockwaveFlash&Lang=Dutch") and download the .tar.gz file to your desktop.

2. Right-click the file and choose “extract here”.

3. Double click the folder and double click the installer.

4. Run it in terminal.

5. Follow the text installer and make sure you choose to install it for firefox.

6. Done (reboot firefox)

Ooh, look at that!  You were right.  Thanks everyone for all your help.  I love these forums!

---

