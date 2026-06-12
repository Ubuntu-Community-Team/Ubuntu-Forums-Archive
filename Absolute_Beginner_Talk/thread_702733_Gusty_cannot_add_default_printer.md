---
title: "Gusty: cannot add default printer"
date: 2008-02-20
forum: Absolute Beginner Talk
---

### Post by gaten on 2008-02-20
I've got a printer shared on a Feisty machine. Using the Gusty printer GUI, all the options under "Basic Server Settings" are grayed out (even using gksudo) until I hit the "Goto Server" button and enter my printer server. 

Then I am able to see the printer and even print a test page to it, but when I try to add the printer via "New Printer" or even make it my default via the "Make Default" button, I get this error:

> CUPS Server error
There was an error during the CUPS operation: 'client-error-forbidden'

One would think I'm trying to make the printer the default on the other end (ie change the printer setting on the server rather than linking to them from my local machine) but this also happens when I try to add the printer. 

Any ideas? I heard printer setup is a breeze in gusty, not so in my experience so far...

---

### Post by spiderbatdad on 2008-02-20
sounds like a problem in smb.conf settings on the host.

---

### Post by stchman on 2008-02-20
> **gaten said:**
> I've got a printer shared on a Feisty machine. Using the Gusty printer GUI, all the options under "Basic Server Settings" are grayed out (even using gksudo) until I hit the "Goto Server" button and enter my printer server. 

Then I am able to see the printer and even print a test page to it, but when I try to add the printer via "New Printer" or even make it my default via the "Make Default" button, I get this error:



One would think I'm trying to make the printer the default on the other end (ie change the printer setting on the server rather than linking to them from my local machine) but this also happens when I try to add the printer. 

Any ideas? I heard printer setup is a breeze in gusty, not so in my experience so far...

If you have eth printer on a Feisty machine you need to share it first.  I have a tutorial to share printers using Linux.  It is more Feisty based but should work for Gutsy.  You don't need Samba or anything else.

[http://www.stchman.com/share_printer.html](http://www.stchman.com/share_printer.html)

You may need to do the following in a terminal:

```
gksudo system-config-printer
```

Gutsy uses the system-config-printer while older distros use gnome-cups-manager.  Printer addition needs to be done as an administrator.

---

### Post by gaten on 2008-02-20
Thanks for the reply, but I've setup the printers as described in your guide and I've tried adding printers through gksudo already to no avail. It seems like the printer config thinks the remote printers are local printers and when I try to change settings it won't allow me because of access restrictions.

This really shouldn't be that complicated...

---

### Post by spiderbatdad on 2008-02-20
I would think you only need to configure the printers section of /etc/samba/smb.conf on the host machine

---

### Post by gaten on 2008-02-20
I agree. That smb.conf is from the remote host that the printer is located on.

---

### Post by spiderbatdad on 2008-02-20
I don't follow. I thought the Feisty machine hosted. It would be localhost on the feisty rig?

---

### Post by gaten on 2008-02-20
Yes, quick summary:

Fiesty desktop hosting the printer (printer is local to fiesty)

Gusty desktop trying to connect to remote printer. Able to print test pages, but not able to add the printer for use with the Gusty system in anyway.

---

### Post by spiderbatdad on 2008-02-20
so in Gusty printer, smb.conf  change work group domain to Feisty domain and interfaces to ip address of Feisty machine. Very sorry for the crude example. There must be a simple how-to for this.

---

### Post by spiderbatdad on 2008-02-20
The file /etc/cups/cupsd-browsing.conf sets Browsing Off by default. This disallows access from other PCs on the LAN.

To turn browsing on, either edit /etc/cups/cupsd-browsing.conf and change "Off" to "On" or go to /usr/share/cups and do

./enable_browsing 1

Then, (sudo) edit /etc/cups/cupsd.conf to comment out the following line so:

# Listen 127.0.0.1:631

and uncomment, as appropriate, to have these entries:

Port 631
Browsing On
BrowseAddress @LOCAL
<Location />
Order Deny,Allow
Deny From All
Allow From 127.0.0.1
Allow From @LOCAL
</Location>

Finally,

sudo /etc/init.d/cupsys restart

and your CUPS printer should be visible from other PCs on the LAN.
__________________

---

### Post by gaten on 2008-02-20
Sorry for the confusion, but as I mentioned on the first post I can **see** the printer just fine from the Gusty machine, in fact I can print a test page to it! What I **cannot **do is add the printer to the system so that the Gusty computer can print to it (ie from OpenOffice etc).

---

