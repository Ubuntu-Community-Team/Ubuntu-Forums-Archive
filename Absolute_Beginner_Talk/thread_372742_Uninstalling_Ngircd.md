---
title: "Uninstalling Ngircd"
date: 2007-02-28
forum: Absolute Beginner Talk
---

### Post by venik212 on 2007-02-28
Has anyone managed to *uninstall* NGIRCD (Next Generation IRC server)?  When I tried to uninstall it, I was told that an error had occured, and the removal had failed.  This was true even after I stopped the NGIRCD service.  I do not want to remove it manually, since this might confuse Synaptic and Adept.  How do I do it?  I tried to remove it using Synaptic and when that failed, I used the Terminal, which also failed.  The error message I get is:
subprocess post installation script returned error exit status 1.

I email the author of the server but got no response.
Thanks for any help.

---

### Post by fimblo on 2008-02-12
I've got exactly the same problem on my Gutsy server.

[FONT="Courier New"]
fimblo@almbert:/etc/init.d$ sudo apt-get purge ngircd
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ngircd*
0 upgraded, 0 newly installed, 1 to remove and 13 not upgraded.
Need to get 0B of archives.
After unpacking 254kB disk space will be freed.
Do you want to continue [Y/n]? 
(Reading database ... 39524 files and directories currently installed.)
Removing ngircd ...
Stopping Next generation IRC server: invoke-rc.d: initscript ngircd, action "stop" failed.
dpkg: error processing ngircd (--purge):
 subprocess pre-removal script returned error exit status 1
Errors were encountered while processing:
 ngircd
E: Sub-process /usr/bin/dpkg returned an error code (1)
fimblo@almbert:/etc/init.d$ 
[/FONT]

Has someone managed to fix this?

---

### Post by fimblo on 2008-02-12
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/ngircd/+bug/127496](https://bugs.launchpad.net/ubuntu/+source/ngircd/+bug/127496) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Found the lauchpad bug id: #127496

---

