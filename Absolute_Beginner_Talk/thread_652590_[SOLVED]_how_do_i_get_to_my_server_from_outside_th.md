---
title: "[SOLVED] how do i get to my server from outside the local network?"
date: 2007-12-28
forum: Absolute Beginner Talk
---

### Post by e1ektrob0y on 2007-12-28
I have a question about my recently built server. I want to know how to get to the server from outside the network? Like when i go to my IP address, it takes me to the router, so is there a way to get to the server form there?
The reason i want to do this is so i can display my apache web server or just ssh into the server from outside of my network. I'm guessing it is some setting in the router perhaps?

---

### Post by p_quarles on 2007-12-28
> **e1ektrob0y said:**
> I have a question about my recently built server. I want to know how to get to the server from outside the network? Like when i go to my IP address, it takes me to the router, so is there a way to get to the server form there?
The reason i want to do this is so i can display my apache web server or just ssh into the server from outside of my network. I'm guessing it is some setting in the router perhaps?
Yep. You'll need to setup your router to use port forwarding. Basically, you'll choose the ports (defaults are 80 for http and 22 for ssh) you want to forward, and tell the router to send to send those requests to the server's network IP address.

---

### Post by e1ektrob0y on 2007-12-28
> **p_quarles said:**
> Yep. You'll need to setup your router to use port forwarding. Basically, you'll choose the ports (defaults are 80 for http and 22 for ssh) you want to forward, and tell the router to send to send those requests to the server's network IP address.

ok cool, and i can still get to the 192.168.1.1 router LAN address after doing this right?

---

### Post by p_quarles on 2007-12-28
Yeah. Your router will forward requests to the public IP address to the server, but requests to its LAN address will still be picked up by the router config interface.

---

### Post by e1ektrob0y on 2007-12-28
hmm, i tried this...
[IMG]http://i74.photobucket.com/albums/i247/dales618/port_forwarding.jpg[/IMG]
but it still just goes to the router :(

---

### Post by p_quarles on 2007-12-28
The router doesn't know its own public IP address -- that's supplied by whatever DNS server the router is connected to. Either delete the public IP or replace it with the router's LAN address, whichever the interface allows you to do.

---

### Post by e1ektrob0y on 2007-12-29
Ok, that works! Thanks. Is there a way to then make it password protected so not just anyone can go there?

---

### Post by p_quarles on 2007-12-29
> **e1ektrob0y said:**
> Ok, that works! Thanks. Is there a way to then make it password protected so not just anyone can go there?
Not at the router level. In order to make a login page, you'll need to configure Apache itself to provide that service. This will require you to use a server-side scripting language (such as Python, PHP, Ruby) and a database (e.g., MySQL, PostgreSQL) to manage user information and login.

---

