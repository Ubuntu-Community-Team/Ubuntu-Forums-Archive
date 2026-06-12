---
title: "xmms can't connect all of a sudden...firewall?"
date: 2007-03-01
forum: Absolute Beginner Talk
---

### Post by Wartooth on 2007-03-01
Yesterday I was all proud of myself because I managed to make Live365 work with XMMS.  Today, i wake up, go to the computer and try it again.  This time I get a notice telling me it can't connect with an address and a port number.  I also tried making it connect to another online radio station that I know was working, and it did not.  However, I could connect to that same station via Rhythmbox, but never figured out if I could make L365 work with Rhythmbox.

I'm utterly lost with ports, how they do what they do, and I can't understand why something would work one day, and not the next.  I had not rebooted my machine, it stayed on overnight.  I have rebooted it today, with no positive change.  

I am now pretty frustrated after my victory.  I don't understand what went wrong.  Is there some sort of setting somewhere that somehow changed, or is there one that I can find and change so that I can have online radio stations again?

Help. :confused:

---

### Post by nudnik on 2007-03-01
> **Wartooth said:**
> Yesterday I was all proud of myself because I managed to make Live365 work with XMMS.  Today, i wake up, go to the computer and try it again.  This time I get a notice telling me it can't connect with an address and a port number.  I also tried making it connect to another online radio station that I know was working, and it did not.  However, I could connect to that same station via Rhythmbox, but never figured out if I could make L365 work with Rhythmbox.

I'm utterly lost with ports, how they do what they do, and I can't understand why something would work one day, and not the next.  I had not rebooted my machine, it stayed on overnight.  I have rebooted it today, with no positive change.  

I am now pretty frustrated after my victory.  I don't understand what went wrong.  Is there some sort of setting somewhere that somehow changed, or is there one that I can find and change so that I can have online radio stations again?

Help. :confused:

Describe how you are connecting to the internet. If it is via a cable or DSL modem, there are relatively easy ways to open various ports, as well as all of them at once for testing. 

Personally, I am only familiar with two models of Zyxel DSL modem, but I am sure there are those lurking about whose expertise is more diverse.

There is always the possibility it could be something as simple as another application using the specified port.

---

### Post by Wartooth on 2007-03-01
Thank you for your reply. 

I'm on a cable modem.

I noticed different port numbers (I'm assuming that's what the numbers are after the colon in the address, right?) at different times, but :80 is one of the ones I can remember.  

I can try connecting again to various places and make notes of the numbers if that might help.

---

### Post by nudnik on 2007-03-02
> **Wartooth said:**
> Thank you for your reply. 

I'm on a cable modem.

I noticed different port numbers (I'm assuming that's what the numbers are after the colon in the address, right?) at different times, but :80 is one of the ones I can remember.  

I can try connecting again to various places and make notes of the numbers if that might help.

80 is the port used by browsers (like Firefox) to connect to the web. If a browser was open and communicating with the net, that might explain the problem, at least on that port. 

On my DSL modems, you can access the modem by typing a specific address (such as 192.168.1.1) into a web browser. A screen appears and asks for your username and password. Once you have entered these, you can then open ports and configure other settings. Dont do this without a comprehensive guide for your particular modem, and advice from someone who has a good deal of experience with that modem. Unfortunately, I lack any experience whatsoever with cable modems.

---

### Post by Wartooth on 2007-03-02
Just tried it a few moments ago.  Anything through xmms got the error:  Couldn't connect to host localhost:8080

I pulled up a station in Rhythmbox with no problem.  I wonder if there's something other than xmms and Rhythmbox I could try in order to get Live365 and other streaming audio to work.  :/

I'll see if I can figure out something with our cable modem as well. All the other machines are running XP.  I'm the lone Linux on this network.

---

### Post by Wartooth on 2007-03-02
Well, in a moment of inspiration, I uninstalled XMMS, and installed Beep Media Player.   I now have L365 back...but for how long?  We'll see...

---

