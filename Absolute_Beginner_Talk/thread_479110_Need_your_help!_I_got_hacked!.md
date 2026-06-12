---
title: "Need your help! I got hacked!"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by naonao on 2007-06-20
[SIZE="2"]Hi all,

I am **very new** to Linux/ubuntu. I just started to use Ubuntu from the beginning of this month. 

I was long time windows user. But I made decision to be programmer or system developer in the near future  so that I was looking for the good linux system, and ended up Ubuntu, becuase it's **very user friendly**. I installed just a couple of extra soft from out of regular one, that's all. I didn't install many out of box. (But I understand that was my fault.) And one more fault was that I leave the PC turnning on one night.

Next morning(that was 18th), I felt strange feeling about PC, becuase my login icon was changed, and arrow by mouse moved strangely. So, immediately I changed my user name and password and looked up network setting etc. I discovered added network(**eth0:avahi**<--which is not mine, mine is eth0), then also discovered that it was accessed from** IP address 169.254.6.99**. Broadcast from **169.254.255.255.** Netmask/prefix was **255.255.0.0**. Mine is totally different. I went to whois then, it is belonged to IANA. I don't have good knowledge of the networking neither. I just start studying!!!

OrgName:    Internet Assigned Numbers Authority 
OrgID:      IANA
Address:    4676 Admiralty Way, Suite 330
City:       Marina del Rey
StateProv:  CA
PostalCode: 90292-6695
Country:    US

NetRange:   169.254.0.0 - 169.254.255.255 
CIDR:       169.254.0.0/16 
NetName:    LINKLOCAL
NetHandle:  NET-169-254-0-0-1
Parent:     NET-169-0-0-0-0
NetType:    IANA Special Use
NameServer: BLACKHOLE-1.IANA.ORG
NameServer: BLACKHOLE-2.IANA.ORG
Comment:    Please see RFC 3330 for additional information.
RegDate:    1998-01-27
Updated:    2002-10-14

OrgAbuseHandle: IANA-IP-ARIN
OrgAbuseName:   Internet Corporation for Assigned Names and Number 
OrgAbusePhone:  +1-310-301-5820
OrgAbuseEmail:  [email]abuse@iana.org[/email]

OrgTechHandle: IANA-IP-ARIN
OrgTechName:   Internet Corporation for Assigned Names and Number 
OrgTechPhone:  +1-310-301-5820
OrgTechEmail:  [email]abuse@iana.org[/email]

My ubuntu had firestarter and I noticed just before hacking that I got hit by this address a couple of times,  becuase the firestarter gave me the notice. But I didn't take it so seriously, because I never got hacked! 

Then, I logged out and logged in again, after that  I cannot get in admin area at all(I can log in normal area), including the terminal. Then I shut down, plugged out from network. even I don't turn it on. That was yesterday. Now, my desktop leave turning off. I used ubuntu 7.04. Now, I am studying how to prevent this happen again. **Please someone give me some advise to make my PC back safely**. I am planning to format harddisk using Gparted liveCD or UltimateCD. Then reinstall the system. But** if possible, is there anyway to get rid of this disgusting guy without format?** Because it took me to set it up long time, so I don't want to waiste time... I didn't back up it yet, what a stupid!!

Also, in order to contribute development team(in the future, I wish to join such great team), **what parts/folder of information that I should pick it up from ubuntu if able and send where? Also, should I contact police or where?** I never, ever got such experiences even if I leave my windows keep connected. I understand that was my fault...I don't blame ubuntu, I love this!!! Anyway so disgusting such hacker! And disgusting myself not able to handle such things!

Finally, **what is the best way to setting up firewall?** iptable and ipfilter? I should have implemented them more earlier! 

I am very strange guy, because I am a pilot now, but I want to be programmer or system developper in the near future and just started to study and planning to change career. I am absolutely not discouraged from this incident, rather I want to discover the best way and learn from it. And make ubuntu more stronger. Hunt him down! Please give me your hand! 

Now, I am connecting the internet from Windows XP/my laptop.(disconnect and made draft and connect again) But I try not connect network as much as possible until I get solution. I have a lot of questions, but I try it after I get your answer. 

God bless all,

Naonao[/SIZE]

---

### Post by thelemech on 2007-06-20
I am not an expert and am new to Ubuntu but I do have OVER extensive experience dealing with Security in other OS - sounds like script kiddies or a bored fellow geek looking for open portals - as you left it on all night - my inexperienced ubuntu advice would be to re-install. ;)

---

### Post by jrusso2 on 2007-06-20
I doubt you got hacked by that IP.  Numbers in that range are automatic IP addresses that are assigned when you have network problems.  Are you running DHCP?  It seems like it didn't get an IP address.

---

### Post by thelemech on 2007-06-20
My experience with automatic IP is that they are easily compromised and used  as a front for marketing robots.

---

### Post by EndPerform on 2007-06-20
Have a look here: [http://en.wikipedia.org/wiki/Private_network](http://en.wikipedia.org/wiki/Private_network) and here: [http://en.wikipedia.org/wiki/Zeroconf](http://en.wikipedia.org/wiki/Zeroconf)

That address falls under a 'Link-Local' range, which is local and used by Zeroconf, NOT by someone externally, so I doubt highly that the issues you are seeing are due to your machine being 'hacked'.

---

### Post by naonao on 2007-06-20
Sorry for any confusion if you got such impression.

I didn't tell IANA is master mind. I am not expert at all. I just wanted to give you many information related this incident. I JUST started to study.

But I am SURE something wrong, becuase I cannot login as sudo or root at all which is obviously not by me. Because I DO NOT know how to do that.

Whatever causes, please give me some advise. And one more, should I submit some log folder to development team? I wish I could, But that is TOO far away now.

naonao[-o<

---

### Post by atria on 2007-06-20
You certainly didn't get hacked by that ip since the ip range (169.254.0.0/16) is private and is automatically assigned by your own computer.

If you are really paranoid, you can log into your computer while your network is offline (take out the cable or something), backup your important documents and do a complete reformat.

Do remember to do a system update before doing anything else after the installation though.

---

### Post by EndPerform on 2007-06-20
> **naonao said:**
> Sorry for any confusion if you got such impression.

I didn't tell IANA is master mind. I am not expert at all. I just wanted to give you many information related this incident. I JUST started to study.

But I am SURE something wrong, becuase I cannot login as sudo or root at all which is obviously not by me. Because I DO NOT know how to do that.

Whatever causes, please give me some advise. And one more, should I submit some log folder to development team? I wish I could, But that is TOO far away now.

naonao[-o<

Something may be wrong, but I don'/t think it is at all caused by the address you're seeing.  What happens when you attempt a command with sudo?  What errors are you getting, if any?

---

### Post by jrusso2 on 2007-06-20
I really have insufficient information at this point but I doubt you were hacked.  Was the networking working before you shut it down?

Did you just install this?  Were you able to connect to the internet?  Did you download or install anything?

Did you configure firestarter?

---

### Post by thelemech on 2007-06-20
Maybe not hacked - but played with and the trail cloaked! Marketing firms could care less whether or not you use Wind. Mac. Linux Freebsd etc..... And all systems have vulnerabilities to a dedicated intruder with the right knowledge! 
Or maybe I do not know linux response to intrusion well enough - just throwing my two cents around;)

---

### Post by bodhi.zazen on 2007-06-20
sudo is not a user (unles you added a user by that name) and normally the root account is disabled. So, unless you enabled the root account and set a password, that is normal behavior.

---

### Post by naonao on 2007-06-20
EndPerform,

If not hacked, why such thing happen? And how to recover it? Any references?

I appreciate it if you give me some advise.

naonao

---

### Post by slimdog360 on 2007-06-20
If you are into security and the like you may want to check out a few of the links
[http://news.softpedia.com/news/Encrypted-Filesystem-in-5-Minutes-57104.shtml]("http://news.softpedia.com/news/Encrypted-Filesystem-in-5-Minutes-57104.shtml")
[http://www.nsa.gov/selinux/index.cfm]("http://www.nsa.gov/selinux/index.cfm")
fedora has selinux installed by default [http://fedoraproject.org/wiki/]("http://fedoraproject.org/wiki/")
a lot of reading but it has lots of info [http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables]("http://www.linuxhomenetworking.com/wiki/index.php/Quick_HOWTO_:_Ch14_:_Linux_Firewalls_Using_iptables")
if you have an old computer somewhere [http://www.howtoforge.com/perfect_linux_firewall_ipcop]("http://www.howtoforge.com/perfect_linux_firewall_ipcop")

If you're not a security nut though you would probably just want to invest some time in implementing common sense ideas. Not installing anything from untrusted sources (always try to use the repositories first) and have a good password on your computer.

---

### Post by information_entropy on 2007-06-20
When you start your computer it tries to obtain a network address from a dhcp server. 
If it cannot find one it uses a special one that is reserved for this situation. 
The RFC 3330 mentioned in the whois you posted is where this rule is defined.

From RFC 3330:

 169.254.0.0/16 - This is the "link local" block.  It is allocated for
   communication between hosts on a single link.  Hosts obtain these
   addresses by auto-configuration, such as when a DHCP server may not
   be found.

Avahi is a system which facilitates service discovery on a local network. This means that you can plug your laptop or computer into a network and instantly be able to view other people who you can chat with, find printers to print to or find files being shared.

You are probably not being attacked, what you are seeing is the result of starting your computer when is is not connected to a dchp server, it defaults to a local link address, and  avahi starts looking for network resources.

---

### Post by bodhi.zazen on 2007-06-20
I will be watching this thread. I am concerned that it is going nowhere fast.

naonao is inexperienced and may not know what is normal and what is not. naonao, it seems you installed software form outside of the Ubuntu repositories ? Well then, how do you know you  have been hacked?

My advice is you re-install Ubutnu, stay with the official repositories, and do a little research into how Linux/Ubuntu works, what is normal and what is not. Only install from trusted sources.

And please do not raise the general alarm "I got hacked" until you have a little confirmatory information.

There seems to be a fair amount of chatter from additional folks, that while well meaning, are not adding much to the discussion.

Please keep this thread on topic, If you do not know something of how linux security works, please cut the chatter.

---

### Post by dfreer on 2007-06-20
> **naonao said:**
> And one more fault was that I leave the PC turnning on one night.
Ubuntu ships with nothing listening to any port by default. Furthermore, you have firestarter enabled which further shores up your defense. There is absolutely nothing wrong then with leaving your PC running. EDIT: well, it does of course leave your system online. but I meant was although it shouldn't hurt to leave it on, it can't do anything bad if it is offline ;)
Servers have to be on 24/7, and they run on linux. Although there's always the possibility that you could be hacked, i doubt it. 

Have you enabled any services (SSH, FTP, SMB file sharing, etc)? if so, you can go into /var/log/ and check out the various log files to see what exactly went wrong, if anything. If nothing else, if your first username was the only user account on the system, you could go through ~/.bash_history and see if there were any commands that you are sure you didn't make during the time the system was "hacked".

> **naonao said:**
> So, immediately I changed my user name and password... Then, I logged out and logged in again, after that  I cannot get in admin area at all(I can log in normal area), including the terminal.

Did you remember to add your new username to the sudoer's list, or the admin group? this is most likely the reason why you cannot access admin areas, although if I was a hacker I'd do **one** of two things:
(1) I'd disable your access to the machine, especially the root account, so you wouldn't mess me up. then I would gather whatever I wanted from the system, then fsk up your machine for the heck of it.
(2) I'd make myself *invisible*, erasing log files and any indication I'd been on your system, so that I can use your machine without you knowing. 

Since you noticed (btw, the symptoms you described, icon changes and mouse behavior modified.. rings more like you messed with a program/settings somewhere, or possibly spyware than a hacker hacked your system). Why would a hacker simply change a few icons or make your mouse weird? Just trying to tone down your seeming paranoia, you *really* don't need to worry about getting hacked unless you are running risky software, playing around with the root account, or are running a server hooked up 24/7 that's subject to massive brute force script kiddies. don't worry and enjoy ubuntu :D


> **naonao said:**
> ....and looked up network setting etc. I discovered added network(**eth0:avahi**<--which is not mine, mine is eth0)

The new network manager applet (added in feisty 7.04 by default), uses that avahi thing, although for what purposes I do not quite understand. It seems it likes to create it's own virtual interfaces instead of using the default ones, really I don't know about this too much, but I'm pretty sure this is normal.

> **naonao said:**
> then also discovered that it was accessed from** IP address 169.254.6.99**. Broadcast from **169.254.255.255.** Netmask/prefix was **255.255.0.0**. Mine is totally different.

Private IP address, set when network manager doesn't receive an IP address from DHCP. Disgustingly like windows (what is the point of doing this? but i digress), but again this is normal. Try reconnecting to your network, and if nothing else, run:
```
sudo dhclient eth0
```


> **naonao said:**
> Finally, **what is the best way to setting up firewall?** iptable and ipfilter? I should have implemented them more earlier!
I personally use iptables, although the learning curve is quite steep for this. Firestarter should work just fine, you may want to make sure it starts at boot time (never figured out whether it did by default, or if you have to specify this).


> **naonao said:**
> I am very strange guy, because I am a pilot now, but I want to be programmer or system developper in the near future and just started to study and planning to change career. I am absolutely not discouraged from this incident, rather I want to discover the best way and learn from it. And make ubuntu more stronger.

You, sir, have one of the best attitudes concerning linux/ubuntu I've seen around here. Glad to have you as part of the community! Hopefully I helped you understand a bit of what's going on, let us know if you can't get your new username/password working with sudo!

---

### Post by thelemech on 2007-06-20
Sorry!!!!!!!!!!!!!!!! like I said just throwing my two cents around(if comment was directed my way:p) 
re- isntall and a start over is your best bet anyway- should not take to long - think of the reward :D
QUOTE=bodhi.zazen;2878600]I will be watching this thread. I am concerned that it is going nowhere fast.

naonao is inexperienced and may not know what is normal and what is not. naonao, it seems you installed software form outside of the Ubuntu repositories ? Well then, how do you know you  have been hacked?

My advice is you re-install Ubutnu, stay with the official repositories, and do a little research into how Linux/Ubuntu works, what is normal and what is not. Only install from trusted sources.

And please do not raise the general alarm "I got hacked" until you have a little confirmatory information.

There seems to be a fair amount of chatter from additional folks, that while well meaning, are not adding much to the discussion.

Please keep this thread on topic, If you do not know something of how linux security works, please cut the chatter.[/QUOTE]

---

### Post by dfreer on 2007-06-20
> **thelemech said:**
> Sorry!!!!!!!!!!!!!!!! like I said just throwing my two cents around(if comment was directed my way:p) 
re- isntall and a start over is your best bet anyway- should not take to long - think of the reward :D


True, once you are truly hacked, the only real way to trust your system again is with a full reinstall. However, like several people have already stated it is very unlikely that you actually got hacked. and if you did get hacked, it's also good advice to do what you did. keep the system alive, off the network though, and forensically examine your system for indications of what the hacker did and who the hacker is, and most importantly how they got in your system and how you can prevent them from doing it again. If you just wipe your machine blindly, you're not learning anything, and you are subject to getting hacked the exact same way again.

Sorry bodhi.zazen if this is considered off topic :p I'll refrain from now on.

---

### Post by bodhi.zazen on 2007-06-20
> **dfreer said:**
> Sorry bodhi.zazen if this is considered off topic :p I'll refrain from now on.

LOL

The only choices are Forensics or re-install.

If you want forensics you may consider professional help.

These two links will get you started :

[http://www.securityfocus.com/infocus/1769](http://www.securityfocus.com/infocus/1769)

[http://www.securityfocus.com/infocus/1773](http://www.securityfocus.com/infocus/1773)

Otherwise, read a little about linux security, re-install and look at hardening linux.

[http://www.ibm.com/developerworks/linux/library/l-seclnx3/](http://www.ibm.com/developerworks/linux/library/l-seclnx3/)

---

### Post by sad_iq on 2007-06-20
That's funny...of all the people out there no one suggested the use of a rootkit scanner or such...so here goes(type in terminal):
 ```
sudo apt-get install rkhunter
sudo rkhunter --update && sudo rkhunter -c
```
 That should check your system for possible breakins and calm you a little!!!

---

### Post by thelemech on 2007-06-20
> **dfreer said:**
> True, once you are truly hacked, the only real way to trust your system again is with a full reinstall. However, like several people have already stated it is very unlikely that you actually got hacked. and if you did get hacked, it's also good advice to do what you did. keep the system alive, off the network though, and forensically examine your system for indications of what the hacker did and who the hacker is, and most importantly how they got in your system and how you can prevent them from doing it again. If you just wipe your machine blindly, you're not learning anything, and you are subject to getting hacked the exact same way again.

Sorry bodhi.zazen if this is considered off topic :p I'll refrain from now on.


;)MMMM a different world in Linux

Yet the same!

All I was trying to point out is that if you are a bored geek/nerd/loner/hobbyist/cracker/hacker then no systems gaping security beacons are off limits to second hand fun!

Anyway - most of the other posters know linux better than me - just trying to be useful:D

---

