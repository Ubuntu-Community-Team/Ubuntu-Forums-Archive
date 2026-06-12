---
title: "Share Dapper Ubuntu printer with OSX?"
date: 2007-01-10
forum: Apple PPC Users
---

### Post by aforonda on 2007-01-10
I've googled and googled and have not found a good answer to my question. Can someone give me a step by step on how I can share the hp laserjet 4ml printer connected to my dapper ubuntu machine with the OS X iMac in my house?

Thanks in advance,
A

---

### Post by didg on 2007-01-11
I'm not using dapper but:

On the linux box:
From the gui as user with admin right:
- open a web browser

- go to 127.0.0.1:631/admin
set at least 'Share published printers connected to this system'

- click 'change setting'

- enter your user name and passwd if it doesn't authenticate you're not an admin.

if the browser  returns an error like can't load page (I does here but It's not dapper)  go to gnome system/admin/services and stop/start cupsys.

- Now printers should be  in OSX system prefs (may be after clicking add).
If not:
saying your linux box is 192.168.1.2
on the linux box:
in a browser double check that 192.168.1.2:631 go to cups admin page
do the same from an OSX browser  (firewall ?).  
If from the Mac you can go to 192.168.1.2:631 but still don't see the printer, sorry but I don't know :(

---

### Post by ssam on 2007-01-11
you can also turn on printer sharing in system -> administration -> printing.

the printer description in linux is the printer name in mac os x. you can change this in the printer properties.

---

### Post by aforonda on 2007-01-11
Ok I see the ubuntu shared printer on the os x machine but when I try to print from the mac i'm getting an error that lamely reads "error while printing" help?

---

### Post by didg on 2007-01-12
What do you have in /var/log/cups (linux box)?

---

### Post by aforonda on 2007-01-12
access log is empty
error log reads as the following:
I [12/Jan/2007:07:35:08 -0800] Saving job cache file "/var/cache/cups/job.cache"...
I [12/Jan/2007:07:35:08 -0800] Listening to 127.0.0.1:631 (IPv4)
I [12/Jan/2007:07:35:08 -0800] Listening to /var/run/cups/cups.sock (Domain)
I [12/Jan/2007:07:35:08 -0800] Listening to :::631 (IPv6)
I [12/Jan/2007:07:35:08 -0800] Listening to 0.0.0.0:631 (IPv4)
I [12/Jan/2007:07:35:08 -0800] Listening to /var/run/cups/cups.sock (Domain)
I [12/Jan/2007:07:35:08 -0800] Loaded configuration file "/etc/cups/cupsd.conf"
I [12/Jan/2007:07:35:08 -0800] Cleaning out old temporary files in "/var/spool/cups/tmp"...
I [12/Jan/2007:07:35:08 -0800] Configured for up to 100 clients.
I [12/Jan/2007:07:35:08 -0800] Allowing up to 100 client connections per host.
I [12/Jan/2007:07:35:08 -0800] Using policy "default" as the default!
I [12/Jan/2007:07:35:08 -0800] Full reload is required.
I [12/Jan/2007:07:35:08 -0800] Loaded MIME database from '/etc/cups': 34 types, 39 filters...
I [12/Jan/2007:07:35:08 -0800] Loading job cache file "/var/cache/cups/job.cache"...
I [12/Jan/2007:07:35:08 -0800] Full reload complete.
I [12/Jan/2007:07:35:08 -0800] Listening to 127.0.0.1:631 on fd 0...
I [12/Jan/2007:07:35:08 -0800] Listening to /var/run/cups/cups.sock on fd 1...
I [12/Jan/2007:07:35:08 -0800] Listening to :::631 on fd 3...
E [12/Jan/2007:07:35:08 -0800] Unable to bind socket for address 0.0.0.0:631 - Address already in use.
I [12/Jan/2007:07:35:08 -0800] Listening to /var/run/cups/cups.sock on fd 4...

Thanks,
A

---

### Post by didg on 2007-01-12
There's something wrong with /etc/cups/cupsd.conf
it's like you have
*Listen 127.0.0.1:631*
*Listen 631*
or
*Port 631*

*Listen /var/run/cups/cups.sock*

Remove the line
*Listen 127.0.0.1:631*

---

