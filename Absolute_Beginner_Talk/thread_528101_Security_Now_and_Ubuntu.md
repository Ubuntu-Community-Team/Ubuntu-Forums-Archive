---
title: "Security Now and Ubuntu"
date: 2007-08-17
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-08-17
Just got through listen to Leo Leporte and Steve Gibson most recent Podcast
of " Security Now ".  Is Linux / Ubuntu Secured against all these Malware and
Virus threats that they spoke of.  This show was based on Leaky firewalls
that wouldn't protect you from outbound threats.

I know that Linux is secure with iptables from inbound but what about
outbound.  I mean my Nat Router protects me from inbound.

I'm new to linux so I'm not sure how secure it is. I've heard it's
Fort Knox but would like to here what the community has to say.

Does FireStarter protect from outbound?

---

### Post by oilchangeguy on 2007-08-17
read this:
[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

and this:
given the low installed base of linux, verses windows. and the fact that each distro of linux is slightly different. someone would have to go thru alot of trouble to target one, or several distro's of linux. while there are different flavors of windows (xp) home, pro, media center. under the skin, it's still windows xp. and since 90+ percent of the worlds computers run a microsoft operating system. what's the biggest virus target? i'm not saying it can't happen. but chances are veeeeeeeeeeeeeerrrrrrrrrrrry low that it will.

---

### Post by euler_fan on 2007-08-17
> **Orbital75 said:**
> Just got through listen to Leo Leporte and Steve Gibson most recent Podcast
of " Security Now ".  Is Linux / Ubuntu Secured against all these Malware and
Virus threats that they spoke of.  This show was based on Leaky firewalls
that wouldn't protect you from outbound threats.

I know that Linux is secure with iptables from inbound but what about
outbound.  I mean my Nat Router protects me from inbound.

I'm new to linux so I'm not sure how secure it is. I've heard it's
Fort Knox but would like to here what the community has to say.

Does FireStarter protect from outbound?

I can't speak to the malware threats except to concur with the previous responder.

IPTables can do inbound and outbound filtering. You just have to set it up. You could, for instance, forbid all outbound traffic except for a couple little things which you really happen to want to run.

Linux security like all security is relative. A fully patched EnGuarde install or something like that with properly configured SELinux, IDS/IPS, firewalls, etc is going to be about as tough as they come insofar as those things go. On the desktop the consensus is that Ubuntu out of the box is more secure than most Windows OS configurations, but the out of the box security can either be enhanced or detracted from significantly. Another good security thread is this one [here]("http://ubuntuforums.org/showthread.php?t=510812"). It is a good compliment to the one already posted.

Firestarter is a front end to IPTables. If you set a restrictive outbound policy it will block anything you don't white list (explicitly allow).

If you mean something like ZoneAlarm where it will try to recognize if the app sending stuff out is good software or not, well, that's not something IPTables can really do. For that you would need to use TuxGuardian or something similar. I think it looks like an interesting project, but I'm not sure how much utility there is for it until we start to see a larger malware threat on Linux. Besides which, I suspect the general consensus is going to be to patch the hole the viruses use rather than try to block them from talking to the web.

---

### Post by Orbital75 on 2007-08-17
Yeah, I currectly run Zone Alarm Free on my Windows XP Pro machine
and as you can see from this test, it failed miserably. 

[IMG]http://img515.imageshack.us/img515/6149/01screenshotww8.jpg[/IMG]

[IMG]http://img250.imageshack.us/img250/9434/00screenshotyg6.jpg[/IMG]

---

### Post by az on 2007-08-17
The only reason you need an outgoing applications-based firewall on windoes is because it's a black-box, a computer running software that does not allow you to know what it is doing.

Ubuntu is FLOSS.  The applications are uploaded as source and compiled by the Ubuntu archive builders.  It would be very very unlikely that you install malware from the repositories.

---

### Post by Orbital75 on 2007-08-17
Oh, I totally trust the Ubuntu / Linux community. I'm just stating that visiting
a malformed Website which intentions of inserting code into Firefox or Explorer
Since I'm new to Linux, I don't know if this is possible with Ubuntu.
This is mostly the reason I would switch, just the assurance that nothing
bad is going to happen as long as I don't do anything stupid.  In a windows
world you can lock your system down pretty tight but as you said it's a Black
Box and you don't know whats happening in the background sometimes.

---

### Post by hyper_ch on 2007-08-17
By default Ubuntu is quite secure but it leaves it up to you whether you want to change that... by installing networing stuff / servers / daemons you make it more vunerable...

But then windows has a monolithic design and linux is modular. If on windows someone gets access, he normally has admin privileges and can wreck havoc... on linux he normally only has user rights and those are quite limited... so the machine itself cannot be harmed that easily on linux but user files could be deleted, altered....

And of course there is little protection agains unknown flaws... that counts for windows and linux... but on linux the response time to release a fix is way superior compared to windows... sometimes you have a fix within a couple of hours after a security issue was made public... there are still some windows security issues where M$ said it will never be fixed...

---

### Post by por100pre1 on 2007-08-17
Outbound protection is useful only if it's actually working. Once a powerful piece of malware is already running it can disable any firewall easily in Windows. Many Windows vulnerabilities have been exploited this way. Gibson says that is not likely to happen anymore but in the same show he mentions that Symantec products have a serious vulnerability. Now, the question is: **Do Windows or Norton vulnerabilities affect Ubuntu? You know the answer.** :)

---

### Post by perfecttao on 2007-10-12
If possible, I tend to steer clear of application style firewall solutions and try to handle all firewalling at gateway level.  An example of this is using an Open Source firewall like IPCop at my home network perimeter, and denying inbound/outbound traffic except on trusted ports (DNS/SMTP/PPTP/HTTP/HTTPS, etc). IPCop is easy to configure, and runs on any old hardware you happen to have kicking around......mines on an old PII 233mhz with 256Mb RAM and a 10Gb HDD.....

That way you can be pretty sure that even in the event of application level vulnerabilities, the security is handled at a different location....

---

### Post by Orbital75 on 2007-10-12
> **perfecttao said:**
> If possible, I tend to steer clear of application style firewall solutions and try to handle all firewalling at gateway level.

I actually do the same, I'm running a Standard SmoothWall 2.0 box.
Works great but since I'm not an iptables expert it only does default
inbound protection.

As far as I know, it won't warm me of something trying to go out.
I have to figure that out for myself and then manual add the rule to the table.

Correct me if I'm wrong, but I believe you can block bad stuff by the Port it wants to use.
I am assuming this would do the trick in SmoothWall.

```
# Block Bad Traffic from this specific PC on Port 1234
iptables -A FORWARD -p TCP -i $GREEN_DEV -s 192.168.1.1 --dport 1234 -j DROP
```

---

