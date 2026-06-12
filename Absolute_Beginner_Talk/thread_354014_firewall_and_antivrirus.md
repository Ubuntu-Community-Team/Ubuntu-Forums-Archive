---
title: "firewall and antivrirus"
date: 2007-02-05
forum: Absolute Beginner Talk
---

### Post by ubername on 2007-02-05
Hi

On my XP setup I run keiro firewall, avg, scotty and sbybot S&D. What should I run under ubuntu?

---

### Post by mcduck on 2007-02-05
There's no need for antivirus or antispyware software. If you want, you can install Firestarter to control the built-in firewall, but even that's optional. Welcome to Linux ;)

---

### Post by Ryan450 on 2007-02-05
yes firestarter great app to control the default firewall, gives you lots of control and pretty straight forward. 

As for anti-virus its generally not needed because of how unix-like systems operate. Sure there are a few but very little to actually cause concerns, and installing applications and accessing sensitive stuff is password protected. 

Although if you want to download and install the avg linux version, that'll help you stop spreading virus's via e-mails to other windows boxes.

---

### Post by ubername on 2007-02-05
> **mcduck said:**
> There's no need for antivirus or antispyware software. If you want, you can install Firestarter to control the built-in firewall, but even that's optional. Welcome to Linux ;)

Thanks!

Is it really so safe that I don't need these things? Not even to give little reassuring messages that 'program X has tried to access the internet although it hasn't before. Is that OK?'

Thanks for the reply

---

### Post by mcduck on 2007-02-05
> **ubername said:**
> Thanks!

Is it really so safe that I don't need these things? Not even to give little reassuring messages that 'program X has tried to access the internet although it hasn't before. Is that OK?'

Thanks for the reply
Linux programs do not 'call home' or contain spyware. If you only use Ubuntu's repositories to get programs and don't install random packages from untrusted sites you don't need such things.

And even running without a firewall is safe if you don't install any servers open to the network. In default Ubuntu install there is no program responding to any port, so you are safe even without a firewall.

---

### Post by kinematic on 2007-02-05
there is no program x that wants to access the internet....all the ports are closed by default.
if a program or service needs access you have to open a port yourself.
as for virusses and crapware....don't worry about it.
trojans,malware,adware and all that other stuff doesn't work on linux
there are some linux virusses but they were created as a proof of concept and are not in the wild.

---

### Post by r4ik on 2007-02-05
"there are some linux virusses but they were created as a proof of concept and are not in the wild"
Every time a read something like this i get this weird itch.
Linux virusses can be and will be written.
Hopefully there is a good scanner on somebody's shelf by the time it is needed.

---

### Post by ubername on 2007-02-05
Ah.

I can see why people like Linux.

That is very encouraging. I might just have to install firestarter and Linux avg (for a while) just to acclimatise!

Thanks for your responses.

---

### Post by Perfect Storm on 2007-02-05
The best protection is to keep an updated system.

---

### Post by kinematic on 2007-02-05
> **r4ik said:**
> "there are some linux virusses but they were created as a proof of concept and are not in the wild"
Every time a read something like this i get this weird itch.
Linux virusses can be and will be written.
Hopefully there is a good scanner on somebody's shelf by the time it is needed.

if a virus appears and it wants access to your system you'll have to give it permission ;)

---

### Post by ubername on 2007-02-05
> **kinematic said:**
> there is no program x that wants to access the internet....all the ports are closed by default.
if a program or service needs access you have to open a port yourself.
as for virusses and crapware....don't worry about it.
trojans,malware,adware and all that other stuff doesn't work on linux
there are some linux virusses but they were created as a proof of concept and are not in the wild.

Just to reassure myself:

When I downloaded and ran a newer version of firefox than that which came with the ubuntu distro, I got no messages before it hit the net. How could I know it was using the same ports as the previous version, or doing things I wanted it to? 

Obviously it's a hypothetical question in a sense, because if I had been prompted I would have confirmed the action.

But worth a thought surely. I don't know anything about the fundamental architecture of Linux. I assume that a large part of why viruses etc.. are not a problem is because there are too few linux machines out there, and there users are too savvy. I still like they idea of belt, braces and anything else to protect me!

---

### Post by r4ik on 2007-02-05
In that case it would not be a virus.
My definition of a virus is "something" that enters the system unauthorized.
Sorry in reply to kinematic this one :)

---

### Post by steve.horsley on 2007-02-05
> **r4ik said:**
> "there are some linux virusses but they were created as a proof of concept and are not in the wild"
Every time a read something like this i get this weird itch.
Linux virusses can be and will be written.
Hopefully there is a good scanner on somebody's shelf by the time it is needed.

You can't write a scanner to look for a virus that doesn't exist yet. I am certain that the time will come when you need a virus scanner for Linux, but  right now there's nothing to look for.

---

### Post by r4ik on 2007-02-05
By scanner on the shelf i meant that a little 'awareness" and anticipation will do no harm.
But for the moment agreed.

---

### Post by Contrid on 2007-02-05
Firestarter is great. Give it a shot.

```
sudo apt-get install firestarter
```

...and then you'll get something like this :

[[IMG]http://img101.imageshack.us/img101/2224/firestarterdu5.th.png[/IMG]](http://img101.imageshack.us/my.php?image=firestarterdu5.png)

You can find it under System -> Administration after installation.

Good luck. ;)

---

### Post by old_geekster on 2007-02-05
Linux is going to be like Apple.  Once more people became enamored with it, the more it became a target for the "Hackers".

My son kept telling me how he wasn't worried about viruses with his Apple rig, but now he is reading about viruses popping up here and there.

---

### Post by InfernalPenguin on 2007-02-05
Firestarter is a great application. As for virus scanner you can look into ClamAv. People mostly use it on mail servers and such. You can also use it to scan your Windows partitions.

---

