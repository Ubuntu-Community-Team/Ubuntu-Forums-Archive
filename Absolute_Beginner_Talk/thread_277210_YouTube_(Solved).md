---
title: "YouTube (Solved)"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by spyker3292 on 2006-10-14
When I play youtube videos from firefox there isn't sound. Anyone know how to fix this?

---

### Post by sdubois92 on 2006-10-14
The problem porbably isnt youtube, its probably that ubuntu hasnt detected your soundcard.
 go to the #ubuntu room on freenode. they helped me when i had this problem.

---

### Post by xpod on 2006-10-14
I had the same issue with online sound and was given this

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd
```

after a reboot you tube and google video sound all worked great...

---

### Post by ThrobbingBrain66 on 2006-10-14
> **spyker3292 said:**
> When I play youtube videos from firefox there isn't sound. Anyone know how to fix this?

hi spyker, try this howto.  the first part is on installing flash, but the second tells you how to fix the no sound problem.

[http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox](http://ubuntuguide.org/wiki/Dapper#How_to_install_Flash_Player_.28Macromedia_Flash.29_Plug-in_for_Mozilla_Firefox)

good luck,
brad

---

### Post by pay on 2006-10-14
Do you get sound outside of youtube?  Try using oss.
```
sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
```change```
FIREFOX_DSP=""
```to```
FIREFOX_DSP="aoss"
```

---

### Post by spyker3292 on 2006-10-14
> **xpod said:**
> I had the same issue with online sound and was given this

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd
```

after a reboot you tube and google video sound all worked great...

perfect!

---

### Post by xpod on 2006-10-14
Sometimes sound will still get zonked when you use different apps so try using the "multimedia system selector" in the preferences tab.....

If it aint in the menu then use the alacarte menu editor and scroll down to prefs,click on it then check the box for the MSS...

It will let you easily check sound and change which kind you use...or might need to use.....

Thats my first port of call... ive also had to run that second command again too once when my sound went again.....

Good luck regardless:mrgreen:

EDIT:...excuse me while my wife runs round the square naked.......she did promise to IF any advice i ever gave anybody actually worked:D ...
...Bout time she got an ASBO

---

### Post by cunawarit on 2006-10-14
I had the same problem with Debian Etch. All sounds would play for all apps, except the Flash plugin. 

I installed the ALSA drivers, ran the config, rebooted and it worked... Try Googling for it, I found plenty of ppl who had the same problem with plenty of step by step solutions.

---

### Post by raul_ on 2006-10-14
Tons of threads about this problem in the forum =p

---

### Post by xpod on 2006-10-14
me thinks he solved it 3 posts ago:mrgreen:

---

### Post by raul_ on 2006-10-14
That was not the point :) anywayz, solved

---

### Post by r4ik on 2006-10-14
> **xpod said:**
> I had the same issue with online sound and was given this

```
sudo ln -s /usr/lib/libesd.so.0 /usr/lib/libesd.so.1
ln -s /tmp/.esd-1000 /tmp/.esd
```

after a reboot you tube and google video sound all worked great...

I have been searching for that one thanks !

---

### Post by Sef on 2006-10-14
> Do you get sound outside of youtube? Try using oss.
Code:

sudo aptitude install alsa-oss gksudo gedit /etc/firefox/firefoxrc

change
Code:

FIREFOX_DSP=""

to
Code:

FIREFOX_DSP="aoss"



Thank you pay.  That solved my problem.  It's nice to have sound on youtube.

---

### Post by xpod on 2006-10-14
I cant believe a staff member was having trouble with their sound too;) 
Seems like sound is one of the most common problems....for ALL of us..eh??lol

PS...Sorry for missing the point......a habit of mine;)

---

### Post by PriceChild on 2006-10-14
> **xpod said:**
> I cant believe a staff member was having trouble with their sound too;)May be hard to believe but we're just you with extra buttons to press :P

I had problems a few weeks ago which boiled down to ubuntu trying to output to by video tuner instead of sound card... but anyway...

---

### Post by xpod on 2006-10-14
lol.....Yeah i realise that but you`se must have some sort of extended knowlage to get the positions in the first place.....

The thought of "you" all being just like "me" with extra buttons is indeed a frightening thought to behold.I only switched a pc on in march and i got too many buttons as it is:confused: 

This forum would be ten times as busy;)

EDIT:great job by all of you`se regardless

---

### Post by jkvv_1973 on 2006-10-18
> **pay said:**
> Do you get sound outside of youtube?  Try using oss.
```
sudo aptitude install alsa-oss
gksudo gedit /etc/firefox/firefoxrc
```change```
FIREFOX_DSP=""
```to```
FIREFOX_DSP="aoss"
```



This worked for me too...thanks so much!!!

---

### Post by Burningorc on 2006-10-22
Sorry if this is digging around in an old forum, but xpod's help fixed one of the major problems this particular rookie was having. I just copied and pasted it into the terminal and re-opened the page, and like magic it worked. Thanks alot.

-Orc

---

