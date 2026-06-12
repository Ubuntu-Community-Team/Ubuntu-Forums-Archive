---
title: "How to install internet"
date: 2005-12-22
forum: Absolute Beginner Talk
---

### Post by kennethalan on 2005-12-22
I've just got going with Ubuntu Live disc.  Installation seems OK.

Now how can I setup the internet connection?  I've got adsl subscription but what do I have to do to get it up and running?

Now I'm obliged to re-boot Windows in order to use internet.

Thanks

---

### Post by bscbrit on 2005-12-22
You've possibly got everything you need, but you haven't really given us much information to go on.  How do you connect to the internet using Windows?  Do you have an internal modem, an external modem, a modem/router, a cable connection?  And what make and model of modem have you got?  Somebody here can probably help to get you online if you can answer these questions.

---

### Post by kennethalan on 2005-12-22
Thanks for the response, Monsieur bscbrit

I've been using an external modem for the adsl connection provided by the local telephone company.  The modem was installed under windows with a disc that accompanied the modem when I subscribed to adsl a year ago.  The make and model I don't know, everything has the logo of the telephone company. 

The follwoing is in the instruction manual:
"international specifications ANSI T1.413 Edition 2
                                      ITU-T G.992.1 (G.DMT)
                                      ITU-T G.992.2 (G.LITE)" 

I don't know if this identifies the model.  
 ALso, in the manual are specified the WOndows operation systems, so maybe the modem won't work with Ubuntu.

I've also got a DLink modem/router, that I don't know how to install either (even under windows), although I'd like to.

---

### Post by bscbrit on 2005-12-22
Your DLink modem/router is probably a dream come true!  What model is it?  These are probably the best kind of ADSL modems to use under linux, especially if it is linked by ethernet.

ps Offline for a while - I have to work as well.....   But I'll be back if no-one can help you in the meantime.

---

### Post by kennethalan on 2005-12-22
Monsieur bscbrit

The DLink box says "Wireless ADSL ROuter Kit DSL 904".  On the router itself it says "DSL G604T"

I've got an ethernet plug on my computer.  But when I was trying to install the thing under windows, following the instructions on the installation disc, my computer didn't seem to recognize the presence of the router.  I hadn't yet had time to go back to the computer shop to ask for advice when the Ubuntu discs arrived in the mail.



I see that you are in Gibraltar.  I suspected that you must be in Europe, considering what time it would be in the US

Myself, I'm in Andorra.

Your message is very encouraging and very kind.  Thank you.  I'll be eagerly watching for your response all morning long.

---

### Post by nijinsky on 2005-12-22
[QUOTE=kennethalan]Monsieur bscbrit

The DLink box says "Wireless ADSL ROuter Kit DSL 904".  On the router itself it says "DSL G604T"

I've got an ethernet plug on my computer.  But when I was trying to install the thing under windows, following the instructions on the installation disc, my computer didn't seem to recognize the presence of the router.  I hadn't yet had time to go back to the computer shop to ask for advice when the Ubuntu discs arrived in the mail.



I see that you are in Gibraltar.  I suspected that you must be in Europe, considering what time it would be in the US

Myself, I'm in Andorra.

Your message is very encouraging and very kind.  Thank you.  I'll be eagerly watching for your response all morning long.[/QUOTE]


Hi Kenneth.

OK I'm now to ubuntu but try this.

Go into windows and plug in the router to the machine. The 604T is slod as an adsl router IE a router that is compatable with adsl, however, I beleive it is also a modem, I think the T indicates this. OK have a look here
[http://www.adslguide.org.uk/hardware/reviews/2004/q4/dlink-dsl300t.asp](http://www.adslguide.org.uk/hardware/reviews/2004/q4/dlink-dsl300t.asp)

It shows how to setup the 300T but it should be the same web based interface. I dont think you actually need the install disks since this should just install the dlink network acccess software. Windows networking and a browser should be fine.

Once you can confirm that the internet connection is working in windows then you should be able to switch to linux and configure your ethernet eth0 in system-administration-networking.

The router should be dhcp so it should provide the IP to the computer.

I'm doing this from memory of my old system. netgear modem-router and d-link wifi router. I now use a dlink and I'm at work.


I would persevere, since I just got wifi up via ubuntu and if rocks.

cheers
bob

---

### Post by kennethalan on 2005-12-22
I have perserverd, and I have succeeded! Hip Hip Hooray! Thanks monsieur bob

I am now on firefox and ubuntu.  

Stick around, it surely won't be long till I need more help

---

### Post by bscbrit on 2005-12-22
Kenneth - I get back to my computer to find that you have already solved the problem - great news.  I hope to see you around the forums in the future.

---

### Post by akos.szalay on 2006-11-18
The same problem, surfing with ubuntu (6.06 LTS).
DSL-904, on windows it works both wired and wireless.
On ubuntu connected wired I can ping e.g. google.com, but trying to reach google.com in firefox times out, but 64.233.167.99 gives me google.com. So I guess I have a problem with dns, but why does it work with windoze then, and more important how to get it to work on ubuntu ?

A'kos

---

### Post by ComplexNumber on 2006-11-18
> **akos.szalay said:**
> The same problem, surfing with ubuntu (6.06 LTS).
DSL-904, on windows it works both wired and wireless.
On ubuntu connected wired I can ping e.g. google.com, but trying to reach google.com in firefox times out, but 64.233.167.99 gives me google.com. So I guess I have a problem with dns, but why does it work with windoze then, and more important how to get it to work on ubuntu ?

A'kos
in the address bar in firefox, type in 'about:config'(without the quotes) and press return. then type in "v6"(without the quotes) in the search bar (the one that will appear underneath it). then set it to *true*.

---

### Post by akos.szalay on 2006-11-18
Thanx for the quick answer, guess where I'm writing this reply from.
Yes you guessed correctly, ubuntu (wired). :D 
Unfortunately wireless still doesn't work.
I can see my router, selected key type "plain (ascii)" and entered wep key "abcd1234" with configuration dhcp.
Even f I disable eth0 (wired) and only eth1 (wireless) is active, clicking onto the network connection icon in the right upper corner lets me select only eth0 or lo (whatever that is).
Any idea what's wrong ?
Also if I connect wired and click Applications->add/remove downloading package information tells me "http://archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg: Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out".
What am I doing wrong ?

A'kos

---

### Post by akos.szalay on 2006-11-30
Right, I had to change the nameserver in /etc/resolv.conf from 192.168.1.1 to 203.8.183.1. 
So installing packages works now, but wireless still doesn't. Any suggestion?
Thanx

A'kos

---

