---
title: "I have no sound in my ubuntu 6.06"
date: 2007-11-16
forum: Absolute Beginner Talk
---

### Post by pmn.blazer on 2007-11-16
Hello...
I have no sound in my compaq laptop..
Please help me to get sound...
best regards
blazer:(

---

### Post by Inxsible on 2007-11-16
Any particular reason you have gone with Dapper as opposed to Gutsy which is much newer and has out of the box support for a lot more hardware than Dapper?

Also if you give more information, it would be helpful. Have you tried the various how tos on getting sound working ?

---

### Post by pmn.blazer on 2007-11-16
yes...my compaq PC
and i think it is HDA Intel...
no sound!!!:(:(

---

### Post by pmn.blazer on 2007-11-16
please help me!!! 
no sound at all...
It make me ill for 2 month...
please...
which command i type or something
best regards
blazer

---

### Post by Sims2789 on 2007-11-16
> **pmn.blazer said:**
> please help me!!! 
no sound at all...
It make me ill for 2 month...
please...
which command i type or something
best regards
blazer

Modern usability-oriented operating systems don't need the command line, despite what Gentoo Linux users will tell you.

The problem is that many developers still have Gentoo mentality and won't make nice GUI install packages (.msi in Windows, GDebi in Ubuntu). It's almost as if they want to keep Linux from the masses. Microsoft conspiracy? ;-)

Anyway...

In Ubuntu 7.10, go to System -> Preferences -> Sound. Chances are, you want to select *HDA Intel (ALSA mixer)* under Default Mixer Tracks. Then, select the correct device from the list and make sure it's highlighted. I don't know which one's the right one for your computer, but on my laptop it's PCM.

If sound still doesn't work, go into the Volume Control by right-clicking on the speaker in the top menubar and make sure that the Speakers checkbox under the Switches tab is checked. Under the Playback tab, make sure the volume isn't muted.

---

### Post by Inxsible on 2007-11-16
open up a terminal and type in```
alsamixer
``` and make sure you increase the levels of all to the max

---

### Post by pmn.blazer on 2007-11-16
&#9484;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;[AlsaMixer v1.0.10 (Press Escape to quit)]&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9488;&#9474; Card: HDA Intel                                                              &#9474;&#9474; Chip: Realtek ID 268                                                         &#9474;&#9474; View: [Playback] Capture  All                                                &#9474;&#9474; Item: Master                                                                 &#9474;&#9474;                                                                              &#9474;&#9474;                       &#9484;&#9472;&#9472;&#9488;                        &#9484;&#9472;&#9472;&#9488;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9474;&#9618;&#9618;&#9474;                        &#9474;&#9618;&#9618;&#9474;                       &#9474;&#9474;                       &#9492;&#9472;&#9472;&#9496;                        &#9492;&#9472;&#9472;&#9496;                       &#9474;&#9474;                                                                              &#9474;&#9474;                                                                              &#9474;&#9474;                      94<>94                     100<>100                     &#9474;&#9474;                    < Master >                     PCM                        &#9474;&#9492;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;&#9472;


that is my  alsamixer fri....
:(
what can i do for next??

---

### Post by Pumalite on 2007-11-16
Have you tried this link:

 [https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

### Post by pmn.blazer on 2007-11-16
yes i have alreadyy try it but....
I dunna know how is it copy in where???
or sth...eventhrough i have tried it...

---

### Post by pmn.blazer on 2007-11-16
hello in here...

sudo mkdir -p /usr/src/alsa
cd /usr/src/alsa
sudo cp ~/downloads/alsa* .
sudo tar xjf alsa-driver*.bz2
sudo tar xjf alsa-lib*.tar.bz2
sudo tar xjf alsa-utils*.tar.bz2

sudo cp  ~/downloads/alsa* .

what do u think this one????what is that and how can i copy it????
to usr/src/alsa............


please help me again.

ref; i am doing as it doing 
[https://help.ubuntu.com/community/HdaIntelSoundHowto](https://help.ubuntu.com/community/HdaIntelSoundHowto)

---

