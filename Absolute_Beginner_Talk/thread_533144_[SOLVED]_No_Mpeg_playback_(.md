---
title: "[SOLVED] No Mpeg playback :("
date: 2007-08-23
forum: Absolute Beginner Talk
---

### Post by chrome307 on 2007-08-23
I have no idea why this does not work :confused: Not one of the installed players can handle a VCD disc ..... have also tried VLC same result

[IMG]http://img522.imageshack.us/img522/6620/21383472eb0.jpg[/IMG]

[IMG]http://img516.imageshack.us/img516/1079/16145770mr3.jpg[/IMG]

[IMG]http://img522.imageshack.us/img522/5102/69212612oa4.jpg[/IMG]

[IMG]http://img522.imageshack.us/img522/9337/80915430ll5.jpg[/IMG]

[IMG]http://img516.imageshack.us/img516/66/42596518ds5.jpg[/IMG]

---

### Post by chrome307 on 2007-08-23
I have also tried this, with no luck

```


in synaptic, gstreamer0.8-misc should give you vcd playability.


```

Package installed .... still no playback facility

---

### Post by jingo811 on 2007-08-23
Did you follow this tutorial?  Which is a sticky in the Absolute Beginners section.
[http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)

---

### Post by stchman on 2007-08-23
Try my procedures here.

Installs the Medibuntu stuff
[http://www.stchman.com/dvd_rip.html](http://www.stchman.com/dvd_rip.html)

Use the big apt-get gstreamer stuff
[http://www.stchman.com/cd_rip.html](http://www.stchman.com/cd_rip.html)

I can play any media type.

---

### Post by chrome307 on 2007-08-23
Yes I did follow the tutorial posted. [COLOR="Red"](the sticky)[/COLOR]

Followed the instructions in the 2nd tutorial and the only program that gives me playback is VLC. The others Mplayer - Totem and Xine simply fail to respond.

I'm very surprised with Mplayer as I use this on my Xbox console for a number of years now, so am disappointed this failed in this instance.

Thank your for your advice/suggestions!!

---

### Post by mcduck on 2007-08-23
> **chrome307 said:**
> I have also tried this, with no luck

```


in synaptic, gstreamer0.8-misc should give you vcd playability.


```

Package installed .... still no playback facility
In feisty most programs use gstreamer0.10, not older gstreamer0.8. So try installing all available gstreamer0.10-plugins...

The mplayer error seems to be about selected video output, not about the VCD itself. Try some other video output in mplayer's options.

---

### Post by jingo811 on 2007-08-23
Well I remember once when I needed to watch some VCD disc.  Even after doing all the official general media codec installs it still wasn't working.

4 months back when someone didn't tell my how bad recommeding Automatix would be for new users.  I used it to install some media player by point and click it worked.  The GUI was really ugly and not clean but it worked compared to Mplayer, VLC, Totem.

Maybe I'm just bad at installing VCD support for those mentioned players.  But Automatix helped me in a jiffy for that issue.
Psst. you didn't hear that from me regarding using[COLOR="Red"] Automatix[/COLOR] on your Ubuntu 8-[ 
( [COLOR="Red"]it has wrecked ppls Ubuntus before but it worked for me from day one so...[/COLOR])

---

### Post by chrome307 on 2007-08-23
Thanks for the advice, I've decided just to stick to VLC as my native video player and removed the others.

---

