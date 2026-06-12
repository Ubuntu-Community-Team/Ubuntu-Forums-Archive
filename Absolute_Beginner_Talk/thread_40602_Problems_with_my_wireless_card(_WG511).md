---
title: "Problems with my wireless card( WG511)"
date: 2005-06-09
forum: Absolute Beginner Talk
---

### Post by czambran on 2005-06-09
It appears on the Ubuntu supported hardware list, and it is suppose to work out of the box, but it doesn't. It seemsto get detected but the lights on the card never come on, and therefore I can not connect to the internet. Am I missing something?

---

### Post by poofyhairguy on 2005-06-09
[QUOTE=czambran]It appears on the Ubuntu supported hardware list, and it is suppose to work out of the box, but it doesn't. It seemsto get detected but the lights on the card never come on, and therefore I can not connect to the internet. Am I missing something?[/QUOTE]

Go to "system" then "administration" then "networking." Is wireless listed as an option at all? (maybe greyed out or something). If not, well, I bet your card isn't natively compatible. Sometimes card sellers will switch the chips on the inside and not give a clue (what version number is it?). If it is not in networking, then you have to install it with ndiswrapper. Get the driver *.inf file from the card maker and use this howto:

[http://www.ubuntulinux.org/wiki/NdiswrapperWithoutInternetAccessSlowFirefox/view?searchterm=ndiswrapper](http://www.ubuntulinux.org/wiki/NdiswrapperWithoutInternetAccessSlowFirefox/view?searchterm=ndiswrapper)

---

### Post by czambran on 2005-06-10
Actually it gets detected, and when I go to System->Administration->Networking it is there, at first it tells me that it isn't activated. So I click on it, and then I activate it, it takes a while but it seems it finally activates it, and then I click ok, it again takes a while and then the networking window disappears. But the lights on the card never light up. So the card gets detected, it seems to get activated, but the lights never come up and I am still unable to connect to the internet.

Any suggestions will be appreciated.

Thanks so much.

Christian

---

### Post by poofyhairguy on 2005-06-10
[QUOTE=czambran]Actually it gets detected, and when I go to System->Administration->Networking it is there, at first it tells me that it isn't activated. So I click on it, and then I activate it, it takes a while but it seems it finally activates it, and then I click ok, it again takes a while and then the networking window disappears. But the lights on the card never light up. So the card gets detected, it seems to get activated, but the lights never come up and I am still unable to connect to the internet.
[/QUOTE]

Awesome. You are lucky, the hardest problem (ndiswrapper) is avoided. The card doesn't work because:

A. You are too far from hub when you try to activate (first time I get close)

B. Your access point needs a hard reset (mine does every now and then).

C. Something else is wrong. Try using the ssid "any" in a place were you KNOW there is open/freee wifi to test it out.

There is a bug in Gnome that its says its activated when its not. The rule for me is "if it takes more than 20 secs to activate, it didn't do it."

I think A is most likely.

---

### Post by czambran on 2005-06-10
> A. You are too far from hub when you try to activate (first time I get close) 

I have my own router, and I put the computer next to it, and nothing. My other laptop has no problem though. It's s windows box, once I get this one going, I will replace it with ubuntu.

> B. Your access point needs a hard reset (mine does every now and then). 
Humm, I'll do that, but if the acces point(router on this case) was having any problems, my other laptop wouldn't be able to connect as well.

> C. Something else is wrong. Try using the ssid "any" in a place were you KNOW there is open/freee wifi to test it out. 
I know is free because it's mine! ;)

Any other suggestions/comments will be appreciated. poofyhairguy you have been a great help, thank u so much.

Christian

---

### Post by poofyhairguy on 2005-06-10
[QUOTE=czambran]

Any other suggestions/comments will be appreciated. poofyhairguy you have been a great help, thank u so much.

Christian[/QUOTE]

Ok. I have looked more. I think maybe that the card you have might have some odder firmware and so the native Linux driver isn't working.

Read here:

[http://news.tiker.net/node/205](http://news.tiker.net/node/205)

> #

The Intersil PrismGT was a hopeful contender, until the card manufacturers discovered that they can save a few cents on each card if they stick the MAC-layer processing into the host driver instead of the card’s firmware. (This cheaper type of card is called SoftMAC and will make the prism54 driver complain about “no 'reset complete' IRQ seen - retrying” and “prism54: Your card/socket may be faulty, or IRQ line too busy”). The driver is complete, functional and open, but it doesn’t support the SoftMAC cards, and the earlier hardware versions that aren’t SoftMAC are nowhere to be found, not even on ebay. I find it a shame that a good piece of software is ruined by the manufacturers’ greed. Honestly, I’d gladly pay more for a card that just works with an open driver, and I believe that I’m not alone. What’s worse: There is no sure-fire way to tell the bad cards from the good ones. In some instances (like the Netgear WG511, which I bought and returned), both types are almost indistinguishable visually. (In fact, for the Netgear cards, the label MADE IN CHINA is the only feature that seems to suggest unsupportedness.) 

I can't find a firmware upgrade on the net, so the best solution is to use ndiswrapper till the next Ubuntu release.


Combine this:

[http://ubuntuforums.org/showpost.php?p=187173&postcount=4](http://ubuntuforums.org/showpost.php?p=187173&postcount=4)

Plus this:

[http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto/view?searchterm=ndiswrapper](http://www.ubuntulinux.org/wiki/SetupNdiswrapperHowto/view?searchterm=ndiswrapper)

Skip the compiling from source part (unless it doesn't work otherwise) and replace:

bcmwl5.inf

with whatever Windows 2000 *.inf this site gives you:

[http://kbserver.netgear.com/support_details.asp?dnldID=927](http://kbserver.netgear.com/support_details.asp?dnldID=927)

---

### Post by czambran on 2005-06-10
Well, I am writing from my computer that was having problem with the Netgear card, so as u might have guessed, IT WORKS!!!!! 


Thank u so much.

---

### Post by eltadcirad on 2005-06-13
My netgear wg511 (based on the prism54) worked with the prism54 driver only after I specified the kernel parameter 

pci=routeirq

prior to that I got various IRQ related messages, which has led some people to use ndiswrapper.

---

### Post by czambran on 2005-06-13
how do u specify that? My card is working, but I would like to know just in case.

---

