---
title: "firewall, drivers and linux on the net"
date: 2007-10-12
forum: Absolute Beginner Talk
---

### Post by helane on 2007-10-12
maybe you can help me...

first - the firewall. i found a way to run automatically - autostart - other programs, but the firestarter still has to be run manually with a password. any way to make it automatic like other programs?

the other question - is there any way to be completely "legal"? i had to install a driver while installing the system for my compaq presario v3000 that was propietary and also it seems like there is a few drivers that u need to play music and video that i installed. i still do not understand if these are illegal, in a grey zone... should i pay for these? [http://ubuntuforums.org/images/smilies/confused.gif](http://ubuntuforums.org/images/smilies/confused.gif)

and one more - is there any way to hide what web browser and system am i using? when i browse sometimes i stumble upon a website that will say: u r using linux ubuntu, firefox x.x etc.

cheers, helane.

---

### Post by bodhi.zazen on 2007-10-12
Firestarter is a configuration tool for the firewall.

Your firewall is ip tables. IP tables is running, as configured by firestarter, at boot, so nothing to do. You should not run firestarter to moonitor trafffic as it is being run as root.

See here : [[color=black]Ubuntu Security[/color]](http://ubuntuforums.org/showthread.php?t=510812)

---

### Post by helane on 2007-10-12
so the moment i installed ubuntu it was protected? 

should i leave the default configuration in Furestarter then? 

h.

---

### Post by -grubby on 2007-10-12
> **helane said:**
> so the moment i installed ubuntu it was protected? 


h.

yep

---

### Post by por100pre1 on 2007-10-12
Just open Firestarter, set it up to your needs, and close it. You will be protected all the time. To run Firestarter at startup is a security breach because Firestarter requires superuser privileges to run.

---

### Post by helane on 2007-10-12
[http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html)

in here it says to out it in the sessions startup... why?

h.

---

### Post by bodhi.zazen on 2007-10-12
> **helane said:**
> so the moment i installed ubuntu it was protected? 

should i leave the default configuration in Furestarter then? 

h.

Yes and no ...

With a default install the rules for firestarter are to permit all traffic. This is OK as a default install has no open ports ...

This is the information I usually give :

[quote=bodhi.zazen]Firewall Information.

The Ubuntu (Linux) firewall is called IP tables and is included with your Ubuntu installation.

The default settings are permissive (meaning they allow all traffic) and, if you are not running a server, you may feel this is adequate protection.

If you would like to configure your firewall the two options are to use a gui front end or write IP rules for yourself (there are various scripts on the web that will help with this).

The most popular gui tools are Firestarter and Guard dog (KDE). Keep in mind that these applications are not firewalls, but rather configuration tools. This is sometimes a source of confusion as the application should be run *only to configure your firewall*. Once configured, IP tables (the actual firewall) is active (at boot) *without having to run firestarter/guarddog*. firestarter will monitor traffic, but it runs as root and there are better monitoring programs, so configure you firewall, shut down firestarter/grauddog, and let IP tables do the rest :twisted:.

See these links for further information/how to use these tools :

[center][[color=red][Size=6]How to Firestarter[/size][/color]](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html) - [[color=blue][size=6]How to Guard Dog (KDE)[/size][/color]](http://www.simonzone.com/software/guarddog/manual2/index.html)[/center]

Firestarter Home Page : [http://www.fs-security.com/](http://www.fs-security.com/)

**Default Firestarter Policies**:
> [list][*]New inbound connections from the Internet to the firewall or client hosts are blocked.
[*]The firewall host is freely allowed to establish new connections.
[*]All client hosts are allowed to establish new connections to the Internet, but not to the firewall host.
[*]Traffic from the Internet in response to connection requests from the firewall or client hosts is allowed back in through the firewall.[/list]

If you would like to learn more about IP tables, here are some starting points:

_**Iptables references_** :
[list][*][https://help.ubuntu.com/community/IptablesHowTo](https://help.ubuntu.com/community/IptablesHowTo)
[*][http://www.linuxguruz.com/iptables/howto/](http://www.linuxguruz.com/iptables/howto/)
[*][http://iptables-tutorial.frozentux.net/iptables-tutorial.html](http://iptables-tutorial.frozentux.net/iptables-tutorial.html)[/list][/quote]

---

### Post by xpod on 2007-10-12
You only really need firestarter *if* you plan on opening ports for whatever types of services etc.
If you have no intention of opening ports then you really dont need it.It`s handy for ics and one or two other things too mind you,which i use it for myself but i *never* leave firestarter running.

It`s only really for us mortals who dont know our way round iptables well enough.:)

If your in the USA then there are issues with all the codecs and what not but thats entirely your decison.
You can install them all ...including java,flash,dvd & mp3 etc by installing the Ubuntu restricted package in add/remove or synaptic

The last i`m not sure about,thats info thats available to any site you connect to as far as i know.
If you dont want a site knowing your details.....dont connect to it:wink:

I still remember panacking last year when i first ever seen those little images in peoples sig`s etc declaring your system & browser etc.:)

---

### Post by xpod on 2007-10-12
> Yes and no ...

Stop it you...your just confusing me again:lolflag:

---

### Post by helane on 2007-10-12
oh well i understood from this website [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html) that i was supposed to run firestarter all the time (in the startup)...so i did. they should write a different instruction for women. mind you there is not too many women using  linux anyways so... ;)

regarding the drivers... i am in canada. is it different than us?

h.

---

### Post by bodhi.zazen on 2007-10-12
> **helane said:**
> oh well i understood from this website [http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html](http://www.debianadmin.com/secure-ubuntu-desktop-using-firestarter-firewall.html) that i was supposed to run firestarter all the time (in the startup)...so i did. they should write a different instruction for women. mind you there is not too many women using  linux anyways so... ;)

regarding the drivers... i am in canada. is it different than us?

h.

I do not know why that link advised to run Firestarter that way, my guess is that either the author does not understand ip tables or I do not understand Firestarter :rolleyes:.

Seriously, firestarter is NOT the firewall, is a configuration tool and most people advise you do not run it all the time, but only if you need to configure your firewall.

Also, women are very much active and welcome on the Ubuntu forums. Have you seen this : [http://ubuntuforums.org/forumdisplay.php?f=76](http://ubuntuforums.org/forumdisplay.php?f=76)

@ipod : Good to see you m8

---

### Post by whiteraven on 2007-10-13
> Your firewall is ip tables. IP tables is running, as configured by firestarter, at boot, so nothing to do. You should not run firestarter to moonitor trafffic as it is being run as root.

One way to confirn what bodhi.zazen said is to head on over to [_grc.com_]("http://www.grc.com") and run the Shields Up! test without starting Firestarter. You'll see that all the ports are either closed or stealth.

---

### Post by helane on 2007-10-13
well it was a joke... :) i know there is a significant group of women interested in computers and alternative systems. mind you, creating a special part of ubuntu forums - for women, might be perceived as a bit sexist by some female members. :)

well, regarding firewall - i turned off the firestarter and yes u r right - the shields up website shows everything as stealth. 

i figured out that the firefox is showing all the info about my computer... how is security for this browser? is there any way to prevent it from giving information away?

h.

---

### Post by whiteraven on 2007-10-13
> i figured out that the firefox is showing all the info about my computer... how is security for this browser? is there any way to prevent it from giving information away?

If you are concerned about what Firefox is telling others, you might want to consider installing one or more of the Privacy & Security add-ons from the [_Firefox Add-ons site_]("https://addons.mozilla.org/en-US/firefox/browse/type:1/cat:12") or search [_Google_]("http://www.google.com/") for a free proxy service.

---

### Post by xpod on 2007-10-13
> @ipod : Good to see you m8
__________________

Here you .....less o the ipod:)

Could be worse i suppose....you could be calling me [Spod](http://www.penddraig.co.uk/pen/tests/spod.htm):lolflag:

> well it was a joke...  i know there is a significant group of women interested in computers and alternative systems. mind you, creating a special part of ubuntu forums - for women, might be perceived as a bit sexist by some female members. 

If at least some *did`nt* complain *then* i`d be worried there was something wrong.:wink:
I`m actually outnumbered by the little Ubuntu using women here at home so i better tread carefully eh.

---

### Post by NotTheMessiah on 2007-10-13
You can install TOR and PRIVOXY(read about it before you decide to use it) and there is a  Fire Fox add-on called User Agent Switcher

---

### Post by helane on 2008-03-09
thank you all for your help. figured it all out but was away for a while so was not posting...

---

