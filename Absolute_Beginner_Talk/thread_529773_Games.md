---
title: "Games?"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by redfox1160 on 2007-08-19
Is there a way to run games on Ubuntu. The Two games i was thinking of were, half-life (the first one) and possibly tribes vengence. I have heard of something called WINE or something, but i wasnt sure of everything.

---

### Post by Jimmyfj on 2007-08-19
Most Windows games will run just fine under Wine - Else there's always Cross Over office or other emulators. I run Return to castle wolfenstein just perfect in Wine, the rest of my games are natively for Linux

---

### Post by redfox1160 on 2007-08-19
Is WINE a large file?

---

### Post by crav on 2007-08-19
Jimmyfj, I'm curious, what are some of your other games (especially some fps's)?

---

### Post by por100pre1 on 2007-08-19
Here's the [WINE]("http://www.winehq.org/") webpage with lots of information on WINE. You can find it in Add/Remove or just copy/paste and ENTER this in a terminal window to install it:

```
sudo apt-get install wine
```

in the meantime you can also install some games with Add/Remove. Try Tremulous, it rocks:

```
sudo apt-get install tremulous
```

Enjoy! :)

---

### Post by lgambett on 2007-08-19
Do not forget Planet Penguin Racer !
sudo apt-get install planetpenguin-racer

---

### Post by redfox1160 on 2007-08-19
> **por100pre1 said:**
> Here's the [WINE]("http://www.winehq.org/") webpage with lots of information on WINE. You can find it in Add/Remove or just copy/paste and ENTER this in a terminal window to install it:

```
sudo apt-get install wine
```

in the meantime you can also install some games with Add/Remove. Try Tremulous, it rocks:

```
sudo apt-get install tremulous
```

Enjoy! :)

Im Not sure What the terminal thing your talking about is cause i havent installed Ubuntu yet...

---

### Post by por100pre1 on 2007-08-19
> **redfox1160@verizon.net said:**
> Im Not sure What the terminal thing your talking about is cause i havent installed Ubuntu yet...

Ok, don't worry at this moment for it. First try Ubuntu with a LiveCD and check it out. If Ubuntu works OK on your PC all this about gaming will be next.

---

### Post by redfox1160 on 2007-08-19
> **por100pre1 said:**
> Ok, don't worry at this moment for it. First try Ubuntu with a LiveCD and check it out. If Ubuntu works OK on your PC all this about gaming will be next.

Ok, but what is the LiveCD (sry im really new).

---

### Post by Boreras on 2007-08-19
according to appdb.winehq.org (which has a list of a lot op Windows applications (like games), indexed and with results of testing, and people willing to help out), [half-life 1](http://appdb.winehq.org/appview.php?iAppId=8) would be perfectly fine (2 as well).

[Tribes: Vengance](http://appdb.winehq.org/appview.php?iVersionId=6342) isn't tested with newer versions of WINE, so it's hard to tell. The version of WINE that has been used for testing is 0.9.27, but WINE 0.9.43 is already out, and differences can be enormous.

---

### Post by Majorix on 2007-08-19
> **redfox1160@verizon.net said:**
> Ok, but what is the LiveCD (sry im really new).

LiveCD is the Ubuntu CD you download off the net.

---

### Post by por100pre1 on 2007-08-19
> **redfox1160@verizon.net said:**
> Ok, but what is the LiveCD (sry im really new).

There an Ubuntu CD called Live CD that can run Ubuntu without touching your computer's hard disk drive and install only if you really want to do so. It runs really slow but it gives you an idea about Ubuntu and it let's you know if it works on your PC.

---

### Post by redfox1160 on 2007-08-19
where do i get LiveCD

---

### Post by Ek0nomik on 2007-08-19
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)

---

### Post by redfox1160 on 2007-08-19
so if i burn an image disk of this, it wont install ubuntu? Cause i want it to install ubuntu...

---

### Post by Ek0nomik on 2007-08-19
If you burn the image of the link I provided you with, then stick the CD in your CD-ROM, boot into the CD from the BIOS, you will be able to install Ubuntu.

Just open your favorite burning software, and it will *hopefully* have something like:  'Burn Image...'.  You will want to do that and select your newly downloaded .iso file.

Then, reboot your computer and boot onto the CD.  Generally something like F2 or F12 will need to be hit to select what device you want to boot into.

---

### Post by Hobo Joe on 2007-08-20
> **redfox1160 said:**
> so if i burn an image disk of this, it wont install ubuntu? Cause i want it to install ubuntu...

It will not only give you the ability to install Ubuntu, but it will also let you navigate around in it a little bit before installing it. Pretty cool huh?

---

### Post by redfox1160 on 2007-08-20
yeah... will this work with no operating system on the computer?

---

### Post by jusmurph on 2007-08-20
Yes it will.

Seriosuly just give it a go.

---

### Post by redfox1160 on 2007-08-20
well i need to get a monitor (probably tomorrow). If i put the disk into my computer im using now, what would happen?

---

### Post by Hobo Joe on 2007-08-20
> **redfox1160 said:**
> well i need to get a monitor (probably tomorrow). If i put the disk into my computer im using now, what would happen?

Nothing permanent. It will boot into Linux using the CD, but will make no changes at all to your system unless you press the install icon on the desktop.

---

### Post by PHuN on 2007-08-20
You will essentially be running a temporary Ubuntu. It should be able to do anything that installed Ubuntu should do, but when you take the disk out and restart your computer, it is like it was never there.

---

### Post by redfox1160 on 2007-08-20
Are You positively sure? Cause i could get in trouble (from my parents) if i mess up this computer...

---

### Post by Guyver1 on 2007-08-20
how old are you?

you should really be talking to your parents about doing this if its not your machine, you obviously very young and very new to all this stuff and you have a LARGE chance of hosing your folks machine and getting into some serious trouble.

talk to them first.

---

### Post by Ek0nomik on 2007-08-20
How could your parents get upset at you if the computer is useless as of now?

> yeah... will this work with no operating system on the computer?

Without an operating system you can't do much, so you might be doing them a favor.  :)

You may need to hit F2 or F12 while in the BIOS to boot to the CD, but you can just put the CD in, turn on the computer and see what happens for now.

---

### Post by redfox1160 on 2007-08-28
Is there a way to get WINE on a CD,Floppy, or flash drive and then install it on another computer? Also, i cant use the terminal on that computer because that computer isnt connected to the internet (but this one is). So can i download it from somewhere?

---

### Post by Fixman on 2007-08-28
> **redfox1160 said:**
> Ok, but what is the LiveCD (sry im really new).

Well, there are two ways of installing Ubuntu:

a) The free and lazy one but unsecure: Go to Ubuntu homepage, install Ubuntu, you run the .exe, follow the instructions (not trying this time)

b) The $0.50 and energy consuming but secure one: Go, stand up from that computer, risk to go to the outside to buy a virgin CD, go to Ubuntu homepage, download Live-CD ISO, boot into the virgin CD, and there you have a CD-version of Ubuntu you can use witout deleting your files, so you can test it. Laterm you could install Ubuntu by using the program "install" that is on the CD.

---

### Post by Fixman on 2007-08-28
> **redfox1160 said:**
> Also, i cant use the terminal on that computer because that computer isnt connected to the internet (but this one is). So can i download it from somewhere?

Actually, you can use the terminal on any computer, no matter if you are connected to the internet or not.

Windows XP-Vista: windowskey-r -> cmd
Other windowses: windowskey-r -> command

---

### Post by redfox1160 on 2007-08-28
i dont want to install it on this computer, i want to install it on the other one... the other computer is running ubuntu 7.04 and it isnt connected to the internet. i want to install wine on that computer...

---

