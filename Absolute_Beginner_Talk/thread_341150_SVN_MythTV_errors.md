---
title: "SVN MythTV errors"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by dazzed and confussed on 2007-01-18
I seem to be having problems with svn.
When I attempt a entry like

sudo svn co [http://svn.mythtv.org/svn/trunk/mythtv](http://svn.mythtv.org/svn/trunk/mythtv)

I receive the error

svn: PROPFIND request failed on '/svn/trunk/mythtv'
svn: PROPFIND of '/svn/trunk/mythtv': Could not resolve hostname `svn.mythtv.org': Host not found ([http://svn.mythtv.org](http://svn.mythtv.org))


All svn commands give the same kind of errors

I've tried reinstalling subversion which gives me the the following message.

frierd@media2:/usr/src$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
subversion is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

I am behind a firewall which could be causing the problem but googling for a soloution hasn't helped.

Can any one help.

---

