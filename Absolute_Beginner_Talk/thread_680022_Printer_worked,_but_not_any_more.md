---
title: "Printer worked, but not any more"
date: 2008-01-27
forum: Absolute Beginner Talk
---

### Post by daytimer045 on 2008-01-27
Slowly but surely plugging my way towards a working Gutsy file and print server.

First there was Ndiswrapper, then WPA, then a laptop display not functioning, then failure to wireless on bootup, then installing samba, then sharing an external HD with Vista.  All struggles, all solved with reference to the many excellent posts, and in some cases specific help from users!  Thank you, Thank you.  (I really wanted to give up, and just run a Windows XP file/print server, but three weeks into this, I can't give up).
[SIZE="3"]
[COLOR="Red"]The last challenge:  My printer.[/COLOR][/SIZE]


So when I plugged it in for the very first time.  It played.  Worked fine.  Printed test pages, and from Open Office.

Then I tried messing around with cupsys, thinking this the route to share my printer on the network.  Oh dear.  Because I thought I need to update the install I:

sudo apt-get install cupsys cupsys-client

It turned out that  I didn't have to..it was already installed with Gutsy server.  But i did notice tons of errors generated associated with scrollkeeper!

So I:

sudo apt-get autoremove cupsys cupsys-client

And I noticed the same scrollkeeper errors, though cupsys did get uninstalled.

I reinstalled it, with the same scrollkeeper errors.  And changed a few settings to get the [http://gutsybox:631](http://gutsybox:631) interface working.  It works!  But the printer doesn't now.

Using the gutsybox:631 or the GNOME printer interface I can even find my HP PSC 1210 printer attached to the USB, and I can add it as a new printer.  However when I print a test page (either from the GNOME interface or from the gutsybox:631 it just adds it to the queue and nothing prints).

Heck i can even add it as a new printer on Vista using the ip address:631/printers/psc_1200_series approach.  It finds it, but it won't print!

What went wrong......

How can I reset cupsys, or the state of my printer to before I started messing around.

---

### Post by angelot on 2008-01-28
I had some of the same problems (I belive it's the install/uninstall that gets the box confused).

You can try my howto. If it helps fine - if it don't just replace cupsd.conf with your backup og the server/klient...

It's actually a setup for sharing local printers on a network, but it might work....

1. Install gnome-cups-manager on both server and client.
sudo apt-get install gnome-cups-manager

2. Make a backup of cupsd.conf on both machines.
sudo cp /etc/cups/cupsd.conf /etc/cups/cupsd.conf-bak

3. Replace /etc/cups/cupsd.conf on server with:
```
ConfigFilePerm 0600
LogLevel info
Printcap /var/run/cups/printcap
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
BrowseAddress 10.0.0.0/8
BrowseAddress 172.16.0.0/12
BrowseAddress 192.168.0.0/16

AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 10.0.0.0/8
Allow From 172.16.0.0/12
Allow From 192.168.0.0/16

AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 10.0.0.0/8
Allow From 172.16.0.0/12
Allow From 192.168.0.0/16

AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 10.0.0.0/8
Allow From 172.16.0.0/12
Allow From 192.168.0.0/16

AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
Allow From 10.0.0.0/8
Allow From 172.16.0.0/12
Allow From 192.168.0.0/16
```
4. Replace /etc/cups/cupsd.conf on client with:
```
ConfigFilePerm 0600
LogLevel info
Printcap /var/run/cups/printcap
RunAsUser Yes
Port 631

Include cupsd-browsing.conf
BrowseOrder deny,allow
BrowseDeny from All
BrowseAllow from @LOCAL
BrowseAllow from 10.0.0.0/8
BrowseAllow from 172.16.0.0/12
BrowseAllow from 192.168.0.0/16

AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL

AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL

AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL

AuthType None
Order Deny,Allow
Deny From All
Allow From @LOCAL
```
5. Restart cupsys on both machines.
sudo /etc/init.d/cupsys restart

You can now access your printer on the following networks: 10.0.0.x, 192.168.0.x and 172.16.0.x. The printer will automatically show under printersettings on the clients.

---

### Post by daytimer045 on 2008-01-28
Angelot,
  Thank you for the Howto.  It didn't work:  the printer is still not printing.  Indeed, the print queue registers it as "Stopped" immediately after a job is sent to it.

I installed gnome-cups-manager, and recreated the cupsd.conf as you suggested.

  I then removed the existing printer, and added it again using the GNOME cups manager. 

The printer was found and installed correctly. 

When the Cups Manager started it dumped a massive list of warnings to an open terminal all something of this nature: (gnome-cups-manager:11327)  Warning**: Two ppds have driver == 'Standard'

When I tried to print a test page, it dumped this, perhaps very informative (?) error message.  Do you or anyone else have a clue about this?

IPP request failed with status 1028

Any further help would be appreciated.

Thanks.

---

