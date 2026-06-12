---
title: "Possible Security Problem?"
date: 2005-09-14
forum: Absolute Beginner Talk
---

### Post by zappa86 on 2005-09-14
I made a post in another thread, but perhaps its more approiate here.

I did a netstat -l to see what was opened on my system and I found several entries 
like:
unix  2      [ ACC ]     STREAM     LISTENING     13734   /tmp/orbit-harry/linc-226f-0-1bac2d62a9d22

and

unix  2      [ ACC ]     STREAM     LISTENING     13186    @/tmp/dbus-hIk2dV0DVj

I'm somewhat new to linux, however in windows I know that programs in the tmp directory that look that that can be problems? is this normal or do I have a virus or worm or something?

---

### Post by Jussi Kukkonen on 2005-09-14
Those are local Unix Domain Sockets (used in communication between processes on localhost), and should be harmless, useful even.

---

### Post by Nequeo on 2005-09-14
Just in case you're curious, 'dbus' is a system messaging process. It lets different parts of the desktop (or other programs) talk to each other, in a sense. 'Orbit', on the other hand, is related to CORBA, which stands for Common Object Request Broker Architecture. It's related to programs communicating over a network. However, Jussi mentioned, anything you see in netstat that starts with 'Unix' isn't listening over the network. These webpages:

DBUS: [http://www.freedesktop.org/Software/dbus](http://www.freedesktop.org/Software/dbus)

Orbit (part of CORBA): [http://www.omg.org/gettingstarted/corbafaq.htm](http://www.omg.org/gettingstarted/corbafaq.htm)

... will give you more information, if you want it. 

The reason these things are in /tmp (as far as I know) is because that's the most logical place to put them! These things only exist as long as the applications that need them are open, and they change all the time. 

Moreover, in the Old Days before Desktop Linux, when multi-user UNIX systems were common, most of the system was mounted as 'read only' for security reasons. This would mean that the only place you could be certain of being able to create a temporary file is, not surprisingly, in /tmp. Linux geeks can be fairly heavy on tradition, (though they're more likely to call it 'good software engineering'!), so even these days, you'll see /tmp used a fair bit if you look for it.

---

