---
title: "Firefox hangs 30 to 40 seconds before loading page"
date: 2007-06-22
forum: Absolute Beginner Talk
---

### Post by gasnmyveins on 2007-06-22
6.06LTS 3meg DSL  connected to router with ethernet cord, Windows laptop is connected wirelessly and functions properly. 

It hangs up for 30 to 40 seconds before loading most pages. It says "Looking up www.whatever" I've still got my bandwidth when I do a download. I get at least 200k download speed. Everthing worked fine in windows before I switched. Any ideas? Thanks.

---

### Post by Quintin Riis on 2007-06-22
Probably a problem with your internet provider.  Try disabling ipv6, see if that helps.


Type "about:config" in the Firefox address bar.  

Filter by "IPv6"

Change the value for "network.dns.disableIPv6" to true.

Open /etc/modprobe.d/aliases in a text editor.  

Find "alias net-pf-10 ipv6", change it to "alias net-pf-10 off".

Do /etc/init.d/networking restart, or reboot.

HTH

---

### Post by gasnmyveins on 2007-06-22
If it was a problem with my provider, Shouldn't I be seeing the same thing with the windows laptop? It's working fine. Also, the tower (with firefox) worked fine before I switched to Ubuntu. The only thing that has changed is my OS.

 Do the things you are suggesting change settings in my computer or in my router? 

 Thanks.

---

### Post by Seisen on 2007-06-22
Are you running tor and running through a proxy?

---

### Post by Quintin Riis on 2007-06-22
Those commands only affect the local machine, if that is not obvious.  Generally before you can mess with a router you have to authenticate somehow.

Unless you're using UPnP.  :popcorn:

---

### Post by gasnmyveins on 2007-06-22
Seisen: No proxies, just an ethernet cable to the router and a standard dsl connection after that. Nothing out of the ordinary.

 Quintin: Thanks for the clarification. I don't know a whole lot about computers yet. I've kind of decided to learn by doing. The problem is that I've just started the "doing" part, so there hasn't been much learning yet. I'll try your suggestions tomorrow and see what happens. Do you mind telling me what those things are intended to do?

 Thanks.

---

### Post by jayson.rowe on 2007-06-22
I had that problem in Ubuntu 6.10 (but not in 7.04), and also in Suse 10.2 (during my brief trial of it - lol - 1hr after install), try opendns ([http://www.opendns.com/](http://www.opendns.com/)) I'll bet it'll fix your problem.

---

