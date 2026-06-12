---
title: "Slow internet connection"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by Strongbad on 2005-07-28
My computer will only connect to the Internet at 28k. I have a 3com 56k pci modem, but I don't think it is configured properly. Is there a way to select a more suitable driver for it? Or any other way to get it to speed up a bit? I have tried playing with the firefox settings, but it hasn't helped much.

-Strongbad- :???:

---

### Post by NovaWo1f on 2005-07-28
What program are you using to dialin? I was getting terrible transfer rates of only .9-1k, I started using WvDial and now get my full 52k connections I used to get.

---

### Post by Strongbad on 2005-07-28
I just connect by typing "pon" in terminal. I used the pppconfig command to set it up. Does wvdial come with ubuntu?

-Strongbad-

---

### Post by Strongbad on 2005-07-28
I just connect by typing "pon" in terminal. I used the pppconfig command to set it up. Does wvdial come with ubuntu?

-Strongbad-

---

### Post by NovaWo1f on 2005-07-29
[QUOTE=Strongbad]I just connect by typing "pon" in terminal. I used the pppconfig command to set it up. Does wvdial come with ubuntu?

-Strongbad-[/QUOTE]
 Hmm, i used the ppp-on/off commands when I used slackware, but couldn't find them in ubuntu, guess its just pon :p
Anyways, wvdial was allready installed for me, All I did was create the /etc/wvdial.conf file, then just type wvdial in console and it starts up. If your using pon, I would assume it uses the /etc/ppp/peers/ppp0 config file, if thats the case I have read that if you just add "115200" to the bottom of that file you get faster connections. That didn't work with me, because the GUI would reseet the file and remove that setting. But using console might prevent that from happening.

---

### Post by Strongbad on 2005-07-29
ok, I connected with wvdial, and I'm still getting a slow connection. It seems to fumble around in the connecting process though, when I type wvdial, it dials and then spits out a bunch of gibberish before finally connecting. How is your wvdial.conf file set up? And how do you check your connection  speed?

-Strongbad- :-?

---

### Post by NovaWo1f on 2005-07-29
[Dialer Defaults]
Modem = /dev/ttyS1
Baud = 115200
Init1 = ATZ
Init2 = ATQ0 V1 E1 S0=0 &C1 &D2 +FCLASS=0
ISDN = 0
Modem Type = Analog Modem
Phone = 8176651880
Username = [email]novawo1f@peoplepc.com[/email]
Password = jkasif12
Stupid Mode = yes


Thats mine, and after it connects it should say
CONNECT <con speed>/<other junk>

I know mine was really slow, but my speed got fine after I started using wvdial.
Anything else and I'm affraid I won't be of much help :P

---

### Post by Strongbad on 2005-07-31
Still really slow! ](*,)  Any other ideas?

-Strongbad-

---

### Post by NovaWo1f on 2005-07-31
Well, I'm clueless, get broadband? :p

---

### Post by kevlar16 on 2005-07-31
Try this thread to see if it will work.

[http://www.ubuntuforums.org/showthread.php?p=280806#post280806](http://www.ubuntuforums.org/showthread.php?p=280806#post280806)

- Goodluck

---

### Post by autocrosser on 2005-07-31
Try downloading gnomeppp--it will allow you more choices than wvdial & has a fairly good GUI--I've been using it with a Zoom external fax/modem (56k)--am getting a average 40k out in the sticks--just took my time to conf it-- :) 

I put it as a panel launcher & have it run a applet while it is connected--MUCH easier than pon/poff or wvdial--not as geekish--but it works the way I want it to---

---

