---
title: "Could use a little help"
date: 2007-02-27
forum: Absolute Beginner Talk
---

### Post by fultn22 on 2007-02-27
Hey so i'm totaly new to ubuntu. So far all i've used it for is the games and am trying to switch from windows over to it.  But i cann't figure out what programs i can run on it i download some programs that i had on the computer already such as itunes as well as trillian a program that runs AIM and yahoo messenger but the system cann't run it is there any way around this?

---

### Post by Maestro23 on 2007-02-27
> **fultn22 said:**
> Hey so i'm totaly new to ubuntu. So far all i've used it for is the games and am trying to switch from windows over to it.  But i cann't figure out what programs i can run on it i download some programs that i had on the computer already such as itunes as well as trillian a program that runs AIM and yahoo messenger but the system cann't run it is there any way around this?

You can't run Windows programs on a Linux system unless you get a program like:

> Wine: [http://www.winehq.com/](http://www.winehq.com/)

Cedega(Games): [http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1](http://www.transgaming.com/index.php?module=ContentExpress&func=display&ceid=2&meid=-1)

or, Run Windows in a virtual environment like Vmware.

Vmware: [http://www.vmware.com/](http://www.vmware.com/)

Some links to introduce you to Ubuntu:

> How to Install in Ubuntu: [http://www.cutlersoftware.com/ubuntuinstall/](http://www.cutlersoftware.com/ubuntuinstall/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Restricted Formats(mp3 and DVD): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
*Ubuntu Guide link is in my sig.

Welcome to the community and good luck.

---

### Post by dcj65 on 2007-02-27
Try using Gaim and Banshee..... Gaim for your instant messaging and Banshee for Itunes

and you can look for other programs at  [www.packages.ubuntu.com](www.packages.ubuntu.com)

---

### Post by angryfirelord on 2007-02-27
It seems that you're trying to download a windows file (.exe) and attempting to run it under Ubuntu. Err, sorry, not going to happen that way. :) 

Instead, you use a nifty little tool under the Applications menu called Add/Remove programs. Select which ones you want & download them!

Ex:
AIM/Yahoo/Msn-->Gaim
iTunes-->AmaroK

---

### Post by Brunellus on 2007-02-27
Ubuntu is not windows.  WINE might work for installing some windows software, but it is far from flawless.  In fact, I usually hesitate to recommend WINE except as a last resort.

There is no iTunes for Linux.  Playing tracks purchased from iTMS in Linux is tricky and of questionable legality.  But if you're looking for software that will index and play your music files, there are plenty of alternatives.

Ubuntu (with GNOME) installs Rhythmbox by default.  Kubuntu installs the (arguably superior) AmaroK jukebox.  Banshee is also a good alternative.  

Be advised that Ubuntu does not play non-free formats and codecs by default.  For guidance, see

[http://help.ubuntu.com/community/RestrictedFormats](http://help.ubuntu.com/community/RestrictedFormats)

Instant messaging is one of the easier things to do.  Ubuntu comes with GAIM by default;  Kubuntu with Kopete.  Adding new accounts to those clients should be pretty straightforward.

---

### Post by luke411 on 2007-02-27
If you want to run Itunes, MS OFfice, Real Player and any of a long list of windows programs, you  can purchase Crossover Office from Codeweavers. I use it, for the Office aps I have to use for work, as OPen Office is a little unreliable when it comes to macros. Having said that, you can get it for about 40.00 from their web site and also read the long list of programs that it will run. You install it and launch it, and from there, install whatever Windows program you are trying to run. I've used them for years. Once you buy the latest version, you can download it whenever and as often as you like but you will have to repurchase the program if you want a newer version (once it's released). I think the latest Itunes it will run is v 4. but you can read about it yourself. Good luck. It really is the easiest way to transition from windows when you have a few programs that must run. We all love linux here, but the reality is, it's a windows world.

---

### Post by Brunellus on 2007-02-27
> **luke411 said:**
> If you want to run Itunes, MS OFfice, Real Player and any of a long list of windows programs, you  can purchase Crossover Office from Codeweavers. I use it, for the Office aps I have to use for work, as OPen Office is a little unreliable when it comes to macros. Having said that, you can get it for about 40.00 from their web site and also read the long list of programs that it will run. You install it and launch it, and from there, install whatever Windows program you are trying to run. I've used them for years. Once you buy the latest version, you can download it whenever and as often as you like but you will have to repurchase the program if you want a newer version (once it's released). I think the latest Itunes it will run is v 4. but you can read about it yourself. Good luck. It really is the easiest way to transition from windows when you have a few programs that must run. We all love linux here, but the reality is, it's a windows world.
I only recommend compatibility layers as a last resort.  If you're highly dependent on VB or macros, then you might not have much of a choice, but if you have no compelling reason to use Microsoft software other than outputting files to .doc and .xls without a lot of finessing, then you should probably try the alternatives first.

---

### Post by luke411 on 2007-02-27
You're right Brunellas, I agree completely. But being new to Linux can be frustrating and I assume if it's a program he is willing to pay 40.00 for, he must want to run it enough to get frustrated with linux and switch back to windows. So, I would rather see him take the easy way out, at least initially, than see him give up on Linux over Itunes or some other program.

But I understand your point of view and agree.

---

### Post by fultn22 on 2007-02-27
Hey thanks for all the help everyone. I'm stating to figure things out a little get some programs working and understanding how this system works a little. I decided to go with the Banshee program to get my music from my external hard drive but once it was done loading none of the music works it says i might be missing plugins where do i go for those? i went to the Banshee website and kinda got the impression that maybe something had gone wrong threw add/remove programs. Any help is much appreciated

---

### Post by Maestro23 on 2007-02-27
> **fultn22 said:**
> Hey thanks for all the help everyone. I'm stating to figure things out a little get some programs working and understanding how this system works a little. I decided to go with the Banshee program to get my music from my external hard drive but once it was done loading none of the music works it says i might be missing plugins where do i go for those? i went to the Banshee website and kinda got the impression that maybe something had gone wrong threw add/remove programs. Any help is much appreciated

Restricted Formats: [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by RomeReactor on 2007-02-27
Hi. As Brunellus said, Ubuntu won't play restricted formats out-of-the-box, but adding that feature isn't really all that difficult, i think: Open Synaptic (System-->Administration-->Synaptic Package Manager), search for **banshee**, and when it shows up, right-click on it and on "Mark Recommended for Installation" you'll see that **gstreamer0.10-plugins-ugly** is available (if the Universe repositories are enabled); i usually install every **Recommended** and **Suggested** package Synaptic mentions whenever i install a program. Makes them less likely to need any further plugins. To enable Universe and Multiverse repositories, look [here]("http://www.ubuntuforums.org/showpost.php?p=2157232&postcount=9"). Hope this helps you.

---

### Post by fultn22 on 2007-02-27
Thanks again. Sorry to bug people again but is there something to run PDF files. i've gone threw about 3 of them threw add/remove programs but when i try to pull up files on the internet they don't work.

---

### Post by Brunellus on 2007-02-27
you should be able to read pdfs with no problem using evince or even xpdf.  

In fact, there should be a pdf reader included by default in Ubuntu and Kubuntu.

---

