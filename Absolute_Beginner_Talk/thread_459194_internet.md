---
title: "internet???"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by AkalPurakhDiFauj on 2007-05-30
Hi all.
I am verrry new to Ubuntu. 
very. = )

i installed it, everything worked fine.
all except my internet.
i looked at variosu sites on the internet, and i couldn't find an answer.

id have to connect to the internet using one of these:

[http://www.2wire.com/?p=124](http://www.2wire.com/?p=124)

i have sbc yahoo dsl.
but, when i plugged in my 2Wire PC Port Phoneline Adapter,
my pc didn't even pick it up.
so i put in the 2wire cd, but i couldn't install it. confused. = )

any help would be appreciated. 
thanks.
Peace.

---

### Post by oilchangeguy on 2007-05-30
does your dsl modem have an ethernet connection? you'll need to use that, usb probably will not work.

---

### Post by meborc on 2007-05-30
do you hook your phone line right to that device and to the usb? ... do you use dial-up?

---

### Post by starcraft.man on 2007-05-30
I think your problem lies in the page you linked to...
[QUOTE=2Wire]
Operating Systems
    * Windows: 98, 98SE, ME, 2000 and XP
    * Mac: 8.6, 9.x and 10.1.3 or higher[/QUOTE]

I'm pretty sure that piece of hardware requires the software on the CD specifically, so it is useless with Linux unless someone has made some specific hack/driver for it. I would doubt it, I don't think its popular (i could be wrong). Search the forums and google for it, if not your out of luck...

So like others above pointed out, you need to find an ethernet line from your modem(most preferable) or well... if theres no driver, your not gonna get internet.

---

### Post by lyceum on 2007-05-30
I have 2WIRE and use Yahoo/AT&T. You will need to use ethernet, it looks like a fat phone cord. You can get a used one for around $5 if you do not have one installed.

---

### Post by AkalPurakhDiFauj on 2007-05-30
I have an ethernet thing, but i tried connecting through it, and it still didn't work. any tips?

---

### Post by oilchangeguy on 2007-05-30
> **AkalPurakhDiFauj said:**
> I have an ethernet thing, but i tried connecting through it, and it still didn't work. any tips?

try resetting the modem (unplug the elec. power) your linux box has a different ip address than your windows box does.

---

### Post by daimaru on 2007-05-30
unplug your modem 
open applications-->accessories-->terminal type in:
```
sudo tail -f /var/log/messages
```
hit enter
plug in your modem and check if anything shows up in the console.
if so post the output . ( only the stuff that showed up new ) 
if nothing else works you might be able to use NDISwrapper to install the drivers. NDISwrapper installs windows drivers for use in linux. never used it before but maybe someone has and can help out.

---

### Post by AkalPurakhDiFauj on 2007-05-31
hmm..
this is more of an internet question, doens't really have to do with ubuntu.
i have the main dsl thing in another room.
would i need a long ethernet wire?

or.

what ive been trying was,
i have another dsl main thing from a long time ago.
i hooked it up.
and connected its dsl thourhg the phone dsl filter line.
and then hooked is ethernet port to my pc, with ubuntu.

the power and ethernet light on my dsl thing light up green.
the activity light blinks green sometimes.
but the DSL light is blinking red.
on my pc, it says 
CONNECTION ESTABLISHED
YOU ARE NOW CONNECTED TO THE WIRED NETWORK.

lol.
am i making sense?
thanks guys.

---

### Post by lyceum on 2007-05-31
You can be connected to your router, but your router may not be set up. If it is still not working, call them and tell them you are using Vista. They will walk you through hacking your router so it can be used. If you tell them you use Linux they will not help you. But, their program that does the work for you is not compatible for Vista, so they will walk you through how to do it through your web browser, which doesn't really require windows but the act like it does. (Don't ask, I do not know why, I asked them and they just told me that they no longer help Linux customers).

---

