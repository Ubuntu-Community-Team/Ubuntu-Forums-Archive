---
title: "Network between windows xp and ubuntu 7.10"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by kogia on 2007-10-21
hi. i have a server with windows xp connecting to internet through a modem-router fritz!boxfon. i have also a laptop with ubuntu 7.10 connected to server through my router.pls tell me what i have to do to make a network between my server and laptop.i forgot to tell u that i have internet in both pcs through my router.

---

### Post by HermanAB on 2007-10-21
Windows will run a service called 'server' when you enable file and printer sharing and drag a folder to the shared folders area.  The Linux emulation of this service is called Samba ([www.samba.org](www.samba.org)).

If Windows is running the server, then you only need a client on Linux to connect to it.  First check to see if you have basic connectivity, using telnet:
$ telnet serveripaddress 445

If you get connection refused, then either server isn't running on Windows, or Linux is blocking port 445 in its firewall.

Once telnet can open a connection (close with ctrl ] and q) then run 'smb4k', or 'linneighborhood' to browse the Windows file shares.  Otherwise, install KDE and run Konqueror (it runs in Gnome too), then in the address box type:
smb://serveripaddress/sharename

and La Voila!

Cheers,

Herman

---

