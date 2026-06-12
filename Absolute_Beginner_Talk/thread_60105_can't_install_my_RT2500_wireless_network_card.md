---
title: "can't install my RT2500 wireless network card"
date: 2005-08-26
forum: Absolute Beginner Talk
---

### Post by sippo on 2005-08-26
im new so be gentle :)


So i figured i whanted to give linux a try.. im a noob that is. and ubuntu "Linux for Human Beings" sounded just like the right start

its all nice and that but theres allways an rotten apple (he he) i can't figure out how to install my ralink wireless network card (sitting on a windows machine to be online)
 
its a rt2500 chipset based card so the guide [Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo?highlight=%28rt2500%29)  should do the trick.. but that all look'd wierd to me.. but i have exprience with dos so i kinda think i know what i did :D

But how am i supost to apt-get qt3-dev when im not online ?
Maybe i could just download in with windows.. but on [trolltech](http://www.trolltech.com/)  (the ones i figured makes qt3) it looks like they whant money for the ting..

To make a short story long: how do a noob install a ralink2500 card with out being online.. i have a flash drive if i need to transport some files..

please help

-sippo-

---

### Post by KingBahamut on 2005-08-26
Ok, here we go.......

ease back and relax. 

<cracks fingers> 

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

Doesn look like its supported. 

Is that a Raylink, or a Ralink?

---

### Post by essexman on 2005-08-26
[QUOTE=sippo]im new so be gentle :)


So i figured i whanted to give linux a try.. im a noob that is. and ubuntu "Linux for Human Beings" sounded just like the right start

its all nice and that but theres allways an rotten apple (he he) i can't figure out how to install my ralink wireless network card (sitting on a windows machine to be online)
 
its a rt2500 chipset based card so the guide [Rt2500WirelessCardsHowTo](https://wiki.ubuntu.com/Rt2500WirelessCardsHowTo?highlight=%28rt2500%29)  should do the trick.. but that all look'd wierd to me.. but i have exprience with dos so i kinda think i know what i did :D

But how am i supost to apt-get qt3-dev when im not online ?
Maybe i could just download in with windows.. but on [trolltech](http://www.trolltech.com/)  (the ones i figured makes qt3) it looks like they whant money for the ting..

To make a short story long: how do a noob install a ralink2500 card with out being online.. i have a flash drive if i need to transport some files..

please help

-sippo-[/QUOTE]


Hey sippo

The RT2500 wiki how-to works great.  It is the easiest of any Distro IMO.

However I installed it on my destop using a cable connection to my Router.

I think your question should be: "how do I install files on my computer without an internet connection?"

Hopefully someone else will read this and supply a simple answer.

---

### Post by essexman on 2005-08-26
[QUOTE=KingBahamut]Ok, here we go.......

ease back and relax. 

<cracks fingers> 

[http://www.linux-wlan.org/docs/wlan_adapters.html.gz](http://www.linux-wlan.org/docs/wlan_adapters.html.gz)

Doesn't look like its supported. 

Is that a Raylink, or a Ralink?[/QUOTE]

Is cracking knuckles wise when someone makes their 1st post?

The RT2500 is an open source driver and the excellent wiki howto involves compilation.

 It is a shame that this driver is not well supported in Linux generally as I feel that manufacturers who free up their driver could be better rewarded.

Fortunately the RT2500 is well supported in Ubuntu; which is the main reason I started using it.

Anyway, please be a little nicer (human) to people, especially when it is their first post. [-X

---

### Post by KingBahamut on 2005-08-26
Hmmm that seems a little over presumptuous essex. This would be the first time , as expressed to bored2k in irc one night, the first time anyone has called me the proverbial "jackass". 

Helps to know who those think that im being unkind, because if anything Im not. I asked the user to sit back, relax. How much more accomodating do you wish for me to be. 

As far as cracking my fingers, well, im an old programmer, and tendonitis sets into these fingers of mine very easily.

---

### Post by essexman on 2005-08-26
[QUOTE=KingBahamut]Hmmm that seems a little over presumptuous essex. This would be the first time , as expressed to bored2k in irc one night, the first time anyone has called me the proverbial "jackass". 

Helps to know who those think that im being unkind, because if anything Im not. I asked the user to sit back, relax. How much more accomodating do you wish for me to be. 

As far as cracking my fingers, well, im an old programmer, and tendonitis sets into these fingers of mine very easily.[/QUOTE]

King

Thanks for the reply.  I apologise; "presumptuous" is my middle name.  Some phrases don't always translate.

Back to the poin of the original post on the thread...
Could you point Sippo in the direction of an answer?

Is it possible to copy the files needed for an apt-get onto removable media to install on another machine?  Or does he have to buy a very long cable, like I did?

 :wink: 

Essexman

---

### Post by sippo on 2005-08-26
> 
Is that a Raylink, or a Ralink? 

Ita a Ralink based on RT2500 so it must be suportet.

doing all the stuff in the wiki guide made the networkcard show up under the network window. the all the RaConfig stuff that needs qmake stuff is the problem..

and yes i gues the simple question is as essexman says.

how do i apt-get without a working internet connection

---

### Post by KingBahamut on 2005-08-26
Sippo you can add a cd source to your sources file. 

Also,I thought there was a CD extras thing floating around with other nessecaries on it. but I cant remember for sure, someone else jog my harddrive please.

---

### Post by sippo on 2005-08-27
okay.. i got it working now.. aparently i allrady installd the network card. 
wierd how fubling around in the blind can make you do that..

all i had to do was follow the [WiFiWithSomeoneElsesRouterHowTo](https://wiki.ubuntu.com/WiFiWithSomeoneElsesRouterHowTo?action=fullsearch&value=linkto%3A%22WiFiWithSomeoneElsesRouterHowTo%22&context=180) guide.. to bad i have to do that at every reboot. 

enyways thaks for the welcome to the forum and now im gonna go play with ubuntu..

---

