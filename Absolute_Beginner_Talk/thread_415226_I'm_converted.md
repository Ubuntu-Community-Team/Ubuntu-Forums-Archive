---
title: "I'm converted"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by jwstaton on 2007-04-20
Hey guys...

I think I've found my new fav OS. I havent messed around with LInux since the early days of Mandrake and decided to install Ubuntu last night.

I ended up using the alternate CD and installing in text mode but all is well - with one exception. 

My wireless card refuses to work. I'm using an HP notebook that has a Broadcom Wireless card built in - any ideas for making it work?

Other than that, I love Ubuntu!

---

### Post by Noah0504 on 2007-04-20
What model is your card?  If it's any of the bcm43xx type, you can try installing bcm43xx-fwcutter from the repositories, or search the forum for bcm43xx and NdisWrapper.

---

### Post by Kobalt on 2007-04-20
Did you install the latest version of Ubuntu ? 
If so, you're glad you did : just install the *ndisgtk* package and fire it up under System -> Administration -> Windows Wireless Drivers, it will install your card using windows drivers just so easily.

Welcome to Ubuntu ;)

---

### Post by ubuntu27 on 2007-04-20
Check this site out:
[https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported](https://help.ubuntu.com/community/WifiDocs/WirelessCardsSupported)

You say that you have a Broadcom Card. But do you know what chipset does it have?

Open the Terminal which is located at Applications Menu/Accessories/Terminal

and type the following:

```
lspci -v | less
```


Copy and paste what you got there in this thread.

---

### Post by teddybairs1 on 2007-04-20
Broadcom cards are some of the orneriest cards to get working. Broadcom refuses to allow Ubuntu to bundled with the firmware, even though the driver is there.

There are two ways you can do this. One is with ndiswrapper and the windows drivers for the card. The second is with the installed bcm43xx driver and the firmware. Probably the easiest thing to do is to do a search on this forum for a .deb someone created which will install the firmware for you, and then restart your system and do some checks with network-manager or download wlassistant with synaptic and check for a signal.

Broadcom cards don't seem to have any rhyme or reason as to when they work and why. I used ndiswrapper under edgy to get mine to work because the bcm43xx didn't want to work. Under fiesty the ndiswrapper doesn't want to work with mine, but the bcm43xx driver is working perfectly with the firmware. (I've got a Broadcom 4318 card).

Try the firmware and installed driver first. If that doesn't work, use one of the guides on this site for ndiswrapper. It takes a little dance, but it's possible so don't give up. Do the search on the forum for "ndiswrapper broadcom wifi" etc. and you'll come up with all the right posts.

---

### Post by jwstaton on 2007-04-20
I love playing with this stuff. 

Here's what I did:

Ran terminal:

sudo apt-get install bcm43xx-fwcutter

It ran and automatically extracted the firmware but no joy. Then I found an older post about installing ndiswrapper but it didn't work.

I'll try the suggested search and post my results.

Thanks for all the help!

---

### Post by Seisen on 2007-04-20
To get my D-Link card to work a while back I actually had to compile ndiswrapper and install wireless tools. 

[http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html]("http://www.hpl.hp.com/personal/Jean_Tourrilhes/Linux/Tools.html")
[http://ndiswrapper.sourceforge.net/]("http://ndiswrapper.sourceforge.net/")

---

### Post by jwstaton on 2007-04-20
YES! SUCCESS!

Found this post, thanks to you guys (maybe this will help someone else):

[http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+broadcom+wifi](http://ubuntuforums.org/showthread.php?t=197102&highlight=ndiswrapper+broadcom+wifi)

Ran the installer and my wifi now works like a dream!

Why use anything else but Ubuntu? Now to install the server edition on another machine here....

:) :) :)

---

