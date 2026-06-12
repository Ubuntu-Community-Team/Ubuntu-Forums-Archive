---
title: "What firewall? (firestarter doesnt cut it)"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by lllj on 2006-05-12
I searched for it, read all the stickies and googled it, but im still not clear on what the firewall of choice for linux is. Other then firestarter that is. Firestarter responds to ping requests and has port nill "closed" instead of in stealth. Not very impressive. 

I did a search in synaptic but there were to many to test them all. 

Which ones are any good?

---

### Post by red_shrike on 2006-05-12
When you find out, notify me! I am loking for one too

---

### Post by ZiLOG_Z80 on 2006-05-12
what did you use to test firestarter, I'm using it and all tests I have done show full stealth including ping. maybe you need to alter options?

Tested using [sheilds up]("https://www.grc.com/x/ne.dll?bh0bkyd2") and [auditmypc]("http://www.auditmypc.com/")

---

### Post by steve.horsley on 2006-05-12
That sounds like the firewall isn't running. You can find out what rules it has actually applied with the command **iptables -L**

What is pirt nill?

---

### Post by mlind on 2006-05-12
firestarter is not a firewall, it's a GUI frontend for IPTABLES firewall built-in kernel.

Have you tried fwbuilder? It's more complex, but very good alternative iptables gui.

/edit
oops typo, cheers erik1397

---

### Post by user1397 on 2006-05-12
[quote=mlind]firestarter is now a firewall[/quote] you mean firestarter is _***not***_ a firewall (just a small detail)

---

### Post by mlind on 2006-05-12
[QUOTE=erik1397]you mean firestarter is _***not***_ a firewall[/QUOTE]

details.. :mrgreen:

---

### Post by 5-HT on 2006-05-12
[quote=lllj] Firestarter responds to ping requests and has port nill "closed" instead of in stealth. Not very impressive. [/quote] 
Firestarter can refrain from responding to ping requests and stealth ports.
Those options can be found in the preferences menu.[LIST]
[*] ICMP filtering options, appropriately enough, are under the ICMP filtering section[/LIST][LIST]
[*]The option to stealth ports (drop rejected packets silently) is under the advanced options[/LIST]BTW, port stealthing doesn't necessarily offer any increased protection (this has been discussed on this forum and elsewhere, a google or forum search will provide you with the information).

Hope that helps.

---

### Post by openmind on 2006-05-12
Ubuntu ships with a very efficient and secure-by-default firewall (Iptables). Firestarter is just a front-end for that which allows you to alter those defaults (opening a torrent port for instance). Iptables doesn't listen to any ports by default.

My suspicion is that without altering firestarter in any way the tests would show an extremely secure system.

---

### Post by lllj on 2006-05-12
[QUOTE=5-HT]

[*]The option to stealth ports (drop rejected packets silently) is under the advanced options[/LIST]

[/QUOTE]

Ok, found the ICMP settings. ](*,)  

But drop silently is checked, and it works for every port but nill. What do I do about that?

Thanks for all the answers guys.

---

### Post by Papa-san on 2006-05-12
What are you using to test your firewall?

I'd like to test my unaltered iptables there just to see...

Please?

---

### Post by lllj on 2006-05-12
[QUOTE=Papa-san]What are you using to test your firewall?

I'd like to test my unaltered iptables there just to see...

Please?[/QUOTE]

[QUOTE=ZiLOG_Z80]

Tested using [sheilds up]("https://www.grc.com/x/ne.dll?bh0bkyd2") and [auditmypc]("http://www.auditmypc.com/")[/QUOTE]

:-k

---

### Post by lllj on 2006-05-12
[QUOTE=steve.horsley][/B]

What is pirt nill?[/QUOTE]

[https://www.grc.com/port_0.htm](https://www.grc.com/port_0.htm)

---

### Post by Papa-san on 2006-05-12
> Originally Posted by **_ZiLOG_Z80_** (not lllj...)

Tested using sheilds up and auditmypc
:-k

---

### Post by gingermark on 2006-05-12
Just to say, Guarddog is a KDE front-end for iptables that I think is far easier to use than Firestarter.

Installing it in Gnome would mean installing some KDE libraries (unless you've installed other KDE programs), but if you fancy giving it a go, you can use aptitude so you can remove all those libs again if you don't like it.

"sudo aptitude install guarddog" should do the trick. Then, if you don't like it, "sudo aptitude remove guarddog" would remove all the dependencies as well.

But I think you'll like it - it makes iptables REALLY easy, and works great!

---

### Post by 5-HT on 2006-05-12
[quote=lllj]Ok, found the ICMP settings. ](*,)  

But drop silently is checked, and it works for every port but nill. What do I do about that?

Thanks for all the answers guys.[/quote] 
Hmm...I don't really know much about port 0, but from what I could find, it seems to be a funny one.

What about going into preferences -> advanced options -> block traffic from reserved addresses on public interfaces?

---

### Post by Papa-san on 2006-05-12
Well, I went to both sites and failed at both of them... Many open ports and dozens showing 'closed' Then I reconfigured firestarter and rebooted. once again, failing at both sites... any suggestions?

---

### Post by dirtvoyles on 2006-05-12
I used Guarddog to configure my iptables, and I passed all but the port 113 scan.

---

### Post by mlind on 2006-05-13
I use firestarter 1.0.3 with default settings, DHCP lease renewal enabled and only
allowing ICMP packets Echo reply, Timestamping and Unreachable.

GRC Shields Up! portscan shows "passed" result 
and I tried with nmap too, same results.

---

### Post by ZiLOG_Z80 on 2006-05-14
[QUOTE=Papa-san]Well, I went to both sites and failed at both of them... Many open ports and dozens showing 'closed' Then I reconfigured firestarter and rebooted. once again, failing at both sites... any suggestions?[/QUOTE]

I'm using Firestarter 1.0.3, ICMP Filtering enabled but nothing else and under Advanced Options set to Drop Silently and Block Broadcasts from External Network.

If that doesnt work I can only suggest setting up iptables manually

---

### Post by cgjones on 2006-05-14
[QUOTE=openmind]Ubuntu ships with a very efficient and secure-by-default firewall (Iptables). Firestarter is just a front-end for that which allows you to alter those defaults (opening a torrent port for instance). Iptables doesn't listen to any ports by default.

My suspicion is that without altering firestarter in any way the tests would show an extremely secure system.[/QUOTE]

I was under the impression that a default install of Ubuntu had iptables set up, but with no rules in place.

---

### Post by Papa-san on 2006-05-14
Reset defaults, and set ICMP's as suggested previously...

Pass all but the port 113 now :D 

I do have the latest firmware for my linksys, but don't know what to put in the blanks to do the port forwarding to stealth that port... I suppose it is much better than it was!
Thanks!

---

### Post by 5-HT on 2006-05-14
[quote=Papa-san]Reset defaults, and set ICMP's as suggested previously...

Pass all but the port 113 now :D 

I do have the latest firmware for my linksys, but don't know what to put in the blanks to do the port forwarding to stealth that port... I suppose it is much better than it was!
Thanks![/quote] 
Port 113 is another funny one (there's lots of info on it that a google search will yield).

If you want to stealth the port after reading a little about it, simply forward traffic on that port to a non-existent address on the subnet.

Hope that helps.

---

### Post by lllj on 2006-05-14
Ive tried the setting you all wrote you used, and never had problems with 113. Strange, one would think we should get the same results.

I cant figure out however, how to stealth 0 and 1. 

Any ideas?

---

### Post by ZiLOG_Z80 on 2006-05-14
[QUOTE=cgjones]I was under the impression that a default install of Ubuntu had iptables set up, but with no rules in place.[/QUOTE]

No rules are set by default, this means anything can connect to a port that software is listening on. By default Ubuntu has no software listening on any port and is therefore secure. Onec software starts opening ports up unless you have iptables set to filter the traffic, they may be connected to by anyone who has the know how

---

### Post by ZiLOG_Z80 on 2006-05-16
[QUOTE=lllj]Ive tried the setting you all wrote you used, and never had problems with 113. Strange, one would think we should get the same results.

I cant figure out however, how to stealth 0 and 1. 

Any ideas?[/QUOTE]

try removing firestarter (you could just disable it, but removing it is best) and then list you iptables setup```
sudo iptables -L
```

Your listing should be empty```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination         

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination         

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination 
```if not use```
sudo iptables --flush
``` and list again. If its still not empty try```
sudo iptables --flush -t filter
sudo iptables --flush -t nat
sudo iptables --flush -t raw
```now it should be empty. If not I have no idea.

Now try reinstalling firestarter and hopefully you should be stealthed.

If you dont remain stealthed or if stop being stealthed after a reboot you must have a script or something altering your iptables

---

### Post by frodon on 2006-05-16
The best way is to write the firewall rules yourself trough iptables, it's not hard to do and i (and many of us here) can provide you some support.
If you're interested i advice you to start reading my small guide on the topic : [http://doc.gwos.org/index.php/IptablesFirewall](http://doc.gwos.org/index.php/IptablesFirewall)

---

### Post by derjames on 2006-05-16
Hi there, actually iptables is quite powerful, you just need a bit of reading to understand how it works. Please see the iptables project webpage at

[http://www.netfilter.org](http://www.netfilter.org)
for further information and also check

[http://www.netfilter.org/documentation/index.html](http://www.netfilter.org/documentation/index.html)

for the full documentation, after reading deeply this; perhaps you won't need  frontend software such as firestarter... hope this helps

cheers

---

### Post by red_shrike on 2006-05-19
Wait, considering ports are being used by malware which doesn't exist on Linux, how useful is this anyway? I have checked few ecurity sites and such, and even while ports are secured and s* like that, it is still capable of reading my resolution, IP and simmilar information. To my understanding, part of the problem is also in the application that browses the web (Firefox in my case), + other settings. Threfore, my question is whether is there some way of not giving out you real IP adress, resolution and other personal data? Besides proxy I mean.:confused:

---

### Post by kriding on 2006-05-20
When I use the shields up site, it says that my box is replying to the ping request, but I have the ICMP's set to block it, but it stil there. Any suggestions?

---

### Post by ZiLOG_Z80 on 2006-05-20
Are your advanced settings set to drop?

---

### Post by kriding on 2006-05-20
yes

---

