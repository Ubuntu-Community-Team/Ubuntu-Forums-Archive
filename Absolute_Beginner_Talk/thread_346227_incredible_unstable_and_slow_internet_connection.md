---
title: "incredible unstable and slow internet connection"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by b9anders on 2007-01-25
I am having a problem with Xubuntu, which has persisted ever since I did this installation - my internet connection is generally incredibly slow and unstable. 

Often it will disappear entirely, then pop back for a measily couple of hundred bytes per second, before nodging up to a more acceptable speed for a few minutes. Any suggestions as to what could be causing this and what I can do to rectify it?

---

### Post by budgie9 on 2007-01-25
You may find you will get some respose if you give a little more detail as to your equipment, modem, speed expected, Ubuntu version etc. for others to help you. Your message is some what vague.

---

### Post by hyper_ch on 2007-01-25
Do you have a router and if so, does it support IPV6?

---

### Post by r4ik on 2007-01-25
Try option 2 and ipv6 from this howto (doesnt come easy sorry)
Credits go to stream303

HOWTO: fix browsing problems with common routers
A quick summary on how to fix the most common dns issues when using dhcp behind an inexpensive router and why editing /etc/resolv.conf manually doesn't work for very long:

When manually adding a nameserver to /etc/resolv.conf, it is only a temporary solution since dhclient (actually dhclient-script) overwrites this file on re-lease or reboot. This only happens when using dhcp. Thus manually editing resolv.conf might only be useful during a "live-cd" session or when you are running a static ip.

Various tricks like changing the permissions of resolv.conf eventually fail because dhclient runs as root and overwrites it. Other tricks like making the file immutable (using chattr) are also not recommended.

Of course one could always run static where nothing overwrites resolv.conf, but the following is what I recommend for the anyone behind an inexpensive router running dhcp when they only see their router's dns server (actually a dns forwarder masquerading as a dns server in many cases) in resolv.conf. Typically this is a private-ip address such as 172.16.0.254 etc.

Option 1: place your isp's primary and backup dns server addresses in the router setup page.

Option 2: Uncomment and edit (as root, ie sudo nano) the PREPEND line of /etc/dhcp3/dhclient.conf and place your isp's dns nameserver(s) there. In the case of multiple nameservers, be sure to separate them with a comma, and end the line with a semicolon;

Option 3: Edit (as root) dhclient-script and remove all the commands in the mk_resolv.conf{} function so your edited resolv.conf won't be overwritten. Not recommended as option 1 or 2 usually suffices and many of us (myself included) can mess up the edit.

After applying one of these fixes, you should bring your interface down and up again, or maybe the easiest is to just reboot.

example:
Code:

sudo ifdown eth0 sudo ifup eth0

IPV6 - even after all this, sometimes our inexpensive hardware may have trouble with IPV6. Normally I don't recommend disabling it, but if you feel you should, you can disable it globally by creating a file titled "bad_list" in /etc/modprobe.d directory. bad_list can contain just this line:

alias net-pf-10 off

UPDATE: the above technique used to work, but now thanks to dbott67, the following is what works to disable ipv6 on my system:

Code:

sudo -s echo "blacklist ipv6" > /etc/modprobe.d/blacklist-ipv6 exit

You can test to see if IPV6 has been disabled by running

Code:

ip a | grep inet6

If there is no output from this command, (after you have cycled your interface, or rebooted) you are good to go. Lately I just run ifconfig and see if any inet6 addresses show up on my interface after rebooting. Not elegant I know...

You can also disable IPV6 in Firefox by entering

about:config

in the url bar. Once the configurations are found, in the filter bar, search for IPV6. Once found, doubleclick the search result to change the boolean value from false to true. Restart Firefox.

Tip: When you purchase a router, make sure to check the router configuration to be sure it doesn't have the same ip address as your modem.

Good luck !

---

### Post by manokaran on 2007-01-26
I too had similar problems. With Edgy Eft though. Please check this thread. It might help:

[http://ubuntuforums.org/showthread.php?t=346836](http://ubuntuforums.org/showthread.php?t=346836)

regds,
mano

---

