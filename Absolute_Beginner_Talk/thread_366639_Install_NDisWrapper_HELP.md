---
title: "Install NDisWrapper HELP"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by Wowl on 2007-02-21
I've just downloaded the laest ubuntu iso and installed it on my old laptop to try it out (and it may then go on my other PCs) I'm impressed so far but can't find   a way to get my WPC54g wireless card installed. I've read many tutorials, but I just can't install ndiswrapper. I've tried the synaptics app but it can't find ndiswraper in the search.

Can anyone help please?

NOTE: I am a complete newbie to linux!

---

### Post by bigken on 2007-02-21
install [automatix]("http://www.getautomatix.com/") this will install it for you

---

### Post by Wowl on 2007-02-21
Thanks, 


My laptop hasn't go intenet access as its not networked yet, will this still work?

---

### Post by bigken on 2007-02-21
no you need internet access cant you use the onboard ethernet ?

---

### Post by Wowl on 2007-02-21
thats the problem my laptop oly has a wifi card

---

### Post by bigken on 2007-02-21
are you sure ?


what is the make and model of the laptop

---

### Post by paydaydaddy on 2007-02-21
Here is how I found it:
Open the Synaptic package manager then click on settings. When the Software preferences window opens click +Add. When the Add Channel box opens, make sure all boxes are ticked then click +Add. Close all boxes and click Reload. After the page has reloaded click on search. In the search window type ndiswrapper and click search. ndiswrapper should show up. Right click and choose "Mark for installation" then click apply.

---

### Post by Wowl on 2007-02-21
Dell Latitude - it's a fairly old machine (500Mhz) and there is definitely no ethernet port. Can I download and use a pen dive t transfer it?

---

### Post by paydaydaddy on 2007-02-21
Looks like I was slow on the trigger. You need internet access. If you have usb ports you can get a network dongle that plugs into usb then you can connect with a cat5 cable. Of course that doesn't help much right now, does it.

---

### Post by Wowl on 2007-02-21
> **paydaydaddy said:**
> Here is how I found it:
Open the Synaptic package manager then click on settings. When the Software preferences window opens click +Add. When the Add Channel box opens, make sure all boxes are ticked then click +Add. Close all boxes and click Reload. After the page has reloaded click on search. In the search window type ndiswrapper and click search. ndiswrapper should show up. Right click and choose "Mark for installation" then click apply.

Does this work without Internet acess?

---

### Post by bigken on 2007-02-21
no cos you need the internet to download the programs it installs :(

---

### Post by bigken on 2007-02-21
take a look here 

[http://ubuntuforums.org/showthread.php?t=361991&highlight=ndiswrapper](http://ubuntuforums.org/showthread.php?t=361991&highlight=ndiswrapper)

---

### Post by Wowl on 2007-02-21
Is there any way to get my laptop on the network then when at the moment it's a stand-alone?

I can burn the software to a CD or download it from this PC and put it on a pen drive, how would I do this please?

---

### Post by Wowl on 2007-02-21
I have the CD so ill try now

---

### Post by paydaydaddy on 2007-02-21
I have never tried using a pendrive to do installs, but I would think it would work> I didi a quick google search and found a download with unzip instructions. The worst that could happen if it doesn't work is that you end up back where you started.

---

### Post by Wowl on 2007-02-21
Thanks, cn I have the pen dive link please. I dont think Ubuntu has the drivers for my CD drive as even though the ISO (burn correctly as it installed form it) is in the drive it says "failed to mount CD"

And theres no CD drive in places.
Sorry to be a noob, but how do I install the CD drivers?

---

### Post by bigken on 2007-02-21
do a search for mount cdrom see what others have done to mount there drives


sorry cant help anymore got to go good luck

---

### Post by paydaydaddy on 2007-02-21
[http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation](http://ndiswrapper.sourceforge.net/mediawiki/index.php/Installation)

That is the page I looked at. Scroll down to "Download" and you will see a link for the download. Then cut and paste the commands into a terminal to unzip and load. Find the terminal under <applications><accessories><terminal>

---

### Post by Wowl on 2007-02-21
Thanks, wil try the pen drive now.

You don't happen to know what / how to mount a CD drive?

---

### Post by paydaydaddy on 2007-02-21
The best I can recommend for the CD drive is search the forums for the answer. I got lucky and mine worked with the standard Ubuntu drivers so I have no experience in that area. Good luck. I'm off to bed.

---

### Post by Wowl on 2007-02-21
Thanks, I'm a bit confused by all this terminal business but hopefll can get it woking.

Thanks for the suggestions

---

### Post by helliewm on 2007-02-21
I had 3 different Wireless cards and one was a WPC54G Linksys card that I could not get working with ndiswrapper. If I remember correctly there are problems with this card, from what I read.

In the end Bigken ( he lives down the road from me, odd we met through the forum!) very kindly sent me a compatible Network Card. If may be quicker just to buy a compatible Network card they are not very expensive.

Helen

---

### Post by Wowl on 2007-02-22
Thanks but I'd rather get what I have working and learn my way around ubuntu a bit better before buying new hardware

---

### Post by teaker1s on 2007-02-22
if you have ndiswrapper problems look at this link they found the issue
[http://ubuntuforums.org/showthread.php?t=5645]("http://ubuntuforums.org/showthread.php?t=5645")

---

