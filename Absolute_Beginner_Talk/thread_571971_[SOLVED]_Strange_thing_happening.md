---
title: "[SOLVED] Strange thing happening"
date: 2007-10-09
forum: Absolute Beginner Talk
---

### Post by rdsii64 on 2007-10-09
I was messing around with my linux box today and decided to play with nmap. when I started the program it immediately informed me that I was not root and some options would not be available. So I logged out and tried to log in as root. 
Here is where the strange stuff started happening.  I then got an error msg stating that the administrator could not long in at the long in prompt. So to get around that I logged back in with my regular user account and went to the terminal. entered the su command and typed in my password. the I ran the graphical front end of Nmap and got the same msg that I was not root.

How do I run the graphical front end of nmap as root?

---

### Post by llamakc on 2007-10-09
gksudo nmap

---

### Post by zetsumei on 2007-10-09
Try typing

```
gksudo nmap
```

in the terminal

---

### Post by rdsii64 on 2007-10-09
I ran that command and I could run nmap from the console. this is ok I guess. But what I wanted to do was run the graphical front end as root. This part still escapes me.

thanks.

---

### Post by llamakc on 2007-10-10
Run "gksudo WITH-THE-NAME-OF-THE-COMMAND"

for the graphical front end.

Which one of these have you installed?

[http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nmap&searchon=names&subword=1&version=feisty&release=all](http://packages.ubuntu.com/cgi-bin/search_packages.pl?keywords=nmap&searchon=names&subword=1&version=feisty&release=all)

---

### Post by The Tronyx on 2007-10-10
> **rdsii64 said:**
> I ran that command and I could run nmap from the console. this is ok I guess. But what I wanted to do was run the graphical front end as root. This part still escapes me.

thanks.

gksudo nmapfe

Assuming you have the graphical front end installed.

Hope that helps :guitar:

---

### Post by rdsii64 on 2007-10-10
> **2point0 said:**
> gksudo nmapfe

Assuming you have the graphical front end installed.

Hope that helps :guitar:
thanks. worked like a charm

---

