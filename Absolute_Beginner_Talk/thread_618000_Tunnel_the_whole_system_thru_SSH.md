---
title: "Tunnel the whole system thru SSH"
date: 2007-11-19
forum: Absolute Beginner Talk
---

### Post by trizuk on 2007-11-19
I have an SSH server at home and ubuntu on my laptop. i downloaded gnome SSH Tunnel Manager. I was wondering if there is another app that proxifies all the apps so they go thru the tunnel. i prefer gui and not command line. thanks.

---

### Post by Dr Small on 2007-11-19
I thought you could setup your entire system to go through a proxy, by going to:
System > Preferences > Network Proxy

and just have it point to your SSH Server.

---

### Post by houstonbofh on 2007-11-19
I go old school...  In a terminal (or write a script, but you need an output console) type 'ssh your.ip.com -Xl username' and you have an X tunnel.  Now type 'nautilus --no-desktop' and you have a file manager.  You will need the terminal for message output, but you can minimize it and forget it until you log out.

---

