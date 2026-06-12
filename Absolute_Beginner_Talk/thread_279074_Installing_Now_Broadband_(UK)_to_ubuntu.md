---
title: "Installing Now Broadband (UK) to ubuntu"
date: 2006-10-17
forum: Absolute Beginner Talk
---

### Post by Mr_Bond_UK on 2006-10-17
Help. Im trying to install now broadband to unbutu live cd before i install, but it doesnt seem to be working! I have no experiance in linux at all so any help would be greatly accepted! i can get on to the modems internal page but i cannot connect to the internet!

---

### Post by caravel on 2006-10-17
Are you using a modem or a router?  I'm presuming it's a router?  If you can log into the router's 'web based interface' then your LAN connection to the router is fine.  Your problem may be the DNS servers.  You may have to manually specify them in your network setup.  Also make sure the router is connecting properly.

If you're not behind a NAT router then what type of modem are you using?

---

### Post by Mr_Bond_UK on 2006-10-17
Its a UT starcom modem, basically its broadband without having a phone line. It uses secure radio frequencies. Not sure why its not working, its fine on windows. Could you just give me a basic idea of how to set up a normal connection?

---

### Post by chewbunny on 2006-10-17
Is this a USB modem or are you connecting via ethernet?

You'll find a wealth of info on adsl/cable and modem setup in general at:

[http://ubuntuforums.org/tags/index.php/adsl/](http://ubuntuforums.org/tags/index.php/adsl/)

and not sure of your model but....

[http://ubuntuforums.org/showthread.php?t=208771](http://ubuntuforums.org/showthread.php?t=208771)

has instructions on setting up a starcom router

enjoy...

---

### Post by Mr_Bond_UK on 2006-10-17
Thank you for you help guys, but after pratting about for abit on my own. Ive cracked it. Im typing this from a live cd boot of ubuntu! the sudo pppoeconf command was exactly what i needed!

---

