---
title: "Install printer"
date: 2006-01-20
forum: Absolute Beginner Talk
---

### Post by marcha23 on 2006-01-20
Well I have linux alrady 24 hours ( after 7 years of windows )  and I wanted to instal my printer Samsung CLP - 500 ( which works great in windows ) So i trayed to install from cd a programm which allow to add printer in linux from printer cd. BUT it do not work : error after root pasword; I trayed to do it also manualy ( find ppd file from cd and add priner ), all is okey, the printer is detected, but nothing is printed!!
Well is it possible to instal it on ubuntu??

---

### Post by deNoobius on 2006-01-20
Yes, it is possible, LOL!!  I'm laughing because the same thing happened to me with the CLP 510.  I got the answer in this thread:

[http://www.ubuntuforums.org/showthread.php?t=92747](http://www.ubuntuforums.org/showthread.php?t=92747)

---

### Post by marcha23 on 2006-01-20
tell me then what i did wrong
I have still got this problem:

So I aded to file cupsd.conf and saved:

in front of AuthType Basic
                AuthClass System
#
and 3 lines :
AuthType None
AuthClass Anonymous
AuthGroupName lp
 then 
sudo /etc/init.d/cupsys restart

 then I have still to enter administrator pasword, and when I did happens the seme as before

---

### Post by deNoobius on 2006-01-20
Hmm...post the entire <Location> section of the cupsd.conf file here and I'll compare it to my working one when I get home.

---

### Post by marcha23 on 2006-01-20
UPS now I do not understend, I think there is a mistake I did something wrong
Better poste your version of file


# Locations are relative to DocumentRoot...
#
# AuthType: the authorization to use:
#
#    None   - Perform no authentication
#    Basic  - Perform authentication using the HTTP Basic method.
#    Digest - Perform authentication using the HTTP Digest method.
#
#    (Note: local certificate authentication can be substituted by
#           the client for Basic or Digest when connecting to the
#           localhost interface)
#
# AuthClass: the authorization class; currently only "Anonymous", "User",
# "System" (valid user belonging to group SystemGroup), and "Group"
# (valid user belonging to the specified group) are supported.
#
# AuthGroupName: the group name for "Group" authorization.
#
# Order: the order of Allow/Deny processing.
#
# Allow: allows access from the specified hostname, domain, IP address,
# network, or interface.
#
# Deny: denies access from the specified hostname, domain, IP address,
# network, or interface.
#
# Both "Allow" and "Deny" accept the following notations for addresses:
#
#     All
#     None
#     *.domain.com
#     .domain.com
#     host.domain.com
#     nnn.*
#     nnn.nnn.*
#     nnn.nnn.nnn.*
#     nnn.nnn.nnn.nnn
#     nnn.nnn.nnn.nnn/mm
#     nnn.nnn.nnn.nnn/mmm.mmm.mmm.mmm
#     @LOCAL
#     @IF(name)
#
# The host and domain address require that you enable hostname lookups
# with "HostNameLookups On" above.
#
# The @LOCAL address allows or denies from all non point-to-point
# interfaces.  For example, if you have a LAN and a dial-up link,
# @LOCAL could allow connections from the LAN but not from the dial-up
# link.  Similarly, the @IF(name) address allows or denies from the
# named network interface, e.g. @IF(eth0) under Linux.  Interfaces are
# refreshed automatically (no more than once every 60 seconds), so
# they can be used on dynamically-configured interfaces, e.g. PPP,
# 802.11, etc.
#
# Encryption: whether or not to use encryption; this depends on having
# the OpenSSL library linked into the CUPS library and scheduler.
#
# Possible values:
#
#     Always       - Always use encryption (SSL)
#     Never        - Never use encryption
#     Required     - Use TLS encryption upgrade
#     IfRequested  - Use encryption if the server requests it
#
# The default value is "IfRequested".
#

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

#<Location /classes>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

#<Location /classes/name>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

<Location /jobs>
#
# You may wish to limit access to job operations, either with Allow
# and Deny lines, or by requiring a username and password.
#
AuthType Basic
AuthClass User
</Location>

#<Location /printers>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

#<Location /printers/name>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#

## Anonymous access (default)
#AuthType None

## Require a username and password (Basic authentication)
#AuthType Basic
#AuthClass User

## Require a username and password (Digest/MD5 authentication)
#AuthType Digest
#AuthClass User

## Restrict access to local domain
#Order Deny,Allow
#Deny From All
#Allow From .mydomain.com
#</Location>

<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

#AuthType Basic
#AuthClass System

AuthType None
AuthClass Anonymous
AuthGroupName lp

## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1

#Encryption Required
</Location>

#
#

---

### Post by deNoobius on 2006-01-20
Sure, I'll do it when I get home, where my Ubuntu machine lives.  Also, I'll scan it and see if anything occurs to me about yours.

---

### Post by marcha23 on 2006-01-20
I changed the last lines
O sorry you are from US

---

### Post by deNoobius on 2006-01-20
[QUOTE=marcha23]I changed the last lines
O sorry you are from US[/QUOTE]

I see the lines, there's nothing obvious to me about why it isn't working.  I'll post again when I get home from work.

---

### Post by deNoobius on 2006-01-20
```
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.1.*
</Location>

#<Location /classes>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

#<Location /classes/name>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

<Location /jobs>
#
# You may wish to limit access to job operations, either with Allow
# and Deny lines, or by requiring a username and password.
#
AuthType Basic
AuthClass User
</Location>

#<Location /printers>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#
#</Location>

#<Location /printers/name>
#
# You may wish to limit access to printers and classes, either with Allow
# and Deny lines, or by requiring a username and password.
#

## Anonymous access (default)
#AuthType None

## Require a username and password (Basic authentication)
#AuthType Basic
#AuthClass User

## Require a username and password (Digest/MD5 authentication)
#AuthType Digest
#AuthClass User

## Restrict access to local domain
#Order Deny,Allow
#Deny From All
#Allow From .mydomain.com
#</Location>

<Location /admin>
#
# You definitely will want to limit access to the administration functions.
# The default configuration requires a local connection from a user who
# is a member of the system group to do any admin tasks.  You can change
# the group name using the SystemGroup directive.
#

#AuthType Basic
#AuthClass System
AuthType None
AuthClass Anonymous
AuthGroupName lp
## Restrict access to local domain
Order Deny,Allow
Deny From All
Allow From 127.0.0.1

#Encryption Required
</Location>

#
```

Here is the relevant portion from my file.  Let's both take a look.

---

### Post by deNoobius on 2006-01-20
OK, I see one thing.  I'm not sure this solves the installation problem, but you have to add the IP for your network or machine under the loopback 127.0.0.1.

# The default value is "IfRequested".
#

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 192.168.x.*
</Location>

---

### Post by marcha23 on 2006-01-20
I will check it later today it is just 5 am, but I was traying to do that for a local printer.
But did you managed to run linux-config. To log on on it?
IT all seems to be quit complicated.
It seems that will need to return back to windows, when I get my second pc back.

---

### Post by deNoobius on 2006-01-21
Yes, once you've made the change to the cupsd.conf file as discussed, running the printer config should just skip the logon and allow you to configure your printer.  

You might try running it from Gnome.  In my case, the printer configuration appears under Applications/Other.

---

