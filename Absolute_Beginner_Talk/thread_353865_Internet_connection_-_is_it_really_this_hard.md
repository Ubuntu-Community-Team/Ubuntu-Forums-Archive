---
title: "Internet connection - is it really this hard?"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by whitefort on 2007-02-05
Hi - sorry if this sounds like a whine - it's really not meant that way.

At present my main PC is running XP and connecting to the internet via an ASDL broadband modem.  My Ubuntu machine is in another room, connected to it by an Ethernet cable, thereby sharing the internet connection with no problems.

This afternoon, toying with the idea of getting TOTALLY free from windows, I tried the live CD on the XP machine, and found that I couldn't get an internet connection no matter what I tried.

Ok...  back to windows, so I can get on-line.   I found some googles on the subject all saying that USB modems are a problem - and the fixes all involved an AWFUL lot of downloading stuff, installing it, then pages and pages of changes to configuration files.

This is all a bit scary for me.  I'm a PC wimp.

Some of these help pages were a few years old, so I thought I'd ask:  Is it ***still ***necessary to jump through all these hoops to get a USB modem to work with Ubuntu, or (please, please) is there now a much easier way to do it?

In one of the help files it says that USB should stand for 'UnSuitable for Broadband'...  I mean, yeah, very witty and all that...  but surely most of us out here have USB modems, so not terribly helpful!

At present, my Ubuntu machine has to depend on an XP machine to give it its internet connection.  Deep in my soul, I feel that this Should Not Be.  :)

---

### Post by renzokuken on 2007-02-05
i had a lot of issues trying to get my old speedtouch/alcatel usb modem to work on any distro.......in the end i binned and got myself a cheap ethernet based modem, plugged it in and away i went.

sorry dude, there is no easy way to get them working, if you can get hold of an ethernet based one i would use that instead

---

### Post by Jussi Kukkonen on 2007-02-05
I'm not an expert on this subject, but I believe you'll have to be more specific -- usb modems are not a standard as far as I know, so the manufacturer, model and possibly even the chipset of your device matter here.  

> 
In one of the help files it says that USB should stand for 'UnSuitable for Broadband'... I mean, yeah, very witty and all that... but surely most of us out here have USB modems, so not terribly helpful!
Don't mistake this to be just arrogance on part of the writer -- the problem is that your hardware manufacturer does not release linux drivers, does not release specifications so others could write the drivers and is not interested in implementing their hardware to any common standard.

By the way does the modem have an ethernet port too? network cards are dirt cheap (and even USB ones work pretty well)...

---

### Post by lunaz on 2007-02-05
ya i'm having issues too. i got the Qwest ActionTec GT701-WG hooked up by ethernet to my winxp comp, and it does internet stuff just fine. when i bring it to the living room where my ubuntu comp is, it dont stay connected good. the light are always on but the net goes really slow or sites time out. i have turne off wireless since i couldnt get that working either. any advice? i'm not getting any replies ot my thread.

---

### Post by Spr0k3t on 2007-02-05
I'm confused here.  You say the ubuntu machine is shared but the modem is USB?  Are you using a crossover cable to connect to the XP system?  Also, does your DSL modem support ethernet by chance?  If it does, you could get a hub/router and let the router do all the sharing for you through IP/NAT (Internet Protocol/Network Address Translation).

As for USB problems with modems, it's pretty accurate.  If the modem is not supported, it will be a bit of a struggle.

---

### Post by Jussi Kukkonen on 2007-02-05
> **lunaz said:**
> any advice? i'm not getting any replies ot my thread.

That's really not an excuse for hijacking someone elses thread...

---

### Post by Ryan450 on 2007-02-05
> **whitefort said:**
> 
At present my main PC is running XP and connecting to the internet via an ASDL broadband modem.  My Ubuntu machine is in another room, connected to it by an Ethernet cable, thereby sharing the internet connection with no problems.


hmmm this is where you've lost me. How is your ubuntu machine shared to the modem? Is it going through a router? are you swapping out the ethernet connection from XP to ubuntu when you swap computers? Are you trying to use a cross-over cable to go from your XP machine to your ubuntu setup? 

If your connection is going through ethernet then it should be able to get dhcp from it quite easily as your not going through the usb ports which is where a lot of the linux distro funky stuff comes into play.

---

### Post by John E on 2007-02-05
Is it a Speedtouch 330 modem? And are you running Dapper or Edgy?

---

### Post by whitefort on 2007-02-05
Hi, guys - sorry if I didn't give enough information.

Ok - starting with the phone socket in the wall...  :) 

The modem is a Sagem F@st 800-848.  It plugs by USB into the XP machine, and gives it internet access with Tiscali.co.uk.

The XP machine has an Ethernet card and cable, and this connects it to the Ubuntu (Dapper) machine.

The Ubuntu machine has no trouble sharing the internet connection along this cable - in fact, it just did it, out of the box.

However, my problem is that when I try to convert the XP machine to Ubuntu, it can't see the USB modem.  Therefore it doesn't have an internet connection, and therefore neither does the Ubuntu machine at the end of the ethernet cable.

I was hoping there'd be some quick and easy fix, but I guess not.  I'm finding you really need to know a lot about computers to run Linux.

Anyway, (and I'm sorry to sound SO dumb!) If I buy an ethernet modem, does that mean that one end will plug into the phone socket, the other into the PC's other ethernet socket, and Ubuntu will get the internet easily?

---

### Post by Jussi Kukkonen on 2007-02-05
> 
Anyway, (and I'm sorry to sound SO dumb!) If I buy an ethernet modem, does that mean that one end will plug into the phone socket, the other into the PC's other ethernet socket, and Ubuntu will get the internet easily?
Asking questions before buying hardware is definitely not dumb :) Basically you got it correct. You should have no problem finding a modem that is also a router with e.g. 4 ethernet ports -- that way you can connect both machines.

---

### Post by whitefort on 2007-02-05
> **Jussi Kukkonen said:**
> You should have no problem finding a modem that is also a router with e.g. 4 ethernet ports -- that way you can connect both machines.

That's helpful - Many thanks.  Is there any make/model that gets an especially good reputation as being Ubuntu-friendly?

Just one last question - are they hard to set up?  I mean beyond feeding it my ISP details - ID, password.  Does it get much more complex than that?- because I get the feeling that my ISPs tech support totally lose interest when they hear it's not a Windows question.

Presumably if I open the properties of my (current) modem connection in XP and write down just about everything I can see, that will give me everything I need to get the ethernet modem connected to the ISP?

Thanks again - and sorry if my initial post WAS a bit more whiny than I intended!

---

### Post by renzokuken on 2007-02-05
if you get something like a linksys/belkin/netgear, usually all you do is type 192.168.1.1 into your webbrowser and you get a webbased configuration page, dead easy.

---

### Post by Jussi Kukkonen on 2007-02-05
Well, the nice thing about ethernet is that it's not OS-specific -- any modem-router will work with Ubuntu, and what renzokuken said applies (the IP might be different though).

About your ISP support: You don't need to tell them you're not on Windows as you are configuring an appliance (the modem) through the web interface. I doubt you will need anything special from them though, the instructions that come with the device and the basic network info should be enough. Writing stuff down from Windows is probably a good idea.

---

