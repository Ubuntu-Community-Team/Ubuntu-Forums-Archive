---
title: "how do you play ram files in ubuntu?"
date: 2007-06-18
forum: Absolute Beginner Talk
---

### Post by legolas_w on 2007-06-18
Hi
thank you for reading my post
can you pelase tell me what is best tool to play 
urls like
[http://www.bbc.co.uk/worldservice/learningenglish/flatmates/episode01/episode.ram](http://www.bbc.co.uk/worldservice/learningenglish/flatmates/episode01/episode.ram) 


in ubuntu?


thanks

---

### Post by koshari on 2007-06-18
i was just thinking this tonight..... does anyone still use real media?

---

### Post by RomeReactor on 2007-06-18
Hi. You can download [Real Player]("http://www.real.com/linux"). After downloading it (preferably save it in your desktop), you install it following [these steps]("http://ubuntuforums.org/showthread.php?p=2717302#post2717302").  Take note of where you install it, you'll need to know the location of the **RealPlayer** folder (if you're the only user on your system, you can install it in your home folder); so when the installer asks you the location to install, you tell it to install in **/home/YOUR_USER_NAME**. After the installation finishes, post back so, if you want, we go about making an entry for it in the menu.

---

### Post by AtrejuT on 2007-06-18
gxine can play some .ram-files but I did have problems occasionally.
There is also a realplayer for linux:
[http://forms.real.com/real/player/blackjack.html](http://forms.real.com/real/player/blackjack.html)
not free as in speech, but free as in beer...

mhm... to late... and the link above was way better too...

---

### Post by ugm6hr on 2007-06-18
This is an easier way to install Realplayer, and get it to work with BBC website (which has caused a few problems in Linux):

Download this:
[http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb](http://www.youmortals.com/ubuntu/packages/realplayer_10.0.7-0.0_i386.deb)

Then open it (double click from File Manager). It should automatically open and install in GDebi.

I would recommend you then go to:
[https://addons.mozilla.org/en-US/firefox/addon/446](https://addons.mozilla.org/en-US/firefox/addon/446)
And Click on install now to get Media Player Connectivity which will allow you to define realplayer as default player for realmedia (assuming you have Firefox).

Interestingly, VLC media player can play windows media player files, although I haven't yet been able to get sound to work, so I stick to realplayer.

PS: This is for Feisty, since realplayer seems not to be in Synaptics for Feisty.

PPS: I am not hosting this - just passing the information on... Don't want to take credit for someone else's work!

---

### Post by RomeReactor on 2007-06-18
**legolas_w**, in case you haven't yet downloaded or installed Real Player from their official site, I just found out [ugm6hr]("http://ubuntuforums.org/showpost.php?p=2720883&postcount=4") seems to be maintaining a .deb file for it. Much easier to install.

EDIT: Ooops. Speak of the devil...

---

### Post by jeroach on 2008-04-02
ugm6hr's link does not work.

---

### Post by hyper_ch on 2008-04-02
realplayer is in the ubuntu partner repos. That's probably the easiest way...

---

### Post by philinux on 2008-04-02
When i clicked that link it was mplayers plugin which picked it up. Mozilla-mplayer.

However on the bbc website to listen radio streams I use the helix dna plugin which gets installed along with realplayer.

[http://archive.canonical.com/pool/partner/r/realplay/](http://archive.canonical.com/pool/partner/r/realplay/)

Choose the last one in the list. Dont worry is labelled feisty. The gutsy one has a bug that does not install the helix plugin.

---

### Post by ugm6hr on 2008-04-02
I'd suggest everyone read this: [http://ubuntuforums.org/showthread.php?t=661833](http://ubuntuforums.org/showthread.php?t=661833)

My previous posts are probably outdated now.

---

### Post by philinux on 2008-04-02
+1

The only thing i would say is the mplayer settings dont work on my rig but I would expect thats a one off. I had to use x11 for video.

---

### Post by hyper_ch on 2008-04-02
I still think adding the partner repos is the simplest way for getting RealPlayer

---

