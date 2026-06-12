---
title: "[SOLVED] Setup and using Wine"
date: 2007-10-10
forum: Absolute Beginner Talk
---

### Post by GZBurtchell on 2007-10-10
Hi All,

I've been using Ubuntu for a couple months now and so far it's been good. I still have a lot learn but I'm getting there. Right now, I'm having quite some difficulty setting up Wine to run some of my Windows apps. The truth is, I have no idea how to setup and use this program. The user guide hasn't helped much, it seems geared more toward someone that knows what they're doing with this program than for someone like me. It's tough to admit but I really need simple step-by-step instructions. For instance, I want to set up my Adobe Photoshop program to run hopefully by just double clicking an icon on my desktop.

Another small problem I encountered was I had installed Wine 0.9.33 and right afterwards saw that there was an update on the Wine Home page so I installed the Wine 0.9.46 update via the command line instructions there. When it was done downloading and installing it had disappeared from the Applications/Accessories, Applications/System Tools, and System Preferences menus. I know I can run it on the command line with Terminal but I'd rather have it where I can find it easy enough to just click on it. Any way to fix that?

Thank you for any and all help!

---

### Post by Dr Small on 2007-10-10
[http://psychocats.net/ubuntu/wine](http://psychocats.net/ubuntu/wine) << About as simple as it gets.

---

### Post by mevets on 2007-10-10
I dont know whose instructions you followed to install Wine but here is a good set:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)

Whenever you read that there is an update to Wine you should:
1. Alt + F2
2. Type: update-manager
3. When it loads, press Check
4. If it lists a new version of wine (or any othe program) its a good idea to hit Install updates

This all should be done for you though if you wait long enough after an update. You'll notice the update-applet popup in your notification-area.

---

### Post by GZBurtchell on 2007-10-10
I>  dont know whose instructions you followed to install Wine but here is a good set:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)


That was the site and the instructions I followed. Something isn't right and I don't know what. I no longer have a .wine directory under my home/"username", which was there before when I first installed the 0.9.33.

---

### Post by GZBurtchell on 2007-10-10
> [http://psychocats.net/ubuntu/wine](http://psychocats.net/ubuntu/wine) << About as simple as it gets.


If this is as simple as it gets, I'm in trouble.:-) It's not a very good explanation of how to do things, and I'm totally guessing by the example I found there that I have to be in Linux, put my Photoshop install cd in, run setup, and Wine will do something or other and it will be installed to a folder under my home\"username". Sorry, I'm lost with this.

---

### Post by GZBurtchell on 2007-10-10
Udpate:

I got Wine sorted out, a little bit. The folders were there, just hidden. I pretty much just guessed my way through this. :-) I grabbed my Photoshop install cd, ran Winefile, navigated to the CD and ran Setup.exe. The Installer came up and went through the install.When it was done it did a reset and I logged back in to Ubuntu. Photoshop showed up on my applications menu under Wine/Programs. Started it up, a bit slower on the start up but it eventually came up just as I would see it in Windows.

Unfortunately, nothing works on the menus. I can't select File/Open, or anything from the menu either by mouse or keyboard. It just won't do anything. When I go to close it, I get a "The Program Is Not Responding" and had to do a force quit to close it.

I don't know if I did something wrong with running Winefile, or if I need to tweak it with Winecfg. Not that I would know how to tweak what settings in Winecfg. Does anyone have any ideas, suggestions, or tips? :-)

---

### Post by frup on 2007-10-10
frankscorner.org can be helpful... which version of photoshop?
I have seen that some apps work better with the virtual desktop setting in wincfg too.

---

### Post by GZBurtchell on 2007-10-10
> frankscorner.org can be helpful... which version of photoshop?
I have seen that some apps work better with the virtual desktop setting in wincfg too.


Thanks for the link, I'll give it a better lookover later on. I'm running Photoshop CS (8.0). I'll give the virtual desktop setting a go and see how that works. Can't hurt to try.

---

### Post by Dr Small on 2007-10-10
Just use GIMP... it's open source, free, and better than Photoshop ;)

---

### Post by frup on 2007-10-10
> **Dr Small said:**
> Just use GIMP... it's open source, free, and better than Photoshop ;)

That is the best option :D

---

### Post by GZBurtchell on 2007-10-10
> Just use GIMP... it's open source, free, and better than Photoshop


I have GIMP installed.:-) It's good for some things but it just can't do a lot of the things I do in photoshop. I've added a ton of filters and tools to my photoshop that I use for my work.

---

