---
title: "Problem with login after installin Kubuntu 9.10"
date: 2010-03-07
forum: Apple Hardware Users
---

### Post by iggybeans on 2010-03-07
Hi, I'm new to this and I may be doing something stupid, but I need help.
I'm installing Kubuntu 9.10 on my Powermac Quicksilver. During instillation I enter a name for my account and a password, but when I go to login the system doesn't recognize either. Got any tips as to what could be wrong?

---

### Post by linuxopjemac on 2010-03-08
[http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0](http://mac.linux.be/content/login-problems-powerbook-g4-dead-pram-0)

---

### Post by iggybeans on 2010-03-08
Tried what your reference mentioned (I replaced the clock battery, started the machine, and using the O F Apple Option keys, I entered the correct time and date).
The system still won't let me log in.
Should I reinstall Kubuntu?

---

### Post by tjl01 on 2010-03-08
I ran into the same problem today. What I did was reloaded the kubuntu cd and ran the installation as repair-powerpc? i think it was the repair option. not to sure. after installation was done, my user info finally worked. When I get home ill confirm exactly what I did.

I installed kubuntu on my old imac powerpc g3

---

### Post by iggybeans on 2010-03-09
Thanks, I've been at my wits end. I should be able to login and start using it, but it won't recognize my login and password. I'll try your idea next. Thanks again.

---

### Post by Atilana on 2010-03-10
Yeah, access to this link is very helpful

---

### Post by iggybeans on 2010-03-15
OK, new battery in place and Kubuntu 9.10 installs correctly (sort of). Still can't get the network setup. Like any other OS (supporting DHCP), my internet connection (via Comcast) should just work (just like Windows, I should just be able to plug it in and go).
But, so far, nothing. I've tried letting it set itself up and I've tried manually setting it up, but nothing works.
My internet connection DOES  work (I'm using it under the much maligned Vista OS right now).
Also, 9.10 comes with a Firefox installer that the OS says should uninstall after Firefox is installed and once run this installer tells me Firefox is already installed.
I'm fond of UNIX like OS' (and I used to work for a company in the late 80's and early 90's that built 68K based OS-9 computer systems). I remember the power of early SCO OS', the introduction of Minix, and have watched Linux as its developed. But, this stuff's still too buggy.
Hey! That why the market still favors Windows. It may not be as impressive, but overall its not nearly as much of a pain in the ***.

---

### Post by linuxopjemac on 2010-03-16
Maybe a bit late for you, but I only run Debian on PPC based machines, because it's really a lot better.

[http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso](http://cdimage.debian.org/debian-cd/5.0.4/powerpc/iso-cd/debian-504-powerpc-netinst.iso)

It's the netinstaller, so you immediately know if Debian gets your internet connection sorted out.

---

### Post by iggybeans on 2010-03-16
Thanks, I'll check it out. 
I didn't mean to sound negative, the forum has provided useful information.
It's just been a few years since I've had to struggle to get an OS set up.

---

### Post by linuxopjemac on 2010-03-16
I looked at the specs for a PowerMac Quicksilver. They were not equipped with a lot of RAM by default. I would recommend to have at least 512 Mb there, otherwise you won't be able to get the graphical user interface going. You need at least 256 Mb for a GUI. If you have that little, I would go for fluxbox or something like that, instead of Gnome or KDE.

---

### Post by iggybeans on 2010-03-16
OK, tried to install Debian (which uses very similar net detection).
Debian finds the port, but like Kubuntu (and probably Ubuntu), my Comcast internet connection (which should support DHCP) isn't found.

I guess my next move is to try something slightly more different.
I'm going to download a copy of Yellow Dog Linux.
Thanks for the help.

---

### Post by iggybeans on 2010-03-16
[QUOTE=linuxopjemac;8976618]I looked at the specs for a PowerMac Quicksilver. They were not equipped with a lot of RAM by default. I would recommend to have at least 512 Mb there, otherwise you won't be able to get the graphical user interface going.


Thanks, I've got 768MB (with 3 256MB strips). For some reason, most 512MB strips that  work in PCs won't work in a Quicksilver. Oddly enough, there's a lot more compatibility with 256MB strips (all my strips come from X86 machines). 
The graphic interface is not a problem (it runs). Frankly, considering that ATI and Nvidia haven't provided complete documentation on their products, I'm amazed that Linux programmers have been able to write functioning drivers at all.
I just need to figure out what's preventing me from connecting to a Comcast cable modem (and why Kubuntu insists Firefox is installed when I can't find it).

---

### Post by linuxopjemac on 2010-03-16
I read more problems with this modem. I would hook it up to a wired router (can be cheap) and then connect your Mac to the router.

---

### Post by linuxopjemac on 2010-03-16
If you still insist on getting that modem to work under Linux prepare yourself for some trouble. You have to get that machine to make IP addresses as a DHCP server I read.

[http://my.brandeis.edu/bboard/q-and-a-fetch-msg?msg_id=0001nG&topic_id=21&topic=Technical%20Support](http://my.brandeis.edu/bboard/q-and-a-fetch-msg?msg_id=0001nG&topic_id=21&topic=Technical%20Support)

[http://www.astro.umd.edu/~teuben/linux/comcast.html](http://www.astro.umd.edu/~teuben/linux/comcast.html)

I read here that every distribution has problems with that modem:


> My only additions are as follows: The problem is not fixed by changing
distributions and using Redhat, or Slackware, or Suse. They all have this
problem. It also doesn\'t matter if you use dhclient or dhcpcd or pump.
(Though pump is a little nicer.) They all have this problem.


[http://www.linuxquestions.org/questions/linux-networking-3/problems-with-dhcp-and-comcast-cable-modem-internet-access-62324/](http://www.linuxquestions.org/questions/linux-networking-3/problems-with-dhcp-and-comcast-cable-modem-internet-access-62324/)

---

### Post by iggybeans on 2010-03-17
I have no idea how I got this to work, but I'm posting this message under Kubuntu 9.10. The battery replacement corrected the login problem, but I couldn't get OSX or Kubuntu to recognize my Comcast internet connection.
After several reinstalls, both OS' have correctly set up the connection. What possible difference could there be? I have NO idea.
BTW - After comparing OSX and Kubuntu, I'll take the later. I have no idea why Mac users think their OS has ANY superior traits (Open Office installed perfectly under Kubuntu, and I still haven't figured out why it bombed under OSX).

Thank you all for your help and support.

---

### Post by linuxopjemac on 2010-03-18
Great to hear another happy convert! Good work.

---

### Post by zeny123 on 2010-03-18
> **iggybeans said:**
> Hi, I'm new to this and I may be doing something stupid, but I need help.
I'm installing Kubuntu 9.10 on my Powermac Quicksilver. During instillation I enter a name for my account and a password, but when I go to login the system doesn't recognize either. Got any tips as to what could be wrong?


Hiii... dude have geat detail regarding Web Hosting either it is dedicated or other .for 
 hosting solution  you can move to [http://www.go4hosting.com/managedhosting.htm.](http://www.go4hosting.com/managedhosting.htm.)

[Go4hosting is]("http://www.go4hosting.com") a company  where  hosting service 24/7 are provided Our team is dedicated to every client   Web   Hosting India

---

