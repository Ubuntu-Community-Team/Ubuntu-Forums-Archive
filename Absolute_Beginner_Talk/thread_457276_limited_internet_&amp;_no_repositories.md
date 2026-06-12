---
title: "limited internet &amp; no repositories"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by WhiteSphinx on 2007-05-28
This is a real weird problem.  I can access Google.com but I cannot access Yahoo.com.  From Google, I can only link to about 5% of the links on any given search page.  I do not have access to repositories (I get a "waiting for headers" message).  When I boot to Windows I have full internet access, but in Ubuntu I only have 5% internet access.  How do I fix this.  If I change the nameservers in /etc/resolv.conf to the OpenDNS nameservers, I cannot access the internet at all -- not even Google will come up.  If I try to prepend the nameservers with OpenDNS the same thing happens.  Disabling ipv6 does not work.  Can anyone suggest another solution? 

When I ping yahoo from the terminal all packets are sent and received but I cannot access yahoo from Firefox or from Swiftfox.

Add/Remove does not work

Synaptic does not work

---

### Post by sankarv on 2007-05-29
check the proxy settings anyway thats just an idea... there might be problem with ur network files. u could compare urs with sample files available in web...

---

### Post by WhiteSphinx on 2007-10-28
Okay this is too cool.  Problem solved.  This should work for anyone with an A33G PC Chips Motherboard or for anyone with an SiS190/191 ethernet.

First do this:

```
export EDITOR=gedit && sudo visudo
```

This will bring up the sudoers file.

Replace the following line (because of a bug)

> Defaults !lecture,tty_tickets,!fqdn

with:

> #Defaults !lecture,tty_tickets,!fqdn
Defaults !lecture,tty_tickets,!fqdn,env_keep+="DISPLAY HOME"

Add this line to the end of the sudoers file:

> username ALL=NOPASSWD: /sbin/ifconfig
Be sure to replace "username" with your own username.

Then open System>Preference>Sessions

Click Add

_N_ame > Configure LAN
_C_ommand > sudo ifconfig eth0 mtu 1492

Now you will be able to access the internet with you SiS190 Ethernet after you restart.

---

