---
title: "invoke-rc.d: initscript gdm, action &quot;reload&quot; failed"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by whimsical-annie on 2007-10-19
I have been following the instructions in the "read this first newbie" area on how to deal with X-server.  I got to the dpkg-reconfigure gdm command and this was the response I got:

* Reloading GNOME Display Manager configuration...
*Changes will take effect when all current X sessions have ended.
invoke-rc.d: initscript gdm, action "reload" failed.


Now, I started down this path because Konsole won't run since I upgraded to 7.10

And, when I attempt to run root console (or what ever it is called - I'm on my husband's computer right now) I keep being told that it can't connect to x server.

Help!!

Annie
*Ubuntu day 4*

---

### Post by whimsical-annie on 2007-10-19
bump

I know this is two issues in one post - but, what the heck - I can't get adept manager to run either - here is the response I'm getting:

root@Es-air:/home/whimsical-annie# sudo adept-manager 
sudo: adept-manager: command not found 
root@Es-air:/home/whimsical-annie# indo sudo 
bash: indo: command not found 
root@Es-air:/home/whimsical-annie# info sudo 
root@Es-air:/home/whimsical-annie# sudo adept_manager 
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed 
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed 
kbuildsycoca running... 
DCOP Cleaning up dead connections. 
kapture::PkgSystem::PkgSystem() 
debconf 
adduser 
sysklogd 
snort-mysql 
oinkmaster 
debconf 
adduser 
sysklogd 
snort-mysql 
oinkmaster 
kdecore (KProcess): WARNING: _attachPty() 33

---

