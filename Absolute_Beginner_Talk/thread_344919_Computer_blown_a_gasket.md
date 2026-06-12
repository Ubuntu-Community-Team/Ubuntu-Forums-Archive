---
title: "Computer blown a gasket?"
date: 2007-01-23
forum: Absolute Beginner Talk
---

### Post by chrispy212 on 2007-01-23
OK, Im not a complete newbie. I had FC6 for a few months but nothing worked. It was an old box that my dad gave me to mess with, so I decided on linux. I dont know why I chose fc6, it just wasnt for me.

OK. I install ubuntu (after finding the alternative installer). Wahay, it's easy, say the moron. I'll install ndiswrapper now because Im clever. OK, so that works (eventually!) but my network is WPA-PSK. So I do all the this and that, and install wpa_supplicant, then try running it by
sudo wpa_supplicant -Dwext -iwlan0 -c/etc/wpa_supplicant.conf -dd
It flashes text constantly in the console until it just locks up. So I give it a minute, and then decide to restart.
So I do, and I login, and I start to get ready to try again, and the screen turns off, then on again!!!
I can see two mice, Im on the login screen but if I wiggle the mouse I can files from the folder I was in, and windows I had open. The mouse is trailing and it doesnt look good.
I restart After a while, same thing.
And to top it all off, the computer is running hella slow. In console, I type a command and need to wait 2-3 minutes for anything to happen.
I was SO close to getting my wireless card working, what has gone wrong? Im thinking overheat, but I don't think any components in this box are replacable, its real old. 
Thanks

---

### Post by oilchangeguy on 2007-01-23
if it were overheating it would shut off. you didn't say what type of computer, or any specs. it just may not have the power to run whatever version of ubuntu you're trying to run. just as xp would run slooooooooow if you were able to load it on a machine that was born with 95 on it and never had any upgrades. you might want to try damnsmall linux. from what i've read about it it's designed to run on older, low powered computers.

---

### Post by Happy_Man on 2007-01-23
Or, if you're dead-set on using Ubuntu, you can always try Xubuntu. It's got the XFCE environment and is very friendly to computers that are past their prime.

---

### Post by jvc26 on 2007-01-23
Xubuntu is designed for older computers, but it may not be as fast as it could be, from my experience, although it is faster its not as fast as it would appear, and so Fluxbuntu could well be an option as well as DSL (damn small linux)
Il

---

### Post by chrispy212 on 2007-01-24
Well. Thing is, it isnt a great computer, but it has run well. It had W.2000/ME on it, and I really don't think it's aperformance issue. I REALLY dont want to re-install because of the sheer number of packages I've installed to get the make command working, which is difficult without net access!!!
So no solutions eh?

---

### Post by houstonbofh on 2007-01-24
You still haven't answered the first basic questions.  What is the hardware?  We need CPU, memory, NIC, graphics card, version of Ubuntu, and software installed to get the nic up.

---

### Post by chrispy212 on 2007-01-26
Sorry!
Well I have very little knowledge about what is actually inside, b ut I dont think that is the cause. I can tell you that there is 128mb of ram, and it is an old machine, with a processor <1ghz. The error seems to be caused by an untested d-link driver installed by ndiswrapper. I have uninstalled said driver but the problems persist, and I am looking at a complete reinstall. 
Thanks for your help. I tell you this so that people who have had similar issues will find out that installing drivers with ndiswrapper can cause kernel malfunction
Thanks

---

