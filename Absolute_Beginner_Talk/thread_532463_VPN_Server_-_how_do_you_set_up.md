---
title: "VPN Server - how do you set up"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-08-22
How do you set up Ubuntu to be a VPN server?

Carl

---

### Post by bodhi.zazen on 2007-08-22
VNC :

[list][*] Using default vnc server (share desktop, user must remain logged in): [http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html](http://www.ubuntugeek.com/share-your-ubuntu-desktop-using-remote-desktop.html)

[*]x11vnx (share 1 desktop) : x11vnc : [http://ubuntuforums.org/showthread.php?t=45565](http://ubuntuforums.org/showthread.php?t=45565)

[*]VNC (over ssh, new desktop, you do not need to remain logged in): 	[https://help.ubuntu.com/community/VNCOverSSH](https://help.ubuntu.com/community/VNCOverSSH)

[*]Reverse VNC (AKA easy router setup) : [http://www.ubuntuforums.org/showthread.php?t=299489](http://www.ubuntuforums.org/showthread.php?t=299489)[/list]

Secure ssh: [list][*][https://help.ubuntu.com/community/AdvancedOpenSSH](https://help.ubuntu.com/community/AdvancedOpenSSH)
	
[*]See also [denyhosts](http://denyhosts.sourceforge.net/) ~ it is in the repos, but you should read the config file ...[/list]

---

