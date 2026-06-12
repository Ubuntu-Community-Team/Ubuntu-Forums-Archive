---
title: "setting-up dns &amp; apache."
date: 2007-05-19
forum: Absolute Beginner Talk
---

### Post by richard101 on 2007-05-19
Hi All

My internet router runs as a dhcp/dns server, but assigns a static ip-address to my webserver box (so all incoming HTTP requests are routed to a fixed ip-address).

I've a dyndns domain-name.

When I added Ubuntu 6.06 as a dual boot, connectivity became intermittent. Which I cured temporairly with 'sudo dhclient', then more permenently by putting my static details into /etc/network/interfaces.

Now I've installed Apache2 and saw a message about not being able to "... determine the fully qualified domain name".

Also, browsing locally to <hostname> shows a folder called "apache2-default" inside of which is the default web-page (I copied index.html.en to index.html).

QUESTIONS

I dont really want to put a static address into INTERFACES. I'd rather it asked my dns server/router and got the same info all the time (the Windows boot is set to get stuff from dhcp/dns). That way, all my local ip configurations are centralised (at the router).

Similarly, I want Apache to work more like IIS, and serve up a default web-page (IE: I don't want to have to put my dyndns domain-name into Apache - if thats truly what it's asking for??).

And lastly, why doesn't <hostname> show the default web-page?


(phew, perhaps I should invest in a good book :-) )

thanks in advance

richard101

---

### Post by VorDesigns on 2007-05-19
Hi,

Try reveiwing this [https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html]("https://help.ubuntu.com/6.10/ubuntu/serverguide/C/network-configuration.html") for your networking issues and name resolution.
Somewhere on the server guides or maybe it's the Postfix on Ruby Rails how-to I ran across last night, can't remember that has references for naming the server, fqdn naming the server, and network resolution steps.
I just wiped my test box or I would give the steps I took

You need to set the hostname, the fqdn name and then check it to make sure it works.  You need to edit your hosts file and a couple of other items.
When I finish starting over with mine, I may come back and update this for you.

Here's the Postfix document that has some good information for networking; not happy with the postfix/amavis etc., install but I will work around what I don't like.
[http://ubuntuforums.org/showthread.php?t=398866]("http://ubuntuforums.org/showthread.php?t=398866")

---

