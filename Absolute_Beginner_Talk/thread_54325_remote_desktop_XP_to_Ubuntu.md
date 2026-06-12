---
title: "remote desktop XP to Ubuntu"
date: 2005-08-04
forum: Absolute Beginner Talk
---

### Post by Druidor on 2005-08-04
Hello all,

Not sure about this as I have only just started using Ubuntu & have been a M$ user for god knows how long DOS days lol.

What would be a good GUI based remote desktop utility that I can use to connect from a Windows XP Pro system to my Ubuntu machine.

I Used M$ remote desktop to connect to it as it saved mucking about with th wires etc.



PS how long does it take to get the disks posted I ordered some ages ago & still nothing.

---

### Post by heimo on 2005-08-04
Just a quick reply (I'm in hurry...) crossplatform remote desktop - vnc. Search [http://packages.ubuntu.com/](http://packages.ubuntu.com/) for server and ie. tucows for windows client.

---

### Post by Maxplayer14 on 2005-08-04
[QUOTE=Druidor]Hello all,

Not sure about this as I have only just started using Ubuntu & have been a M$ user for god knows how long DOS days lol.

What would be a good GUI based remote desktop utility that I can use to connect from a Windows XP Pro system to my Ubuntu machine.

I Used M$ remote desktop to connect to it as it saved mucking about with th wires etc.



PS how long does it take to get the disks posted I ordered some ages ago & still nothing.[/QUOTE]
 The absolute best thing I have used so far is Freenx.  I just installed it the other day for my box and it works like a charm.  Best thing I have seen yet.  Do a search on the forum, there is a howto.

---

### Post by jimcooncat on 2005-08-04
If you're doing this all behind a firewall, a good Windows package is UltraVNC
[http://ultravnc.sourceforge.net/](http://ultravnc.sourceforge.net/)

Help for the Ubuntu side
[http://ubuntuguide.org/#remotedesktop](http://ubuntuguide.org/#remotedesktop)

If you're doing this across the internet, you need to understand a lot about the security risks. 
Freenx is probably the best way to do this, but some folks have had trouble with the install. Maybe this has been cleared up by now.

A different way to do this is to forward X:
Free (as in beer): [http://www.pexus.com/](http://www.pexus.com/)
Totally free: [http://x.cygwin.com/](http://x.cygwin.com/)

---

