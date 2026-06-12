---
title: "Firestarter: Source &amp; Destination both localhost (Port 47472)"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by gerrymoth on 2007-04-25
Can anyone tell me if this is normal for the Source & Destination both to be "localhost" (127.0.0.1) with connection to Port 47472. I installed Amarok last night and I never noticed it doing this last night, but it is today.

Can someone explain to me what this is doing?

---

### Post by leibowitz on 2007-04-25
Maybe it's just connecting to itself. What's so wrong about this situation. I don't get it.

---

### Post by gerrymoth on 2007-04-25
> **leibowitz said:**
> Maybe it's just connecting to itself. What's so wrong about this situation. I don't get it.

I'm not to clued up on these things, its the first I've seen it doing it and just thought it didn't look right?

---

### Post by leibowitz on 2007-04-25
To me it seems totally OK.

---

### Post by gerrymoth on 2007-04-26
Thanks, noticed it was only doing it while I connect to last.fm from within Amarok.

Maybe one day I'll trust the firewall is working properly and stop looking at Firestarter. Been that used to Windows for the last 20 years and only been using Linux for a few months.

---

### Post by misterfixit on 2007-09-14
My system has had a series of anomalies which were shown as localhost trying to contact localhost using either ports 2206, 2207, 2208 or 2209 on several occasions.  Here is wht my investigation has found out so far and how I did what I did:

System:  Ubuntu Linux; latest updates, etc.

I ran both rkhunter and chkrootkit one after the other and then
compared the output (which I pipe to a txt file and then print so I can
physically compare, highlight and then shred).  I am aware of the propensity for both applications to return false positives and to be easily defeated by file name changes.

Some warnings are easy to figure out (like the LKM) but others are more
obscure.  I did extensive Google searching on each and every one of the warnings.

For example, I found a warning  about susiicious script -- which I couldn't figure out why, and  then simply
opened, examined it, and then seeing nothing which made sense to me,
changed the name of the file and chowned it to "neiman" (my nobody file
and general bit bucket).  Of course user neiman (German for no-one and a
name which has interesting historical connections) is set to have no
permissions at all.

Next, using a combination of wireshark (as root) and the verbose output
from firestarter I found that there was a port opened (2208) between
"localhost and localhost" as if the work station was talking to itself via
port 2208.

I set firestarter to deny ports 2206, 2207, 2208 and 2209 (being extra
careful in case of a roll-over.)  Then I did a complete and drastic cold
reboot (shutting everything off at the power mains, unplugging the cat 5
cable from both the workstation card and from the router, then restarting
the box, the router, the cable adapter, and other bits and pieces dangling
from the workstation.

Next, after the workstation was up and running with the log-on prompt
screen, I signed on as user neiman and proceeded to load sequentially each
of the application which normally run open on user dave.  user dave has 12
windows set up with each one a different function and name.  Looking like
this:

Window #:

1 = Thunderbird email
2 = Firefox browser
3 = System work area (usually no applications open)
4 = Connection Mapping (EtherApe and xtraceroute)
5 = e-Books (browser and PDF reader for e-Books I am reading)
6 = Working Area #1 (Open Office word processing)
7 = Kopete Chat
8 = Google Earth (usually not loaded)
9 = Music (xmms connected to [www.radioparadise.com](www.radioparadise.com) - 24/7)
10 = Solitaire, of course
11 = KOrganizer schedule application open 
12 = System Status (Ghod view of system, including firestarter, gkrellm, sysmonitor, terminal window open, ksysdisk)

What transpired on the real-time view from EtherApe compared with
firestarter firewall, was that localhost was transmitting "where is {ip
address of the linux box in question}" packets to localhost in what
appeared to be an endless loop.

I began shutting off each active process, using root top application in
an sudo'd terminal.  I recognizing that deliberately killing processes one
by one is dangerous, so I chose my victims carefully before
beginning the wack-a-mole process.

At the end of the killing floor process, firestarter's display of active
connections still listed the localhost --> localhost connection on port
2208.

Now ports 2207 and 2208 are well known as potential holes for trojan
behavior.  My question then at that time, did the Linux box in question
have a trojan or not?

I continued the wack-a-mole process and eventually crashed the system when
I yanked lifesupport on a netstat process which appeared to be a zombie
rather than asleep.

I once again powered up the system and returned to user dave and the Full
Monty of screens and applications.  Neither firestarter or EtherApe showed
any activity on pots 2008, et al.

I used WireShark to scan the dormant and unused WIFI card ra0 (which has
had the actual antenna removed at the card and a terminating dummy
antenna/RF sink screwed into the antenna connector).  Nothing there,
Citizen, no move along.

I used WireShark again using the ea0 Cat 5 network card in both
promiscuous mode and in non-slut mode.  Again, nothing to or from 2206,
07, or 08.

So far (after a measured 465 hours of up time) there has been no further
indication of any activity on the suspect ports 2206, 07, 08, 09.  Neither
has there been any other suspect behavior on other ports.  Meaning that
the ports which are sending and receiving data are the ports that are
supposed to be there and working for the various applications loaded which
need communications.

Any ideas, comments, or remarks are requested.

---

### Post by VraiChevalier on 2007-09-14
> Any ideas, comments, or remarks are requested
Nice! Now that's what I'm talkin' about!

Question: What was the root of the port requests? (or did I just miss it?) 

I'm a paranoid former Windows user. Always trying to learn about ports, netstat, etc., etc.

---

### Post by misterfixit on 2007-09-14
As to why .. I haven;t figured it out yet.   When user neiman (German for "nobody", a name with some interesting historical connotations) is the only user there are NO scripts executing.  So, I don't know the answer to this situation.

Dave

---

