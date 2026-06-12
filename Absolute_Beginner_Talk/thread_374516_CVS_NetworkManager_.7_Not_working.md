---
title: "CVS NetworkManager .7 Not working"
date: 2007-03-02
forum: Absolute Beginner Talk
---

### Post by theonlyrealperson on 2007-03-02
Hello everyone, I'm a complete noob to Linux, and I love my Ubuntu. I need LEAP wifi access for school, so I installed CVS NetworkManager .70 using the wonderful .debs Mischa posted in the HowTo. I'm using Ubuntu 6.06 on a IBM T-42p, with a Intel internal wireless. The wireless driver is ipw2200, which from what I can tell is the correct driver for that wireless card. My wireless works (other than with NetworkManager).

The problem is, I can't get NetworkManager to pick up any wireless signals, or to connect to any. I've tried everything I can find in the forums and on the net. Using Synaptic I've completely uninstalled Wifi-Radar (including the config files), and I've changed my /etc/network/interfaces to this:
> # This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback

And that didn't help. Any more ideas? The gnome-icon thingy just has a "!" on it, and when I click on the NetworkManager icon it never lists any wireless networks. In testing it, I couldn't get it to connect to even unencrypted systems. (although it does break any connections I might have!)

Thanks!

---

### Post by robbie75 on 2007-03-02
As far as I know after I took a look
to feisty, there's a difference between
nm in dapper and the one in feisty/edgy:
for dapper it's necessary to remove every
interface instance from /etc/network/interfaces, or
to disable them from the network-admin panel;
edgy and feisty, on the contrary, benefit of a better 
integration of network-manager into gnome so you have to
enable network interfaces in order to manage them
by nm-applet.
HTH ;-)

p.s.
can you point me to the svn .deb of nm for dapper?

---

### Post by theonlyrealperson on 2007-03-02
Hmmm, ok. Well, I did comment everything out... So I should look to upgrade to Edgy in order for it to work? Dang, I really wanted to stick with ultra stable stuff. I was going to wait until Feisty went into release stage. Oh well, I'll give Edgy a try.

Here's where the .debs are, they're attached to the bottom of the first post:

[http://www.ubuntuforums.org/showthread.php?t=235655]("http://www.ubuntuforums.org/showthread.php?t=235655")

---

### Post by theonlyrealperson on 2007-03-02
ARGH! I updated to Edgy, and i still have the same problem.

What am I doing wrong?!?!?!?!? :confused: :confused:

---

### Post by robbie75 on 2007-03-03
I'm sorry for your troubles in getting 
wireless working so now I try to be as clearest
as possible to help you :)

I meant: if you're on dapper you have to disable
network interfaces from network-admin and into
/etc/network/interfaces, while, if you're on edgy/feisty
you have to do the contrary since network-manager
is now very well integrated into gnome.
But that's correct if you're using the packages from upstream,
while, since the latest network-manager behaves a little different
maybe that once installed the new version on dapper you have
to set it up as you were on edgy/feisty.

However, I'm on dapper with an intel internal wireless card
(centrino, ipw2100) and network-manager (the one from
upstream) is working flawlessly even with wpa/wpa2...

Some time ago I tried to compile nm from cvs but I had to give up
since I found a dependecy on the new dbus and didn't want
to upgrade all that stuff on my stable dapper....then I found
unofficial plugins for nm on dapper for vpn and so on.

But your first problem here is to make nm manage your wireless
card so, since you're now on edgy (that's not too bad anyway ;) )
you should set it up so: enable your wireless interface from
the gnome-network-admin and restart nm and finally you should
be able to manage it from the systray applet.
Take a look to syslog to discover what's happening while restarting
nm, and if you're still out of luck, please post your syslog ;)
good luck
Rob

---

### Post by theonlyrealperson on 2007-03-04
Ok, I'm back to square one, literally. The upgrade to Edgy broke a lot of other things - and I still couldn't get my NetworkManager to work. So, I Re-installed Dapper, and I've just finished system upgrading that again and such.

I don't know, I'm going to try another way to work with LEAP.

Thanks though!

Or, I'll just wait it out. I'm graduating in May - and I won't have any more reason (that I can see, at least) to use LEAP!

---

### Post by robbie75 on 2007-03-05
Can you post what's up in your syslog during
the execution of network-manager?

Are you able to, at least, see a list of the available wlans
from nm-applet dropdown?

Anyway there's a couples of  wlan manager you can try
in place of nm but you'd better off with nm so we can give it
another chance ;-)

Let me know.
Robbie

---

### Post by theonlyrealperson on 2007-03-05
Umm, I don't want to seem like a complete noob, but how do I find my syslog to post it? 

In the interim, I am on the LEAP network now by following these instructions:
[http://ubuntuforums.org/showthread.php?t=202834&highlight=LEAP](http://ubuntuforums.org/showthread.php?t=202834&highlight=LEAP)

So, I know it works!!! This is exciting, now I just want to make it a little user-friendly...

thanks!

---

### Post by robbie75 on 2007-03-06
simply type:
```
sudo tail -f -n 20 /var/log/syslog 
```

The -n param stands for how many lines "tail" has to display
from the input file.

Let me know ;)

---

### Post by theonlyrealperson on 2007-03-08
Ok, here is what I have in the syslog:

> Mar  8 00:21:36 localhost syslogd 1.4.1#17ubuntu7: restart.
Mar  8 00:21:36 localhost anacron[4855]: Job `cron.daily' terminated
Mar  8 00:21:36 localhost anacron[4855]: Normal exit (1 job run)
Mar  8 00:23:02 localhost gconfd (root-5948): starting (version 2.14.0), pid 5948 user 'root'
Mar  8 00:23:02 localhost gconfd (root-5948): Resolved address "xml:readonly:/etc/gconf/gconf.xml.mandatory" to a read-only configuration source at position 0
Mar  8 00:23:02 localhost gconfd (root-5948): Resolved address "xml:readwrite:/root/.gconf" to a writable configuration source at position 1
Mar  8 00:23:02 localhost gconfd (root-5948): Resolved address "xml:readonly:/etc/gconf/gconf.xml.defaults" to a read-only configuration source at position 2
Mar  8 00:23:02 localhost gconfd (root-5948): Resolved address "xml:readonly:/var/lib/gconf/debian.defaults" to a read-only configuration source at position 3
Mar  8 00:23:02 localhost gconfd (root-5948): Resolved address "xml:readonly:/var/lib/gconf/defaults" to a read-only configuration source at position 4
Mar  8 00:23:05 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Mar  8 00:23:07 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Mar  8 00:23:12 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 5
Mar  8 00:23:17 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 8
Mar  8 00:23:25 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 12
Mar  8 00:23:37 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 11
Mar  8 00:23:48 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 17
Mar  8 00:24:05 localhost dhclient: No DHCPOFFERS received.
Mar  8 00:24:05 localhost dhclient: No working leases in persistent database - sleeping.
Mar  8 00:24:32 localhost gconfd (root-5948): GConf server is not in use, shutting down.
Mar  8 00:24:32 localhost gconfd (root-5948): Exiting



To me, this doesn't look like it is even querying eth1. But, I'm not sure... I will have to say, that in order to post the syslog I had to hop back on the internet by re-enabling the device in the System Monitor. I hope that's not what this is showing. 

Even weirder, if I plug into eth0, NetworkManager works. It's only the wireless that it doesn't pick up. 

Any ideas? I really appreciate the help, Robbie.

Jeremy

---

### Post by robbie75 on 2007-03-08
Uhmmm actually, from what I can see in in your syslog
I have to say that nm is not working at all.
Now you're on Dapper, do you?
And, as far as I know the nm you are managing to get working
is the one from upstream (it should be v0.6.2) so in order to
make it monitoring your network interfaces you have to go to
system->network-admin and then, from the properties view of
each interface you have to uncheck the "enable this interface"
checkbox. Then restart network manager and, e.g. , if you plug
a cable you have to see something like this in your syslog:
```
Mar  8 21:39:24 localhost kernel: [17207268.932000] ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
Mar  8 21:39:24 localhost NetworkManager: <information>^IWill activate wired connection 'eth0' because it now has a link.
Mar  8 21:39:24 localhost NetworkManager: <information>^ISWITCH: no current connection, found better connection 'eth0'.
Mar  8 21:39:24 localhost NetworkManager: <information>^IWill activate connection 'eth0'.
Mar  8 21:39:24 localhost NetworkManager: <information>^IDevice eth0 activation scheduled...
Mar  8 21:39:24 localhost NetworkManager: <information>^Imatch
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) started...
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) scheduled...
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) started...
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) scheduled...
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 1 of 5 (Device Prepare) complete.
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) starting...
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) successful.
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) scheduled.
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 2 of 5 (Device Configure) complete.
Mar  8 21:39:24 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) started...
Mar  8 21:39:24 localhost NetworkManager: <information>^Imatch
Mar  8 21:39:24 localhost last message repeated 3 times
Mar  8 21:39:25 localhost NetworkManager: <information>^IActivation (eth0) Beginning DHCP transaction.
Mar  8 21:39:25 localhost NetworkManager: <information>^IActivation (eth0) Stage 3 of 5 (IP Configure Start) complete.
Mar  8 21:39:25 localhost NetworkManager: <information>^IDHCP daemon state is now 12 (successfully started) for interface eth0
Mar  8 21:39:26 localhost NetworkManager: <information>^IDHCP daemon state is now 1 (starting) for interface eth0
Mar  8 21:39:30 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 6
Mar  8 21:39:30 localhost dhclient: DHCPOFFER from 192.168.1.254
Mar  8 21:39:30 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Mar  8 21:39:30 localhost dhclient: DHCPNAK from 192.168.1.254
Mar  8 21:39:30 localhost dhclient: DHCPDISCOVER on eth0 to 255.255.255.255 port 67 interval 3
Mar  8 21:39:30 localhost dhclient: DHCPOFFER from 192.168.1.254
Mar  8 21:39:30 localhost dhclient: DHCPREQUEST on eth0 to 255.255.255.255 port 67
Mar  8 21:39:30 localhost dhclient: DHCPACK from 192.168.1.254
Mar  8 21:39:30 localhost NetworkManager: <information>^IDHCP daemon state is now 2 (bound) for interface eth0
Mar  8 21:39:30 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) scheduled...
Mar  8 21:39:30 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) started...
Mar  8 21:39:30 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar  8 21:39:30 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.domain_name
Mar  8 21:39:30 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar  8 21:39:30 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Mar  8 21:39:30 localhost NetworkManager: <information>^IRetrieved the following IP4 configuration from the DHCP daemon:
Mar  8 21:39:30 localhost NetworkManager: <information>^I  address 192.168.1.52
Mar  8 21:39:30 localhost NetworkManager: <information>^I  netmask 255.255.255.0
Mar  8 21:39:30 localhost NetworkManager: <information>^I  broadcast 255.255.255.255
Mar  8 21:39:30 localhost NetworkManager: <information>^I  gateway 192.168.1.254
Mar  8 21:39:30 localhost NetworkManager: <information>^I  nameserver 192.168.1.254
Mar  8 21:39:30 localhost NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar  8 21:39:30 localhost NetworkManager: <information>^IActivation (eth0) Stage 4 of 5 (IP Configure Get) complete.
Mar  8 21:39:30 localhost NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar  8 21:39:30 localhost dhclient: bound to 192.168.1.52 -- renewal in 37718 seconds.
Mar  8 21:39:31 localhost NetworkManager: <information>^IDHCP returned name servers but system has disabled dynamic modification!
Mar  8 21:39:31 localhost NetworkManager: <information>^IActivation (eth0) Finish handler scheduled.
Mar  8 21:39:31 localhost NetworkManager: <information>^IActivation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar  8 21:39:31 localhost NetworkManager: <information>^IActivation (eth0) successful, device activated.
Mar  8 21:39:31 localhost NetworkManager: <information>^Imatch
Mar  8 21:39:31 localhost last message repeated 2 times
Mar  8 21:39:31 localhost dnsmasq[22959]: reading /var/run/dnsmasq/resolv.conf
Mar  8 21:39:31 localhost dnsmasq[22959]: using nameserver 192.168.1.254#53
Mar  8 21:39:32 localhost ntpdate[28806]: step time server 82.211.81.145 offset -0.049323 sec
Mar  8 21:39:42 localhost kernel: [17207287.236000] eth0: no IPv6 routers present

```

The above is a complete execution of nm managing a wired connection ;)

Let me know.
Rob

---

### Post by theonlyrealperson on 2007-03-09
Ok, I did it the right way this time. I plugged in, reset everything and restarted "/etc/init.d/networking" and NetworkManager. Then I took the copied the log here.  I took out my ip addresses with stars, for privacy's sake.

This is what my syslog looks like:
> 
Mar  9 00:33:02 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.host_name
Mar  9 00:33:02 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_domain
Mar  9 00:33:02 localhost dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/eth0 for sub-path eth0.dbus.get.nis_servers
Mar  9 00:33:02 localhost NetworkManager: <info>  Retrieved the following IP4 configuration from the DHCP daemon:
Mar  9 00:33:02 localhost NetworkManager: <info>    address ***.***.*.***
Mar  9 00:33:02 localhost NetworkManager: <info>    netmask ***.***.***.*
Mar  9 00:33:02 localhost NetworkManager: <info>    broadcast ***.***.*.***
Mar  9 00:33:02 localhost NetworkManager: <info>    gateway ***.***.*.*
Mar  9 00:33:02 localhost NetworkManager: <info>    nameserver **.**.**.***
Mar  9 00:33:02 localhost NetworkManager: <info>    nameserver **.**.**.***
Mar  9 00:33:02 localhost NetworkManager: <info>    domain name '****************.'
Mar  9 00:33:02 localhost NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) scheduled...
Mar  9 00:33:02 localhost NetworkManager: <info>  Activation (eth0) Stage 4 of 5 (IP Configure Get) complete.
Mar  9 00:33:02 localhost NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) started...
Mar  9 00:33:02 localhost dhclient: bound to ***.***.**.*** -- renewal in 33707 seconds.
Mar  9 00:33:03 localhost NetworkManager: <info>  Activation (eth0) Finish handler scheduled.
Mar  9 00:33:03 localhost NetworkManager: <info>  Activation (eth0) Stage 5 of 5 (IP Configure Commit) complete.
Mar  9 00:33:03 localhost NetworkManager: <info>  Activation (eth0) successful, device activated.
Mar  9 00:33:09 localhost kernel: [17186985.068000] eth1: no IPv6 routers present
Mar  9 00:33:13 localhost kernel: [17186989.148000] eth0: no IPv6 routers present
Mar  9 00:36:05 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 3
Mar  9 00:36:08 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 5
Mar  9 00:36:13 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 13
Mar  9 00:36:26 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 10
Mar  9 00:36:36 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 17
Mar  9 00:36:53 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 9
Mar  9 00:37:02 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 4
Mar  9 00:37:06 localhost dhclient: No DHCPOFFERS received.
Mar  9 00:37:06 localhost dhclient: No working leases in persistent database - sleeping.
Mar  9 00:40:17 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 6
Mar  9 00:40:23 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 13
Mar  9 00:40:36 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 13
Mar  9 00:40:49 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 20
Mar  9 00:41:09 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 9
Mar  9 00:41:18 localhost dhclient: No DHCPOFFERS received.
Mar  9 00:41:18 localhost dhclient: No working leases in persistent database - sleeping.
Mar  9 00:46:49 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 8
Mar  9 00:46:57 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 8
Mar  9 00:47:05 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 15
Mar  9 00:47:20 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 8
Mar  9 00:47:28 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 12
Mar  9 00:47:40 localhost dhclient: DHCPDISCOVER on eth1 to ***.***.***.*** port 67 interval 10
Mar  9 00:47:50 localhost dhclient: No DHCPOFFERS received.
Mar  9 00:47:50 localhost dhclient: No working leases in persistent database - sleeping.



This is what my /etc/network/interfaces looks like:
> auto lo
iface lo inet loopback


My wireless driver is ipw2200, which came with the Dapper install. 

Thanks for all your help... :)

---

### Post by theonlyrealperson on 2007-03-12
bump - anyone?

---

### Post by robbie75 on 2007-03-13
Hi,
sorry for that lag.

looking at your log I can tell that nm is actually
managing only the wired connection (eth0) and not
eth1 which if I correctly recall is your wireless interface...

That's very strange since your interfaces file looks correct
to me....

---

### Post by theonlyrealperson on 2007-03-13
I know, grrr. All right, I'm going to uninstall the CVS version and install the repository version and see if I can get that working. I'll just have to keep manually changing 'interfaces' when I go to school until I figure this out. I'll let you know when I get the repository network manager installed and (hopefully!) working. 

Thanks for all your help!

---

### Post by compmodder26 on 2007-03-13
Perhaps I'm totally wrong here, but it's been my experience that NM will only allow you to connect to wireless if you aren't connected to a wired network.  Try unplugging your wired connection and see what happens.

---

### Post by theonlyrealperson on 2007-03-13
I think you are right, and I did try that. It just doesn't want to see eth1. I can't figure it out.

---

### Post by theonlyrealperson on 2007-03-14
All right, well, regular NetworkManager (from the repositories) works just fine... It's gotta be something with .7 and my computer then. 

Oh well, thanks for all the help!!!

---

### Post by robbie75 on 2007-03-14
No probl at all.
Glad you solved finally :)

Uhmm I was just thinking to upgrade my nm (now it's the
one from upstream) but after what I've heard from you I
don't know it that's a good choice...
Anyway, I was looking for the nm plugin for ppp dialer:
I'd like to connect to my vpns through my umts phone
by network-manager....

---

### Post by theonlyrealperson on 2007-03-14
Unfortuneately, my computer has a soft-modem - and I never used it very much anyway. I haven't gotten around to playing with it yet. There has got to be something out there though, NM controls the other two devices!

I'm intrigued by the idea of a NM-plugin, I wonder if I can find one of those for LEAP access, that would solve all my problems.

---

### Post by robbie75 on 2007-03-17
Check this out:
[http://compwiz18.blackhole.cx/wicd/wb/pages/features.php](http://compwiz18.blackhole.cx/wicd/wb/pages/features.php)
;)

---

### Post by theonlyrealperson on 2007-03-17
> **robbie75 said:**
> Check this out:
[http://compwiz18.blackhole.cx/wicd/wb/pages/features.php](http://compwiz18.blackhole.cx/wicd/wb/pages/features.php)
;)

HAHAHA! It's not pretty, but it's working well so far. Thanks! I'll know if it works on the LEAP system on Monday, when I go back to school. 

Wow, this is great. I really hope it works! Thanks a lot!!!! :)

---

### Post by theonlyrealperson on 2007-03-19
Well... It works great except for LEAP. I can't get on the university system with it. It states that it is "obtaining ip address" but then never connects. 

I guess I'll have to work with it a bit. It works for everything else though, so I'm happy so far!

---

