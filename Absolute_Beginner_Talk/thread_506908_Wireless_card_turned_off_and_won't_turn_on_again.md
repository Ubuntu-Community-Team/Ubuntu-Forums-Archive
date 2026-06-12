---
title: "Wireless card turned off and won't turn on again"
date: 2007-07-22
forum: Absolute Beginner Talk
---

### Post by CheshireMac on 2007-07-22
Hey folks. I've had a wifi connection for a week with basically no problems. Two days ago, I stopped getting any signal from any router, and I can't seem to get it back. I tried turning the power back on for my card, but it's not permitted. I don't know what else to do now except plead for help. I'm screwed without my connection, so please help! Thanks.

---

### Post by omegamike3 on 2007-07-22
Is the card being seen by Ubuntu? is this a notebook or desktop machine? what type of card is it?

---

### Post by CheshireMac on 2007-07-22
> **omegamike3 said:**
> Is the card being seen by Ubuntu? is this a notebook or desktop machine? what type of card is it?
I have a HP nc8000 laptop, running with an Intel 2200BG card, and yes, Ubuntu at least recognizes that the card is there.

---

### Post by walkerk on 2007-07-22
> **CheshireMac said:**
> I have a HP nc8000 laptop, running with an Intel 2200BG card, and yes, Ubuntu at least recognizes that the card is there.

are you using network-manager? i suggest removing it and using wicd instead:
```
sudo apt-get remove network-manager gnome-network-manager
```

to install wicd

edit sources.list:
```
sudo gedit /etc/apt/sources.list
```

add this to the above:
```
deb http://wicd.longren.org feisty all
```

now update throught terminal:
```
sudo apt-get update
```

install wicd:
```
sudo apt-get install wicd
```

its installed. to choose network: Applications > Internet > Wicd

to run daemon at login: System > Preferences > Sessions
Name: Wicd
Command: /opt/wicd/tray.py


still having troubles?

---

### Post by CheshireMac on 2007-07-22
So I've checked almost every possible solution, and I can't seeanything that would work in thissituation. I can't connect thecomputer to the net in any way (I'm using a cafe's computer). I'm unable to get a driver, but then,I shouldn't need to, since I've already had the net working. I just really need someone who knows what they're doing to walk me through what's happeninghere.

---

### Post by CheshireMac on 2007-07-22
This would be a wonderful fix if I was able to access the repos. Unfortunately, I have no way of connecting the machine in question.

---

### Post by omegamike3 on 2007-07-22
you may want to give wicd a try, if you haven't already.the one opportunity i've had to use it, it turned out i had a dying card anyways. but everyone else i know who's used it says that it works quite smashingly. otherwise you can always try intel's official drivers if you don't have those yet or perhaps want to try an alternative.

WICD:  [http://wicd.sourceforge.net/](http://wicd.sourceforge.net/)

Intel Drivers:  [http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1637&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21](http://downloadcenter.intel.com/filter_results.aspx?strTypes=all&ProductID=1637&OSFullName=Linux*&lang=eng&strOSs=39&submit=Go%21)

---

### Post by omegamike3 on 2007-07-22
> **CheshireMac said:**
> This would be a wonderful fix if I was able to access the repos. Unfortunately, I have no way of connecting the machine in question.

just go to the downloads section and grab the .deb
[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

---

### Post by Papi-KB7VGW on 2007-07-22
Is the radio turned on?  On my notebook function/f2 turns it on and off.  Had a problem where it wouldn't turn on no matter what.  Had to use windows to turn it on.  Haven't had a problem since.

---

### Post by walkerk on 2007-07-22
> **omegamike3 said:**
> just go to the downloads section and grab the .deb
[https://sourceforge.net/project/showfiles.php?group_id=194573](https://sourceforge.net/project/showfiles.php?group_id=194573)

if you're using a cafe's computer try burning this .deb to a cd.. if you can. then go **home** and run it..

edit: are you connecting using someone's wireless? i'm assuming yes because otherwise you could use the wired nic to connect.. ?

edit: the beer is talking :P

---

### Post by CheshireMac on 2007-07-22
> **Papi-KB7VGW said:**
> Is the radio turned on? On my notebook function/f2 turns it on and off. Had a problem where it wouldn't turn on no matter what. Had to use windows to turn it on. Haven't had a problem since.
The radio is off...crap. I never thought of that . ..okay. How do I turn it back on? I tried fn/F2, and it does nothing ...

---

### Post by CheshireMac on 2007-07-22
> **walkerk said:**
> if you're using a cafe's computer try burning this .deb to a cd.. if you can. then go run and run it..
 
edit: are you connecting using someone's wireless? i'm assuming yes because otherwise you could use the wired nic to connect.. ?
Screwed otherwise?

---

### Post by omegamike3 on 2007-07-22
> **walkerk said:**
> if you're using a cafe's computer try burning this .deb to a cd.. if you can. then go run and run it..

good call, i suppose i omitted that part...#-o

---

### Post by walkerk on 2007-07-22
> **CheshireMac said:**
> Screwed otherwise?

Not screwed. You say it was working before.. right?

lets see the following outputs

```
lspci | grep Network
```
```
iwconfig
```
```
iwlist scanning
```

---

### Post by omegamike3 on 2007-07-22
> **CheshireMac said:**
> Screwed otherwise?

there's always thumb drives and floppys?

---

### Post by CheshireMac on 2007-07-22
> **walkerk said:**
> Not screwed. You say it was working before.. right?
 
lets see the following outputs
 
```
lspci | grep Network
```
```
iwconfig
```
```
iwlist scanning
```
 
Okay, I think I did the first one wrong. . .what's that line character?
lwconfig comes up with all my options : lo, irda0, eth0, eth1, sit0.
eth1 is my wireless, and it reads : radio off, Essid is one I gave it (linksys), Power management is off, andthe rest is greek to me, and long to type...
The scan is only supported on eth1, and it came up with no results.

---

### Post by walkerk on 2007-07-22
> **CheshireMac said:**
> Okay, I think I did the first one wrong. . .what's that line character?
lwconfig comes up with all my options : lo, irda0, eth0, eth1, sit0.
eth1 is my wireless, and it reads : radio off, Essid is one I gave it (linksys), Power management is off, andthe rest is greek to me, and long to type...
The scan is only supported on eth1, and it came up with no results.

the line character is shift+\

copy each output from terminal and post it in here so we can see the full reading..

---

