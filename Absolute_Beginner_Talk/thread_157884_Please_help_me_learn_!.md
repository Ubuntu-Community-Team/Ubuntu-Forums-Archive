---
title: "Please help me learn !"
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by pumpkinruby on 2006-04-10
Hi, I'm Liselot, I've always been using Windows without really knowing what I was doing, I feel like I'm starting from scratch and I don't know all the lingo, so I might call things by weird names. ;)  When we bought a new computer the guy in the shop gave me Ubuntu to try for our old computer, I haven't installed it on the old one yet (I'll probably keep Windows on that one to please my boyfriend) I put it on the new one. I'd rather not use Microsoft on the new pc anymore and learn a lot about computers in the process. Just don't really know how to start, and my boyfriend knows even less about computers and is only asking when I get the router hooked up so he can use MSN on the old computer, and the sound working on the new pc.

I've been reading about the command line all day yesterday, I'll probably have to revise that info today because I can't remember it all at once. I've still got some problems, the soundcard (Terratec 5.1 fun), the printer (canon Pixma IP400) being the main ones.

Soundcard: I've found it on ALSA, [here](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Terratec&card=Aureon+5.1+Fun.&chip=CMI8738&module=cmipci)
, I checked to see if I had a soundcore compiled as a module (all Greek to me to be honest, but         modinfo soundcore returned it. next step I got this:
duncanenliselot@kbl-mdb14535:~$ cd /usr/src
duncanenliselot@kbl-mdb14535:/usr/src$ mkdir alsa
mkdir: kan map `alsa' niet aanmaken: Toegang geweigerd (translation; mkdir: can't make folder 'alsa', acces denied)
What went wrong and what should I do ?



Printer, I found the HOWTO on the forum [http://www.ubuntuforums.org/showthread.php?t=38995](http://www.ubuntuforums.org/showthread.php?t=38995) , but I can't get the .rpm file converted to .deb
I installed libxml1, when I searched for alien it was already installed on my computer. I did step 2, and on step 3 I got this: duncanenliselot@kbl-mdb14535:~$  sudo alien bjfilter-common-2.50-2.i386.rpm Password: 
sudo: alien: command not found
What went/did I do wrong and what should I do about that ?

I hope someone can help me with this.

---

### Post by Praetorian on 2006-04-10
[QUOTE=pumpkinruby]
Soundcard: I've found it on ALSA, [here](http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Terratec&card=Aureon+5.1+Fun.&chip=CMI8738&module=cmipci)
, I checked to see if I had a soundcore compiled as a module (all Greek to me to be honest, but         modinfo soundcore returned it. next step I got this:
duncanenliselot@kbl-mdb14535:~$ cd /usr/src
duncanenliselot@kbl-mdb14535:/usr/src$ mkdir alsa
mkdir: kan map `alsa' niet aanmaken: Toegang geweigerd (translation; mkdir: can't make folder 'alsa', acces denied)
What went wrong and what should I do ?
[/QUOTE]

Try 
```
sudo mkdir alsa
```

---

### Post by OffHand on 2006-04-10
Hi Liselot. This guide should help you on your Ubuntu journey:

[http://makuchaku.info/amnesty/#](http://makuchaku.info/amnesty/#)

---

### Post by steve.horsley on 2006-04-10
Re the soundcard: You are way over my head in the stuff you are looking at there. I hope someone will be able to come up witha mush simpler fix than that. The page you reference seems to be a tutorial on how to compile and install sound into the OS. Not for the beginner.

Printer: Alien is a utility for converting RPM to DEB. You should be able to install this from the menu System->Administration->Synaptic Package Manager. Search for alien, then mark it for install and click Apply.

That's a lot of messing around for the printer. I guess the canon drivers are not released under a license that allows bundling with the O/S.

---

### Post by elamericano on 2006-04-10
The first error sounds like a lack of permissions. sudo mkdir alsa should work. 

The second: Double check that alien is really installed. Try whereis alien. If "sudo find / -name alien" doesn't return it, then there is no file called alien on your computer. Synaptic can install it for you.

If you do find it, but can't invoke it from any directory, you could cd to that folder and use "sudo ./alien ..." In that case you'd include the futh path for the rpm file.

It's too bad you need to follow procedures that you can't understand just to get up and running. I remember I couldn't get sound working several years ago with Mandrake, and I just gave up for a couple of years. Things are so much better now, but there are exceptions. Maybe the older computer is a better candidate for linux.

---

### Post by pumpkinruby on 2006-04-10
Thanks, that worked. At least now I'm reminded about the whole " user"  system.

---

### Post by pumpkinruby on 2006-04-10
I checked with whereis (and I seemed to remember the command " which" too, so I tried that as well) no alien. So I installed it with synaptic.

The main thing we wanted to do with the new pc is just surf the net and play music, so I really need to get the soundcard working. I'm starting to think more and more I'm going to install windows on the new pc and Ubuntu on the old one, I have never installed Windows but at least the helpdesk of my internet provider supports that, I could play around with and learn about Linux on the old pc. In my enthusiasm I tried this set-up first :)

---

### Post by catlett on 2006-04-10
People here may get mad at me but, the windows install is very easy. Just put the cd in and start your computer, just like you did with the live cd. The windows install is all graphical. I t wil ask you minimal questions. Most of the time you just watch a splash screen with a presentation about the new features. Just choose to let it go on line for updates. It walks you thru the whole thing. And the big advantage windows has is that every hardware manufacturer has written a windows driver.  Windows will go on the web automatically to get them
But put Ubuntu on thge older computer. It will have enough resources for linux. You will end up on that one more than your windows. I do. Good luck with Ubuntu

---

### Post by gr0kzer0 on 2006-04-10
That's probably a good idea - linux hardware support gets better all the time but new kit can sometimes be a problem. Glad to see you're still enthusiastic though. Don't give up! I started recently too and have had a few difficulties. But it's all becoming clearer (though i'll never learn enough) and am so glad i stuck at it. That pc salesman who gave you ubuntu... world needs more like him!

---

### Post by Urmas on 2006-04-10
[QUOTE=steve.horsley]Re the soundcard: You are way over my head in the stuff you are looking at there. I hope someone will be able to come up witha mush simpler fix than that. The page you reference seems to be a tutorial on how to compile and install sound into the OS. Not for the beginner.[/QUOTE]

HI, Liselot! Have you checked out "Sound&Video" -> "Sound Management" (or something like it... I'm on a Finnish system)? 

Anyhow... what have you listed there? (see the following pic)? How about the "levels"? Are they muted?

[IMG]http://img50.imageshack.us/img50/634/ksnapshot33gg.jpg[/IMG]

---

