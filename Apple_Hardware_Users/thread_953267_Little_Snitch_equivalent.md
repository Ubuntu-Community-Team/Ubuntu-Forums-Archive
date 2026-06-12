---
title: "Little Snitch equivalent?"
date: 2008-10-20
forum: Apple Hardware Users
---

### Post by gutsy08 on 2008-10-20
Hello, I'm wondering if anyone here knows if there's a Linux equivalent for Little Snitch on OS X.  In other words, an interactive firewall that can warn you about outgoing connections and prompt you when they're initiated and give you an option to set rules for them then.  Being able to handle incoming connections as well would be a nice bonus.  Thanks in advance.

---

### Post by handy on 2008-10-20
I'm not aware of any.

What I do use is [***_Vidalia_***]("http://www.vidalia-project.net/"), which handles [***_Tor_***]("http://tor.eff.org/") & [***_Privoxy_***]("http://www.privoxy.org/") very nicely with its GUI front end, I run Vidalia on everything all the time: Leopard, Arch, Sabayon, & any other distro' I'm playing with.

Vidalia is not a replacement for Little Snitch, more of a compliment really; I use both under Leopard.

---

### Post by DowntownIT on 2009-08-03
I find it hard to believe that there isn't an interactive firewall for Ubuntu.

---

### Post by ryanczak on 2009-08-07
> **DowntownIT said:**
> I find it hard to believe that there isn't an interactive firewall for Ubuntu.

I've been using Linux on the desktop for many years and I have never seen an interactive firewall on any distribution. the current firewalling code, netfilter (iptables), is not application aware, it would take significant effort to make it capable of this. I'm not saying it is impossible but it is not trivial either.

---

### Post by produnis on 2010-01-15
I added this as an idea to brainstorm.ubuntu.com

Please consider voting for it :-)
[http://brainstorm.ubuntu.com/idea/23333/](http://brainstorm.ubuntu.com/idea/23333/)

---

### Post by scottuss on 2010-01-15
I know it's not exactly what you want (not application based) but Firestarter is the GUI I use for my firewall.

It can be set up with whitelist / blacklist rules etc (only for ports/services, not applications)

---

### Post by hoy on 2010-03-13
> **scottuss said:**
> I know it's not exactly what you want (not application based) but Firestarter is the GUI I use for my firewall.

It can be set up with whitelist / blacklist rules etc (only for ports/services, not applications)
Hey! Last version of Firestarter released "January 2005" (5 years ago), is this normal? I don't think so...

Currently I use Gufw. Maybe some day we will have application-level firewall...

---

### Post by linuxopjemac on 2010-03-14
I don't know of the features you describe as I don't really use a firewall (I am behind a router), but I know firestarter. There are other firewall programs in the repository. Just open Synaptic Package Manager and search firewall. You will see a few options.

Good luck

---

### Post by corn13read on 2010-07-06
firestarter is dated. little snitch is amazing, you can see what all is using the internet currently and stop certain processes using it on the fly etc.

might as well just use an iptables gui as firestarter...

---

### Post by scottuss on 2010-07-10
> **corn13read said:**
> firestarter is dated. little snitch is amazing, you can see what all is using the internet currently and stop certain processes using it on the fly etc.

might as well just use an iptables gui as firestarter...

Firestarter *is* dated, but it's the closest thing you're going to get to Little Snitch at the moment.

It may be that UFW (and it's gui) will advance and have such features in the future.

---

### Post by d3v1150m471c on 2010-07-10
firestarter isn't pretty and iptables definitely isn't either. however, last time i checked they both worked flawlessly. Pop-ups won't make your system more secure. If something is connecting to you or vice versa without you knowing about it...hey, the popup doesn't work anyways...so. learn what you've got, mate.

---

### Post by modelmaker on 2010-08-09
> **gutsy08 said:**
> Hello, I'm wondering if anyone here knows if there's a Linux equivalent for Little Snitch on OS X.  In other words, an interactive firewall that can warn you about outgoing connections and prompt you when they're initiated and give you an option to set rules for them then.  Being able to handle incoming connections as well would be a nice bonus.  Thanks in advance.

 It's been a while since this request was posted. Has anyone found a Little Snitch equivalent?      It's a superb help in privacy and security.

---

### Post by 2cute4u on 2011-01-01
Well it's been a long time since anyone has posted here.  Has anyone found anything like little snitch?

Reading the posts, I think most people misunderstand what we are asking for. Little snitch is a reverse firewall for applications. It monitors and blocks outgoing traffic, not incoming traffic. It's main purpose is to block programs (spyware, etc)  from "phoning home".

---

### Post by rosciol on 2011-02-11
I agree with the last post; why isn't there more desire for a reverse firewall in Ubuntu (or just in general).  With people being increasingly concerned about privacy, and with tools like Little Snitch being the only viable defense against programs running on your computer telling anyone anything they want, it would be reasonable to assume that this is a program people are looking for.  Yet the somewhat niche popularity of Little Snitch and the unavailability of alternatives on other platforms suggests that most people don't use these products and don't seek them out; is it that they can't be bothered to define outbound rules, or simply that they just don't care about what information is transmitted from their computer?

---

### Post by tjwoosta on 2011-02-11
> **hoy said:**
> Hey! Last version of Firestarter released "January 2005" (5 years ago), is this normal? I don't think so...

Currently I use Gufw. Maybe some day we will have application-level firewall...

Firestarted is simply a gui frontend for iptables. Its it does its job, which is modifying iptables through a graphical interface, and it does it fairly well. Theres an old saying "If it aint broke, dont fix it."


As far as application layer firewalls, the only one I know of is TuxGuardian which apparently hasnt been updated since 2006. Ive never used it mysel, so I have no idea how good or bad it is.

[http://tuxguardian.sourceforge.net/](http://tuxguardian.sourceforge.net/)

---

### Post by nogoodnamesleft on 2011-03-18
There aren't many because they aren't really necessary for Ubuntu right now.

If there is a need for something, a bunch of people will make one and it will start to appear in distros as standard.

---

### Post by Rainer Phantasiename on 2012-06-23
@nogoodnamesleft

That's wrong. Little Snitch's main purpose is, to control OUTGOING network activity on application/service level in an easy an convenient way. That said you are able to see AND to decide on the fly whether you want to let a service or application talk to the mothership or not.

Ubuntu - theoretical - has the tools on board to block outgoing connections as well. But not at application level. You have to decide whether to allow a certaint protocol, port, ip or not. From my point of view, that's enough for most server setups where blocking incoming activity is much more important because you normally know what's running on the box. But if you have a desktop and probably some Windows Apps on it (in Wine or in a whole an VM) than you might want to limit those apps and service a little bit.

Anyhow... Also attacker-szenarios are not impossible. See flame or stuxnet. Yes, they won't run on linux currently but thinking that linux is NOT vulnerable against such attacks where the attackers have nearly unlimited budget and ressources, is a bit silly - a weakness of such software is the necessity of an outgoind network connection. If you were able to easily recognize and block that, life could be much better.

The problem is, that Linux has failed to conquer the desktop market, therefore the demand for such tools might be not very high. So the chances, that someone developes something like Little Snitch might be small.

BTW: Little Snitch is a module which plugs into the mach kernel of OS-X with an very easy to use, intuitive user interface. So if one will doe something like little snitch he has to do it at kernel level to achieve optimal performance and maximum effectivity.

Regards,

RP

---

### Post by AnoPoli on 2013-05-17
Let's face it...
Little snitch is so popular because 99% of their user base, using it for blocking stolen software
from communicating with the developer's servers, avoiding blacklisting.
With GNU/Linux there isn't really such an urge for that kind of acting.
There is a good free app for almost everything in the repositories and out there.
Maybe our pockets are dead empty, but we have peace of mind.

---

