---
title: "Logging of remote syslog messages not working."
date: 2006-04-10
forum: Absolute Beginner Talk
---

### Post by marc_zw on 2006-04-10
Hi,

This is my first time using this forum so I am doing something wrong please let me know.  

I installed Ubuntu 5.10 for the first time only yesterday.  I have never used any version of *nix before so am learning as I go along.  I would like to setup a syslog server.  I have researched this endlessly and have attempted to get this working by myself but I have had no joy.  I also find it a little confusing with finding files that seem to be related in places that are not mentioned in anyones posts.  Let me clarify what I have done:

I edited the /etc/syslog.conf file and added the following entries:

local0.* /var/log/local/local0
local1.* /var/log/local/local1
local2.* /var/log/local/local2
local3.* /var/log/local/local3
local4.* /var/log/local/local4
local5.* /var/log/local/local5
local6.* /var/log/local/local6
local7.* /var/log/local/local7

As I understand it, this will instruct the syslog server where to store syslogs from a Cisco PIX Firewall.

I edited the startup script /etc/init.d/sysklogd and changed the following options:

SYSLOG="-u SYSLOG" to SYSLOG="-r"

As I understand it, this will enable the syslo server to listen for syslog messages across the network on UDP Port 514.

The problem is that there is no information being recorded in any of the logs.  Is there any way to test the configuration I have made?  Do I need to change any file or folder permissions to allow syslog messages to be written to the specified folder?  Or is it more likely the configuration of logging on the firewall is incorrect?

---

### Post by ubuntuuser on 2006-04-10
I can't help you with syslog itself, but when I wanted to do some content specific filtering of syslog messages, I found that syslog-ng was far more flexible, and the syntax of the config files is easier. I suggest you have a look at it. It's in the repositories.

---

### Post by steve.horsley on 2006-04-10
I can't easily test here, but I would think that instead of 
**SYSLOG="-r"**
your line should read:
**SYSLOGD="-r -u syslog"**
Note that case is important.
You will also need to restart the deamon with this command:
**sudo /etc/init.d/sysklogd restart**

---

### Post by marc_zw on 2006-04-10
Thanks for all the help guys.  Turns out there was a problem with the Firewall configuration.  One minor change and the logs started logging.  Now to setup Logrotate!

---

