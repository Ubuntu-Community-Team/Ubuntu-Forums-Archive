---
title: "Wifi Help!!!! Please"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by mrMistermattsy on 2007-01-06
I am completely new to Ubuntu and I can't find any help on any website on how to install drivers for wifi cards!! all i see is stuff about ndiswrapper and i downloaded about a million things and none of them installed it. See, I used damn small linux at one point and ndiswrapper was builtin and was shown on the control panel or whatever it was called. I see nothing of the sort with Ubuntu. I really badly need to install my Linksys wifi card and I have the driver but I need to know how to install the driver!! so basically im completely clueless when it comes to this and I need someone to walk me through this. But remember I am completely new to Ubuntu so I need detailed info on how to do this and/or get the stuff i need to get me up and running. ](*,)

---

### Post by Spin Doctor on 2007-01-06
Did you look at the following page:

[https://help.ubuntu.com/community/WifiDocs](https://help.ubuntu.com/community/WifiDocs)

---

### Post by mrMistermattsy on 2007-01-06
I just saw that but my card isnt listed I have a Linksys WMP54G and I do have the driver for it from its original setup cd. what I dont know is how to install the driver. help?

---

### Post by celem on 2007-01-06
I far prefer using a card that has native support, but your will work under ndiswrapper. See:

[http://www.ubuntuforums.org/archive/index.php/t-79742.html](http://www.ubuntuforums.org/archive/index.php/t-79742.html)

and 

[http://www.linuxquestions.org/questions/showthread.php?t=317009](http://www.linuxquestions.org/questions/showthread.php?t=317009)

---

### Post by Frak on 2007-01-06
The Windows driver for WMP54G wont work, the driver is present in Dapper Drake, but not Edgy Eft, so its present in 6.06 but not in 6.10, just to let you know, I have the exact same card, Belkins are more supported than linksys are, because Belkins use athero and broadcom chipset, while all Linksys cards use the Realtek and Ralink chipsets.

---

### Post by mrMistermattsy on 2007-01-06
ok i'm not sure what version of Ubuntu i have! my installation cd says version 6.06.1 lts. is that the one its supposed to be compatible with??

---

### Post by Frak on 2007-01-06
Supposedly, right click on the top bar->add to panel->network monitor->change lo to ra0->configure->wireless card->properties(or something like that)->then put in the necissary info into the boxes.

---

### Post by mrMistermattsy on 2007-01-06
well can you tell me what info I need?? I hope i dont need my IP

---

### Post by Frak on 2007-01-06
just set it to DHCP, and if that doesn't work, call your provider and ask for your Static IP address, but I doubt you'll need that.

---

### Post by mrMistermattsy on 2007-01-06
thanks i hope that'll work. i really dont want to go through anymore trouble.

---

### Post by Frak on 2007-01-06
oh and set the access point to yours, and set the WEP if you need it, self explanitory though.

---

### Post by mrMistermattsy on 2007-01-06
ok I hope all this works because i've been sick of windows for years! I tried lots of different kinds of linux like slax and knoppix and redhat. and I didnt care for them. Ubuntu is the only Linux that has a nice look to it.

---

### Post by Spin Doctor on 2007-01-06
> **mrMistermattsy said:**
> ok I hope all this works because i've been sick of windows for years! I tried lots of different kinds of linux like slax and knoppix and redhat. and I didnt care for them. Ubuntu is the only Linux that has a nice look to it.

Great looks is important, but a keypart what makes Ubuntu a serious distribution  is the Ubuntu community, and its willingness to help users solving their problems  =)

I am excited to see the future with Linux.

---

### Post by maniacmusician on 2007-01-06
in case you still need ndiswrapper after this, to get that graphical utility for ndiswrapper that you were talking about, do:

> sudo aptitude install ndiswrapper-utils ndisgtk
in a terminal. Then, Ndiswrapper should show up somewhere in your menu. 

I understand what it's like to be new to linux and have a tough time with it, but believe me, if you stick it out and start **understanding** linux (rather than just doing what people tell you to), you'll love it. so to facilitate that, always ask questions about what other people are telling you to do so you know really what is being done.

if you need help with ndiswrapper and I dont see this thread again, be sure to give me a PM or something. I've had lots of trouble with ndiswrapper so I'm pretty handy with it now :)

Good luck with your problem!

---

### Post by Frak on 2007-01-06
We thank you posting that ManiacMusician, but there is no compatable Windows driver for NDISWrapper, as I stated before, you have to

1. Hope it just works, which Ubuntu is the only one it works on for me
2. Compile the driver from [here]("http://www.ralinktech.com/ralink/data/RT61_Linux_STA_Drv1.1.0.0.tar.gz"), as a module and add it to etc/bin/modules, I think thats the right directory, I'm not swearing on it, not real sure, just look for it.

---

### Post by maniacmusician on 2007-01-06
ahh sorry Frak didn't catch that! If the card has a Ralink chipset, then do a search on these forums, I'm pretty sure that there is a guide on how to compile the ralink drivers. in fact, I used it a while back to help a guy succesfully install his card. 

but the guide has the user use vi to edit things and that was hard for me, haha, not much of a vi user here.

edit: here it is [http://www.ubuntuforums.org/showthread.php?t=296822&highlight=ralink+drivers](http://www.ubuntuforums.org/showthread.php?t=296822&highlight=ralink+drivers) Like I said the vi part can get a little confusing, and I'm not sure if the drivers named in the tutorial are the **newest** version, you should check the ralink site for that (at the link that Frak provided)

edit again: here's another tutorial that doesn't use vi. I don't know how well this one works, I haven't tested it, but here you go: [http://www.ubuntuforums.org/showthread.php?t=132980&highlight=ralink+drivers](http://www.ubuntuforums.org/showthread.php?t=132980&highlight=ralink+drivers)

---

### Post by celem on 2007-01-06
This link may help you. Not your card but similar steps:

[http://ubuntuforums.org/showthread.php?p=1071920&mode=linear](http://ubuntuforums.org/showthread.php?p=1071920&mode=linear)

---

