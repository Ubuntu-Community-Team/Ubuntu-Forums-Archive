---
title: "Thinking of installing Ubuntu"
date: 2005-10-23
forum: Absolute Beginner Talk
---

### Post by Dinerty on 2005-10-23
Current system spec:

AMD XP 1.5ghz
768MB of RAM (PC2100 lol)
ATI radeon 9700 pro with omega drivers
40GB IDE drive
500GB Ext Firewire 800
Samsung 913N
Speedtouch 330 USB modem

Currently on windows XP Proffessional (Think it is really good to be honest, but want more from a OS, better memory mangement and stability). I have briefly used Slackware but did not use it much as I didnt have internet on it.


First question

I'm yet to try the live cd and i was just wondering before hand if all of my hardware will work under breezy badger 5.10?

Second question

In the past while trying to setup my internet with a linux disto i ran into various issues and never actually successfully got my internet working, im just wondering now how easy to setup my speedtouch 330?

Third question

Ive recently read that ATi's drivers for linux distros isnt as efficient nor as easy to setup as nvidias, would this be an issue and also does anyone know of any guides on how to configure my card succfessully? also has anyone ran into any problems with the card im using?

Fourth question

In the near future i plan to be running a wireless network, and i was wondering how easy this was to setup / configure under ubuntu, also if anyone has had any issues while trying to achieve this?

Fifth question

Any advice for me, thanks all

---

### Post by Darkhack on 2005-10-23
AMD XP 1.5ghz -- YES
768MB of RAM (PC2100 lol) -- YES
ATI radeon 9700 pro with omega drivers -- SHOULD WORK
40GB IDE drive -- YES
500GB Ext Firewire 800 -- SHOULD WORK
Samsung 913N -- ???
Speedtouch 330 USB modem -- HIGHLY DOUBTFUL

That about sums up your hardware atleast from my expierences.  The ones I labelled "should work" I am 99% posative that they'll run just fine although you MIGHT need to do a little configuration.  If your lucky it'll work out of the box.  For your Samsung, I have no clue.  For the Speedtouch I am doubting it because I am guessing that it is whats called a "winModem" meaning it depends on certain software found only in windows to operate.  Try googling for it and maybe you can find some more info.  If it does turn out to be a winModem like I am guessing you'll have to find one that does work for Linux.  =(

For your wireless card question, you might have trouble finding a card that works 100% natively with Linux.  They are out their, but I wasn't able to find them.  However... fear not!  There is a solution.  A peice of software called ndiswrapper allows you to use Wireless cards under Linux that would normally only work for Windows.  Google for "ndiswrapper" and check their compatibility list for a card you are interested in buying and see what success they've had with it.

I hope that answers your question.  I am still a noob myself, so hopefully a more advanced user can give you some more information about your hardware.

---

### Post by Iandefor on 2005-10-23
I get the feeling that the majority of your hardware will work with a bit of tinkering, with the exception of the Speedtouch 330- that will most likely require a lot of hacking to make it work. The Egyptian Linux Users Group has a page dealing with it, if you're interested: [EGLUG]("http://www.eglug.org/node/1074").
It seems like the ATI card is going to have issues. I've seen people having lots of trouble with wireless networking, but Darkhack is right- ndiswrapper should work dandy. Samsung 913n should work fine.

If you feel like trying to keep your partition with Windows XP, the System Rescue CD comes with QTParted, which includes a feature for safely resizing a partition, but I'd warn you to make a backup of your installation before you try it.

---

