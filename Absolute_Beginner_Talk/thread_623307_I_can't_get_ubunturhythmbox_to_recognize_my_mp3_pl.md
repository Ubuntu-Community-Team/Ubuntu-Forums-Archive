---
title: "I can't get ubuntu/rhythmbox to recognize my mp3 player"
date: 2007-11-25
forum: Absolute Beginner Talk
---

### Post by JBrehm on 2007-11-25
Hey guys,

Been using ubuntu now for a few months, overall I love it! Got a few issues such as not being able to view videos online without closing beryl, and not being able to watch stage6 divx type videos (gotta switch to XP for that... blah), having firefox randomly close on me, but overall, it's amazing!

One major problem though for me... I can't seem to get ubuntu and rhythmbox to recognize when I have my Creative Zen Touch mp3 player connected to the computer, thus not being able to put songs onto my mp3 player. Any idea what the matter is? Keep in mind I'm still very new to this and don't have much lingo down, so laymans terms would be amazing!

---

### Post by kodak on 2007-11-25
> **JBrehm said:**
> having firefox randomly close on me.!

Thant may be compiz, as firefox is the only thing i found to be buggy with compiz. all other programs and apps work swimmingly with it.

---

### Post by scrooge_74 on 2007-11-25
plug your player and then in a terminal type dmesg, the last couple of lines should tell you if it is being recognize or not

---

### Post by FuturePilot on 2007-11-25
Open Rhythmbox and open the Plugins menu Edit>Plugins I think. Enable the MTP Device Plugin and it should recognize it.

---

### Post by JBrehm on 2007-11-26
```
[ 2917.237302] usb 5-5: new high speed USB device using ehci_hcd and address 4
[ 2917.370372] usb 5-5: configuration #1 chosen from 1 choice

```

This is what I got after connecting my mp3 player and typing in dmesg in the terminal. Is this what I should see?

I also tried the plugin deal... these are the only plugins that I had for rhythmbox:

[[IMG]http://img139.imageshack.us/img139/65/screenshotconfigureplugyc4.th.png[/IMG]](http://img139.imageshack.us/my.php?image=screenshotconfigureplugyc4.png)

I also don't have the mp3 icon popping up on the desktop like I used to. Thanks guys!

---

### Post by FuturePilot on 2007-11-26
Hmm. It used to show up on the desktop? Maybe it's not an MTP device like I thought.

---

### Post by software pimp on 2007-12-22
try switching the mode from MTP to MSC - however you cant make playlists (im still trying to figure that one out)

---

### Post by JBrehm on 2007-12-26
So, I still don't have my Zen Touch working with ubuntu, and it's driving me nuts. 

It used to pop up on my desktop as an icon and I could easily access it through rhythmbox, but at some point it just stopped working. I try connecting it now and it simply won't connect. It doesn't even show through "Computer". And when I go to the terminal and type in dmesg, I get the same response I said I had gotten earlier.


ANY help possible? This and my problems with watching dvds and online movies is making me think the only thing ubuntu is good for is office work and internet.

---

### Post by roboxking on 2008-01-22
Hm, well, I followed what was told earlier, I went to plug-ins and enabled the Portable Player - MTP plug in, and my Zen V Plus worked just fine. There's no icon and I have to manage it through the player, but it connects just fine. (Windows is slowly becoming a distant memory.) If this doesn't help, then maybe your player is just too new technology. That's the only explanation I can give.

---

