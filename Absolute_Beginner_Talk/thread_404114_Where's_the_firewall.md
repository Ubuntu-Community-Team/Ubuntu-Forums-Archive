---
title: "Where's the firewall?"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by CSMatt on 2007-04-08
Something I've found extremely alarming is that my Ubuntu installation is broadcasting its ports to any computer that queries it (as found out with a ShieldsUP! test).  The ports are closed, but they should ideally be Stealth (ie. undetectable when probed).  The Windows and Mac OS X firewalls all "stealthify" their ports, as do many proprietary firewalls today.  Why has Ubuntu not been installed with an incoming firewall that at the very least "stealths" all ports from intruders?  While it may take an intruder more time to open a closed port on a GNU/Linux-based system than on a Windows one, the fact that I exist to the intruder is still incentive enough for him or her to at least try.  Why is there not a firewall that protects against this?  I'm not talking about iptables here, I'm talking about an all-in-one FOSS firewall that is at least the equivalent of the Windows and Mac OS X built-in firewalls, if not a free ZoneAlarm-type product?  If there is, why is it not thrown in?

---

### Post by ComplexNumber on 2007-04-08
i thought that it was the router that is responsible for having the ports closed/open, or stealthed....ideally. most people seem to have a router these days. iptables is actually a very good firewall, but its only a backend. use firestarter or guarddog if you want to use a frontend GUI applications.

btw the windows firewall doesn't stealth. in fact, the windows firewall is hopeless beyond belief. it doesn't even protect against traffic going out.

btw2 what makes you think that ubuntu is giving out the ports to any entity that asks based on your observation of gibson research(ier sheids up)?

you may want to have a read of [this]("http://ubuntuforums.org/showthread.php?t=159661").

---

### Post by CSMatt on 2007-04-10
So then why isn't this kind of thing already set up then as part of Ubuntu's default install?  Having iptables disabled by default seem like a Windows-y stupidity move.

While I'd normally use my router that has a hardware firewall, I'm connected directly into my college network and there is no campus-wide hardware firewall, which is why I need a software firewall.  The security software the campus provides for as far as firewalls are concerned only covers Windows and Mac OS X.

---

### Post by ubunter1 on 2007-04-10
i switched to ubuntu about a year ago and have never had any kind of firewall,and have never had a problem of any kind,with windows with all the firewalls antivirus progs and the like there was always something going wrong with it,the computer was slow as well because of all the progs.one of the reasons i love ubuntu virtually no virus etc problems.:)

---

### Post by Swab on 2007-04-10
> **ComplexNumber said:**
> 
btw2 what makes you think that ubuntu is giving out the ports to any entity that asks based on your observation of gibson research(ier sheids up)?


Is there some reason to not believe Shields Up?

---

### Post by CSMatt on 2007-05-20
Okay, So I installed Firestarter and am pretty comfortable with it and its protection, even if it only offers white listing of port and IP ranges and not programs with its outbound protection.  However it never starts when the computer does, which is problematic because I connect with either an Ethernet or a wireless connection.  Firestarter offers the option of automatically activating upon a connection being established with a modem, but not with an Ethernet or wireless card.  I can't add it to the startup sessions without adding "gksu" to the command, which makes me have to enter my password twice now upon login (once for login, once for Firestarter).  Is there a way for Firestarter to operate under its own user name in a unique group, similar to how ClamAV operates?

I apologize in advance for bumping an old thread.

---

### Post by ramjet_1953 on 2007-05-20
You will probably find that your ISP is the culprit here, not your Linux installation. By default, all ports are closed and iptables keeps a pretty good hold on them.

If you read the documentation on the ShiledsUp page, it talks about ISP's giving incorrect readings, when using this software.

Regards,
Roger 

ps Unless you have a specific need to open up ports for software like aMSN, it is best not to use Firestarter to alter the standard settings of iptables, unless you really know what you are doing. Linux, by default is very secure.

---

### Post by CSMatt on 2007-05-21
It's better to be undetectable than to be detected and impervious.  Your strategy is similar to walking around in a high-crime area in plain sight with a bullet-proof vest on underneath your shirt.  The chances of being hurt are slim, but you still run the risk of attack.  Having stealthed ports in addition to a secure system is like avoiding the area entirely or walking around in less noticeable areas while still wearing the vest for good measure.  This prevents both attacks and intrusion.

I don't rely purely on the firewall for protection, if that's what you are alluding to.  I always install updates when notified and try to practice safe procedures so as to avoid a nasty situation.  However the belief that you can let your guard down because "Linux is more secure" is a bad judgment, even if the statement is true.  There is not and never will be a silver bullet for security.

That's the way I see it anyway.  You are free to implement you own policies as you wish, however I wish to not be broadcasting myself just in case a black hat discovers a backdoor before everybody else does.  I realize that this is far more unlikely in free software than proprietary software, but I'd rather not risk it regardless.

PS: the only thing I find regarding false testing results and ISPs in the ShieldsUP! documentation is the statement that ports may appear to be stealth regardless of the presence of a firewall due to their blocking by the ISP.  If you can provide a link to the specific section in question, that would be appreciated.

---

### Post by Nekiruhs on 2007-05-21
Hmm. i just got scanned, and it coulden't sniff a single port. Even on the first 1056 ports not one showed up. Im not even running any firewall (except iptables which is built into the kernal)

---

### Post by Moop on 2007-05-21
I've never changed any firewall settings on my recent Feisty install and every port scans stealth at shields up for me. I am using a dd-wrt router too.

---

### Post by CSMatt on 2007-05-21
You're probably under an NAT router in that case.  Most routers include an NAT hardware firewall that stealths ports, but they only block unwanted incoming connections due to the inability of hardware to detect what outbound connections are wanted and what are not wanted (such as those made by tojans or keyloggers).

Try plugging in your computer directly to the modem and run the test again after you connect.  Iptables alone and unconfigured did not stealth the unused ports for me when I was connected to my unfirewalled campus Ethernet.

---

### Post by Moop on 2007-05-22
> **CSMatt said:**
> You're probably under an NAT router in that case.  Most routers include an NAT hardware firewall that stealths ports, but they only block unwanted incoming connections due to the inability of hardware to detect what outbound connections are wanted and what are not wanted (such as those made by tojans or keyloggers).

Try plugging in your computer directly to the modem and run the test again after you connect.  Iptables alone and unconfigured did not stealth the unused ports for me when I was connected to my unfirewalled campus Ethernet.

I'll take your word for it. My router does make a good firewall. I just don't think that trojans, spyware, etc is that big a deal with linux. But I'm sure you can configure your security anyway you would like with Ubuntu. :) I think that out of the box security is acceptable for most users and easy to configure once you get the hang of things.

---

### Post by CSMatt on 2007-05-22
Just in case iptables had indeed been improved in Feisty, I booted an Xubuntu 7.04 LiveCD, remotely turned off NAT, and did a ShieldsUP! test.  With the exception of ports 80 and 135, the results were once again "closed" and not "stealth."  So yes, you guys are under NAT.

---

### Post by rootkowski on 2007-05-22
[http://www.builderau.com.au/program/linux/soa/10-things-you-should-do-to-a-new-Linux-PC-before-exposing-it-to-the-Internet/0,339028299,339274586,00.htm]("http://www.builderau.com.au/program/linux/soa/10-things-you-should-do-to-a-new-Linux-PC-before-exposing-it-to-the-Internet/0,339028299,339274586,00.htm")

This might be interesting for you. An article about Linux security.

---

### Post by CSMatt on 2007-05-22
Good article, albeit a bit complicated.

---

### Post by RedSquirrel on 2007-05-22
CSMatt:

The part of Firestarter that configures iptables should be started automatically when you start your computer. You shouldn't have to start anything manually, especially not the GUI. If iptables is not being properly configured by Firestarter, then it may be a bug. There was a thread a little while ago discussing this, but I didn't follow it too closely because I have been using the method that ComplexNumber suggested. Have you tried that? It's this one:

[ HOWTO: Set a custom firewall (iptables) and Tips]("http://ubuntuforums.org/showthread.php?t=159661")

It works like a charm.

---

### Post by CSMatt on 2007-05-23
I do recall something in the boot process (I turned "quiet" off in GRUB explicitly to see what happened if the process lags or fails) stating that it starts Firestarter, but that always fails.  That prompt appears after GDM starts, so it can only be seen if X is restarted.

---

### Post by Cloudedbrains on 2007-05-23
I used Wubi to install Ubuntu 7.04 and not set up any firewall and ALL my ports are stealthed :D

---

