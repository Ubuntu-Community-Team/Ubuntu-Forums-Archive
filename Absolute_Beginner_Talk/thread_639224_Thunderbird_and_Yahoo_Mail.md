---
title: "Thunderbird and Yahoo Mail"
date: 2007-12-12
forum: Absolute Beginner Talk
---

### Post by Orbital75 on 2007-12-12
When I was using Thunderbird on Windows XP Pro, I was able to
use Thunderbird to check my Yahoo email account. I used an
extension called WebMail. I tied webmail with Ubuntu and
Thunderbird but it doesn't seem to work. I believe this is because
Linux must work differently and block it some how....
[http://webmail.mozdev.org](http://webmail.mozdev.org)

Anyone know how to get Thunderbird to check Yahoo mail?

From the WebMail:

This panel controls the POP, SMTP, and IMAP servers

    * Status

      This shows the status of the three servers. There are three possible values Running, Stopped, Error.
   
 * Enable

      This is used to enable or disable the servers. By default the POP and SMTP servers are enabled.
   
 * Ports

      This is used to set the port numbers of the servers. By default POP=110, SMTP=25, IMAP=143.
      Some operating systems block ports below 1024.

---

### Post by zvacet on 2007-12-13
You can try [ypops](http://ypopsemail.com/modules.php?op=modload&name=Sections&file=index&req=listarticles&secid=1)

---

### Post by philinux on 2007-12-13
I'm using it for hotmail ok, I just followed the instructions from mozilla to install the addon and set the ports in TB.

Server name localhost port 1025

---

### Post by Orbital75 on 2007-12-13
Yeah, I kinda thought that changing the ports would solve the problem but since
I'm new to linux, I didn't know if it would be safe.  I guess it's safe then
right?

---

### Post by Orbital75 on 2007-12-13
Well, I just changed the port #'s to
 POP: 1024  and  SMTP: 1025 
Is this safe?

Also,  Do I need to change these ports in
my ThunderBird Account Settings?

[IMG]http://img248.imageshack.us/img248/1536/screenshotsc8.png[/IMG]

---

