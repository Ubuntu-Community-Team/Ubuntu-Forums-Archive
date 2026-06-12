---
title: "Gaim only working under certain conditions"
date: 2006-12-01
forum: Absolute Beginner Talk
---

### Post by mongooseman1128 on 2006-12-01
I have a strange problem. Gaim will only work if I have used Kopete first. It doesn't matter if I close the kopete session or not before using gaim. Also, after kopete is closed for a while gaim will not function and I have to use kopete again to get gaim to work.

---

### Post by apjone on 2006-12-01
try 

sudo dpkg-reconfigure gaim

---

### Post by mongooseman1128 on 2006-12-02
thanks, I'll give that a shot when I get home. what does dpkg do? I understand the rest of the command I've just never used dpkg before

---

### Post by mongooseman1128 on 2006-12-02
okay I ran that command, but it still didn't work. Was there supposed to be any output from the command? because I didn't get any

---

### Post by Caligula on 2006-12-02
what do you mean by "doesn't work"? what exactly doesn't function?

---

### Post by mongooseman1128 on 2006-12-03
it opens up and I can create a username and everything, but what I mean by work is connect

---

### Post by sardion on 2006-12-03
Can you try running gaim from a terminal like this:

gaim -d

(The -d tells it to print debug messages).

And then post whatever it says here.  Make sure you try to connect with gaim when its running this way so we can see whatever errors happen.

Also, do you mean that gaim will connect and work fine so long as you have run Kopete at some point before or does Kopete need to be running at the same time?

---

### Post by mongooseman1128 on 2006-12-07
Kopete needs to have been running at some point, but there also seems to be a time out at which kopete has to be run again.

---

### Post by mongooseman1128 on 2006-12-08
okay, I ran gaim -d from terminal. One thing I just noticed was I restarted the computer and when I got back on the computer gaim connected without problem. Then I reset my modem and the connection wouldn't work. I don't know if that helps. anyway, here's the output from gaim -d (the output is really long)

```
sound: Initializing sound output drivers.
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
plugins: probing /usr/lib/gaim/autorecon.so
plugins: probing /usr/lib/gaim/docklet.so
plugins: probing /usr/lib/gaim/extplacement.so
plugins: probing /usr/lib/gaim/gaim-remote.so
plugins: probing /usr/lib/gaim/gestures.so
plugins: probing /usr/lib/gaim/gevolution.so
plugins: probing /usr/lib/gaim/history.so
plugins: probing /usr/lib/gaim/iconaway.so
plugins: probing /usr/lib/gaim/idle.so
plugins: probing /usr/lib/gaim/libgg.so
plugins: probing /usr/lib/gaim/libirc.so
plugins: probing /usr/lib/gaim/libjabber.so
plugins: probing /usr/lib/gaim/libmsn.so
plugins: probing /usr/lib/gaim/libnapster.so
plugins: probing /usr/lib/gaim/libnovell.so
plugins: probing /usr/lib/gaim/liboscar.so
plugins: probing /usr/lib/gaim/libyahoo.so
plugins: probing /usr/lib/gaim/libzephyr.so
plugins: /usr/lib/gaim/libzephyr.so is unloadable: libzephyr.so.3: cannot open shared object file: No such file or directory
plugins: probing /usr/lib/gaim/nautilus.so
plugins: probing /usr/lib/gaim/notify.so
plugins: probing /usr/lib/gaim/relnot.so
plugins: probing /usr/lib/gaim/spellchk.so
plugins: probing /usr/lib/gaim/ssl-gnutls.so
plugins: probing /usr/lib/gaim/ssl-nss.so
plugins: probing /usr/lib/gaim/ssl.so
plugins: probing /usr/lib/gaim/statenotify.so
plugins: probing /usr/lib/gaim/tcl.so
plugins: probing /usr/lib/gaim/ticker.so
plugins: probing /usr/lib/gaim/timestamp.so
plugins: probing /usr/lib/gaim/libextprefs.so
plugins: probing /usr/lib/gaim/libextprefs.la
plugins: probing /usr/lib/gaim/libextprefs.a
plugins: probing /home/charlie/.gaim/smileys
plugins: probing /home/charlie/.gaim/accounts.xml
plugins: probing /home/charlie/.gaim/icons
plugins: probing /home/charlie/.gaim/prefs.xml
plugins: probing /home/charlie/.gaim/blist.xml
plugins: probing /home/charlie/.gaim/accels
plugins: registering plugin-load signal
plugins: registering plugin-unload signal
blist import: Reading /home/charlie/.gaim/blist.xml
blist import: Finished reading /home/charlie/.gaim/blist.xml
prefs: Reading /home/charlie/.gaim/prefs.xml
prefs: Finished reading /home/charlie/.gaim/prefs.xml
plugins: Loading saved plugin /usr/lib/gaim/docklet.so
tray icon: plugin loaded
tray icon: created
plugins: Loading saved plugin /usr/lib/gaim/notify.so
plugins: Loading saved plugin /usr/lib/gaim/nautilus.so
plugins: Loading saved plugin /usr/lib/gaim/autorecon.so
pounces: Error reading pounces: Failed to open file '/home/charlie/.gaim/pounces.xml': No such file or directory
status: Error reading statuses: Failed to open file '/home/charlie/.gaim/status.xml': No such file or directory
Session Management: ICE initialized.
Session Management: Connecting with no previous ID
Session Management: Handling new ICE connection... done.
Session Management: Connected to manager (GnomeSM) with client ID 117f000101000116562176000000046700010
Session Management: Using gaim as command
Session Management: Received first save_yourself
Session Management: Received save_complete
tray icon: embedded
accounts: Writing accounts to disk.
nautilus: save blist online
account: Connecting to account 0x81fd7b0. gc = 0x849fbc0
connection: Connecting. gc = 0x849fbc0
connection: Calling serv_login
server: gaim 1.5.1cvs logging in SportsChuck11 using AIM/ICQ
oscar: oscar_login: gc = 0x849fbc0
dns: Created new DNS child 4971, there are now 1 children.
dns: Host 'login.oscar.aol.com' resolved
proxy: Connecting to login.oscar.aol.com:5190 with no proxy
proxy: Connect would have blocked.
nautilus: don't save blist online. No change
accounts: Writing accounts to disk.
nautilus: don't save blist online. No change
nautilus: don't save blist online. No change
nautilus: don't save blist online. No change
nautilus: don't save blist online. No change
nautilus: don't save blist online. No change
nautilus: don't save blist online. No change
nautilus: don't save blist online. No change
dns[4971]: nobody needs me... =(
nautilus: don't save blist online. No change
```
then the last line repeats until I disconnect

---

