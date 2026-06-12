---
title: "Is my wifi card supported?"
date: 2005-11-13
forum: Absolute Beginner Talk
---

### Post by OmniDistortion on 2005-11-13
I use the D-Link DWL-G510 and in the device manager it was displayed as unidentified. I looked for drivers or some info about it and found that there were no drivers available as seen here:
[http://support.dlink.com/products/view.asp?productid=DWL%2DG510](http://support.dlink.com/products/view.asp?productid=DWL%2DG510)

Is there a way I can get this card working or am I screwed? I guess if all else fails I can purchase a new card, but I'd like to get this working tonight if I can. Thanks for any replies!

---

### Post by Mustard on 2005-11-13
Here is a list of hardware and what the support is like in ubuntu;

[https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29](https://wiki.ubuntu.com/HardwareSupportComponentsWirelessNetworkCards?highlight=%28wireless%29)

Here is a how to on getting wifi started;

[https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29](https://wiki.ubuntu.com/WiFiHowto?highlight=%28wifi%29)

I suspect you will be using an ndiswrapper and using your windows driver (refer to two previous links to confirm that first);

[https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29](https://wiki.ubuntu.com/HowToSetUpNdiswrapper?highlight=%28ndiswrapper%29)

-edit-

Reading the first link it seems that your card should work out of the box, so you shouldn't have too much trouble with it.

I would suggest if you want some real time assistance, you could try joining the #ubuntu IRC channel on irc.freenode.net.  They will link you to the same HOW TO's above, and can answer any questions you may have along the way.

---

### Post by dbott67 on 2005-11-13
You should be a able to use NDISWrapper.  Here are a couple of links on how to set it up:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

-Dave

EDIT: Beaten to the punch again!  BTW, check my sig for a link to 'supported hardware list'

---

### Post by Mustard on 2005-11-13
[QUOTE=dbott67]You should be a able to use NDISWrapper.  Here are a couple of links on how to set it up:

[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Ubuntu)
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto)

-Dave

EDIT: Beaten to the punch again!  BTW, check my sig for a link to 'supported hardware list'[/QUOTE]

I think your ndiswrapper links look a bit more comprehensive than the ones I posted. :)

---

### Post by OmniDistortion on 2005-11-13
Hmm quite odd. It says mine is supported and works "out of the box". However it doesn't identify it in the device list. Not sure what to do now.

Edit: NDISwrapper? I'll try it out.

---

### Post by ctcecil on 2005-11-13
what version of ubuntu are you using?
[https://wiki.ubuntu.com/SetupNdiswrapperHowto](https://wiki.ubuntu.com/SetupNdiswrapperHowto) -- worked miracles for me.

---

### Post by OmniDistortion on 2005-11-15
Thanks guys, the wrapper did wonders. I am unable to login through my own router though. I think it might have to do with the fact that rather than hex the WEP is actually a worded password I made and that might have something to do with it. I recall someone else having this problem, possible on this forum.

Problem is if I change it I have to set both of my uncle's and father's PCs and it won't nearly be as easy to remember if it's in hex.

---

