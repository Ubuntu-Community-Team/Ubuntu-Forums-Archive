---
title: "Wireless Internet Connection"
date: 2006-04-09
forum: Absolute Beginner Talk
---

### Post by tartarian on 2006-04-09
I'm sorry if there's a really obvious solution to my problem but I cant find one 
](*,)
I'm running a dualboot system with WinXP Professional and Ubuntu Dapper Drake.
I have a built in wireless card in my Packard Bell Easynote R4250 laptop.

I'm trying to connect to my wireless internet in Ubuntu but it's not working. I've disabled the ethernet and modem options in the networking panel so the wireless   is the only one enabled. The WEP key is definatley correct and ive manually put in my I.P address etc, copied from the settings on my WinXP OS which connects no problems. When I click on the icon in the top - right corner of the Ubuntu screen for the internet (the one with the two computer screens) and click on repair (or something like that) it says type: ethernet which confuses me because the ethernet card is disabled. Please help.

---

### Post by htinn on 2006-04-09
I think you may be confusing Network Manager and the Network Admin (which are mutually exclusive). The Network Manager applet will not find any devices that you are actively using in the Networking (admin settings).

---

### Post by tartarian on 2006-04-09
Sorry, that didnt make sense :-? I am only 14 :( #
Any chance you  could re-phrase/re-word that a bit please. thankyou.

---

### Post by htinn on 2006-04-09
Don't use the icon in the top right of your screen.

---

### Post by tartarian on 2006-04-09
[IMG]http://www.filelodge.com/files/hdd5/118485/Screenshot.png[/IMG]
[IMG]http://www.filelodge.com/files/hdd5/118485/Screenshot-1.png[/IMG]

Here are some screen shots of all the networking things I can find

---

### Post by chele on 2006-04-09
Try it without WEP by disabling WEP on your wireless network.

---

### Post by htinn on 2006-04-09
Try changing the key type. It might be that "ascii" mode is what is messing it up.

---

### Post by tartarian on 2006-04-10
Ok, ive changed the WEP key type but it still doesn't work

I cant change the WEP key to nothing, as the rest of the computers in my house connect to it so I'd have to re-configure them all. My parents wouldn;t be pleased if they lost their internet connection

I'm thinking it could be something to do with:
In network tools >>>> Network device: it says "unknown interface (ra0)"
Is there any way to make it a known interface?

Thankyou for all your help!

---

