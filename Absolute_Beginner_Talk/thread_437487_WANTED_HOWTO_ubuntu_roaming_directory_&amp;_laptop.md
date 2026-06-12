---
title: "WANTED: HOWTO ubuntu roaming directory &amp; laptop syncing"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by chillin on 2007-05-08
> **Network and Portable Home Directories**
You can also use Workgroup Manager to provide network-based home directories, so users can access their own personalized desktop, applications and files from any computer on the network — or use them to back up their work. With Mac OS X Server v10.4, PowerBook and iBook users can now enjoy synchronized versions of home directory folders locally and on the network. When a user goes offline, her home directory goes with her, so she can continue to work just as if she would back at the office. When she reconnects to the network, Mac OS X automatically syncs up selected content in her local home directory with the one on the server.
**Source:*** Apple's [OS X Server](http://www.apple.com/server/macosx/workgroupmanagement.html) page*


Can Ubuntu replace OS X Server for the purposes of 
[color=brown][size=+1]roaming directories[/size][/color]

[color=white].................[/color]AND 
[color=brown][size=+1]syncing laptops and desktops[/size][/color] 

(specifically for OS X client machines)?

Which Ubuntu flavor is recommended? What packages are necessary? How does it work?

*Please* show me the **HOWTO** !!

---

### Post by Qchan on 2007-05-08
[b][color=darkred]
You're looking for Stateless Linux
[http://fedoraproject.org/wiki/StatelessLinux](http://fedoraproject.org/wiki/StatelessLinux)

Here are a few HowTos as you requested.

[http://fedoraproject.org/wiki/StatelessLinuxHOWTO](http://fedoraproject.org/wiki/StatelessLinuxHOWTO)
[/b][/color]

---

### Post by chillin on 2007-05-08
Thank you for the reply.
Stateless linux is intriguing, but I'm not sure that's what I am looking for... I don't need to netboot, necessarily, and that is what the howtos you link to instruct.

In fact, I'd prefer a local system independent of the server. What I am looking for is a way to sync home directories between laptops and desktops, but also for a way to have roaming logins with the user directories following the user regardless of which client they log into, all integrated in and set up for an OS X client user environment. I don't see how stateless, in and of itself, is supposed to provide this. 

Maybe if you could describe in more detail just how stateless will do this... 

thanks

(in the mean time, I'll keep reading about stateless, just to makes sure, but what I need is incremental syncing)
-----

Found what I was looking for courtesy of the mad understanding and searching skills of Eudimorphodon (thanks man) and the very clever Greg Neagle.
For those interested, all the work's been done for us:
[[color=brown][size=+2]Portable Home Directories without Open Directory[/size][/color]](http://managingosx.wordpress.com/2006/03/15/portable-home-directories-without-open-directory/)

---

### Post by chillin on 2007-06-08
I've learned some more...

Open Directory (& Netinfo*) **is** [[color=brown]OpenLDAP[/color]](http://www.openldap.org/), but with Apple's gui. Active Directory is Microsoft's implementation of LDAP. Its all very confusing, but not at all confused. 
*Netinfo wasn't always LDAP, but at some point, Apple changed it to be LDAP.

---

