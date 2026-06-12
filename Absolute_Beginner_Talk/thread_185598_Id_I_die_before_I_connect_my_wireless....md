---
title: "Id I die before I connect my wireless..."
date: 2006-06-01
forum: Absolute Beginner Talk
---

### Post by NewDisciple on 2006-06-01
If I die before I connect my wireless please remember me and spread my ashes over my laptop.  I thought I had made progress but part way thru I discovered that my wife no longer had internet access.  Could this be because she has windows and I have linus, trying to share one router?  Also, for some reason I have to re-enter the DNS address everytime I want to go online.  Any ideas?  It seems to me that some of the past forums have conflicting information which I can't make heads or tails of.  At one point I thought I had a handle on this, but now I'm so turned around - just color me confused!

---

### Post by disciple on 2006-06-01
ahm. had a similar problem..  you can modify the DNS file manually

"sudo nano /etc/resolv.conf"
and add  "nameserver 196.3.132.1"   <---if 196.3.132.1 is your DNS and repeat for others


then make it read-only with "sudo chmod 444 /etc/resolv.conf"

so far, that's working for me..

with regards to what's happening with your other box, perhaps a bit more detail?

are you using dhcp, what router, wireless chipsets , etc

---

### Post by NewDisciple on 2006-06-01
My computer is a Dell E1705 laptop with Intel 3945.  The rounter is Belkin Wireless G.  And yes I am using dhcp.

---

### Post by NewDisciple on 2006-06-01
I forgot to mention that I have 6.06 LTS installed.  Please forgive my typo's.  I really can read and write, but my fingers   however, went to a different school.

---

### Post by disciple on 2006-06-01
[QUOTE=NewDisciple]My computer is a Dell E1705 laptop with Intel 3945.  The rounter is Belkin Wireless G.  And yes I am using dhcp.[/QUOTE]


hmm.. the fact that your wife's machine uses win, and you use linux , should not  be a problem..

you're using dhcp, so their shouldn't be any conflict with both machines gettin the same address..


your wife's machine.. when your machine is successfully accessing the net, what happens?  does it get a unique ip address, and when your linux machine is off, does she get through?

---

### Post by NewDisciple on 2006-06-01
I tried the sudo nano line, but all I got was-no command found.

---

### Post by nalmeth on 2006-06-01
Are you sure you spelled it correctly? nano surely is included by default..
You can replace nano with gedit (gnome) or kate (KDE). Nano is just a terminal-based text editor. 

Read thru the wireless help link in my signature, it may help you out.

---

### Post by ProjectGod on 2006-06-01
"I'd die before i connect my wireless" :lol: 

you can also use "pico" instead of nano! :D

besides the fact that i'm getting crosseyed just reading this thread...

you might want to enable DHCP via the GUI for the ethernet adapter... then using your windows machine log into the router... open up Internet Explorer and in the address bar type the routers address e.g. [http://192.168.2.1](http://192.168.2.1) ... after logging into the router... make sure the router is DHCP enabled and giving out addresses... also check to see if the ISP's DNS server address is also being given out to the DHCP clients (ubuntu and windows machiens)

i find that most of the time the DNS server is set to the router itself... which isn't going to help if you want to access the internet.

cheers

---

### Post by NewDisciple on 2006-06-01
I can't answer your last question as my wife is watching a movie on her laptop.  But, I will investigate that tomorrow.

---

### Post by ProjectGod on 2006-06-01
you can try using your ubuntu machine to log into your router...

try this at the terminal... and please print out what you get 

ifconfig

cheersie :p

---

### Post by morequarky on 2006-06-01
Everyone here is giving great answers.

You have internet coming to your house.  One computer can have access yet the other can't.

1. You have a router?  Or do you have a "HUB"?  What does your linksys say?   You need a router, not a hub.
2. 192.168.1.1 is usually the address to access a linksys router. in the general setup you need to make sure DHCP is enabled like another poster said. The username AND password for your router is probaby "admin".  Don't worry, we can't access your router and probably don't want to.
3. Is there any other access points(routers) around in other houses/apartments?  You might be trying to connect to the wrong router.
4. Do you have a dual boot system?  boot both computers to windows and see if they connect ok.  Linux may not support your wifi card in your computer, in which case you need to update something or buy a different computer.  I am guessing your dell doesn't have this issue, but you may need to download something somewhere.

Just some ideas.

---

