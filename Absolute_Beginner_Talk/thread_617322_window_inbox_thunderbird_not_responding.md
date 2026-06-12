---
title: "window inbox thunderbird not responding"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by luvinit on 2007-11-19
Hi, every time I receive an email to the inbox folder of thunderbird 2.0.0.6, the program locks up and I end up having to close it, getting the message 

window inbox thunderbird not responding

to which I choose "force quit" to close it. This doesn't happen if the email is sent to the junk folder. I have tried compacting and deleting msf files, but it makes no difference. I have tried deleting everything, re installing, but it makes no difference. Any suggestions? Thanks.

Gutsy Gibbon upgraded from feisty.

---

### Post by cmnorton on 2007-11-19
How much RAM is installed?

What is running along with Thunrderbird?

I have an Acer Travelmate 630, and I increased its RAM from 250 MB up to its max-allowed with an intermediate upgrade to 750MB along the way to 1GB. The almost "hung" quality of Evolution stopped at 750 MB, and the system has started responding better at 1GB.

---

### Post by luvinit on 2007-11-19
Hi,
I have 1.5 gb ram. I am running firefox, moblock, firestarter, bittornado, compiz fusion. It was working fine until about a week ago. The only thing that changed was that the number of messages in the inbox increased and automatic updates as changed things on the Ubuntu setup. I have deleted and compacted all the old messages and folders, which is the only explanation that I am aware of that causes strange behaviour in Thunderbird. No matter what the program ceases working the moment something enters the inbox, but only the inbox.

---

### Post by philinux on 2007-11-19
How many messages are in your inbox?

Have you any addons, extensions installed?

---

### Post by luvinit on 2007-11-19
there are no longer any messages, but there were about 500 when the trouble started. I assumed this was the problem, but it remains now they're gone. The Torbutton add  on is installed, but I rarely use it.

---

### Post by banzayats on 2007-12-22
I have the same problem: every time I receive an email to the inbox folder, the program locks up. Message also the same: "window inbox thunderbird not responding".

Version of  ubuntu - Gutsy
Version of  thunderbird - 2.0.0.6
Addons:
[LIST=1]
[*]Contacts Sidebar 0.7.1 
[*]Dictionary Switcher 1.1.3 
[*]InfoLister 0.9f.2 
[*]Lightning 0.7 
[*]Remove Duplicate Messages (Alternate) 0.2.1 
[*]Russian hot keys bugfix 1.4.1 
[*]Russian spell dictionary 0.1 
[*]Tag the Bird 1.3 
[*]ThunderBirthDay 0.2.3 
[*]Ukrainian dictionary 1.4.0 
[*]United States English Dictionary 2.0.0.6 
[*]Update Notifier 0.1.5.3
[*]ViewSourceWith 0.0.9.1 
[/LIST]
Themes
[LIST=1]
[*]Azerty 'mail 
[*]Tango Icons for Thunderbird [&#1074;&#1099;&#1073;&#1088;&#1072;&#1085;&#1086;]
[*]Thunderbird (default)
[/LIST]
Any suggestions?...

---

### Post by philinux on 2007-12-22
Start it via the terminal in safe mode.

```
thunderbird -safe-mode
```

Once in compact the folders.

File>Compact

---

### Post by banzayats on 2008-01-03
> **philinux said:**
> Start it via the terminal in safe mode.

```
thunderbird -safe-mode
```

Once in compact the folders.

File>Compact

Nothing went out :(
The problem still goes on...

---

### Post by luvinit on 2008-01-07
Ok after a long drawn out process I discovered that my problem was caused by using a theme other than the default, such as the tango theme, for example. Don't use add on themes.

---

