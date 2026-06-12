---
title: "How do I configure syslog server"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by scantoria on 2007-01-11
I have Ubuntu version 6.0.6 installed. We have a firewall that has a feature to store event logs in a syslog server. I do not know what syslog is. I was informed by the firewall reseller that syslog is a native feature in linux. 

I know the ip address of the linux box but I do not know what port to use.

Thanks,

Steve C.

---

### Post by scantoria on 2007-01-18
For those that care to know. Here is what I've learned from other websites.

# Ubunto SysLog Setup
#
# Step 1
# Stop syslog service 
/etc/init.d/sysklogd stop

# Step 2
# Ubuntu/Debian:
# Open /etc/init.d/sysklogd with your favorite text editor
# Find the line:
SYSLOGD="-u syslog"

# Replace with
SYSLOGD="-ru syslog"

# Restart the syslog deamon
/etc/init.d/sysklogd restart

tail /var/log/messages

# Step 3 (final step)
iptables -I INPUT -p udp -i eth0 -s 10.31.10.120 -d 10.31.10.2 --dport 514 -j ACCEPT

Thanks,
Steve C.
Director of IT

aim:scantoria

---

### Post by Moldz on 2007-01-18
I'm confused, did you say firewall reseller?  It looks like you are just using syslog and netfilter, two standard and freely available pieces of software.  Why did you have to buy it?

---

### Post by smaug9 on 2008-01-24
I found that changing /etc/init.d/sysklogd for the "-r" didn't work.

I had to change it in /etc/default/syslogd.

It's also really slow, recving logs from an asa firewall. Any ideas?

-Jeff

---

### Post by The Cog on 2008-01-24
How do you mean, slow? 

You know that** tail -f** only polls the input file once a second, yes?

---

