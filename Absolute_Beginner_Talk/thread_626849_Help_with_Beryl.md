---
title: "Help with Beryl"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by leodime on 2007-11-29
Let me start off by saying Hello. I'm new to Linux and the Forums, so please bear with me. I'm loving linux already, and I want to install Beryl, but the installation directions are so difficult! I've also heard some poeple say that's they've installed Beryl on their computers without hi-tech graphics cards, but rather using integrated grpahics . However, they did do some modifying to the scrip that needs to be inputed into Linux in order to get it going. So can someone please help me install Beryl? And remember, i'm new to Linux, so please explain it as if I were a little child. And if you have any screenshots readily available, they would be appreciated too. Thanks!

---

### Post by FuturePilot on 2007-11-29
What version of Ubuntu are you using? Gutsy 7.10 already has Compiz Fusion installed. Usually all you have to do is install the restricted driver. System>Administration>Restricted Driver Manager.
Beryl is no longer developed. It got merged back into Compiz and is now know as Compiz Fusion.

---

### Post by leodime on 2007-11-29
So all I have to do is install the restricted driver? Well that's simple. Anything else after that?

---

### Post by vikramsharma on 2007-11-30
> **leodime said:**
> So all I have to do is install the restricted driver? Well that's simple. Anything else after that?

If you have a laptop/desktop containing Nvidia graphics card all you have to do is use the "Restricted Drivers Manager", in case you have ATI graphics card the process would not be that simple (you would have to goto the ATI's website [http://www.ati.com](http://www.ati.com) and download and install the driver for Linux).  Anyway install xserver-xgl is helpful too for the purpose of enabling visual effects, you install xserver-xgl through Synaptic Package Manager or can use the  Terminal by running "sudo apt-get install xserver-xgl" type that without the quotes.  Hope what I wrote makes some sense to you

---

### Post by santiagoward2000 on 2007-11-30
> **vikramsharma said:**
> If you have a laptop/desktop containing Nvidia graphics card all you have to do is use the "Restricted Drivers Manager", in case you have ATI graphics card the process would not be that simple (you would have to goto the ATI's website [http://www.ati.com](http://www.ati.com) and download and install the driver for Linux).  Anyway install xserver-xgl is helpful too for the purpose of enabling visual effects, you install xserver-xgl through Synaptic Package Manager or can use the  Terminal by running "sudo apt-get install xserver-xgl" type that without the quotes.  Hope what I wrote makes some sense to you

Well, I have a rather old ATI card, and I didn't have to install the drivers from ATI's website. I just used **Restricted Drivers Manager**, and then installed XGL.

---

