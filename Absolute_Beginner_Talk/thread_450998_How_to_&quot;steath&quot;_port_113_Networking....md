---
title: "How to &quot;steath&quot; port 113? Networking..."
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by discmaster on 2007-05-21
I was doing some testing at grc.com (shields up), & it said that my 113 port was closed, which means it still appears on the network.

I would like to have it set to stealth. Does anyone know networking? How is this done?

---

### Post by vtel57 on 2007-05-21
Are you behind a router?

---

### Post by discmaster on 2007-05-21
I have 2 pc's behind a router, yes. One is running xp, the other linux.

---

### Post by vtel57 on 2007-05-21
You can steath the ident port in your router's preferences. You'll have to access the admin rights to the router. Do you know how to do that? I hope so, because the first thing you should have done when you set it up was to change the out-of-the-box admin password.

Let me know...

P.S. Hi discmaster! I didn't even realize it was you. I believe we've bumped into each other around here before. ;)

---

### Post by discmaster on 2007-05-21
> You can steath the ident port in your router's preferences. You'll have to access the admin rights to the router. Do you know how to do that? I hope so, because the first thing you should have done when you set it up was to change the out-of-the-box admin password.I'm lost on that... I do remember reading something about that in the router's paperwork, I believe.

I will read the manual that came with it again, & see if it gives me the info. I need.

> P.S. Hi discmaster! I didn't even realize it was you. I believe we've bumped into each other around here before. :) Yeah, you've helped me out on a couple things before. T-bird mail, which btw is working fine; I have 3 accounts set up under it, & will be adding more!

TY

:)

---

### Post by vtel57 on 2007-05-21
What brand/model router?

Normally, you can access your router's set-up by typing "192.168.1.1" (no quotes) into your browser's address window. The Admin password box should pop up. If it's a Linksys router, I believe the password is "admin" (again, no quotes).

---

### Post by rharris on 2007-05-21
In case you router does not have a simple check box to stealth port 113, you can go into the port forwarding section and forward port 113 to a non-existent IP address outside the range of your network. In other words, outside the range of the DHCP server in the router. An IP such as 168.192.1.255

Rob

---

### Post by discmaster on 2007-05-22
I have a D-link WBR-1310. Manual says to type "192.168.0.1" in browser window. I do that & get the login screen. At that point I type in admin, leave pswd. blank & click enter, & it just reloads the page...

---

### Post by discmaster on 2007-05-22
Disregard prev. post! I reset the router & was able to log in. I am in the process of checking the settings now...

---

### Post by vtel57 on 2007-05-22
You're making progress! :)

---

### Post by discmaster on 2007-05-22
I have had a chance to look thru all the settings for the router; I must confess that I don't see anywhere that I can close port(s)? What exactly am I looking for? I don't want to go in & change settings randomly & goof things up!

---

### Post by vtel57 on 2007-05-22
If your router doesn't have a specific option to stealth Ident 113, then you'll have to "forward" that port to another address, as rharris mentions in a previous posting here. Check your router's instructions (or their website) to see how to do that. Usually, there's a section called "Port Forwarding" or something like that. I had to do this on my old Linksys router, but the newer ones do it automatically for you.

By the way, I think Steve Gibson's site ( [http://www.grc.com/default.htm](http://www.grc.com/default.htm) ) has a tutorial on there somewhere on how to forward the Ident port.

Luck! :)

---

### Post by discmaster on 2007-05-23
> to setup port forwarding on this router your computer needs to have a static ip address. 

Did a google search, found [this.]("http://www.cyberciti.biz/tips/howto-ubuntu-linux-convert-dhcp-network-configuration-to-static-ip-configuration.html")

Is this what I need to do? I wasn't looking to "open a can of worms" with this project!

Seems like more hassle than what it's worth?

Just afraid of making changes & goofing things up bad...

---

### Post by vtel57 on 2007-05-23
Most ISPs only offer static IP addresses for $$$. You most likely have a dynamic IP, so no... I wouldn't try that on your network. Trash the D-link and go out and by yourself a new Linksys. They're cheap, and will stealth Ident automatically for you. ;) If you buy online, buy from a reputable seller. There are a bunch of refurb units running around online these days.

[http://www.ewiz.com/detail.php?p=LS-BEFSR41&c=fr&pid=674ec1e1c951beb7297b86080a9b5702824ef2ba45e28039e085e46333e1c1c5](http://www.ewiz.com/detail.php?p=LS-BEFSR41&c=fr&pid=674ec1e1c951beb7297b86080a9b5702824ef2ba45e28039e085e46333e1c1c5)

Does your D-link even have a NAT firewall? Just for ha-has, post the D-link model number here. If I get a minute or two today, I'll do some research on it.

Later...

---

### Post by Zzl1xndd on 2007-05-23
The Static ip it is refering to in that section normally refers to within the network, so that a machine that has ex 192.168.1.101 with port 1720 forwarded doesn't end up being 192.168.1.102 the next day and not getting the proper forward. in this case forwarding to the non-existaint IP will fix the issue and not cause any problems as it is not intended to forward the port to a spacific machine.

Also

I would recomend a Linksys router the next time you get one as well.

---

### Post by vtel57 on 2007-05-23
> **tweakedenigma said:**
> The Static ip it is refering to in that section normally refers to within the network, so that a machine that has ex 192.168.1.101 with port 1720 forwarded doesn't end up being 192.168.1.102 the next day and not getting the proper forward. in this case forwarding to the non-existaint IP will fix the issue and not cause any problems as it is not intended to forward the port to a spacific machine.

Also

I would recomend a Linksys router the next time you get one as well.

After posting the above and wandering off to other places, I started to think about it. I was just returning here to re-read discmaster's post about the static IP. Thanks for explaining the situation. I should have realized this is what was meant in the first place.

---

### Post by discmaster on 2007-05-23
On my "port fowarding rules" area for my router, I have;

"Name"
Application Name" (ftp,http,https,DNS, POP3, & so on)
Port - Start/End
Traffic Type

No where in the router manual does it refer on how to set these. I also see "application rules" for firewall settings, which I don't use a firewall on this pc, but the other (xp) pc has one. And then there is "MAC filtering"...

Is there a good tutorial anywhere that would cover these items, so a fellow would know what to look for/check, & change settings to the proper ones?

---

### Post by vtel57 on 2007-05-23
I found [THIS](http://portforward.com/routers.htm). Scroll down to your D-link model.

[MORE](http://kbserver.netgear.com/kb_web_files/N101145.asp) stuff.

And [THIS](http://forums.afterdawn.com/thread_view.cfm/223583).

:)

---

### Post by Hunter4u on 2007-05-23
why buy a router if you have a spare pc around?  Linux has a good version out called ipcop, works rightiously......use it at my work with over 50 pc's networked, no problems.


try setting the port forwarding in special applications

Enable :  	
Name : 	<<   113 hidden
Trigger Port Range : 	113
Trigger Protocol : 	Both
Input Port Range : 	113
Input Protocol : 	both
Schedule : 	always




try that

---

### Post by nubutu on 2007-05-23
Hey, discmaster

you don't know how proud I am of seeing you doing as you are, seriously. I just hopped in to see what was on and thought about where could you be. Congratulations, mate. I told you that you were already in...

Good luck!

PS. I don't think we'll see much over here, I changed to Debian three days ago--just hated Feisty so much and I need a really stable system to focus on my work...sorry.

---

### Post by discmaster on 2007-05-23
> you don't know how proud I am of seeing you doing as you are, seriously. I just hopped in to see what was on and thought about where could you be. Congratulations, mate. I told you that you were already in..LOL

Well, thanks for the vote of confidence, but I must say that - honestly, the further I go, the more frustrated I become. Problem is, I really don't have the spare time to learn all this stuff & be doing research; That's why it is (still) so tempting to just return to xp, because it just "works", even though windows does have flaws...

But my stubborn side keeps me pluggin' away at this, so I'll probably stay w/ it, despite the hard times...

As prev. mentioned, part of the issue is conflicting info., lack of tutorials, or ones that I can understand anyway. I need a "Dumbies" guide to "Dumbies for linux"!
:D

---

### Post by vtel57 on 2007-05-23
Ask and ye shall receive...

[http://www.linuxfordummies.org/](http://www.linuxfordummies.org/)

[http://www.amazon.com/Linux-Dummies-6th-Dee-Ann-LeBlanc/dp/0764579371](http://www.amazon.com/Linux-Dummies-6th-Dee-Ann-LeBlanc/dp/0764579371)

[http://www.wiley.com/WileyCDA/WileyTitle/productCd-0470125055.html](http://www.wiley.com/WileyCDA/WileyTitle/productCd-0470125055.html)

:lolflag:

> That's why it is (still) so tempting to just return to xp...

**[COLOR="Red"]NO! NO![/COLOR]** Don't even say UGLY things like that. ;)

---

