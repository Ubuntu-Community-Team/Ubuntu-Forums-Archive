---
title: "[SOLVED] Simple, SMALL, Secure WebServer"
date: 2007-11-21
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-11-21
I am looking to setup a VERY small webserver for my own needs (not open to the public) however it will be accessible via the WAN (internet) using a port forward (Not 80 or 443) thru my router and DynDNS.  The purpose of this small webserver is to aggregate various WebGUI's onto one page.

For example:
I am running the following webGUI's...[list][*]KTorrent - Bit-Torrent Client[*]hellahella - hellanzb GUI - Usenet Client[*]Tomato - My Routers Firmware[*]etc - I might add a few others later[/list] So I'd like to create 1 simple page that will link to the other pages (link to their webGUI ports).

What is the best way to go about this?
I've looked into XAMPP/WAMP, er what ever their calling it these days ;) but people keep telling me it's not secure.

Thanks in advance for any/all comments/suggestions.
-BassKozz

---

### Post by p_quarles on 2007-11-21
If all you want to do is create a single page with a few links, just use Apache. No need for a database server or server-side scripting modules. 

And I don't know who's telling you it's "not secure," but I do know they're wrong. The default Apache installation is very secure, and so long as you don't change anything without knowing what you're doing, and keep up with the security patches, you'll be golden.

---

