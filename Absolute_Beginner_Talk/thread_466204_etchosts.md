---
title: "/etc/hosts"
date: 2007-06-06
forum: Absolute Beginner Talk
---

### Post by OmnificienT on 2007-06-06
I did the following:
sudo gedit /etc/hosts
And then added the following line to it:
213.136.29.196 nl.archive.ubuntu.com 

What does this do exactly?

---

### Post by Songwind on 2007-06-06
It tells your computer that the address nl.archive.ubuntu.com resolves to the IP address 213.136.29.196

Basically, if your computer looks up an address that is in /etc/hosts it doesn't bother with DNS.

---

### Post by OmnificienT on 2007-06-07
So what's DNS exactly?

---

### Post by ticopelp on 2007-06-07
[http://en.wikipedia.org/wiki/Domain_name_system](http://en.wikipedia.org/wiki/Domain_name_system)

---

### Post by Rocket2DMn on 2007-06-07
Domain Name System.  Since all the computer understands is the IP address, the names have to be recognized like "google.com" points to a specific IP address.  People don't like numbers so we use names that get converted to IPs automatically for us.  It's like saving a phone number on your cell phone but you refer to it by the person's name.

---

### Post by Songwind on 2007-06-07
Domain Name Service.

You computer can only communicate with other machines by their IP address.  But humans don't like remembering all those numbers.  So, DNS exists so that we humans can tell the computer we want to talk to "www.ubuntu.com" and the computer can ask the DNS server what IP address that means.

---

