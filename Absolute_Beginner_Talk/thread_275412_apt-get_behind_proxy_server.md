---
title: "apt-get behind proxy server"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by pingun_africa on 2006-10-11
helllo
i.m new comer in linux

i can't apt-get, because i connect to internet by proxy server,
the proxy server ask for username and password before i browse internet. how can i use apt-get??????

thanks

---

### Post by Patsoe on 2006-10-24
You may have found this by now, but since I came across your question while searching for the answer, this worked for me:

[http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html](http://blog.mypapit.net/2006/02/how-to-use-apt-get-behind-proxy-server-ubuntudebian.html)

Note that I chose to change the .bashrc in my homedir rather than in etc, which would be a systemwide change...

---

### Post by mnml on 2007-10-06
Main Menu - > System -> Preferences -> Network Proxy

setup your proxy settings and then reboot, it should work fine.

---

