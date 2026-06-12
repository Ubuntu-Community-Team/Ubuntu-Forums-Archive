---
title: "Security software on ubuntu"
date: 2007-02-15
forum: Absolute Beginner Talk
---

### Post by bluechestdude on 2007-02-15
okay i was thinking of moving to ubuntu and reading through a link you said that ubuntu doesnt need security software why? Im new so i didnt really get many of that server things that was talked about, I just wanted to use ubuntu as a home os. IF i were to install security software any recommended ones that work for linux? (like im sure norton antivirus wouldnt be happy with it)

---

### Post by cet' on 2007-02-15
because Ubuntu us locked down allready, not to many people make viruses or other unwanted software targeted at it, none of the windows security programs will run under Ubuntu and also none of the millions of viruses targted at windows systems will run under Ubuntu, there isnt enough bad stuff out there to go out of your way installing av software in ubuntu

---

### Post by IronMac on 2007-02-15
You should set up Firestarter, which is a software firewall, on your system.

There are a lot of AV programs available for Linux but they are mainly aimed at the server market. Firestarter should be sufficient for you.

---

### Post by tribaal on 2007-02-15
Yeah, firestarter gives you a nice feeling of being in control of your firewall rules.

Antivirus software in Linux are only useful to avoid *spreading* virus to other systems (windows systems), by scanning emails for a mailserver for example.

- trib'

---

### Post by HereInOz on 2007-02-15
Firstly, Linux is a much smaller target than Windows, so if someone wants to write an exploit, a virus or trojan or spyware or something like that, they will write it for Windows, knowing that they are going to hit the vast majority of computers, and certainly the less aware users.

Secondly, when you are using Ubuntu, you are not working with Administrator (Root) priviledges, therefore, any malicious software that wants to install itself will probably (note the use of the word "probably" - there are no guarantees here) have to ask for a password in order for you to temporarily elevate yourself to Administrator status and run the install.  Hopefully this would alert you that something is going on.

Thirdly, it is believed that Linux distributions generally have a greater level of intrinsic security than Windows systems.  There will be those who will argue until the end of time about this one, but we all hope it is true.

However, it is possible for you to download a file to a Linux server, where that file contains a Windows virus, and then you happily infect your Windows computer across the network.  For this reason, if for no other, it is a good idea to run virus checking software on a Linux machine.  Clamav is a good one, and is available through the repositories using Synaptic.  Grisoft (AVG) also produces a virus solution for Linux.

There are probably many other reasons why you are intrinsically more secure using Linux than Windows - these are just a few of my thoughts.

---

### Post by Obor on 2007-02-15
Aysiu explained things nicely [here.]("http://www.psychocats.net/ubuntu/security")

---

### Post by bluechestdude on 2007-02-16
okay thx very much for ur feedback thats pretty much set me for ubuntu. NOw when i get the time...NO MORE WINDOW HAXS!

---

### Post by Aazn on 2007-02-16
Well considering that (as far as I know) sudo and su have no holes, so there is almost no point at all in installing any type of security on a Ubuntu install.

Besides, even if it was wide open, the worst they could do if you were hosting a web server is what? Harm your /var/www directory? Assuming you aren't, they couldn't damage your operating system, only your files in /home.

---

### Post by bodhi.zazen on 2007-02-16
> **HereInOz said:**
> Firstly, Linux is a much smaller target than Windows, so if someone wants to write an exploit, a virus or trojan or spyware or something like that, they will write it for Windows, knowing that they are going to hit the vast majority of computers, and certainly the less aware users.

I think that is false. although M$ may have a large number of home systems, much of the internet is run on *nix and those servers are a valuable target ...

Also you forget that each virus/malware targest a specific vulnerability of the OS. Thus each variant of a virus/malware represents one security flaw/hole.

Thus, IMO, the reason most viruses are written for M$ is a direct reflection of the number of security flaws/holes NOT the number of computers running M$.

> However, it is possible for you to download a file to a Linux server, where that file contains a Windows virus, and then you happily infect your Windows computer across the network.  For this reason, if for no other, it is a good idea to run virus checking software on a Linux machine.  Clamav is a good one, and is available through the repositories using Synaptic.  Grisoft (AVG) also produces a virus solution for Linux.

I disagree. I feel no obligation to "protect" M$. IMO it is the obligation of M$ to protect their users, and since they do not the responsibly then falls to M$ users.

---

### Post by bluechestdude on 2007-02-17
i htink that was why they suggested the firewall. But yes i believe ur right, why else does windows suck so much?

---

