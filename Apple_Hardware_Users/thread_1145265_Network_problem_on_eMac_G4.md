---
title: "Network problem on eMac G4"
date: 2009-05-01
forum: Apple Hardware Users
---

### Post by Omega234 on 2009-05-01
So I'm trying to set up an Ubuntu server at my school for an in-class project.  I got the PowerPC version of 8.10, and it installed just fine.  However, the problem is that network access isn't working.  Here's what I have so far:

In **/etc/network/interfaces**:
```
auto lo
iface lo inet loopback

auto eth0
iface eth0 inet static
     address 163.248.121.106
     netmask 255.255.255.0
     network 163.248.225.0
     broadcast 163.248.121.255
     gateway 163.248.225.1
```

in **/etc/resolv.conf**:
```
nameserver 163.248.25.136
nameserver 205.124.254.2
```

It looks weird, I know, but here's what another Mac on the network gives me in the Network section of System Preferences:

```
IP Address: 163.248.121.103
Subnet Mask: 255.255.255.0
Router: 163.248.225.1
DNS Server: 205.124.254.2
Search Domains: 163.248.25.136, 205.124.254.2
```

And there's no HTTP proxy either.

When I run ```
/etc/init.d/networking restart
```, I get:

```
 * Reconfiguring network interfaces...
SIOCADDRT: No such process
Failed to bring up eth0.
     [ OK ]
```

Any ideas or suggestions?  Thanks in advance for anything.

---

### Post by Omega234 on 2009-05-03
Normally I wouldn't bump a topic like this, but it's for school and an answer would be most appreciated by Monday (tomorrow).  If I should post any more information, please just say so, but I've got nothing to go on right now.  Any ideas?

---

### Post by tiresia on 2009-05-03
Just a very short remark. Shouldn't your broadcast look so? 
163.248.225.255

Here a (maybe) useful link
[http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/](http://www.cyberciti.biz/faq/setting-up-an-network-interfaces-file/)

---

### Post by stream303 on 2009-05-03
And, this is not really specific to PPC, although we're happy to help if we can.

For quicker results, you may want to post this problem in the networking forum, since at this stage the machine architecture doesn't matter.

There is no need for mentioning PPC or the machine type, as this *might* lead some to believe that it is an apple hardware problem, and not just a generic networking issue. :)

---

### Post by Omega234 on 2009-05-03
@tiresia:
Thanks!  I'll have to try that when I get back tomorrow.

@stream303:
If tiresia's suggestion doesn't work out, I'll be sure to do that.  I didn't realize it was more likely a networking issue... should have thought of that.  Oh, well.  Thanks for the input!

---

### Post by stream303 on 2009-05-03
If I could make a suggestion - I'd avoid 8.10 Intrepid on PPC, especially for school since it has known application launching issues.

I'd hate to see you get all your networking worked out, and then run into this mind-numbing problem after all is said and done.

I think that Hardy 8.04 LTS would be your best bet, unless you absolutely needed what is in the latest Jaunty 9.04.

---

### Post by Omega234 on 2009-05-03
If there's nothing particularly pressing about upgrading to 9.04 (aside from a great reason to use "Jackalope" in everyday speech), I guess I'll just go with 8.04.

If I go with 8.04, couldn't I still upgrade to 9.04 for everything except drivers and stuff, or should I just refrain from that?

---

### Post by Omega234 on 2009-05-04
Just an update.  I freshly installed 8.04.1, and while manually configuring the network during installation, discovered that Ubuntu didn't like having an IP address not in the same range as the router.  Meaning that I was trying to use 163.248.121.105 with a router at 163.248.225.1, which I guess Ubuntu didn't agree with.  So I changed the IP address, and it's all working great now!

Thanks for the suggestions - I'm all happy!

---

### Post by stream303 on 2009-05-04
Hey that's great - glad to hear it is working out!

For me, I've found that doing a totally fresh install rather than upgrading, especially with ppc, is the way to go.  Others have had success, so you'll have to decide for yourself.

You could stick to Hardy 8.04.x and perhaps enable the "backports" repository rather than do an upgrade and see if that will suit your needs.

If you are in an uncontrolled environment, and need to quickly reinstall, a total disk backup might be in order.  Or, perhaps install APTONCD, which will allow you to easily make backups of all your downloaded packages, and then if worse comes to worse, you can reinstall with the original disk, and then use the aptoncd disk afterwards to quickly reinstall those updated packages without having to download them all again.  This is just one option - there are plenty more...

Just keep it fun!

---

