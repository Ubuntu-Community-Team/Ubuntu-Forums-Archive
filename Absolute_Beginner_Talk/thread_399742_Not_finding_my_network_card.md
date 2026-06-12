---
title: "Not finding my network card"
date: 2007-04-02
forum: Absolute Beginner Talk
---

### Post by Pringle on 2007-04-02
Hi there, new to the whole Linux and Ubuntu world and after a successful install i tried to get onto the internet using my Agere Systems ET-131x PCI-E Gigabit Ethernet Controller and my Virgin Media Broadband connection.

I think i've managed to work it out that the network card isn't being detected rather than Virgin Media not working on Ubuntu. After hunting around google and managing to find various pages of tips and patches, i realised i was just struggling on working some of the code that was written. 

Hope someone can help
Thanks in advance
Tom

---

### Post by e_james on 2007-04-02
In the absence of responses with greater expertise I might be able to help. I need to know how the virgin media broadband connection is normally made. Is it a usb modem, an ethernet modem or an adsl router or something else?

---

### Post by Pringle on 2007-04-02
Ethernet modem

---

### Post by e_james on 2007-04-02
I've only seen a gadget that fits that description very recently. It's actually a single connection router and does the broadband login by itself. Does that apply to yours or does the PC manage the login?

---

### Post by Pringle on 2007-04-02
The broadband handles it all itself.

---

### Post by e_james on 2007-04-02
I've been running a some searches myself in the last few minutes and I can make a few comments. In my own experience ubuntu detects ethernet hardware easily and also some wireless hardware. My problems usually focus on dns addresses and other settings. Your ethernet card seems to be one of the exceptions (even with Windows there can be difficulties). I would suggest that you might find it much easier with a different ethernet adapter. If you have to stick with the ET-131x you could watch this thread 

[http://www.ubuntuforums.org/showthread.php?t=396467&highlight=Agere+Systems](http://www.ubuntuforums.org/showthread.php?t=396467&highlight=Agere+Systems)

until everything is working and then try to apply the same solution for yourself.

If you do get an ethernet adapter working, you may still have a little bit of a problem with the login. Which is where I started this conversation. That type of problem is easier to solve. I will subscribe to this thread so that I will be notified of new posts

---

### Post by Pringle on 2007-04-03
Thanks for the thread, i found it myself as well and couldn't work out how to use the patches. Think i need to get used to the terminal really. In fact, just had an idea, i can use my girlfriends laptop to follow the instructions on XP and use mine on Ubuntu. 

I'll see if i can work it out tomorrow.

---

### Post by Pringle on 2007-04-03
Ok, on looking at the device manager Ubuntu has my card....i think

[[IMG]http://img256.imageshack.us/img256/3425/cardny6.jpg[/IMG]](http://imageshack.us)

After doing the PPPOECONF in the terminal i get this...

[[IMG]http://img376.imageshack.us/img376/3223/pppoeconf1qs5.jpg[/IMG]](http://imageshack.us)

Which i assume is normal. On selecting yes i get this...

[[IMG]http://img101.imageshack.us/img101/2323/pppoeconf2kv6.jpg[/IMG]](http://imageshack.us)

And after selecting no, i get this in the terminal

```
447: modconf: notfound
```

Any ideas? Maybe it is a login situation as you first thought?

---

### Post by mikeyphi on 2007-04-03
OK - so Ubuntu has seen your card...... have a look under SYSTEM - ADMINISTRATION - NETWORKING   and see if it's listed there.....if yes then highlight and edit to confirm settings are correct.
Then get back if no joy!

---

### Post by Pringle on 2007-04-03
Its not listed :confused:

---

### Post by mikeyphi on 2007-04-03
It looks as though there in no linux driver loaded for your card.
Could be that the card is not yet supported......some deeper research is needed!

---

### Post by Pringle on 2007-04-04
Thanks for your help, hopefully you guys can help me and i'll be on Ubuntu in no time!

---

### Post by Pringle on 2007-04-04
Sorry to bump but i'm running short of ideas now

---

### Post by mikeyphi on 2007-04-04
Might have found a solution for you......
Get your driver from here: [http://sourceforge.net/projects/et131x/](http://sourceforge.net/projects/et131x/)

Good luck!!

---

### Post by Pringle on 2007-04-04
Will this make the modem appear in my networking options?

Also, is it a case of 'Terminal - sudo makefile'? I can't seem to change directory from my desktop or anything

---

### Post by Pringle on 2007-04-05
Just so you know, i've given up and am heading back to a windows only life.
cheers for your help people!

Tom

---

### Post by e_james on 2007-04-05
I understand completely. For myself, I will continue to dual boot Windows XP and Ubuntu until I work out how to do several important things with Ubuntu. I want to record, edit and play back television and other video files. MythTV seems like an excellent system but I haven't succeeded in installing it yet. I also have an extensive cataloging database system in Paradox with a lot of customised code. I believe I can continue to use this using WINE but I haven't succeeded in installing it yet. I also want to operate a remote desktop system. I haven't explored this seriously yet but I think this might be the easiest item to do.

I also anticipate that Microsoft will continue to try to rule the world by exploiting the features of DRM, WGA and TPM. I don't want to be part of that paradigm, which is why I intend to carry on learning about Linux and open source. Therefore I say "Bye for now".

---

### Post by slira on 2007-09-07
Hi
probably you have already a solution... but I had the same problem (the 131x card simply "was not there"...)

I manage to solve it and now it works fine; please see

[http://ubuntuforums.org/showthread.php?p=3319218](http://ubuntuforums.org/showthread.php?p=3319218)

hope it helps!
slira

---

