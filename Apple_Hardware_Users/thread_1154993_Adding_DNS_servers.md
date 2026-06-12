---
title: "Adding DNS servers"
date: 2009-05-10
forum: Apple Hardware Users
---

### Post by Benboom on 2009-05-10
At the moment I'm running Opera 9.64 on a Mac Power PC under Ubuntu 9.04. It works fine except that Opera waits before loading a web page - it's ten seconds or so for each page. I had the same problem on the Mac at first and solved it by adding these DNS servers:

220.67.222.222
220.67.220.220

Do I need to do this in Ubuntu 9.04 as well? I'm not crazy about this as a fix because it messes up a few minor things for other browsers, but the worst part is I can't even FIND where to add it in 9.04! If I go into System>Prefs>Network Connections I can't find any place to add the servers. I did this in Ubuntu 6.10 because Opera just seems to need this to function quickly and I was able to find the appropriate pane easily but at the moment I'm stumped.

Thanks in advance.

---

### Post by Benboom on 2009-05-10
I was able to add the DNS servers thanks to some help from the Opera forum:
-------------
[B]I always use the OpenDNS servers in all Linux distros.
In Ubuntu (including 9.04) you have to edit /etc/dhcp3/dhclient.conf and add this line
prepend domain-name-servers 208.67.222.222, 208.67.220.220;

under the existing line
#prepend domain-name-servers 127.0.0.1;[/B]
-------------

I did that and rebooted and Opera loads sites quickly now. However, Firefox and other browsers no longer take me to domains unless I type in the www. and .com (or .org) pre- and suffixes, and now if I want to change the setting of my DSL modem I have to go through the whole procedure again and comment out the added lines.

In OS X you can just do this in the Network>Ethernet Preferences and apply your changes directly without having to restart or logout. And in fact, I could do this in 6.10 too. Am I missing some prefs pane somewhere or is this not possible anymore?

---

### Post by stream303 on 2009-05-10
The best place to put both of those dns server addresses are **inside your router** if you are using one, rather than having to manually configure it on the box itself.

At the opendns website, they have instructions at the bottom showing you how to do this for most of the more common routers in use.

This helps bypass the router's internal dns-forwarder, which in some instances, are not tuned properly for Linux - so putting those addresses inside the router setup is the best bet.

AND, by doing that you will never have to muck about with reconfiguring dhcpclient configs again.

---

### Post by Benboom on 2009-05-10
I didn't know that. Would that have any adverse effect on the Mac side of things outside of Opera?

---

### Post by stream303 on 2009-05-10
No problem - that is the beautiful thing - it will work just fine with your other windows or mac boxes just fine.

Years ago, the router's internal dns-forwarders in some cases weren't exactly following the published internet standards, and were tuned solely for Windows and Mac use.  Thus the typical problem of having very slow url resolution with Linux, and no problems with Windows or Mac.

Putting those primary and backup dns addresses in the router was the solution.  Note that it doesn't HAVE to be opendns addresses - you could just as easily stick to your known isp's dns server.

What fooled many was that they assumed the typical private address seen in their /etc/resolv.conf (something like 192.168.1.x) was actually the address of the router's internal dns forwarder, with no hint as to what the real isp dns addresses were.

**IMPORTANT** after putting those new dns primary and backup server addresses in either your router or modem, be sure to either restart networking on your box, or just simply reboot them.

Now that the dns issue is fixed, you may still have other issues if the gear is old - like ipv6 also not being fully supported correctly in the router rather than ipv4 - but some confuse the dns and ipv6 issue sometimes.  Some have BOTH problems. :)

**SECURITY ISSUE** - because dns is a big security issue, nobody should go blindly poking in the addresses seen here or elsewhere - these addresses are easily changed in caches etc, so VERIFY what is recommended (in this case actually go to the bottom right of the opendns website page) or verify your own addresses by getting in contact with the isp etc.

---

### Post by Benboom on 2009-05-10
Okay, I tried it out and it seems to work; no problems adding the servers to the modem prefs - the online help for my modem was very useful. I had to take the servers out of the Mac Network Prefs in order to access the modem, but since they're now stored in the modem itself that's fine. So far, everything is working; I'm on my Mac (OS X) right now using Firefox (and remembering why I never use Firefox on the Mac - wow, it's so much nicer on the linux box). Getting this page to let me log in took a while but I have no idea if that was the DNS stuff or just Firefox, which I don't normally use.

I thank you for your help once again. I ran the Live Ubuntu CD in this faster Mac and enjoyed it so much I'm thinking new thoughts. :D

---

### Post by Benboom on 2009-05-11
Update: although I added the DNS servers to the modem's prefs and it appeared to work at first I noticed today that it wasn't working. Firefox would load sites quickly but Opera would not. Finally, I rebooted into OS X and checked Opera's behavior (I still had the DNS servers enabled in OS X Network Ethernet Prefs) and it loaded quickly again. So I went back to Ubuntu and added the servers back into the .conf file again, rebooted, and now Opera is loading the sites without the horrible pause again. I guess Opera needs to be told by the computer where to look...but I have no idea why it seemed to work yesterday with just the modem settings enabled. Maybe I imagined it out of sheer hopefulness. :D

---

### Post by stream303 on 2009-05-11
That's odd behavior indeed for Opera on Linux.  Good to hear that it is working ok all around elsewhere. :)

At this stage, it isn't really ppc-specific, so perhaps the networking forum can pin it down in more detail for why Opera exhibits this behavior when your /etc/resolv.conf is just peachy when the dns addresses are defined in the modem/router instead of in the network config.

Opera's own internal dns-cache maybe?  Don't know why since the addresses are the same.  Good question for research on this end too.

---

### Post by Benboom on 2009-05-12
You might be better off to post this as a new thread so people who have already read this one will check it out.

---

