---
title: "aMule on Ubuntu Server"
date: 2006-12-13
forum: Absolute Beginner Talk
---

### Post by kochen on 2006-12-13
Hello,
is there a way to run aMule (or any other sort of P2P) on an Ubuntu-Server?

I have no Display, so I need it to be used only from command line (or WEB)

thanks

---

### Post by danpre on 2007-01-29
try this:

[http://www.amule.org/wiki/index.php/AMuleCMD]("http://www.amule.org/wiki/index.php/AMuleCMD")

DANIeL

---

### Post by earthforce_1 on 2007-12-29
I am running amulecmd, and am having problems.  AFAIK I set it up correctly, but I get the following errors;
 amulecmd
This is amulecmd 2.1.3
Enter password for mule connection: 

Creating client...
Succeeded! Connection established to aMule 2.1.3

---------------------------------------
|          aMule text client          |
---------------------------------------

Use 'Help' for command list

aMulecmd$ Connect
 > Connecting to ED2K...
 > Connecting to Kad...
aMulecmd$ search local debian
 > Request failed with the following error: aMule is not connected!
aMulecmd$ Connect
 > Connecting to ED2K...
 > Connecting to Kad...
aMulecmd$ search local debian
 > Request failed with the following error: aMule is not connected!
aMulecmd$ search local debian
 > Request failed with the following error: aMule is not connected!
aMulecmd$ search global debian
 > Request failed with the following error: aMule is not connected!
aMulecmd$ Connect
 > Connecting to ED2K...
 > Connecting to Kad...
aMulecmd$ Connect
 > Connecting to ED2K...
 > Connecting to Kad...
aMulecmd$ Status
 > ED2K: Not connected
 > Kad: Not connected
 > Download:    0 bytes/sec
 > Upload:      0 bytes/sec
 > Clients in queue:    0
 > Total sources:       0
aMulecmd$ search local ubuntu
 > Request failed with the following error: aMule is not connected!
aMulecmd$ 

Thinks it is  connected, but it isn't.  I am behind a WRT54GS router, but I don't have any ports blocked as far as I know, and I am not running firewall software on the linux server (yet).   So I don't know what is wrong.  Attempting to get an updated server list yields:

sudo wget [http://ed2k.2x4u.de/822iu9hc/min/server.met](http://ed2k.2x4u.de/822iu9hc/min/server.met)
--20:16:53--  [http://ed2k.2x4u.de/822iu9hc/min/server.met](http://ed2k.2x4u.de/822iu9hc/min/server.met)
           => `server.met.1'
Resolving ed2k.2x4u.de... 217.115.142.116
Connecting to ed2k.2x4u.de|217.115.142.116|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
20:16:53 ERROR 404: Not Found.

Configuration and logfiles are attached....

---

### Post by flim9 on 2008-01-01
Hi, I had the same problem until a minute ago. I was able to connect after downloading a newer version of the server.met file into the proper directory. For me the proper directory was ~/.aMule/ in debian. I got the link to a working downloadable version of the server.met file from [http://ed2k.2x4u.de/](http://ed2k.2x4u.de/)

---

