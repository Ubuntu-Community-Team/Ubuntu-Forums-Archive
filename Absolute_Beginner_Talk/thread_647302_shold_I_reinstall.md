---
title: "shold I reinstall?"
date: 2007-12-22
forum: Absolute Beginner Talk
---

### Post by beanco on 2007-12-22
so I am having one very annoying problem and one smaller one

1:  [is this](http://ubuntuforums.org/showthread.php?t=644874&highlight=robi)

and

2:   [  is this](http://ubuntuforums.org/showthread.php?t=646773&highlight=robi)

Not having net access, other than loggin in remotely to my work places just sucks!

If I start from scratch will this all just happen again?

what could be causing such problems?

any ideas?

Thanks

Robi

---

### Post by beanco on 2007-12-22
I am now on line, using my connection at home and my wifes laptop.

it is a winblows machine but it is working.

i will try switching out the cable from the router to the machines... maybe the wire into my machine is causing problems.

will report back soon

robi

---

### Post by beanco on 2007-12-22
I switched otu teh wires... the laptop in windlbows works fine.

the box with ubuntu does not work still.

so i guess this means the router is not the problem...

it has to be a ubuntu setting i somehow messed up or a FF one.

would removing firefox help?

robi

---

### Post by laidback on 2007-12-22
Good luck.

---

### Post by laidback on 2007-12-22
I would check/recreate network connection from Ubuntu. I would remove what's there and start again. Perhaps run the wizard. Make sure you are using the correct connection type; DHCP or Static IP.

---

### Post by cub682 on 2007-12-22
I had to disable IPv6 to get mine working. I don't know if this is your problem but it may help.

[http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/](http://www.simonscullion.com/2007/11/20/ipv6-issues-with-ubuntu-710/)

---

### Post by bumanie on 2007-12-22
If you are using gutsy, I too suspect that ipv6 may well be your problem.
To disable ipv6 
gksudo gedit /etc/modprobe.d/blacklist
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine.
Another way is to diable ipv6 in firefox
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true

---

### Post by beanco on 2007-12-22
so there's a couple of option here.. i wil have to figure out which to try.

the ip address is static, not dhcp! I know that for sure.


IF that has any effect on what solution I try.


robi

edited to add... I think I am still on feisty fawn.. but have no iea how to check...there is no *about Ubuntu* option in the system menu!

---

### Post by beanco on 2007-12-22
oh, I forgot to say....

maybe it was not clear form my posts but everything had been working fine for a while... i had whatever version onf Ubuntu up and running and used th eNet daily, no probems....

the ony thing I have changed recently is I started to download lot sof stuff using kTorrent.

robi

---

### Post by beanco on 2007-12-22
> **bumanie said:**
> If you are using gutsy, I too suspect that ipv6 may well be your problem.
To disable ipv6 
gksudo gedit /etc/modprobe.d/blacklist
then add 
blacklist ipv6
at the bottom of the gedit list and save.
After reboot, all should work fine.
Another way is to diable ipv6 in firefox
Type about:config in your firefox address bar
Type "ipv6" in the filter 
Change the value of "network.dns.disableIPv6" to true


tried the firefox way, no luck.


robi

---

### Post by beanco on 2007-12-22
just started to try the method in the link provided by cube682


and got this

[HTML](gksudo:5348): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
(gedit:5349): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.

(gedit:5349): Gdk-WARNING **: locale not supported by C library

(gedit:5349): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.
[/HTML]

the aliases still opened in gedit but what does the stuff above ^^^^^ mean?

robi

---

### Post by beanco on 2007-12-22
and I am still on feisty if that makes any difference.

Thanks

Robi

---

### Post by laidback on 2007-12-24
To Blacklist ipv6 I took the attached from a previous forum post; and use it for myself.

$ sudo gedit /etc/modprobe.d/blacklist

type 'blacklist ipv6'     (without the quotes)

Save and exit

You're set

blacklist.bak is original

Is ipv6 Blacklisted? I also found this on the forum:-

Is ipv6 disabled?

$ip a | grep inet6

no output...then it is

---

### Post by bumanie on 2007-12-24
I think that as you are  using feisty, ipv6 should not be an issue.
I would not have suggested blacklisting ipv6 if I had known that (I did put 'if you are using gutsy). 
As far as I know there has never been an ipv6 issue with feisty. If I were you, I would not change any more ipv6 settings - it is likely that ipv6 is not your problem!
I have no idea what the output above means.

---

### Post by bumanie on 2007-12-24
I think you should look at this link, it may help you out.
[http://ubuntuforums.org/showthread.php?t=138022](http://ubuntuforums.org/showthread.php?t=138022)

---

