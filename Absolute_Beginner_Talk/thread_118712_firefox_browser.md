---
title: "firefox browser ?"
date: 2006-01-17
forum: Absolute Beginner Talk
---

### Post by clinton2010 on 2006-01-17
im pretty new with this linux stuff is there anyway to speed up the fire fox browser or any tweaks for it to make it open faster same thing with programs they take a min to open 

thanks in advance

---

### Post by earobinson on 2006-01-17
I searched the forums for [speed firefox] and found: [http://www.ubuntuforums.org/showthread.php?t=114424&highlight=speed+firefox](http://www.ubuntuforums.org/showthread.php?t=114424&highlight=speed+firefox)

---

### Post by hen3rz on 2006-01-17
Hello,

I have done the following to speed up my firefox.

1. Installed Fasterfox (Dunno if this made a diff but u get a cool page load timer)

2. Did the following:
> 1.Type "about:config" into the address bar and hit return. Scroll down and look for the following entries:

network.http.pipelining network.http.proxy.pipelining network.http.pipelining.maxrequests

Normally the browser will make one request to a web page at a time. When you enable pipelining it will make several at once, which really speeds up page loading.

2. Alter the entries as follows:

Set "network.http.pipelining" to "true"

Set "network.http.proxy.pipelining" to "true"

Set "network.http.pipelining.maxrequests" to some number like 30. This means it will make 30 requests at once.

3. Lastly right-click anywhere and select New-> Integer. Name it "nglayout.initialpaint.delay" and set its value to "0". This value is the amount of time the browser waits before it acts on information it recieves.

If you're using a broadband connection you'll load pages MUCH faster now!

Hope that helps.

---

### Post by dueY on 2006-01-17
[QUOTE=hen3rz]Hello,

I have done the following to speed up my firefox.

1. Installed Fasterfox (Dunno if this made a diff but u get a cool page load timer)

2. Did the following:


Hope that helps.[/QUOTE]

I installed fasterfox too and am unsure if it made a difference.  Probably because my config was tweaked before that anyway.  But the page load timer is kind of neat.

---

