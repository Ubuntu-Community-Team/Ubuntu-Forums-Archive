---
title: "Do I need securityware? (firewall, spyware, antivirus)"
date: 2006-09-11
forum: Absolute Beginner Talk
---

### Post by Alveric on 2006-09-11
OK, so I'm just about to make take the big step and swap over from Windows XP to Ubuntu Dapper on my laptop.

I have tried out the live CD and everything - including the wireless - seems to work fine (except the internal modem, but I gather that's not unusual).

Do I need to fit all the antivirus, antispyware and firewall software (well, their Linux equivalents) that I have on my Windows machine.

I can see comments that Linux is more secure - can someone give me a definitive (-ish) pros and cons on whether "more secure" mean that I can dispense with all my securityware?

Thanks in advance.

---

### Post by Najand on 2006-09-11
As far as most of viruses are for Windows machine they cannot infect Linux. However having a virus scanner is recommended. There is a free one in Ubuntu Repositories called clam Anti Virus (clamav). Try ro install it using apt-get or synaptic.

---

### Post by H3HI on 2006-09-11
i think it's needed, be a newbie, protect pc is our first work.

---

### Post by panzer21st on 2006-09-11
I downloaded aegis virus scanner with synaptic.  It's free also.  I don't know about a firewall.  Just make sure you update the virus definitions.  I set it up a root account, to do things, I coundn't do from my regular home desktop directory.  It's made things easier.  I guess it's a preference thing.

---

### Post by az on 2006-09-11
It is not needed.

Just keep up to date with security updates.  All that other crap is useless, including a firewall.  (How do people live like that?)  Everything is free-libre open-source, so there is pretty much no way that anyone can upload spyware or other malware into the repositories.

Stick with ubuntu repositories, too.  Avoid thrird-party precompiled apps - get them in source form.  Better still, get them packaged for Ubuntu in universe.

---

### Post by 3rdalbum on 2006-09-11
Only download programs that come from reputable sources; the repositories, coverdisks of Linux magazines, or actual organisations (like Skype, for instance). You are also probably safe if you download a binary package of a program that someone else has recommended.

Having said that, I've never heard of anyone installing malware on Linux by accident.

Ubuntu comes with a firewall, which you can set up by downloading Firestarter from the Synaptic Package Manager. You only need one firewall, really. And no antivirus, unless you're concerned that you might send something to a Windows machine.

The pros of having some security software is that you will feel safer. Don't discount that; it's important.

The cons are, some people can get obsessive about it. Hands up: How many of you know Windows users who have two antivirus programs and three firewalls? Anti-virus can also slow down your system.

---

### Post by Mimsy on 2006-09-11
I'm concerned that I might send things on to Windows machines, since the laptop needs to work with windows machines a lot. I got the impression that Clam is enough and that I don't need to install another antivirus. Is that right? Also, do I need to manually update it somehow, or does it keep itself updated without my help?

Thanks,
Mimsy

---

### Post by Metacarpal on 2006-09-11
Congrats on deciding to make the switch!

Both Clam and Aegis are good antivirus systems.  You don't have to worry about getting infections yourself, but if you commonly share documents with Windows users, it's kind to have an antivirus on your system for their benefit.  The poor, poor souls. ;)

You don't need to worry about spyware.  One of the great things about the linux setup is that software can't just install itself - it has to ask for your password to get on.  So spyware and other malware is pretty much non-existant on your Linux box.

As for the firewall, as previously mentioned your Ubuntu install has a firewall already.  As for using Firestarter to configure it... unless you know how networking works, it's going to be a bunch of gibberish.  So I wouldn't worry about installing Firestarter at the moment.

Otherwise, if you do as suggested and only install software from trusted sources, you shouldn't have any problems security-wise.

---

### Post by idn on 2006-09-20
A new version of aegis just came out, a complete rewrite, I might try and compile it later unless anyone has any debs :)

---

