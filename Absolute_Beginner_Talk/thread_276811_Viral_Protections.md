---
title: "Viral Protections"
date: 2006-10-13
forum: Absolute Beginner Talk
---

### Post by Zeek00 on 2006-10-13
Hey,

What does Ubuntu, or better yet Linux in general Have in the way of Firewalls, Virus and Trojan Protection and finally spyware protection?

Are these tools integrated in the software and pre configured or must I download special programs to do such tasks. I understand that linux is not as largly attacked with viruses and all that jazz and the focus is more on windows users, but I would still like to have such programs so I'm protected no matter what.

Zeek :D

---

### Post by raul_ on 2006-10-13
Lol
I don't even think that there is anti-virus software. The only one i've seen is for Linux servers. Dude, be happy, you're not in Windows anymore, u don't need that stuff =) although, a firewall is always a good idea. I use Firestarter (available through Synaptic) and never had a problem. I don't know if it's the most user friendly u can find.

---

### Post by bulldog on 2006-10-13
Nothing I suppose............but you can install firestarter as a firewall and Avast as a virus scanner for example.

You normally use linux as a user and so there could be no harm done to the system,because a virus has no acces to the system.

In windows most people act as administrator and have acces to all system files.
When you get a virus it can destroy your install.

This can't happen so easely in Linux.

---

### Post by jordanmthomas on 2006-10-13
Firewall:  already built in.  If you want to **modify** it, then you can use firestarter
Antivirus:  not needed to protect you, but if you want to help protect other, less fortunate, Windows boxes, you can use ClamAV

As far as trojans go, I guess ClamAV takes care of them as well.

**beaten

---

### Post by Zeek00 on 2006-10-13
I don't mind if there is no real graphical interface to the firewall or to install it. I'll lear.

I had dual booted windows and Fedora core three and lost information when windows decided it didn't like itself anymore and commited suicide. So even though the people who write virus software for windows are running linux and what not doesn't mean that there arn't nice presents for those running linux.

---

### Post by Bigbluecat on 2006-10-13
There is anti virus software. Both ClamAV and Avast can installed via synaptic. There are others and different people prefer different programs. In general from what I read there aren't really any viruses for Linux - only a few lab experiments. If you run as a normal user (not as root all the time) it is impossible for anything to install without your knowledge. Do a search on the forums for virus - there is lot's of talk and discussion. Make your own mind up on whether you want one or not.

Firestarter is a GUI front and for the iptables firewall. 

Personally I use Guarddog. It is a little more strict blocking all ports until you explicitlly enable each and every protocol (including basic ones like HTTP for browsing).

---

### Post by gwk on 2006-10-13
Yup, gotta agree, getting a firewall is a good idea (isn't there one already installed?) but the spyware and virus software is like taking out "Getting Hit By Lightning Insurance".  Getting a virus on Linux or a Mac is so unlikely it's just not worth worrying about.

But, if you are still getting used to not being in a Windows environment where viruses are a normal part of every day, then you can get AVG for Linux at [http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-free](http://free.grisoft.com/doc/5390/lng/us/tpl/v5#avg-free)

But really, you don't need it.  Just run a scan every few days for a while, then every week or so, then every month or so.  Eventually you won't get that twitchy feeling from no AV that any sane Windows user would have.

---

### Post by dddouglas on 2006-10-13
If you have a server you might want to protect the Windows boxes that are on your net and if you are still unsure check out this [http://ubuntuforums.org/showthread.php?t=273748&highlight=virus](http://ubuntuforums.org/showthread.php?t=273748&highlight=virus)  as well as the many other threads. The general consensus is that for the desktop it is not needed

---

### Post by steve.horsley on 2006-10-13
You don't need a firewall until you install a service on Ubuntu. The default install is not listening for incoming connections at all. If you do install any services, firestarter and gaurddog are both available in Synaptic - choose the one you like the look of.

There are no Linux viruses in the wild (yet), and therefore a virus scanner cannot help protect Linux. Installing a virus scanner today won't protect you from a virus released tomorrow because it won't know the signature. It will however prevent you from passing on Windows viruses that you receive from your windows friends to other windows friends. The names clamav and f-prot come to mind.

All GUI firewalls on Linux are just pretty front-end cnofiguring tools for iptables which is the text-mode firewall built into the kernel. You really need to know your stuff to configure iptables directly, but it can be done. Use the command **man iptables**.

There is also ip6tables for IPv6, but I don't know of any GUI config tools for that.

---

### Post by Zeek00 on 2006-10-13
Quick Question, to small to start a thread.

Any here that like America's Army. Do you know if they have come out with the new version (Overmatch) for linux yet or do I have to run it using Cedega or WINE?

---

### Post by mahy on 2006-10-13
> **Zeek00 said:**
> Hey,

What does Ubuntu, or better yet Linux in general Have in the way of Firewalls, Virus and Trojan Protection and finally spyware protection?

Zeek :D

In addition to everything mentioned already, there's also aegis-virus-scanner.

---

### Post by three-cushion on 2006-11-04
Whats with the Linux 'firewall'.... If one has a HW Router (Linksys, etc) does that stop the IP lookers... and "open port" hackers?
 
I run Tiger Mac ( OSX 10.4.8 ) and I dual boot Linux on The Mac... On the Mac I run Virtual PC to 'occasionally' run Windows2000. But my Mac OS does have a firewall, tho b/c of the HW Router on the Broadband, I get no intruders at all.

On the Mac I run ClamXav and it does an excellent job of catching the PC (Windows) viruses so I can't forward any viruses along to my Windows friends. :-)
I tried to install AVG on my Linux sys... could not follow the procedure laid out by "Artificial Intelligence; Must be a step or two missing there.

So, what are anyones recommendations re: Linux firewall enhancements 
and/or anti-virus pkgs.

Cheers, Jim b

---

