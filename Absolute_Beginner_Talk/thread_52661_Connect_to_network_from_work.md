---
title: "Connect to network from work???"
date: 2005-07-28
forum: Absolute Beginner Talk
---

### Post by larrinh on 2005-07-28
I have recently installed ubuntu on my XP laptop and I would like to know how to configure it to log on to the network at work so that I can access the internet and browse the network drives?

Can I get all of the necessary  information while logged into XP and enter it into ubuntu?

---

### Post by MikeyXX on 2005-07-28
[QUOTE=larrinh]I have recently installed ubuntu on my XP laptop and I would like to know how to configure it to log on to the network at work so that I can access the internet and browse the network drives?

Can I get all of the necessary  information while logged into XP and enter it into ubuntu?[/QUOTE]
 It depends on your network settings. When you log into XP do you put a user and password in and a domain? Or is there an advanced box under the login box? It MAY require domain authentication before you can get OUT of the network to surf the web. Then go into IE and under TOOLS, INTERNET OPTIONS and CONNECTIONS you can click LAN SETTINGS and see if there is a check box for the proxy. If there is, go to ADVANCED and mimick these settings in Firefox (or whatever) under EDIT, PREFERENCES, GENERAL, and the CONNECTION SETTINGS button.

Be careful, some big companies have policies explicitly indicating that putting a personal laptop on their network can get you fired/written up.

---

### Post by larrinh on 2005-07-29
When I log into the network using XP I enter:

Username: my username
Password:  my password
Log on to:  ESWH  ( I assume this is our local domain)

Where do I enter the domain when I log in using ubuntu?

---

### Post by odin on 2005-07-29
try this [http://www.ubuntuguide.org/#changecomputerdomainworkgroup](http://www.ubuntuguide.org/#changecomputerdomainworkgroup)

---

### Post by WirelessMike on 2005-07-29
I would assume you'd have to access a port through your employer's network firewall (the vast majority have one, so I assume yours does, too).

This can be done one of 2 ways--  Either dialup using a specific access number given you by your employer and enter the username/password supplied, or use vpn software (I use cisco vpn) to access over broadband (cable or dsl).

I, for example, access my employer's network from home using cisco vpn supplied by my employer for that specific purpose.

***EDIT***

Nevermind--  I see now you're at work trying to connect, so you don't have firewall issues.  That leaves only ip issues, which you are obviously on the road to working around.

***/EDIT***

---

