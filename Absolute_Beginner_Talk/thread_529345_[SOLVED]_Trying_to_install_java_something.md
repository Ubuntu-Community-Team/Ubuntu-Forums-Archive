---
title: "[SOLVED] Trying to install java something"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by KaylaJay on 2007-08-19
I think I'm having a problem doing the same thing. As far as I can tell: Yes, it CAN be that hard. But hopefully somebody can help me :). So, I've gotten as far as typing a bunch of babble into my terminal that I found on the internet and it seems to have worked. The website said that my terminal would give me a screen that was a distributor license, and that I would have to hit enter, or OK. This happened, but for some reason the <OK> at the bottom is not a button that I can click, and the enter key does nothing. I'm stuck here. I tried beginning the process all over again, but my terminal is one smart cookie, because it seems to know that I've got this process halfway completed and won't let it start again. So... I guess it's not the end of the world if I don't get this plugin, but it would be nice. I highly doubt anybody's reading this since the original post was like 4 weeks ago, but we'll give it a shot since I'm pretty much running out of options here. As you can probably tell, I know absolutely nothing about my own operating system, and you can go ahead and laugh just like everybody seems to do when I ask for help. But you should know that I'm a tad frustrated right now so please get that out of your system and lend me a hand here, I'd most appreciate it.
Thanks!

---

### Post by Surkow on 2007-08-19
> **KaylaJay said:**
> I think I'm having a problem doing the same thing. As far as I can tell: Yes, it CAN be that hard. But hopefully somebody can help me :). So, I've gotten as far as typing a bunch of babble into my terminal that I found on the internet and it seems to have worked. The website said that my terminal would give me a screen that was a distributor license, and that I would have to hit enter, or OK. This happened, but for some reason the <OK> at the bottom is not a button that I can click, and the enter key does nothing. I'm stuck here. I tried beginning the process all over again, but my terminal is one smart cookie, because it seems to know that I've got this process halfway completed and won't let it start again. So... I guess it's not the end of the world if I don't get this plugin, but it would be nice. I highly doubt anybody's reading this since the original post was like 4 weeks ago, but we'll give it a shot since I'm pretty much running out of options here. As you can probably tell, I know absolutely nothing about my own operating system, and you can go ahead and laugh just like everybody seems to do when I ask for help. But you should know that I'm a tad frustrated right now so please get that out of your system and lend me a hand here, I'd most appreciate it.
Thanks!
Not a button you can click? You cannot click on buttons in a text interface. Use the keyboard to navigate (for example with the arrows/tab) and press enter when "ok" is selected..

---

### Post by KaylaJay on 2007-08-19
I'm trying to install some kind of java plugin and I think I've done everything right so far, but I've hit a roadblock. I found some code stuff on the internet which I typed in my terminal and it began to install. The website told me that I would get a screen which was a license or something, at which point I am supposed to select OK or hit enter. I got this screen, just like it told me I would, only the <OK> at the bottom isn't a button I can click, and my enter key does nothing. I'm stuck. I tried opening a new terminal and trying again, but it seems to know that I've gotten halfway through and it won't let me try again. I feel rediculous because I know everybody who reads this will see exactly how stupid I am. But I am seriously at the end of the rope with this one. I've tried everything and I'm getting really frustrated. I'm willing to sacrifice my pride just to make my computer work. I know this is probably a stupid question, but please help me!

---

### Post by aysiu on 2007-08-19
Click into the text.

Press Tab until the OK "button" is highlighted.

Then, hit Enter to select OK.

---

### Post by KaylaJay on 2007-08-19
Oh My God. You are my hero. You can probably tell I know absolutely nothing about this, but I'm learning..... sloooooowly but surely. Or at least I'm REALLY trying. Thanks a lot, ohh how rediculous I feel! And thanks for the quick response, I really had to work up the guts to actually post this, I was convinced everybody would be laughing. (ok, i know you're laughing, its ok, but seriously thanks for the help!)

---

### Post by aysiu on 2007-08-19
Everything always seems "obvious" *after* you've learned how to do it. Before you do, it's all a big mystery.

Please do not be afraid to ask questions. We don't bite!

---

### Post by KaylaJay on 2007-08-19
Umm... oops... ok I figured out how to do all that, and it's going on with this whole installing process but... it stopped and said there was an error while processing something called bitpim. Any ideas? if you're still reading this, that is. If not thats ok, i just though you guys might know and it would save me the time of sifting through google searches, you know... but i've sort of picked up this vibe about forums where people really don't like it when you post things in the wrong place, so it's alright if that's the case too... just wondering.

---

### Post by aysiu on 2007-08-19
You're posting in the right place.

Can you copy and paste the exact error message relating to *bitpim*?

---

### Post by KaylaJay on 2007-08-19
Here's everything from where it seems to go wrong until the end

dpkg: error processing bitpim (--configure):
 subprocess post-installation script returned error exit status 1
Setting up sun-java5-bin (1.5.0-11-1ubuntu2) ...

Setting up sun-java5-jre (1.5.0-11-1ubuntu2) ...

Errors were encountered while processing:
 bitpim
E: Sub-process /usr/bin/dpkg returned an error code (1)
root@kayla-laptop:/home/kayla#

---

### Post by aysiu on 2007-08-19
Are you using Ubuntu 7.04 (Feisty Fawn)? If so, can you try pasting these commands into [the terminal](http://www.psychocats.net/ubuntu/terminal)? ```
exit
sudo aptitude remove sun-java5-jre sun-java5-bin
sudo aptitude install sun-java6-plugin
```

---

### Post by KaylaJay on 2007-08-19
It said pretty much the same thing:

Setting up bitpim (1.0.0) ...
cp: cannot stat `/usr/lib/BitPim-1.0.0/resources/60-bitpim.rules': No such file or directory
dpkg: error processing bitpim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bitpim
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:
Setting up bitpim (1.0.0) ...
cp: cannot stat `/usr/lib/BitPim-1.0.0/resources/60-bitpim.rules': No such file or directory
dpkg: error processing bitpim (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 bitpim

---

### Post by KaylaJay on 2007-08-19
ohh wait. i tried it agian and it's doing something. I think maybe i missed the word exit the first time.

---

### Post by KaylaJay on 2007-08-19
Welll, it went through everything all over again from the beginning, but it ended with the same error.

---

### Post by aysiu on 2007-08-19
Hm. How about this? ```
sudo dpkg --configure -a
```

---

### Post by KaylaJay on 2007-08-19
It gave me the same error message.

---

### Post by KaylaJay on 2007-08-19
If you're pretty much running out of ideas, that's ok. I sort of accidentally stayed up all night because i'm, you know... becoming addicted to my computer. But my eyelids are starting to be kind of magnetic so if this is gonna get pretty complicated, I can give it a rest until tomorrow. (unless you've got any other fabulous tricks up your sleeve).

---

### Post by KaylaJay on 2007-08-19
Oh my gosh! I did it!!! All i did was go back to the website that originally asked me to download the plugin, and refreshed it. It gave me a bunch of error boxes, you know, but I just kept hitting OK, and after 3 or 4, I guess it figured itself out! Well, thanks for your help, I'm totally going to always come back here when i get stuck!
P.S. I'm glad you don't bite!

---

