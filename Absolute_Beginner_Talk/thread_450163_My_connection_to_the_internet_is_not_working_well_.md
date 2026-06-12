---
title: "My connection to the internet is not working well: Can you help?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by VoidBoy on 2007-05-21
I can access some web pages such as youtube, but when i try to go to msn, it just won't connect.
I installed ubuntu 3 days ago and I want to learn more about this OS, but without internet?
My gues is that my modem is not compatible with this OS. I currently have a DSL connection, but if you tell me more about it, 
it will be more helpful.

please help me out, I will really apreciate your help.
Everybody starts from the bottom so please help.

Thank you

---

### Post by Jimmyfj on 2007-05-21
What version of Ubuntu do you run? 

I run Ubuntu 7.04 Feisty Fawn and I have a ADSL cabled connection to the Internet. None of the sites I go to on the net has any problems loading. 

What browser are you using?

---

### Post by bigken on 2007-05-21
try this in the browser address bar (firefox) type about:config then in the filter bar type iipv6
and change it from false to true if your using a router it could also be your mtu settings

---

### Post by VoidBoy on 2007-05-21
> **bigken said:**
> try this in the browser address bar (firefox) type about:config then in the filter bar type iipv6
and change it from false to true if your using a router it could also be your mtu settings

I did try, but iipv6 wasn't on the menu, so I made one and still didn't worked.

---

### Post by VoidBoy on 2007-05-21
> **Jimmyfj said:**
> What version of Ubuntu do you run? 

I run Ubuntu 7.04 Feisty Fawn and I have a ADSL cabled connection to the Internet. None of the sites I go to on the net has any problems loading. 

What browser are you using?

Im using the default browser which is firefox. I upgraded my ubuntu with the 7.04 live cd so i guess i have pretty much that ubuntu. Would it be best to try to connect my DSL modem with an USB cable? Because I'm not sure what the ADSL cabled connection is.

---

### Post by bigken on 2007-05-21
sorry its ipv6 typo error :(

who is your internet provider ?

did you check what your provider mtu setting should be ?

---

### Post by VoidBoy on 2007-05-21
> **bigken said:**
> sorry its ipv6 typo error :(

who is your internet provider ?

did you check what your provider mtu setting should be ?

My internet provider its Quest and I don't know what the mtu is(sorry about that)...........could you be more specific?

Thank you

---

### Post by bigken on 2007-05-21
the mtu is a setting in the router most uk providers are set at 1500 were as aol is 1400
you need to read the help pages at your providers web site asuming you are using a router 
did you try the ipv6 again ?

---

### Post by VoidBoy on 2007-05-21
No, I haven't try the ipv6 thing because I boot the live CD and using it, I can get connection to the internet...
I believe it's because I had the version 6.10(hopefully that's the problem), but I'm installing 7.04 to see if that's the problem...................................by the way, when i checked the menu system-administration-network, the address for the "wired connection" under properties was the same (except for the picture): AUTOMATIC CONFIGURATION (DHCP)
And right at the bottom is the MODEM CONNECTION, which says "network interface is not configured" (How can I configured?)

---

### Post by VoidBoy on 2007-05-21
HEY THANKS FOR YOUR HELP, YOU REALLY GAVE ME MANY THOUGHTS.
I SOLVED MY PROBLEMS, I THINK IT WAS THE DISC VERSION 6.10 OR SOMETHING WITH THE WINDOWS XP BECAUSE, INSTEAD OF HAVING TWO OSs, I ONLY INSTALLED UBUNTU..............................AND IT WORKED!

ONCE AGAIN REALLY REALLY THANK YOU.

---

### Post by Ruin on 2007-05-31
> **bigken said:**
> the mtu is a setting in the router most uk providers are set at 1500 were as aol is 1400
you need to read the help pages at your providers web site asuming you are using a router 
did you try the ipv6 again ?

I installed Ubuntu today (Ubuntu 6.06 LTS *'- the Dapper Drake'*, I think), the latest version available from the website.  It's my first time ever using Linux and I'm impressed but I'm having problems much like the original poster's here.

Firstly I'm unsure of my version, mentions here of version 7.04, I chose to download 6.06LTS, was this a bad decision? Should I get 7.04 and reinstall? Should that have any effect on my ability to connect to Gaim - even if 6,06 is an older version it is still available for download currently from the ubuntu website..

I can connect to some websites, not others. Slashdot, for example, is fine, while google and aol.com won't load. Also I cannot connect to MSN through Gaim. I get 'error from notification server, unable to connect'. I use a wireless router, ADSL broadband supplied by AOL. A user in the #ubuntu channel suggested it was my MTU, and seeing comments here about AOL using 1400 (while my router is indeed set to 1500 default) makes me wonder if that is the problem. 

Going to about:config and changing my ipv6 to true fixes the problem with websites - I can view aol, google and all others no problem, but connecting to Gaim still doesn't work. 

Should I try changing the MTU things, if so - what to and where would I change them? On the linux machine (if so, how do I do this?), on the router (if so, would altering this affect connectivity for all other (windows) machines in my house?)? Would I change it to 1400 (as my ISP is AOL) or 1462 (as the user on #ubuntu suggested - and 'clamp it')?

I realise this is a lot of information and a lot of questions, but everyone starts somewhere and I figured I would be as specific as possible. 

Please help, it would be greatly appreciated ;)

Thanks, 

Ruin

---

### Post by bigken on 2007-06-01
give both mtu settings a try you change this in the basic router settings you can always change it back ;)

---

### Post by Ruin on 2007-06-01
Before I could play around with my router a friend appeared with a Ubuntu 7.04 disk claiming it has alot of network fixes. So we put that on and everything works fine. Thanks very much for your help ;)

---

