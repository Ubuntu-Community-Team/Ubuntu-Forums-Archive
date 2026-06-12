---
title: "can't connect to a VPN"
date: 2006-09-30
forum: Absolute Beginner Talk
---

### Post by _Dan on 2006-09-30
I tried as it says in the guide, here

[http://ubuntuguide.org/wiki/Dapper#How_to_Configure_and_start_PPTP_tunnels_.28VPN.29](http://ubuntuguide.org/wiki/Dapper#How_to_Configure_and_start_PPTP_tunnels_.28VPN.29)

but that didn't seem to work. The pptp log box said connection failed or something(?).

This is the help I have been given for connecting windows to this network:
[http://www.inf.aber.ac.uk/stunet/wired/wired-802.1x.asp](http://www.inf.aber.ac.uk/stunet/wired/wired-802.1x.asp)
(I post this link in case someone knows the linux equivilants!)

The "pptp" thing I think I remember said EAP or something was not supported??? and this thing seems to want it.

Can anyone suggest other packages to download and try? Perhaps that does support EAP? Note I need to download from windows so can't use apt or anything...

Another note: I can successfully access internal web pages from aber.ac.uk, but not external; this was the same with windows until I enabled VPN. (just to let you know the network is fine)

Thanks, and please help, then I will be able to do all work on linux and keep windows just for games!:KS

---

### Post by _Dan on 2006-10-01
:confused:

---

### Post by _Dan on 2006-10-02
I tried the pptp program troubleshooter and it said maybe there were no "GRE" messages or something. Looking at tcpdump I saw the words "dns1.aber.ac.uk" and "vpnserv.vpn.aber.ac.uk" (or something like that) so it seems *something* is happening.:-k

Also it's annoying how a lot of tutorials assume you have internet working... I get internet *through* the VPN. So I can't even search for other packages.

---

