---
title: "I have a Router &amp; want to create a Web Server - do I need a Firewall?"
date: 2006-03-09
forum: Absolute Beginner Talk
---

### Post by dvarsam on 2006-03-09
Hello All!

I have a DSL Router right now in my computer.

So, it is a Router that ALSO provides Internet Access to my PC...

_Question 1_:
Do I currently need a Firewall?

From other Posts in this Forum I have found the following:

_Quote_:
"Firewalls are only needed to block access to ports you do NOT want certain people to be able to connect to.
By default Ubuntu does NOT have any open ports, so there is nothing to block.

A Router makes a nice Firewall. It will block incoming but NOT outgoing.
But you can watch the blinking lights & see what is happening.
You take action only if you suspect something funny is going on."

_Back to Question 1_:
Since I have a Router (& I guess plays the role of a Firewall), do I really need a Firewall?

_Question 2_:
According to the above "Quote", currently, my Router is my Firewall & I can watch the blinking lights & see what is happening...
I take action, only if I see something funny - e.g. lights blinking when I do nothing...
Is that possible?
Can somebody break-in my PC & bypass my Router's Firewall?
IF so, then my Router's Firewall is uselless...

_Question3_:
As I said (in the title), in the Future, I want to create a Web Server (using apache2).

a. Can that Web Page be behind the Router? 

E.g. that means that I will create a Web Page, open up some of my Router's Ports to give access to my Web Page on the outside world... 

b. In such a case, if some of my Router's Ports are open for people to visit & see my internet page...
IN THIS CASE, do I need a Firewall?
AND Do I also need an Antivirus? 

Thanks

---

### Post by thnogueira on 2006-03-09
Oh god, what a mess... (just a joke)

Well, first of all: A router do protect you and do act like a firewall. The fact is that the internet ip address is assigned  to the router and not to the machines in the intranet. Any atempt to access that ip, is an atempt to the router and not to your computer.

Second: the routers usualy have a configuable log tool and this is the place you can monitoring if it's everithing ok.

Third: Nothing is perfect, so there is the possibility some one break the security. The weak part I see today is the wireless one. If you have a wireless router, it's possible to get in your intranet by snnifing packages and breaking your key. Future 802.11 standards shall make it safer

Fourth: To act as a server, you need to open specifics ports of your router and it's not that problematic since you know what are you doing. The router will still blocking access to the other ports. If you install a soft firewall, You'll need to do the same. So, why do that?

Finally: Thanks god we don't need to intall antivirus in linux yet.

---

### Post by dvarsam on 2006-03-09
> 
Well, first of all: A router do protect you and do act like a firewall. The fact is that the internet ip address is assigned  to the router and not to the machines in the intranet. Any atempt to access that ip, is an atempt to the router and not to your computer.

So I guess I am TOTALLY safe in this case...?

> 
Second: the routers usualy have a configuable log tool and this is the place you can monitoring if it's everithing ok.

Where can I find that?
In which directory/path can I see that?

> 
Third: Nothing is perfect, so there is the possibility some one break the security. The weak part I see today is the wireless one. If you have a wireless router, it's possible to get in your intranet by snnifing packages and breaking your key. Future 802.11 standards shall make it safer.

I have a (US Robotics) WIRED only Router, so I guess I do NOT have to be scared...?

> 
Fourth: To act as a server, you need to open specifics ports of your router and it's not that problematic since you know what are you doing. The router will still blocking access to the other ports. If you install a soft firewall, You'll need to do the same. So, why do that?

Finally: Thanks god we don't need to intall antivirus in linux yet.

Honestly, since I am a Newbie, believe me, I will NOT know what I will be doing...

Ok, I understand that the other ports are going to be safe...

But what about the open ones? !!!
On the open ones, EVERYTHING is going to be wide open to the visitors?
And they can hack me because I (st*pidly) opened the ports?
(sounds like going to the movies & leaving all my house's doors & windows wide open?)

Do I need something to secure, in some way, those open ports?

OR I can feel safe, as long as the "chmod" command does NOT give to visitors "Write" rights (it gives only Read/Execute).

Thanks.

P.S.> Sorry, I am just TOO new at this...

---

### Post by thnogueira on 2006-03-10
```

So I guess I am TOTALLY safe in this case...?

```

As I told, nobody is totaly safe. But we can't be that paranoic. It seems that you're comming from windo* and I should tell you: relax, you are under linux now. And, most important: RELAX, you are behind a router.

```

Where can I find that?
In which directory/path can I see that?

```

I've never used this router model, but i beleive you can view the logs accessing the config page. Some routers have wind* program that allow you to download the logs to your computer. Maybe there is some linux version of this programs. The most important, again: RELAX, you are behind a router.

```

I have a (US Robotics) WIRED only Router, so I guess I do NOT have to be scared...?

```

Yes, don't be scared.

```

On the open ones, EVERYTHING is going to be wide open to the visitors?

```

When you open a port, it's used for specific services. Apache is a quite safe web server. 

Finaly, configure your webserver, put it working, go to the cinema, take your sit and RELAX. The people you see only the garden of your house (because you took a picture of that and published on your web page) and nothing else.

kind regards.

---

### Post by dermotti on 2006-03-10
There are some pretty easy firewalls with GUI's for Linux. Easy to install, easy to setup, so why not? The time it's taking you to get your answer, your firewall could have been setup :-)

---

### Post by dvarsam on 2006-03-10
Sorry guys, but the INSECURITY of the WINDOWS World, has turned me, into:

A paranoic freaq, psychologically unstable & emotionally downgraded...

... while caring ONLY for Antivirus, Antispyware,  Firewalls, Backup Procedures, Formatting Procedures & NO ACTUAL (REAL or TRUE) WORK !!!

I do NOT currently enjoy working in a PC...

I ONLY read/learn stuff about VIRUSES & security, while forgetting the true meaning/purpose of a PC, which is to actually USE all those OTHER programs.

Whenever I see a Computer Screen I get dissapointed, frustrated, etc...

Ubuntu might be a Safe System...

But it is going to take me a LOOONG time to get over this...

Honestly, I do NOT think I can EVER see a Computer, the same way I used to...


P.S.> Hopefully our kids will feel much better about it, because we have ALL 
         managed to become FREAKS - filled with inSecurity...

---

### Post by thnogueira on 2006-03-10
[QUOTE=dermotti]There are some pretty easy firewalls with GUI's for Linux. Easy to install, easy to setup, so why not? The time it's taking you to get your answer, your firewall could have been setup :-)[/QUOTE]

If dvarsam hadn't i router i'd advise him to put a firewall. Since he already has a very good one, i beleive it's waste of time setting up another one.

---

### Post by steve.horsley on 2006-03-10
OK, try this. Your router has a public IP address that anyone can see. But your PC is on an internal LAN and has an IP adddress that is not publicly visible. In order for anyone to be able to connect to your PC, you must configure your router to forward connections on to you. If you set up a web server, you have to get th erouter to forward port 80 to your PC. Then anyone can connect to your web server by connecting to port 80 of the router's address. They can't connect to any other port on your PC, so can't abuse any other services the PC is running. Even if the router passed every port through, Ububtu doesn't open any ports unless you explicitly enable a service - like a web server. Web servers are designed be safe for anyone to connect to. So what have we got:
* Ubuntu has no open ports unless you configure otherwise
* Router prevents connection to ports unless you configure otherwise
It's going to be hard for the baddies to get in. Since a firewall's whole purpose is to prevent baddies connecting to ports you don't want them to, it's not really needed.

This changes if you start running other services. Frinstance, I open an SSH server on port 22, but I don't want the whole world trying passwords on it - I only want to accept connections from where I work. It is possible to configure SSH to only accept calls from work, but I could alternatively configure a firewall to block connections from anywhere else. Other services may not even be configurable to only accept certain addresses only, in which case a firewall would be the oply option.

Another possible use for a firewall is to prevent communication when a compromised system tries calling home or opening a remote control port, but this is not really guaranteed as anything that compromises a PC will probably disable the firewall anyway.

---

### Post by dvarsam on 2006-03-10
Dear "Steve Horsley",

Thank you for your great explanation!
It really helped me a lot!
It has been the BEST one I have ever read.
It helped me understand how things really work...

However, I have some few questions:

Quote:
...But your PC is on an Internal LAN & has an IP address that is NOT publicly visible..."

_Question 1_:
If somebody actually knew my "Internal" LAN PC's IP address, could he attack me?
Example:
Whenever I have trouble, I post stuff (EVEN) in this Forum.
At the same time my Internal LAN IP is Static...
It might be the case, that I have already created a post giving my "Internal" LAN IP to this Forum...
For the sake of the example, lets say that somebody knows that my Internal IP is 192.168.0.102:3021.
So, not only they know the IP, but they also know the Port that sends info - which in this case is 3021.
Is this considered a security hole?
Am I in danger?

And, I know you said this:

Quote:
"...In order for anyone to be able to connect to your PC, you MUST configure your Router to forward connections on to you..."

I believe that my Router is NOT configured to forward connections to me (at least not configured by me)...
And honestly I do NOT know how can I check if it really does...

Let us _assume_ that my Router is NOT configured to forward connections to my Internal LAN PC...
So, EVEN if they know my Internal LAN IP address & open Port, I can still consider myself safe?

Quote:
"...Another possible use for a Firewall is to prevent communication when a compromised system tries calling home or opening a remote control Port..."

_Question 2_:
What do you mean by saying "...tries calling home or opening a remote control Port..."?

Sorry, I am too "dumbcake" to understand...
You mean that MY PC is going to connect to somebody else's PC?
... so that the other can hack-into my PC?...
Can you clarify this a bit...

And when you say "Opening a Remote Control Port", you mean like the "Remote Desktop" thing?
So, whenever I am online, somebody (having activated a Remote Desktop connection - without me knowing about it), is accessing my PC?


You explained those things so nicely...,
I would be very happy if you could answer those "threat" concerns of mine...

Thank you so much for your help...


P.S.> Also a BIG thank you to all those other people that helped me, too!

---

### Post by steve.horsley on 2006-03-13
Q1
There is no way people can connect to you LAN address of 192.168.... This address is not known to the internet, and in fact is guaranteed never to be known to the internet - it will never be assigned. Anyone sending packets the these addresses will never get an answer (except maybe Network Unreachable), and the packets will not be delivered anywhere. 

If your router is not configured to forward port 80 to your server's address then you will not be able to get a web server running. You had better start finding out how to configure your router.

Q2
Malware might do done of two things when ig takes control of your PC. 

First, it might start listening for commands on some port number. E.g. some windows worms install hidden remote-control services so that the hacker can connect to your PC and take control iof it. Yes, exactly like enabling remote desktop without you knowing. A firewall would not normally allow incoming connections to ports other than the services you have explicitly enabled, so a firewall in this case would prevent the hacker taking control. Provided the compromise didn't disable the firewall of course. So having a router that doesn't pass all ports through is a useful addition even if you do have a firewall running on the PC.

Second, the compromise probably involves "calling home" - making an outgoing call to somewhere to tell the new owner that another PC is available for whatever they want to use it for. A firewall could possibly try and block outgoing connections to unusual port numbers, but of course the malware could always try and connect to port 80 which would look like normal web traffic, or might disable the firewall before calling home.

---

### Post by dvarsam on 2006-03-13
Dear "Steve Horsley",

Thank you for your nice response!

You helped me understand a lot!!!

I owe you one... man!

Take care!

---

