---
title: "Installing New Apps"
date: 2007-02-22
forum: Absolute Beginner Talk
---

### Post by ubunutgoz on 2007-02-22
Hi Ubuntu people,  I am an Ubuntu Newbie, so please bear with me...

In short, my problem is installing new software. I thought I had got somewhere with ipv6, but still get the messages (see below). I did get the updates, and installed in the last hour or so.

What I want to do is install stuff like VLC, SKYPE, REALPLAYER etc...

Here's a brief history Edgy-Eft 6.10

1 - Downloaded DVD and installed in non-graphical mode - all ok except FIREFOX wouldn't work.
2 - changed some setting in FIREFOX including turning ipv6 off, and also adjusting some network.http.. setting - ALL WORKED
3 - tried to install VLC, but couldn't update the application register
4 - looked around and learned that i needed to diasble ipv6 in /etc/modprobe.d/aliases using the command alias net-pf-10 off ipv6
5 - then lo and behold, the system recognised i needed security updates, which of course i did.
6 - now FIREFOX didn't work, checked settings were still the same (they were). So in /etc/modporbe.d/aliases I turned ipv6 back on, FIREFOX worked!
7 - But still can't down load new software.

And this is where I am now, not able to add new software, and wondering if the alias net-pf-10 off ipv6 needs to be changed everytime I want to check for security update.

I REALLY REALLY want to get away from Uncle Bill, but this is getting to be a chore. I simply want to use my machine!

HARDWARE
IBM Thinkpad r50e
256k RAM (I will be upgrading!)
40G disk
Intel IPW2200 interner card
D-Link 604 wireless router

Just a thought, would this all go away if I plugged cable between router and computer?

So, Please, if anyone can point me in the right direction, please help.
Many thanks
Alan

PS, also posted this in Networking, but I think it belongs here.

[http://archive.ubuntu.com/ubuntu/dis...y/Release.gpg:](http://archive.ubuntu.com/ubuntu/dis...y/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...s/Release.gpg:](http://archive.ubuntu.com/ubuntu/dis...s/Release.gpg:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:](http://archive.ubuntu.com/ubuntu/dis...ion-en_GB.bz2:) Could not connect to archive.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...y/Release.gpg:](http://security.ubuntu.com/ubuntu/di...y/Release.gpg:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...ion-en_GB.bz2:](http://security.ubuntu.com/ubuntu/di...ion-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...ion-en_GB.bz2:](http://security.ubuntu.com/ubuntu/di...ion-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...ion-en_GB.bz2:](http://security.ubuntu.com/ubuntu/di...ion-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://security.ubuntu.com/ubuntu/di...ion-en_GB.bz2:](http://security.ubuntu.com/ubuntu/di...ion-en_GB.bz2:) Could not connect to security.ubuntu.com:80 (1.0.0.0), connection timed out
[http://packages.freecontrib.org/ubun...t/Release.gpg:](http://packages.freecontrib.org/ubun...t/Release.gpg:) Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
[http://packages.freecontrib.org/ubun...ion-en_GB.bz2:](http://packages.freecontrib.org/ubun...ion-en_GB.bz2:) Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
[http://packages.freecontrib.org/ubun...ion-en_GB.bz2:](http://packages.freecontrib.org/ubun...ion-en_GB.bz2:) Could not connect to packages.freecontrib.org:80 (1.0.0.0), connection timed out
[http://medibuntu.sos-sts.com/repo/di...t/Release.gpg:](http://medibuntu.sos-sts.com/repo/di...t/Release.gpg:) Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out
[http://medibuntu.sos-sts.com/repo/di...ion-en_GB.bz2:](http://medibuntu.sos-sts.com/repo/di...ion-en_GB.bz2:) Could not connect to medibuntu.sos-sts.com:80 (1.0.0.0), connection timed out

---

### Post by Rui Pais on 2007-02-22
hi,
today seems to be the 10.0.0.0' day... check it [here]("http://ubuntuforums.org/showthread.php?p=2193337").

(You got a D-Link route, it happens with this modem/routers...)

Check too [Opendns]("http://www.opendns.com/").

---

### Post by xyz on 2007-02-22
Hi and Welcome! As a beginner you might want to do this in a terminal:
```
wget http://easyubuntu.freecontrib.org/files/easyubuntu-3.023.tar.gz
tar -zxf easyubuntu-3.023.tar.gz
cd easyubuntu
cp packagelist-dapper.pot packagelist-edgy.pot
cp packagelist-dapper.xml packagelist-edgy.xml
sudo python easyubuntu.in
```
One line at a time!

Also go System > Administration > Synaptic Package Manager > Settings >Repositories > Add > Check "Multiverse" and "Universe"

---

### Post by Tomosaur on 2007-02-22
In general - a cable (ethernet) internet connection is virtually guaranteed to work. Linux has issues with wireless cards (nothing to do with Linux really - there are just few reliable drivers available). So yes, try plugging a cable in rather than relying on wireless.

---

### Post by ubunutgoz on 2007-02-22
Thanks for the 2 quick replies... but I am a cautious Ubuntu-er and have some questions...

to Riu Pais...

Am a little afraid of messing with DNS and router settings.  We have 7 Wi-Fi devices which all work fine, maybe a little slow at times!  So please give me a few more comments to increase my confidence...
1 - Apple Mac
2 - Windows PC x 3
3 - Ubuntu 6.10 (this one)
4 - Wi-Fi radio
5 - Wi-fi skype phone

to XYZ

1 - I already checked the boxes you mentioned in repositories.
2 - The thing you're saying to download, what exactly is that?

Thanks
Alan

---

### Post by xyz on 2007-02-22
Check here:
[EasyUbuntu!]("http://easyubuntu.freecontrib.org/")

or:
[Automatix]("http://www.getautomatix.com/")

or:
[Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats")
Basically these are various ways of making the things you want to work...work.
Check'them out; take your time and have fun learning one step at a time!
Good luck.

---

### Post by ubunutgoz on 2007-02-22
Tried the cable thing, no difference!  but thanks for the tip!

---

### Post by ubunutgoz on 2007-02-22
To XYZ

OK, I did the EasyUbuntu thing, and the app worked.  So I checked the boxes I wanted and get the original problem....

Downloading Package Information just stalls.  

See attached screenshot 

THE CONNECTION SEEMS TO BE WORKING OK, I'M USING IT RIGHT NOW AND XFRRING FILES

Maybe I'm being stupid??

Alan

---

### Post by Rui Pais on 2007-02-22
your problem as nothing to do with repos (why people are point you for that?...)

D-Link routers have a know problem with setting DNS automagically by simple add gateway IP address on network config.

You don't need to mess with router settings just edit /etc/resolv.conf and replace for:
> nameserver 208.67.222.222
nameserver 208.67.220.220

that should solve the issue (and even made your connection faster)

---

### Post by ubunutgoz on 2007-02-22
To Riu Pais..

Should I delete the line nameserver 192.169.1.1

Thanks
Alan

PS XYZ - any comments on this?

---

### Post by Rui Pais on 2007-02-22
> **ubunutgoz said:**
> To Riu Pais..

Should I delete the line nameserver 192.169.1.1


Yes, the ip of the router on the D-Link don't work.
If you don't want to use the opendns ones, you can open the router configure window and use the IPs that are listed under the DNS tab (the ones give by your internet provider)

If, for some reason, fails you can easily back to 192.168.1.1

---

### Post by ubunutgoz on 2007-03-04
Just to let you all know, the computer is working fine.  I think a combination of the following is important...

1 - disabling ipv6 at application level (firefox/thunderbird)
2 - using 'open' dns's
3 - being patient.

Thanks to all for your input and help.  I am really happy with my Ubuntu 6.10 machine.  All I need now is some RAM to make it go faster.

Alan

(PS, how do I mark a forum thread as 'closed'?)

---

### Post by sgstarling on 2007-03-04
You don't mark it closed. 

Some forums I visit encourage adding "[solved]" in the thread title, by the original poster when he/she feels the problem has been solved.  (so the thread title would now read: "[solved] Installing New Apps"

I haven't seen that used much at all here on Ubuntu forums.

I like the practice, but some people don't. 
(I don't do it here, cause it's not part of the 'culture').

---

