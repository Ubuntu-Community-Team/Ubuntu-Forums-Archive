---
title: "Strange networking problem"
date: 2008-05-13
forum: Arch and derivatives
---

### Post by will1911a1 on 2008-05-13
My Arch machine will not ping past my router.  It receives an ip via DHCP, it can ping the router, but it won't go past that point.

I'm using a Netgear wireless router but this particular machine is wired directly to the router.  I have rebooted the cable modem, the router, and the machine, with no sucess.

My wife's XP machine (also wired directly to the router) works fine as does my laptop on it's wireless connection.

I logged into the router on my wife's machine and the router does list the Arch box as being connected.

Any suggestions?

---

### Post by Barrucadu on 2008-05-13
Does your router have an error log or something?

---

### Post by will1911a1 on 2008-05-13
> **Barrucadu said:**
> Does your router have an error log or something?

It does have logs.  I checked them and found nothing unusual.

---

### Post by mips on 2008-05-13
Do you have a default route? **route -n** should tell you

In your **/etc/rc.conf** file did you remove the exclamation mark before gateway?

```
# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
gateway="default gw 192.168.0.1"
ROUTES=(gateway)
```

The default is **ROUTES=([COLOR="Red"]![/COLOR]gateway)** you need to remove the "!"

---

### Post by will1911a1 on 2008-05-13
> **mips said:**
> Do you have a default route? **route -n** should tell you

In your **/etc/rc.conf** file did you remove the exclamation mark before gateway?

```
# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
gateway="default gw 192.168.0.1"
ROUTES=(gateway)
```

The default is **ROUTES=([COLOR="Red"]![/COLOR]gateway)** you need to remove the "!"

I have to get to work, but I'll double check that when I take my lunch break.  I believe it's already done (everything's been working fine for weeks up till this point) but I'll have a look at it and get back to you.

Thanks for the suggestion.

---

### Post by Barrucadu on 2008-05-13
Did you install a kernel update recently? I did and things went a little dodgy with my video driver, and with HAL.

---

### Post by will1911a1 on 2008-05-13
> **Barrucadu said:**
> Did you install a kernel update recently? I did and things went a little dodgy with my video driver, and with HAL.

Nope, no kernel updates lately.

---

### Post by Dr Small on 2008-05-13
Maybe a DNS problem? just a guess.

---

### Post by will1911a1 on 2008-05-13
> **Dr Small said:**
> Maybe a DNS problem? just a guess.

That's another thing I want to check.  I get off work in another hour or so and I'll be trying some stuff once I get home.  I'll let you guys know how it turns out.

I really appreciate the suggestions, by the way. :)

---

### Post by will1911a1 on 2008-05-13
Looks like iptables was the culprit.  I stopped it and everything went back to normal.

I'm not sure what happened though.  I haven't changed my iptables configuration lately and it's been working fine for weeks.

Anyway thanks for the suggestions guys.

---

### Post by muadnu on 2008-05-14
I'm having a similar problem (just installed Arch for the first time...) I set up my network with DHCP but it's not working. The relevant part of rc.conf is
```
# DHCP:     Set your interface to "dhcp" (eth0="dhcp")
# Wireless: See network profiles below
#
eth0="dchp"
INTERFACES=(lo eth0)

# Routes to start at boot-up (in this order)
# Declare each route then list in ROUTES
#   - prefix an entry in ROUTES with a ! to disable it
#
gateway="default gw 192.168.0.1"
ROUTES=(!gateway)
```

I log in but there's no network. If I run
```
dhcpcd eth0
```
the network gets started. I'm not sure what it is that I'm doing wrong.

Any suggestions?

---

### Post by Barrucadu on 2008-05-14
If you just need to run that command to get it working, you could stick it /etc/rc.local

---

### Post by muadnu on 2008-05-14
Ok, thanks, it's a good woraround (I actually thought of doing something like that, but being an Arch newbie didn't know how). In any case, I think it shouldn't be necessary, but I'll try this for now.

---

### Post by will1911a1 on 2008-05-14
Nevermind.

Did a quick search to see if I could find a solution to your problem and came up with this:

[http://bugs.archlinux.org/task/2362]("http://bugs.archlinux.org/task/2362")
Sounds like the same problem.

To save you some reading, they couldn't figure it out either.

---

### Post by muadnu on 2008-05-14
Ok, thanks for the reference. The workaround is not too bad in any case. The command does take a couple of seconds to execute, but I guess it's simply because it's connecting.

---

### Post by will1911a1 on 2008-05-14
No problem.  It's weird that this isn't more of an issue.  That bug report is 3 years old and the guy had the same problem on two different computers.

I can't get to the Arch Linux forums from work but when I get a chance I'll read through them at home to see if anyone else has run into the same problem.

---

### Post by will1911a1 on 2008-05-14
Probably a silly question but you have the network daemon in your rc.conf right?

---

### Post by Dr Small on 2008-05-14
Also, doesn't:
```
ROUTES=(!gateway)
```

Need to be?
```
ROUTES=(gateway)
```

---

### Post by will1911a1 on 2008-05-14
> **Dr Small said:**
> Also, doesn't:
```
ROUTES=(!gateway)
```

Need to be?
```
ROUTES=(gateway)
```

Near as I can tell that shouldn't make a difference in this case, but it's worth a shot.

Out of curiosity,muadnu, what does your ifconfig return if you run it without running dhcpcd?

---

### Post by mips on 2008-05-15
> **will1911a1 said:**
> Near as I can tell that shouldn't make a difference in this case, but it's worth a shot.

Out of curiosity,muadnu, what does your ifconfig return if you run it without running dhcpcd?

If you don't remove the "!" then you wont have a default route and in most cases you wont be able to connect to anything beyond your gateway.

---

### Post by mips on 2008-05-15
> **will1911a1 said:**
> Looks like iptables was the culprit.  I stopped it and everything went back to normal.

I'm not sure what happened though.  I haven't changed my iptables configuration lately and it's been working fine for weeks.


Did you have any kernel updates lately? iptables is part of the kernel if I'm not mistaken and if something was amiss then it would have appeared after a kernel update&reboot.

---

### Post by will1911a1 on 2008-05-15
> **mips said:**
> Did you have any kernel updates lately? iptables is part of the kernel if I'm not mistaken and if something was amiss then it would have appeared after a kernel update&reboot.

Nope, no kernel updates.

---

### Post by muadnu on 2008-05-15
> **Dr Small said:**
> Also, doesn't:
```
ROUTES=(!gateway)
```

Need to be?
```
ROUTES=(gateway)
```

In the Arch Beginners Guide, which I followed during the installation, it said to leave the ! when using dhcp.

And about kernel updates, I'm not sure, though I think not. I just installed Arch 2008.04-RC two days ago, and I don't remember seeing any kernel updates after installing, though I might be wrong.

And yes, I'm loading the network daemon...

---

### Post by muadnu on 2008-05-15
> **will1911a1 said:**
> Out of curiosity,muadnu, what does your ifconfig return if you run it without running dhcpcd?

```
$ ifconfig -a
eth0      Link encap:Ethernet  HWaddr 00:1A:A0:FD:64:0B  
          BROADCAST MULTICAST  MTU:1500  Metric:1
          RX packets:0 errors:0 dropped:0 overruns:0 frame:0
          TX packets:0 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:0 (0.0 b)  TX bytes:0 (0.0 b)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:6 errors:0 dropped:0 overruns:0 frame:0
          TX packets:6 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:380 (380.0 b)  TX bytes:380 (380.0 b)

```

---

### Post by will1911a1 on 2008-05-15
Well I'm stumped.  I wasn't able to find any solutions on the Arch forums for you and the wiki wasn't much help.

The only other thing I can think to do is hop over to the arch linux IRC chat and hope someone on there has run in to this before.

---

### Post by will1911a1 on 2008-05-15
You guys think it could be an issue with the nic driver do you?

---

### Post by Barrucadu on 2008-06-22
I just had to bump this to the top - because I read through it again and realised the solution to muadnu's problem!

```
eth0="dchp"
INTERFACES=(lo eth0)
```

You spelled "dhcp" wrong. It's the most obvious error, but we were all expecting something much more difficult and just didn't notice it :lolflag:

---

### Post by handy on 2008-06-22
> **Barrucadu said:**
> I just had to bump this to the top - because I read through it again and realised the solution to muadnu's problem!

```
eth0="dchp"
INTERFACES=(lo eth0)
```

You spelled "dhcp" wrong. It's the most obvious error, but we were all expecting something much more difficult and just didn't notice it :lolflag:

I have been reading through this thread wondering if anyone was going to notice that "dchp".

Easy to do.  It only takes one character to bring down a whole system.

I was going to get political, but I'll be quiet now... :lolflag:

---

### Post by Dr Small on 2008-06-22
> **handy said:**
> I have been reading through this thread wondering if anyone was going to notice that "dchp".

Easy to do.  It only takes one character to bring down a whole system.

I was going to get political, but I'll be quite now... :lolflag:
Yeah tell me about it...
After I got Arch all installed for the second time, with everything in working order and how I wanted it, I went to remove 'boot' while in my home folder. The files were owned by root, but my first command I ran was:
```
rm -R /boot
```

It gave me a permission denied, so then I quickly hit UP, HOME, and typed 'sudo '; ENTER. Boom. It was that fast, and that devistating. Having the '/boot' was the whole problem. I had to reinstall the kernel and grub again before I attempted to reboot!

But you know, the Windows mindset is, if something doesn't work, a reboot will remedy it. In this case, it would have totally messed everything up! lol.

---

### Post by muadnu on 2008-06-24
> **Barrucadu said:**
> I just had to bump this to the top - because I read through it again and realised the solution to muadnu's problem!

```
eth0="dchp"
INTERFACES=(lo eth0)
```

You spelled "dhcp" wrong. It's the most obvious error, but we were all expecting something much more difficult and just didn't notice it :lolflag:

Thanks! It is an obvious error, and I didn't notice it. I'll try it later, but I guess it should work. Thanks again...

---

