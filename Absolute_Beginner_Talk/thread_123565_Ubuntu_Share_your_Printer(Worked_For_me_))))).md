---
title: "Ubuntu Share your Printer(Worked For me :)))))"
date: 2006-01-30
forum: Absolute Beginner Talk
---

### Post by utab on 2006-01-30
[http://occy.net/printing](http://occy.net/printing)

Ubuntu: Share your printer
Submitted by occy on May 9, 2005 - 1:27am.tips and tricks

This might work on other distro's with CUPS, but I have no idea. I do know this works under Ubuntu Linux.

Backup your: /etc/cups/cupsd.conf and replace with the following(adjust to fit your LAN):
DefaultCharset notused
LogLevel info
Printcap /var/run/cups/printcap
User cupsys
Group lpadmin
RunAsUser Yes
Port 631
Include cupsd-browsing.conf
BrowseAddress @LOCAL
SystemGroup lpadmin

<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From 10.10.0.*
</Location>

<Location /jobs>
AuthType Basic
AuthClass User
</Location>

<Location /admin>
AuthType Basic
AuthClass System
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
</Location>

Finally, you may have to add this on the client side(where you are printing from): /etc/cups/client.conf
ServerName hostname(IP might work)

Once this is all setup, You should be able to go to: System / Administration / Printing and in the top tool bar you'll see: Global Settings You'll want to make sure the following is checked:
Detect Lan Printers

Good luck to you, and if you are having problems, you may want to also refer to this forum post on the same subject.

Triple your money back if this doesn't work!

---

### Post by WelterPelter on 2006-02-01
I want triple my zero dollars back. This didn't work for me. The printer shows up in the Gnome printer configuration as a network printer just fine, but I can't even print a test page there. It accepts the job, but keeps automatically setting the printer on pause, no matter how many times I resume it.

---

### Post by utab on 2006-02-02
Once this is all setup, You should be able to go to: System / Administration / Printing and in the top tool bar you'll see: Global Settings You'll want to make sure the f[COLOR="Red"]ollowing is checked:
Detect Lan Printers[/COLOR]

---

### Post by Boelcke on 2006-05-28
I got this working with the ServerName, followed by the IP address of my server PC.  Unfortunately, that IP changes every now and then, thanks to DHCP.  What format can I put this in that uses the PC's hostname?

For example, in that clients.list file, I want to put something like:

ServerName ubuntubox1

rather than:

ServerName 192.168.1.100

---

