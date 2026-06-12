---
title: "Unable to uninstall 'opendchub'"
date: 2007-05-15
forum: Absolute Beginner Talk
---

### Post by DivineOmega on 2007-05-15
When attempting to remove 'opendchub' via synaptic, I receive the error:

> E: opendchub: subprocess pre-removal script returned error exit status 143

The terminal ('details') output appears to be starting the service, rather than shutting it down. It says:

> (Reading database ... 115488 files and directories currently installed.)
Removing opendchub ...
Stopping Open DC Hub: opendchubTerminated
invoke-rc.d: initscript opendchub, action "stop" failed.
dpkg: error processing opendchub (--remove):
 subprocess pre-removal script returned error exit status 143
Starting Open DC Hub: opendchubHub is up and running. Listening for user connections on port 5000
and listening for admin connections on port 53696
.
Errors were encountered while processing:
 opendchub
E: Sub-process /usr/bin/dpkg returned an error code (1)
A package failed to install.  Trying to recover:

---

### Post by Metacarpal on 2007-05-15
Open a terminal (Appplications menu > Accessories > Terminal) and type:
```
sudo pkill opendchub
```

That should (after you give your password) stop the process.  To check, type (or copy/paste):
```
ps aux | grep opendchub
```
That should give you one line, ending in "grep opendchub".  If you see another line returned from that command, try:
```
sudo pkill -9 opendchub
```
Then use the ps code above to check.  Once the process has died, you should be able to remove it.

---

### Post by DivineOmega on 2007-05-16
Thanks. But unfortunately killing the process had no affect. During removal it seems to be attempting to restart the process.

Result from commands:

```
divineomega@crystal:~$ sudo pkill opendchub
Password:
divineomega@crystal:~$ ps aux | grep opendchub
1000     11675  0.0  0.0   2896   784 pts/0    S+   08:59   0:00 grep opendchub
divineomega@crystal:~$ sudo apt-get remove opendchub 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  python-crypto libavahi-compat-howl0 libsilc-1.0-2 libtagc0 dctc zope-common
  tcl8.4 tk8.4 libmeanwhile1 myspell-en-za python-twisted-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  opendchub
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 324kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 115488 files and directories currently installed.)
Removing opendchub ...
Stopping Open DC Hub: opendchubTerminated
invoke-rc.d: initscript opendchub, action "stop" failed.
dpkg: error processing opendchub (--remove):
 subprocess pre-removal script returned error exit status 143
Starting Open DC Hub: opendchubHub is up and running. Listening for user connections on port 5000
and listening for admin connections on port 53696
.
Errors were encountered while processing:
 opendchub
E: Sub-process /usr/bin/dpkg returned an error code (1)
divineomega@crystal:~$ 
```

---

### Post by mo0osah on 2007-05-18
I got the same problem... and it's really bugging me

---

### Post by dogatemycomputer on 2007-05-18
This was posted by a gentlemen named Intelikey in #kubuntu on irc.freenode.org

# stops kubuntu from loading the service
sudo mv /sbin/start-stop-daemon /root   

# convinces kubuntu the load succeeded so the process doesn't error out
sudo ln -s /bin/true /sbin/start-stop-daemon 

### now uninstall your package then continue with ###

# remove the symbolic link
sudo rm /sbin/start-stop-daemon

# restore the start/stop daemon to its original location  
sudo mv /root/start-stop-daemon /sbin/

Good luck!  Hope this helps..

---

### Post by DivineOmega on 2007-05-19
> **dogatemycomputer said:**
> This was posted by a gentlemen named Intelikey in #kubuntu on irc.freenode.org

# stops kubuntu from loading the service
sudo mv /sbin/start-stop-daemon /root   

# convinces kubuntu the load succeeded so the process doesn't error out
sudo ln -s /bin/true /sbin/start-stop-daemon 

### now uninstall your package then continue with ###

# remove the symbolic link
sudo rm /sbin/start-stop-daemon

# restore the start/stop daemon to its original location  
sudo mv /root/start-stop-daemon /sbin/

Good luck!  Hope this helps..

Worked like a dream, thanks.

---

