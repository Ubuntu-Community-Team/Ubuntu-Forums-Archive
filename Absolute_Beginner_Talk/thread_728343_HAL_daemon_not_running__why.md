---
title: "HAL daemon not running ? why"
date: 2008-03-18
forum: Absolute Beginner Talk
---

### Post by BigGeoff on 2008-03-18
Hi guys

More problems with my recent newbie install of Gutsy 7.10

This time I cannot get my Zen V plus to be recognised in Amarok. I am fairly sure I have read most of the related threads here, but none seem to match my problem.

The Zen is not picked up when I plug it in and when I try to autosearch for a new device in Amarok I get the error:

No new media devices were found. If you feel this is an error, ensure that the DBUS and HAL daemons are running and KDE was built with support for them..............etc.

Well firstly I am running Gnome not KDE - does anyone think that is a problem in itself, secondly when I checked with system monitor, dbus is running but hal isn't - any idea why? Can I set it to run and if so how?

Sorry if these are pathetically easy questions but Linux is new to me.

Geoff

---

### Post by (((X))) on 2008-03-19
It should be possible to enable hal going system>administration>services
To start hal(if it is hal daemon amarok complains about)

sudo /etc/init.d/hal start

---

### Post by BigGeoff on 2008-03-22
Hi there please excuse the delay - been away with work.

Hal does not appear in the services options so I cannot stat it there.

When issue the command

sudo /etc/init.d/hal start 

I get the reply

Starting Hardware abstraction layer hald
/usr/sbin/hald already running


This all seems to raise more questions than it answers for me. Is  Amaroc happy to run with GNOME (which I have installed as default) as opposed to KDE?

If both hal and dbus are running why can I not connect to my ZEN? Have I missed something here?

Geoff

---

### Post by ky4623 on 2008-06-12
anyone have any ideas?

---

