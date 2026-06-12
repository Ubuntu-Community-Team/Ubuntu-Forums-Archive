---
title: "[SOLVED] Firewalls: Blocking Outbound Connections"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-06
Got a quick question....... If I want to enable File Sharing ( Samba )
with other windows boxes would one have to Allow it through the default installing of
ubuntu or would it just pass right through..... Also if one installs Fire Starter, I'm assuming
that this would block Samba ports for sure  right?

One other thing I would like to know....
Everyone knows that Windows software such as iTunes and other programs try to connect
to the internet behind the scenes to do updates and what not. Does Linux block this type of 
activity? I know that when I insert a CD into Banshee or Rhythm Box it connects somewhere
and displays all the Artist and Song titles. I wasn't asked if I wanted that to happen
but yet it was allowed to connect.

So, What is and what isn't allowed to go through...... Or is it that it doesn't
protect from outbound transmissions?

---

### Post by kebes on 2007-12-06
The default Ubuntu firewall settings don't block anything, but there are also no listening services (so it's quite secure). If you install Samba, that running service will not be blocked.

If you install Firestarter, it will activate a more restrictive set of firewall rules. So, yes, you will have to open up ports for Samba specifically (which is easy to do).



In Linux it is normally assumed that the programs you have running are "trustworthy" and don't need to be blocked from using the network. So they will be able to connect elsewhere. The software in the standard Ubuntu repositories are "safe" and don't use the network for anything bad (like sending your personal information), so it's okay.

However if you want you can block outbound connections, and only allow connections for the applications you want. Again, Firestarter makes this quite easy to do. But of course you'll then have to authorize all the applications/ports you need (for web browsing, email, etc.).

---

### Post by Orbital75 on 2007-12-06
Yes, I agree and totally trust everything that comes from the repository as being safe.
There way to many eyes watching for something malicious to get in there.  The only thing
I worry about is third party Apps such as Picasa, VirtualBox, and a few other programs that are
allowed to run on linux but are not Truly open source.  Also a few windows programs
that I run in Wine could be an issue.  So, I've never looked but can I Block everything
from accessing the net and only allow certain programs with FireStarter?
Would this be Very difficult or just as easy as Zone Alarm or something similar on
Windows.

Thanks for the help......  Just don't like Big Brother trying to figure out how to
advertise to me.  :KS

---

### Post by kebes on 2007-12-06
You're right about third-party apps. If you want to be extra safe, you can restrict outbound connections. After installing Firestarter, launch it and go to the "Policy" tab. Select the "Outbound traffic policy" option, and set it to "Restrictive by default, whitelist traffic."

This will set it to a "default-deny" policy, so that all outbound traffic will be blocked. You will then have to add the connection types you want unblocked. It won't pop up a question when it blocks something: disallowed connections are silently dropped.

This will allow you to set things like web browsing (HTTP and HTTPS) but block everything else. However you'll notice that there isn't any way to specify blocking on a per-application level: it's only on a port-level. So, in theory a sneaky application could make connections through HTTP and it wouldn't be blocked.


If you really want per-application control, I'm not aware of any application that does that ([this thread]("http://ubuntuforums.org/showthread.php?t=471737") suggests that [TuxGuardian]("http://tuxguardian.sourceforge.net/") may be able to do that, but I've never used it). In principle you can use the commandline "iptables" function to specify very sophisticated firewall rules (but this takes some work to get right). Note that on Linux you have great tools for monitoring network traffic (e.g. "netstat" on the commandline), so you can check to see if applications are accessing the network when you don't expect them to.


I hope that helps!

---

### Post by Orbital75 on 2007-12-06
Thanks you, that helps a lot......  I may look into Tux Guardian and and see what
it's all about.  I'd like a simple firewall that will block on a application bases.
As you said a sneaky app could try to carry info over http (port 80). I know
that I couldn't make a sophisticated firewall that you speak of.  I'm a newbie when
it comes to linux so that is probably out of the question.  Its a shame we have to 
worry about companies doing these kinds of things. Once I find that a product is
doing this, I stop using it but it only takes one time to gather the information and
send it out.  

Does Linux offer a Gui that does the same thing as netstat?
I use TCPview on window and it does the same thing as netstat
which is shows all established connections to your box.

---

### Post by kebes on 2007-12-06
> **Orbital75 said:**
> Does Linux offer a Gui that does the same thing as netstat?
I use TCPview on window and it does the same thing as netstat
which is shows all established connections to your box.

A simple "netstat viewer" can be created by using the program called "[conky]("http://conky.sourceforge.net/")" (it's in the repositories). It creates an overlay on your desktop that shows "vital stats" about your computer, like CPU usage, memory, etc. You can configure it to show different stats. I have mine showing graphs of inbound/outbound data rates, and it lists active connections. By keeping an eye on this, you can get an idea of what is connecting to your system.

Firestarter also has an Events tab that lets you look through the list of connections. I'm sure there are other GUI frontends for netstat, but those are the two I've used. (And netstat on the commandline is very useful, too.)

---

### Post by tech9 on 2007-12-06
> **kebes said:**
> A simple "netstat viewer" can be created by using the program called "[conky]("http://conky.sourceforge.net/")" (it's in the repositories). It creates an overlay on your desktop that shows "vital stats" about your computer, like CPU usage, memory, etc. You can configure it to show different stats. I have mine showing graphs of inbound/outbound data rates, and it lists active connections. By keeping an eye on this, you can get an idea of what is connecting to your system.

Firestarter also has an Events tab that lets you look through the list of connections. I'm sure there are other GUI frontends for netstat, but those are the two I've used. (And netstat on the commandline is very useful, too.)

conky is a neat tool! :)

---

### Post by Orbital75 on 2007-12-07
Ah..... I'll give it a try. :)

---

