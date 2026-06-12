---
title: "breezy install problems"
date: 2005-09-28
forum: Absolute Beginner Talk
---

### Post by aran384 on 2005-09-28
i had a few errors when updating to breezy does any1 know how to fix these problems ?? 

> Setting up postfix (2.2.4-1ubuntu2) ...

Postfix configuration was untouched.  If you need to make changes, edit
/etc/postfix/main.cf (and others) as needed.  To view Postfix configuration
values, see postconf(1).

After modifying main.cf, be sure to run '/etc/init.d/postfix reload'.

Running newaliases
 * Starting Postfix Mail Transport Agent... postfix/postfix-script: fatal: the Postfix mail system is already running
                                                                         [fail]
invoke-rc.d: initscript postfix, action "start" failed.
dpkg: error processing postfix (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of mutt:
 mutt depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mutt (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-core:
 lsb-core depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing lsb-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of mailx:
 mailx depends on postfix | mail-transport-agent; however:
  Package postfix is not configured yet.
  Package mail-transport-agent is not installed.
  Package postfix which provides mail-transport-agent is not configured yet.
dpkg: error processing mailx (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-graphics:
 lsb-graphics depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-graphics (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb:
 lsb depends on lsb-core; however:
  Package lsb-core is not configured yet.
 lsb depends on lsb-graphics; however:
  Package lsb-graphics is not configured yet.
dpkg: error processing lsb (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of lsb-cxx:
 lsb-cxx depends on lsb-core; however:
  Package lsb-core is not configured yet.
dpkg: error processing lsb-cxx (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 postfix
 mutt
 lsb-core
 mailx
 lsb-graphics
 lsb
 lsb-cxx


---

### Post by Perfect Storm on 2005-09-28
I don't how to fix it, but maybe you should try with hoary (5.04), because breezy 5.10 is still under development.

---

### Post by aran384 on 2005-09-28
i was updating to breezy tho dist-upgrade and there are the only problems i have had!:(

---

### Post by Perfect Storm on 2005-09-28
Well, if you want to use breezy pre release I recommend that you do it with a clean install from a breezy CD. Though some people are lucky to upgrade some aren't. There's a chance that an upgrade mess up stuff.

---

### Post by aran384 on 2005-09-28
i did the upgrade everything still works but that....

it needs installing some how... =/ ..

---

### Post by Vectrox on 2005-09-28
Try

> apt-get -f install

---

### Post by aran384 on 2005-09-28
kk thanks i will try that when i get home is that a 

fresh install right ?

---

### Post by David Marrs on 2005-09-28
If you're posting to absolute beginner then you probably shouldn't be trying to install breezy in the first place. It's still being developed for release and is likely to be changing from one day to the next.

---

### Post by aran384 on 2005-09-28
i fixed it :D

booted in recorvery mode and did dist-upgrade worked like a charm....

now i need some good themes and icons to jazz it up :D

---

### Post by Kyral on 2005-09-28
Someone slap a Sticky on this Forum telling people not to use Breezy right now....please. I don't enjoy acting like a BOFH, but I'm getting kinda tired of seeing this kinda things in the ABT Forum.

---

