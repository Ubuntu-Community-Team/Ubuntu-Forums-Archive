---
title: "firestarter settings"
date: 2007-06-09
forum: Absolute Beginner Talk
---

### Post by bobkat60 on 2007-06-09
Can anybody help please , I installed firestarter ,think I got the settings right ,but can't get anything to run through it .
Thanks Bobkat

---

### Post by caffienefree on 2007-06-10
I'm a bit confused. Are you saying that firestarter is blocking ALL traffic, inbound and outbound? Or are you saying that it appears to be doing nothing?

---

### Post by OrangeCrate on 2007-06-10
Take a look here. Pay particular attention to the ICMP Filtering Setup:

[http://firestarter.sourceforge.net/manual/wizard.php](http://firestarter.sourceforge.net/manual/wizard.php)

---

### Post by alienexplorers on 2007-06-10
Firestarter is just a graphical front end for iptables.  iptables is your actual firewall.

---

### Post by bobkat60 on 2007-06-10
> **caffienefree said:**
> I'm a bit confused. Are you saying that firestarter is blocking ALL traffic, inbound and outbound? Or are you saying that it appears to be doing nothing?
Hi thanks for replying 
I installed firestarter and can not get onto any web site I also have an add on 'Forecastfox ' and that isn't updating either when firestarter is on.

---

### Post by bobkat60 on 2007-06-10
Hi Thanks for replying.
I had a look at the link and looking at the ICMP settings I enabled filtering but do I click on the boxes eg:echo (ping) , traceroute etc  I thought they were kept clear. am I wrong?
Running the Wizard,  Firestarter identifies connection by ethernet eth(0) although I see it suggests
for noobs like me to use PPPoe  .I cannot change this from eth(0)

---

### Post by OrangeCrate on 2007-06-10
Here are my settings:

The following are "checked"

Timestamping
MS Traceroute
Traceroute
Unreachable

The others are unchecked.

[http://www.fs-security.com/](http://www.fs-security.com/)

---

### Post by laidback on 2007-06-10
> **OrangeCrate said:**
> Here are my settings:

The following are "checked"

Timestamping
MS Traceroute
Traceroute
Unreachable

The others are unchecked.

[http://www.fs-security.com/](http://www.fs-security.com/)

Why these? what do they do?

---

### Post by OrangeCrate on 2007-06-10
> **laidback said:**
> Why these? what do they do?

Link in post #3 of this thread.

---

### Post by bobkat60 on 2007-06-10
Thankyou  for your reply again. I tried these ;no joy ...I see in firestarter bottom panel 1.1mb received  .  .2mb sent  but nothing yet seems to work .....I'm using DLink Modem dsl320T on ethernet  DHCP settings. IP uses PPPoevmu .   but can't seem to tell FIrestarter that.

---

### Post by OrangeCrate on 2007-06-10
> **bobkat60 said:**
> Thankyou  for your reply again. I tried these ;no joy ...I see in firestarter bottom panel 1.1mb received  .  .2mb sent  but nothing yet seems to work .....I'm using DLink Modem dsl320T on ethernet  DHCP settings. IP uses PPPoevmu .   but can't seem to tell FIrestarter that.

Sorry, I don't know what else to tell you. I suggested the settings that work for me, but if it's not working for you, I would suggest to review the installation instructions, and leave the ICMP settings as default. Maybe someone else will see this and offer an additional solution to help you.

---

### Post by steve.horsley on 2007-06-10
Start off by trying to ping something by name:
**ping [www.ubuntuforums.com](www.ubuntuforums.com)**
It should come back and say it's pinging a particular IP address. If it can't do that then I guess you haven't enabled DNS.

---

### Post by ramjet_1953 on 2007-06-11
Perhaps we need to go back to basics, here.

1. Firstly, why do you need to alter iptables anyway?

2. Do you need to do any port forwarding?

3. If not, leave iptables well alone.

4. It is not good to run the Firestarter GUI all of the time, as root privileges are required to run it and by doing so, you are then creating a security risk.

5. If you need to play with iptables, do your homework first, otherwise you will be leaving yourself open to serious security issues.

Regards,
Roger :cool:

---

### Post by bobkat60 on 2007-06-11
Hi  OrangeCrate
Many Thanks for you help in trying anyway .
back to the drawing board .
Bob

---

### Post by bobkat60 on 2007-06-11
Hi  Rodger
Thanks for your reply. being a newby enrolled from XP I just understand that I still need a firewall
and am trying to get it to work, unfortunatly , its working too well and doesnt allow me to use the internet at all.
any help in trying to get the right settings appreciated . Thanks
Bob W

---

### Post by bobkat60 on 2007-06-13
Hi  AlienExplorers
Thanks for your reply .
I found a book at the library and reading that, see what your saying.
Question: does Iptables start automatically. and when I run firestarter, does it interupt iptables? 
because when i click the button saying start,  it leaves an icon in the top panel showing on /off
When trying to browse I can't get any web pages if On!

---

### Post by Shazaam on 2007-06-13
What Firestarter does is let you easily configure iptables. Iptables loads at boot so you dont really need Firestarter loaded up in your panel to have iptables do it's job. One of the differences between Linux and Windows.:D
Here is a good link, make sure you read the instructions and warnings about security.

[http://ubuntuforums.org/showthread.php?t=187899&highlight=krazypenguin+firestarter](http://ubuntuforums.org/showthread.php?t=187899&highlight=krazypenguin+firestarter)

---

### Post by xpod on 2007-06-13
I use firestarter myself but unless you actually want to open ports for whatever reason then theres really no need for it.If you do want to set any particular rules then you dont need to have firestarter actually running once you`ve set them.

The only time firestarter has prevented me actually browsing is when i`ve had the network settings muffed up.

---

### Post by bobkat60 on 2007-06-30
Thank you Ram jet .
After doing a security test I find that all ports appear to be invisible or closed , so I'll take your advice and leave well enough alone. Thankyou

---

