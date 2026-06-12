---
title: "Is There A Way To Do This Automatically?"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by darKStorm on 2008-02-21
After sorting out my wireless problem (being that I couldn't use my wireless card at all), I rebooted my PC, only to find out that Wireless connection settings had gone from Network (System -> Administration -> Network). However I fixed this by:
Going on to Restricted Drivers Manager (System -> Administration -> Restricted Drivers manager), disabling and then enabling the broadcom firmware, and when I do this it reconnects to my router... however, what I want to know is how to do this automatically, or even better, not need to do this?

  Thanks :D

---

### Post by r4ik on 2008-02-21
Try,



1. Open a terminal window and type the following.

    $ sudo network-admin

Note: Root access is required for this step.
2. Change to the DNS tab and enter the following two addresses in the top of the first field labeled DNS Servers.

    208.67.222.222
    208.67.220.220

To avoid having your settings get revoked after reboots, or after periods of inactivity, do this:

    $ sudo cp /etc/resolv.conf /etc/resolv.conf.auto
    $ sudo gedit /etc/dhcp3/dhclient.conf
    # append the following line to the document
    prepend domain-name-servers 208.67.222.222,208.67.220.220;
    # save and exit
    $ sudo ifdown eth0 && sudo ifup eth0 

You may be required to change eth0 to your own network device's name if it uses a non-standard name.

Best to put you're own Dns but this works for me.

From,

[https://www.opendns.com/start/ubuntu.php](https://www.opendns.com/start/ubuntu.php)

Good luck !

---

