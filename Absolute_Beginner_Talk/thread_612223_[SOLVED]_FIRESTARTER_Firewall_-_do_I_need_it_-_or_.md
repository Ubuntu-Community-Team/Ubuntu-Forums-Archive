---
title: "[SOLVED] FIRESTARTER Firewall - do I need it - or is Gutsy secure without it?"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by MozartlovesUbun2 on 2007-11-13
also as I understand the antivirus is for checking windows mail, so I guess I dont really need that do I?

---

### Post by p_quarles on 2007-11-13
Don't type that command. See my sig.

---

### Post by ByteJuggler on 2007-11-13
Technically, Linux always has a firewall, "Firestarter" is simply a GUI/simplified interface to the kernel "iptables" which implement the firewalling.  You don't particularly need it but it doesn't hurt to install it. Linux is pretty secure by default with default settings.

---

### Post by shad0w_walker on 2007-11-13
Ubuntu is decently secure by default. I will not say it is bullet proof because nothing is perfect but its good enough for normal use.

You only really need a firewall config program if you want to manually tweak. The default install has iptables which is secure as any firewall and should do the average user fine.

---

### Post by mcduck on 2007-11-13
As long as you don't install any server software you are quite safe even without any firewall. Even more so if you are behind any router.

And yes, you don't need any antivirus software with Ubuntu. There really isn't any viruses or spyware for Linux.

Some people prefer to scan for Windows viruses so they don't accidentally forward files or email containing a virus to Windows users, but in my opinion if the Windows user doesn't have a proper antivirus software he/she is pretty much screwed anyway so it doesn't really make any difference..

---

### Post by silent1643 on 2007-11-13
no, general users really dont need firewalls..

if you doing things on the internet that might make you more prone to attacks then sure why not..

also applies to antivirus software

old [article ]("http://www.littleubuntu.com/blog/?p=12")i did

---

### Post by adi82 on 2007-11-13
i read somewhere that if you are connected directly to internet as cabel modem you have to use a firewall.i am using "lokkit" ,a very easy one.

---

### Post by jordank on 2007-11-13
what would be the command to download firestarter?

---

### Post by adi82 on 2007-11-13
> **jordank said:**
> what would be the command to download firestarter?

go to applications >>> add remove applications >> internet >> firestarter

---

### Post by mcduck on 2007-11-13
> **adi82 said:**
> i read somewhere that if you are connected directly to internet as cabel modem you have to use a firewall.i am using "lokkit" ,a very easy one.

Not really, as in the default setup there are no services running that would respond to incoming connections.

---

### Post by adi82 on 2007-11-13
> **mcduck said:**
> Not really, as in the default setup there are no services running that would respond to incoming connections.

what does you mean for default setup ?
should i remove lokkit

---

### Post by Daveski on 2007-11-13
This is a common question for new Linux users (especially those with some knowledge of Windows). I think there are many threads discussing people's opinions on this subject, but I think we should have a particular link explaining security software for Linux and the pros and cons that is usually used. Perhaps one of the decent threads could be made sticky?

---

### Post by p_quarles on 2007-11-13
> **Daveski said:**
> This is a common question for new Linux users (especially those with some knowledge of Windows). I think there are many threads discussing people's opinions on this subject, but I think we should have a particular link explaining security software for Linux and the pros and cons that is usually used. Perhaps one of the decent threads could be made sticky?
Already is:
_[http://ubuntuforums.org/showthread.php?p=3088372](http://ubuntuforums.org/showthread.php?p=3088372)_

---

### Post by adi82 on 2007-11-13
> **Daveski said:**
> This is a common question for new Linux users (especially those with some knowledge of Windows). I think there are many threads discussing people's opinions on this subject, but I think we should have a particular link explaining security software for Linux and the pros and cons that is usually used. Perhaps one of the decent threads could be made sticky?

:lolflag: 
i used windows since "windows 3.0" and is hard for me to believe that we can have a system without viruses,malwares and rootkit. :lolflag:

---

### Post by mcduck on 2007-11-13
> **adi82 said:**
> what does you mean for default setup ?
should i remove lokkit
I mean that out-of-the-box Ubuntu doesn't need any firewall. You only need to run a firewall if you install some program that listens for incoming network connections, such as some kind of web server etc.

If you have a firewall installed, there's no reason why you couldn't keep it. Many users run one, if for no other reason then just because after many years with Windows they don't feel safe without a firewall..

---

### Post by mcduck on 2007-11-13
> **adi82 said:**
> :lolflag: 
i used windows since "windows 3.0" and is hard for me to believe that we can have a system without viruses,malwares and rootkit. :lolflag:

Sadly, there are rootkits for Linux. But hackers still need some way to access your machine before they can actually install one, so as long as you don't have any services running open to network you are quite safe from that kind of threats as well.

---

### Post by Chayak on 2007-11-13
Well working in the security field and asking if ubuntu needs a firewall the instant answer is YES.  It's fairly secure by default but you never know when someone will discover some security hole and exploit it.  Even firewalls are no guarentee but turning on an extra layer of saftey that's already there will never hurt.

---

### Post by bgast1 on 2007-11-13
i don't really know if this fits here, but what if you are downloading, can you pick up virus that way, or do they only work on windows files?

---

### Post by nikolas68 on 2007-11-13
Well....i'm new with Ubuntu....not so experienced yet....but i'm using firestarter and it seems to do its job!

[ [IMG]http://www.imagehosting.com/out.php/t1367486_ScreenshotFirestarterubuntu.png[/IMG]](http://www.imagehosting.com/out.php/i1367486_ScreenshotFirestarterubuntu.png)

---

### Post by crjackson on 2007-11-13
I'm no exprt either, but it seems there is a misunderstanding in this thread.  Ubuntu already has a firewall built in so to speak.  It's called iptables and as soon as you install your OS it's active.  Firestarter and other "so called" firewall programs mentioned here, are nothing more than a GUI so that you can access your already active firewall and tweak it to your needs.

I too use Firestarter, but it's used to OPEN up the firewall on port 21 for my ftp server.

That's my understanding anyway...

---

### Post by bankrupt on 2007-11-13
On my Windows boot I use ZoneAlarm.  One thing I like about that program is that it pops up an alert when programs try to make a connection out from your computer.  Since it seems every fricking program for Windows these days tries to call home, it's nice to see this and block it if I choose.  Is there a similar program available that could be used with Ubuntu so I can see any programs trying to call home?  Will firestarter do this or can it be set up to do this?

---

### Post by p_quarles on 2007-11-13
> **crjackson said:**
> I'm no exprt either, but it seems there is a misunderstanding in this thread.  Ubuntu already has a firewall built in so to speak.  It's called iptables and as soon as you install your OS it's active.  Firestarter and other "so called" firewall programs mentioned here, are nothing more than a GUI so that you can access your already active firewall and tweak it to your needs.

I too use Firestarter, but it's used to OPEN up the firewall on port 21 for my ftp server.

That's my understanding anyway...
Kinda. Here's a short explanation (but the link in my last post in this thread is a more detailed discussion):

Yes, iptables is installed by default in any Linux system. By default, though, it has no rules set, so isn't actually *acting *as a firewall. The default setting is to accept all connections. 

The reason that people say Ubuntu is secure out of the box, though, is because it includes no programs that will accept unsolicited incoming connections. In other words, the connections aren't blocked, but there's absolutely nothing that any remote attacker can tell your system to do. They can send you all kinds of dangerous packets, but there's no program available to run them. For this reason, having iptables rules on a default setup of Ubuntu would be redundant.

When you add server software (such as ftpd) though, then you *are* running software which is capable of responding to some remote commands, and that's when it makes sense to setup rules for iptables, either directly or using a GUI interface like Firestarter.

---

### Post by crjackson on 2007-11-13
> **p_quarles said:**
> Kinda. Here's a short explanation (but the link in my last post in this thread is a more detailed discussion):

Yes, iptables is installed by default in any Linux system. By default, though, it has no rules set, so isn't actually *acting *as a firewall. The default setting is to accept all connections. 

The reason that people say Ubuntu is secure out of the box, though, is because it includes no programs that will accept unsolicited incoming connections. In other words, the connections aren't blocked, but there's absolutely nothing that any remote attacker can tell your system to do. They can send you all kinds of dangerous packets, but there's no program available to run them. For this reason, having iptables rules on a default setup of Ubuntu would be redundant.

When you add server software (such as ftpd) though, then you *are* running software which is capable of responding to some remote commands, and that's when it makes sense to setup rules for iptables, either directly or using a GUI interface like Firestarter.

So then, does the act of installing firestarter activate iptables?  I couldn't even get my ftp server to work until I installed it so that port 21 could be opened when needed.

---

### Post by p_quarles on 2007-11-13
> **crjackson said:**
> So then, does the act of installing firestarter activate iptables?  I couldn't even get my ftp server to work until I installed it so that port 21 could be opened when needed.
No. iptables is always on. I'm not sure why the ftp server wasn't working before you installed Firestarter, but I suspect the two are unrelated.

---

### Post by crjackson on 2007-11-13
> **p_quarles said:**
> No. iptables is always on. I'm not sure why the ftp server wasn't working before you installed Firestarter, but I suspect the two are unrelated.

I'm sure it's related.  I've done many installs on this machine and it's been the case each time.  I would be shocked to find it related to anything else on a fresh install, and repated so many times.  Anythings possible I guess.

One of the other old times told me port 21 was closed. So I installed firestarted and used it to open the port.  It's worked every time.

---

### Post by p_quarles on 2007-11-13
Well, if something's blocking port 21, it's not iptables. The default iptables settings in Ubuntu are like so:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
Meaning, the policy is ACCEPT, and there are no rules set. 

Port 21 *is* inaccessible by default, but AFAIK that's because there's no ftp server installed by default, which in turn means that there's nothing listening for connections on that port. It's possible that there's some other feature that specifically blocks 21, but I don't use FTP, and have never heard of such a thing.

(off-topic: I highly recommend replacing FTP with SFTP, which is part of the openssh-server package; it works with many, but not all, FTP clients, and it's fully encrypted --> more secure)

---

### Post by crjackson on 2007-11-13
> **p_quarles said:**
> Well, if something's blocking port 21, it's not iptables. The default iptables settings in Ubuntu are like so:
```
Chain INPUT (policy ACCEPT)
target     prot opt source               destination

Chain FORWARD (policy ACCEPT)
target     prot opt source               destination

Chain OUTPUT (policy ACCEPT)
target     prot opt source               destination
```
Meaning, the policy is ACCEPT, and there are no rules set. 

Port 21 *is* inaccessible by default, but AFAIK that's because there's no ftp server installed by default, which in turn means that there's nothing listening for connections on that port. It's possible that there's some other feature that specifically blocks 21, but I don't use FTP, and have never heard of such a thing.

(off-topic: I highly recommend replacing FTP with SFTP, which is part of the openssh-server package; it works with many, but not all, FTP clients, and it's fully encrypted --> more secure)

Well, most of this is over my head.  I just know how it behaves on my system with Fiesty.  I haven't done anything since Gutsy.  I don't use FTP on a regular basis, and it stays deactivated most of the time.  It's only when I go out of town on business that I activate this so that I can access all my possibly needed information.

However I will try the SFTP when activating next time with my new Gutsy install...  Thanks for the tip....

Still, does installing Firestarter activate iptables differently when running than when not installed at all?

---

### Post by bodhi.zazen on 2007-11-14
> **crjackson said:**
> Still, does installing Firestarter activate iptables differently when running than when not installed at all?

Yes it does (see my quoted text below for basic information about how firestarter will change your settings).

Let me answer you with a question, what is you expect a firewall to do for you ?

In a nutshell, a firewall is a set of rules for who may access your computer.

Let me give an example using ssh. If you are connected to the internet and you monitor you network traffic you will see you get many requests for connections, everything from ftp to ssh to http to port scans. This is the reality of the internet.

port 22 , ssh, gets hammered on my boxes for example. But I am not running a ssh server, so, who cares ? A potential cracker can send 1,000,000,000 requests to log in over ssh, but they will all fail.

OK, so now let's say I install a ssh server. You bet it needs to be secured. Learning to secure your server(s) is an ongoing process and a firewall can be a part of the solution. See [uwiki]AdvancedOpenSSH[/uwiki]

With that information, how paranoid are your ? If you feel safer installing a firewall to block the ssh, ftp, http, and port scans, \o/. You can start with firestarter and graduate to learning to configure IP tables.

And for completeness :

> Firewall FAQ

Firewall Information.

The Ubuntu (Linux) firewall is called IP tables and is included with your Ubuntu installation.

The default settings are permissive (meaning they allow all traffic) and, if you are not running a server, you may feel this is adequate protection.

If you would like to configure your firewall the two options are to use a gui front end or write IP rules for yourself (there are various scripts on the web that will help with this).

The most popular gui tools are Firestarter and Guard dog (KDE). Keep in mind that these applications are not firewalls, but rather configuration tools. This is sometimes a source of confusion as the application should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest :twisted:.

See these links for further information/how to use these tools :

[center][[color=red][Size=6]How to Firestarter[/size][/color]](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html) - [[color=blue][size=6]How to Guard Dog (KDE)[/size][/color]](http://www.simonzone.com/software/guarddog/manual2/index.html)[/center]

Firestarter Home Page : [http://www.fs-security.com/](http://www.fs-security.com/)

**Default Firestarter Policies**:
[quote][list][*]New inbound connections from the Internet to the firewall or client hosts are blocked.
[*]The firewall host is freely allowed to establish new connections.
[*]All client hosts are allowed to establish new connections to the Internet, but not to the firewall host.
[*]Traffic from the Internet in response to connection requests from the firewall or client hosts is allowed back in through the firewall.[/list]

If you would like to learn more about IP tables, here are some starting points:

_**Iptables references_** :
[list][*][https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[*][http://www.linuxguruz.com/iptables/howto/](http://www.linuxguruz.com/iptables/howto/)
[*][http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)[/list]

If you would like to learn more about basic Ubuntu security, please see this thread :

[[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

If you would like to debate/discuss the use of firewall, please post here:

[ Recurring Discussions](http://ubuntuforums.org/forumdisplay.php?f=302)[/quote]

---

### Post by Sproid on 2007-11-17
Hi.
I have read Linux and Ubuntu are " secure" for common use. But for example , having pidgin, and ktorrent running, is my computer acting as a server? am I so safe just with iptables default?
And what about Shields Up in grc.com. I run it with ubuntu and other distros and it always give me the result of closed ports and a few stealth and it didn't pass the test. With zonealarm they all appeard stealth and pass the test. By now I know stealth and closed are not the same. Closed ports means my computer is/it can detected by port scanners/hackers, so closed ports are not that secure, and stealth are more secure.**The Question is**: how in Ubuntu can I get all the ports stealth as zonealarm do it? with firestarter or guard dog?

---

### Post by MozartlovesUbun2 on 2007-11-17
> **Sproid said:**
> Hi.
I have read Linux and Ubuntu are " secure" for common use. But for example , having pidgin, and ktorrent running, is my computer acting as a server? am I so safe just with iptables default?
And what about Shields Up in grc.com. I run it with ubuntu and other distros and it always give me the result of closed ports and a few stealth and it didn't pass the test. With zonealarm they all appeard stealth and pass the test. By now I know stealth and closed are not the same. Closed ports means my computer is/it can detected by port scanners/hackers, so closed ports are not that secure, and stealth are more secure.**The Question is**: how in Ubuntu can I get all the ports stealth as zonealarm do it? with firestarter or guard dog?

hi

would be better if you start a new thread with this specific "stealth" question, you'll get a faster response.

---

