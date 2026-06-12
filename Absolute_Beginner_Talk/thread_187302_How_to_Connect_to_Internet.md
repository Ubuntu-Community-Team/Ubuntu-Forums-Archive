---
title: "How to Connect to Internet"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by XOSag on 2006-06-02
Hello; as you may probably have guessed, I am a Linux newbie, so bear with me if this question seems idiotic. ;) 

I've been struggling with getting my internet to work under several Linux distros, including MEPIS (back in its Debian days), and, of course, Ubuntu. I have a cable internet connection that's hooked up to a router which is then connected to my computer. When I start up Ubuntu 6.06 (I've only tried the LiveCD as of yet), it detects my ethernet card perfectly and says its active, but I cannot access the internet.

Initially, I tried to use DHCP to obtain an IP address, but, when that failed, I tried setting up a static IP with information from my routher configuration panel. I had a bit of luck with that: I would get a great big pause when I tried to ping a domain or connect to a website, but then I would get the "Hostname unknown: xxx" error in the terminal. 

So, now I'm stuck and would really appreciate any assistance you guys have to offer.

---

### Post by deadgobby on 2006-06-02
Who is your internet provider, like Cox Cable, Meadia Com, and ect?

---

### Post by ComplexNumber on 2006-06-02
[quote=XOSag]Hello; as you may probably have guessed, I am a Linux newbie, so bear with me if this question seems idiotic. ;) 

I've been struggling with getting my internet to work under several Linux distros, including MEPIS (back in its Debian days), and, of course, Ubuntu. I have a cable internet connection that's hooked up to a router which is then connected to my computer. When I start up Ubuntu 6.06 (I've only tried the LiveCD as of yet), it detects my ethernet card perfectly and says its active, but I cannot access the internet.

Initially, I tried to use DHCP to obtain an IP address, but, when that failed, I tried setting up a static IP with information from my routher configuration panel. I had a bit of luck with that: I would get a great big pause when I tried to ping a domain or connect to a website, but then I would get the "Hostname unknown: xxx" error in the terminal. 

So, now I'm stuck and would really appreciate any assistance you guys have to offer.[/quote] strangely enough, i'm having exactly the same problem. i'm beginning to wonder if its something to do with the firewall being too restrictive. i've just (somehow) managed to get my belkin wireless card working today. i can successfully ping address such as google. i can do everything except get a webpage to load. i've tested it on [www.google.com]("http://www.google.com") etc, but i can't get any webpage to load. i suppose i'll figure it out eventually, but i wouldn't mind some tips that i could try out by someone whos been there and done that.


[B]
XOSag[/B]
do you have net-tools installed? thats quite useful and may help you to discover why you're not connecting.

---

### Post by XOSag on 2006-06-02
**DeadGobby**, I'm currently with Adelphia HSI.

**ComplexNumber**, I don't think I have net-tools installed, unfortunately.

---

### Post by Jimmey on 2006-06-02
Have you specified the correct DNS address(es)?

Usually, the router acts as a DNS server, and so you can set your DNS address to be the same as your default gateway address ( the IP address of your router ). You can do this my wading through your Desktop Environment's network manger ( In Ubuntu, that's "System >> Administration >> Networking " ).

If this doesn't work, could you both please post the contents of /etc/networking/interfaces in here, so that I can take a closer look?

Thanks.

---

### Post by ComplexNumber on 2006-06-02
to (partially) connect to the internet, i used an application called wifi-radar. i didn't bother to use network manager because i couldn't find the correct adaptor despite that fact that i installed the indows inf and sys file in addition to the ndiswrappers which 'wrap' around the windows drivers.
if i load up gnome system monitor, then immediately load up firefox, i can see that there are packets both being sent and received. yet the bluebar along the bottom of firefox goes to hald way and then stops there. its got to be either a firewall or DNS problem. i can't think what else it could be. i can successfully ping any web address,  but i can't get any webpage to load.  any ideas? :confused:

btw i'm using a router.

---

### Post by Jimmey on 2006-06-02
It's not a firewall problem - Or at least it shouldn't be.

Try pinging google.com, then about two seconds later, pressing CTRL + C - Then, if you could post the packet loss figures, I'd be very appreciative. 

It does, to me, sound like a DNS problem. Could you also post what > less /etc/resolv.conf shows? ( Press "Q" to exit the screen that appears when you enter that command ).

Thanks.

---

### Post by CameronCalver on 2006-06-02
try this just say your isp is 203.178.1.150 
 
first go to network tools and properties then static then for Ip address what evrer you want just do 192.168.1.110 then gatway 255.255.255.0 and gateway your routers ip then open up a terminal ping 203.178.1.150 it should be like this 
PING 203.178.1.150 (203.178.1.150) 56(84) bytes of data.
64 bytes from 192.168.1.1: icmp_seq=1 ttl=254 time=0.618 ms
64 bytes from 192.168.1.1: icmp_seq=2 ttl=254 time=0.608 ms
64 bytes from 192.168.1.1: icmp_seq=3 ttl=254 time=0.617 ms

if that doesnt work try ping xxx.xxx.x.xxx (yours routers ip usually is 192.168.1.1

---

### Post by ComplexNumber on 2006-06-02
> Try pinging google.com, then about two seconds later, pressing CTRL + C - Then, if you could post the packet loss figures, I'd be very appreciative. pinging is not a problem. 0% bytes lost. 
thats what makes the problem so strange.


> /etc/resolv.conf
 
it shows this :
> 
automatically generated by network manager (do not edit)


namespace <address of my router>

---

### Post by Jimmey on 2006-06-02
Is that the internal, or external address of your router?

It doesn't look like a DNS issue, then. What does > less /etc/network/interfaces/ show?

---

### Post by ComplexNumber on 2006-06-02
> Is that the internal, or external address of your router? i'm not sure what you mean. its not a case of it being internal or externel. its the same as everyone elses router. several computers around the house are conencted to a router int he house. its the address of that.


> 
/etc/network/interfaces/ there is no /etc/network folder

---

### Post by bt224 on 2006-06-02
I don't have this kind of card, but this worked for me perfectly.

[http://www.ubuntuforums.org/showthread.php?t=186430](http://www.ubuntuforums.org/showthread.php?t=186430)

---

### Post by ComplexNumber on 2006-06-03
i am about 90% there. because i can access the internet by typing addresses such as 299.269.99.59 (google, i think), this MSUT be that its a DNS problem.



**XOSag**
instead of typing in [www.google.com]("http://www.google.com") or some other address, type in the address as XXX.XXX.XX.XX. if you can connect that way, it means that its a DNS problem. DNS is responsible for converting XXX.XXX.XX.XX into the domain names such as [www.google.com]("http://www.google.com").

thanks to all who have helped so far :)

---

### Post by deadgobby on 2006-06-03
Here is a K.I.S.S. thing for you to do. Turn off your router and your cable modem off. Wait for a minute and turn them back on. Restart you Linux box with both router and modem on. See if Ubie will auto detect the signal. I have Meadiacom cable with Cisco wired broadband router. Do you have wireless router? You said it work fine with Breezy, do you recall what you did in breazy to have the O/S to read the signal. 
Some times it the simple thing as see if the lamp is plug in.
Gobby ;)

---

### Post by bobpur on 2006-06-03
This worked for me. After I had installed dapper, I didn't have an internet connection either. As it was late, I shut down my system, and went to bed. This morning when I booted back up, I had internet. 
I believe it was the simple act of turning off my router and modem thatfixed the problem.
                                   Good Luck!

---

### Post by ComplexNumber on 2006-06-06
ots also a good idea to go to services in your menu and switch wpa_supplicant OFF and don't have it started at boot time. i switched it off, then the gnome keyring manager popped up, asked me for the password, then i connected.

---

