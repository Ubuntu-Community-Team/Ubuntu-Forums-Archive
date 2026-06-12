---
title: "Seeking Help With Azureus and Firestarter NAT Error"
date: 2007-06-04
forum: Absolute Beginner Talk
---

### Post by thehessian on 2007-06-04
Hey Guys.

I'm having some serious issues trying to resolve a NAT Error in Azureus on my Feisty box.

I have: forwarded the proper ports on my router (TCP and UDP) (no UPnP available, westell versalink 327w)
opened Firestarter and added a rule to allow the desired ports (15000 + range), and made my ip address static, all to no avail.

I have also installed and selected the newest Java as default, re-installed Azureus and even tried to open the ports using the iptables commands.

I am still getting a NAT Error and am wondering if anybody has figured out how to run Azureus at full capacity (green and mean!).
I have searched and tried solving this on my own for the better part of a full day now, so I figured I'd ask the experts here :)

Also, I have completely stopped Firestarter and tried to run the Azureus configuration Wizard, but it still gives me the error, and my torrents are staying yellow all the time.

I downloaded and ran Utorrent through Wine, and still got the same NAT Error, saying that port 15000 is not open.

Any suggestions?

Take Care and Thanks a ton in advance,
Hessian

---

### Post by daimaru on 2007-06-04
thats weird. i use port 50042 for azureus, cleared tcp and udp in router and added a rule in firestarter allowing connectinos for that port .. all my torrents are as green as grass :)

---

### Post by thehessian on 2007-06-04
Crazy...

I did, however, find that there is UPnP available on my router, so I enabled it there and in Azureus as well...
Still no luck though.

What do you mean you "cleared UDP and TCP" in your router?
I'll try anything! ;)

I turned the router firewall off, but still have the TCP/UDP port configs enabled.

Anybody?

Take Care,
Hessian

---

### Post by daimaru on 2007-06-04
sry this is probably going to be different for evey hardware, but i got a fritzbox wlan form avm and all i had to do was to go to ports section and enter my udp and tcp ports to allow connections to my ip address. 
only thing i can think of right now is that ur usig dhcp and that in your router the ports are enabled for a different ip address. i use static ip adress and tell my router that the ports 50042 are supposed to be open for my ip adress eg. 192.168.178.20, it would not work if i had dhcp enabled, cause my router asks for a specific ip adress on which it should grant access to the ports. 

so try using static ip if you dont already. 
sry i cant be of more help right now :(

---

### Post by daimaru on 2007-06-04
oh just remembered if you do get azureus running you will probably encounter the " too many files open " error; 
so to preempt that check [this.]("http://www.azureuswiki.com/index.php/Too_many_open_files")

---

### Post by thehessian on 2007-06-04
No worries ;)

Thanks for the help so far...

I changed my ip back to static, but still with the same results, even after a system reboot.

I don't know what else to try!

I assume there has to be a way to punch open a hole for the necessary ports using the command line.
But, alas, all of my searches have been fruitless so far.

No giving up here, though :)

Hessian

---

### Post by thehessian on 2007-06-04
Also,

Azureus runs and downloads just fine, it even uploads while the torrent is downloading.
The problem is it says I'm firewalled, even after all that I've tried, and after I complete the torrent, it will not seed, because other users cannot connect to me.

Hessian

---

### Post by Nessa on 2007-06-04
Just a thought... Does it work when you bypass the router and connect your computer directly to the modem?

---

### Post by daimaru on 2007-06-04
are your torrents all yellow? and did you try using a different port? maybe the one your using is some internal ubuntu port or something. i'm really not the most qualified person to answer your questions, so :) bear with me
EDIT: and you did add this port under your policy tab in firestarter right ? -- guess so since it doesnt work with firewall off either :(

---

### Post by thehessian on 2007-06-04
I am going to try another port range...

Be right back :D

Also, I'm not sure how to bypass my DSL router to connect to the modem...

---

### Post by Nessa on 2007-06-04
You're right. They usually use an RJ 11 connector which don't work with ethernet.. 

Just to isolate the issue... If you have another computer, can you download with no problems?

---

### Post by thehessian on 2007-06-04
Awesome!

I switched the port range to the 50000+ range and it is working!

Thanks for your help, much appreciated :D

It must be that the 15000+ range is being reserved by the system somehow...

In short, here is what I did to make it happen:

Set ip to static (consult router for info on IP range)
Made rule to allow port range in firestarter
Turned off UPnP on router
Turned off UPnP in Azureus

Thanks and Take Care,
Hessian

---

