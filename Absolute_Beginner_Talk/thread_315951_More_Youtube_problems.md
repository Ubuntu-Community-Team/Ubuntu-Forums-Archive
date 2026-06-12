---
title: "More Youtube problems"
date: 2006-12-10
forum: Absolute Beginner Talk
---

### Post by onemind on 2006-12-10
Hi again,

Yesterday i posted because i had no sound on youtube but had video and some people fixed my problem. Today i wiped my copy of ubuntu to install the latest version (6.10) and the sound in youtube works without that hack but now it gets out of synch with the video after about 10-20 seconds of playing. 

Anyone know how to fix this?

Thanks :)

---

### Post by axle_foley00 on 2006-12-10
Did you try installing the latest [Flash Player 9 beta 2]("http://labs.adobe.com/downloads/flashplayer9.html")?

---

### Post by dbbolton on 2006-12-10
maybe try

 sudo killall esd 

before launching your browser...

---

### Post by IYY on 2006-12-10
Install the latest beta, it fixes pretty much everything.

---

### Post by mormonchess on 2006-12-30
I've installed Flash Beta 9 using the instructions found here:

[http://www.psychocats.net/ubuntu/flash]("http://www.psychocats.net/ubuntu/flash")

However, my Firefox 2.0 isn't recognizing that I have a flash player installed.  How do I get it to find the plugin, so that I can go to youTube without youTube and Firefox telling me that I have no Flash player?

---

### Post by shanepardue on 2006-12-30
Is flash 9 not available in your synaptic? Automatix is how I installed it. It's a good program to have around anyway... [www.getautomatix.com](www.getautomatix.com)

---

### Post by shanepardue on 2006-12-30
Oh and Firefox 2 installs flash 9 by clicking install missing plugins from a website that has flash on it.

---

### Post by mormonchess on 2006-12-30
No it doesn't.  It installs Flash 7, not 9.

I have Automatix, and it doesn't install 9, it installs 7.

---

### Post by shanepardue on 2006-12-30
are you on dapper? maybe it's different for me on edgy

---

### Post by mormonchess on 2006-12-30
Yes, I'm on Dapper.


It's a little frustrating that it's this difficult to get Flash 9 so that I can watch youTube videos without sync issues.

---

### Post by shanepardue on 2006-12-30
Yeah..Edgy installs it through firefox. Have you tried Edgy? I have had less problems with edgy than I did with Dapper.

---

### Post by mormonchess on 2006-12-30
Looks like I'll be upgrading to Edgy!

---

### Post by Suzan on 2006-12-30
C'mon! What is difficult?

Download the Installer for Linux from the Link axle_foley00 gave you in the first answer!

Unpack it an copy the file "libflashplayer.so" in your firefox plugins-directory

.mozilla/plugins

Restart your Firerfox ... et voila!

Remove any older versions of flashplayer before.

---

### Post by shanepardue on 2006-12-30
It's not very difficult, but it is kinda annoying to do that instead of click install missing plugins through firefox or all the other conveniences of edgy.

---

### Post by L Campbell on 2006-12-30
> **mormonchess said:**
> Yes, I'm on Dapper.


It's a little frustrating that it's this difficult to get Flash 9 so that I can watch youTube videos without sync issues.


Here is the link I use to install Flash 9 on Dapper and it worked PERFECTLY.

[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by mormonchess on 2006-12-30
Lewis, your PERFECT method didn't work for me, and I had already tried that route.

However, this method DID work:

> I did a (I think) simpler version.. especially for the non-terminal gui people.

First, go to
[http://labs.adobe.com/technologies/flashplayer9/](http://labs.adobe.com/technologies/flashplayer9/)

Download the plugin and extract to desktop. Then open the file and right-click copy gflashplayer.so

Next open your home directory, hit ctrl+h and put it in your plugins folder under Mozilla.

It works fine for me

---

