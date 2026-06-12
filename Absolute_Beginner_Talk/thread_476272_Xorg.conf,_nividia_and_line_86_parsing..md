---
title: "Xorg.conf, nividia and line 86 parsing."
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by Mairi on 2007-06-17
A friend of mine has messed up her system, and since -I-, with my two month's experience, am somehow her online technical support, I need to ask a question.

She's trying to play Eve Online. She followed this.

[http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=420926](http://myeve.eve-online.com/ingameboard.asp?a=topic&threadID=420926)

She got the Nividia drivers in, according to the directions. Part 2. And she can't reboot. She gets this.

[CODE](==) Using config file: "/etc/x11/xorg.conf"
Parse error on line 86 of section
Imput Device in file /etc/x11/xorg.conf
"'" is not a valad key word in this sectionn.

(EE) Problem parsing the Config File
(EE) Error parsing the config file

Fatal screen error:
no screens found[CODE]

Upon trying the reconfig dpkg-reconfig -phigh xserver-xorg, that I found on the forums and suggested. Only thing I could think of, since I've never dealt with with this issue.

She's on Feisty, she has a Nividia card...doesn't know what kind.

ANY help would be gratefully appreciated.

(Oh, and yes it really IS someone else and not me!)

---

### Post by meborc on 2007-06-17
ok, from the link you posted: > Locate the section: Section "Device"
Change the driver from "nv" to "nvidia"
Add the following options:
Option "NvAGP" "1"
VideoRam 131072 there might be a typo mistake your "friend" made :) boot into recovery mode and open the xorg.conf file... eliminate the options lines you added (NvAGP and videoram) try to see if this way your compuuter boots normally... if so then those lines were the problem

which ubuntu version is your friend using? 6.10 or 7.04? read this on binary nvidia drivers (cause that is what no2 point in the link is trying to do...) - [https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia) there is a different way to install it in feisty... the quide you linked installs it the "old" way

the last thing to do is to force "sudo dpkg-reconfigure xserver-xorg" and chose nvidia from the drivers list...

hope you (sry, your friend) gets it working

:D

edit: and oh, check out the line nr 86 in xorg.conf :) as it seems to be the trouble maker... as you posted yourself the error message which says you have an extra "'" mark in that line :D

---

### Post by Mairi on 2007-06-17
She got it fixed, thanks a lot. SHE is a happy girl. Who lives in California. I live in NC, so THERE! hehe. Anyhow, I thought it might just take a reconfigure, but in all the ways I've messed up my comp, I haven't messed up X yet. *knocks on all kinds of wood*. As everyone here knows, it's SO hard to advise over a distance, to someone who knows even less than I do. 

You're the greatest!

---

