---
title: "Is spyware a problem on linux?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by pilot550 on 2007-04-08
I am really enjoying Linux but I have a question about security. I am connected to the internet through a router but I have no software firewall installed. From what I've read  it seems like a software firewall is unnecessary. I don't have Clam or any other anti-virus installed either. What about spyware? Is there an anti-spyware program for Linux?

I have been thinking that viruses are built to run on Windows and Mac's, and a virus just won't run on Linux. It would be like trying to run an X-box game on a computer. Just not compatible. But Java is compatible across all platforms. Is it possible for a web site to install a key logger or some other type of program to get my online banking information? If so, what steps should I take to keep myself safe?

---

### Post by Swab on 2007-04-08
It may indeed be possible for malicious code to be run on your Linux install.  But as you stated, viruses and other nasty code written for Windows will not affect your Linux box. 

So basically it is extremely unlikely that you will encounter a problem as the people interested in stealing bank details will be targeting the OS with the largest market share (Windows).

Also, exploits found in Firefox seem to be patched much quicker than those in Windows/IE.  So be sure to keep your system up to date and you should be fine.

---

### Post by Jussi01 on 2007-04-08
Also if you are running ubuntu then you actually do have a firewall installed. it is part of the ubuntu kernel an is called iptables. it can be manipulated through the command line  or you can install a gui for it called firestarter. you can install the gui through:
```

sudo apt-get install firestarter
```

---

### Post by aysiu on 2007-04-08
Read this:
[http://psychocats.net/ubuntu/security#firewallantivirus](http://psychocats.net/ubuntu/security#firewallantivirus)

---

### Post by pilot550 on 2007-04-08
Thanks for the quick reply. One great thing about Linux is that it is so easy to keep up to date.

---

### Post by Patrick K on 2007-04-08
You can install Firestarter. It is a frontend for iptables, the firewall already installed on your system. You can set permissions for both incoming and outgoing connections. I haven't set any myself so cannot provide any guidance. When I looked at the permission settings in Firestarter, I found them somewhat confusing. I suspect there is pretty good documentation available on the web but I haven't sought it out, yet.

---

### Post by laidback on 2007-04-08
"One great thing about Linux is that it is so easy to keep up to date."

Oh how right you are. It's quite fantastic. I moved over a few months ago and have been thrilled with Linux and Ubuntu in particular. Not only is it easy to keep up to date but you also have a wealth of software on tap, just run synaptic. Plus the forums, what more does a user need.

Welcome to the fold.

---

### Post by hrsetrdr on 2007-04-08
Not being logged in as Root enhances your invulnerability to the nasties also.  ;)

---

### Post by dwblas on 2007-04-08
I haven't had any problem with Linux as long as I have been using it - since 1995.  Crackers don't want to waste their time on LInux because problems are fixed quickly.  They may spend months finding and programming an exploit, only to have it closed before they get much use out of it, so they zero in on other, easier targets.

---

### Post by hyper_ch on 2007-04-08
and another aspect is there are many linux distros on many platforms (alpha/sparc/sun/....)

---

### Post by infoseeker on 2007-04-08
Regarding Firestarter, it seems to alter the state of the firewall on my PC.  Without Firestarter (ie. before I installed it), apache, vsftp, samba, etc all worked fine, but as soon as I installed Firestarter, I had to open the necessary ports (http, ftp, etc.) for the software to operate normally.

So what exactly does Firestarter do to my firewall to require these ports to be opened? Its almost as if there was no firewall there to start with!

And if I 'STOP FIREWALL' under the Firestarter GUI, does it kill the firewall completely, or does it simply restore the PC to the state before the installation of Firestarter.

Thanks

---

