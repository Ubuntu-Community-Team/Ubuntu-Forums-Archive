---
title: "speed up system a bit"
date: 2007-05-28
forum: Absolute Beginner Talk
---

### Post by firedancer on 2007-05-28
> .Code:

127.0.0.1       localhost inspiron
127.0.1.1       inspiron
..so I added my hostname behind local host 

this is a change that will speed up anyone 's system a bit according to the thread 

Q: i still have   'hostname-desktop'  , do i just type in 'hostname -desktop' behind local host ?

i dont see any with '-desktop' behind the hostname (i left it like this i guess)

need some speed

awaiting an answer

---

### Post by firedancer on 2007-06-01
does anyone else (who's viewing now)  know about this and whether it matters

---

### Post by Patrick K on 2007-06-01
I guess you are talking about the "hosts" file. It should already be there. Here is mine:
127.0.0.1	localhost
127.0.1.1	pk-desktop
(This is Edgy, Feisty doesn't use the "-desktop" part by default, although I don't know if it matters.)
I don't think it speeds up anything. But not having it can freeze up  DNS lookup. 

BTW, I use my hosts file to block many advertising sites. Here is a sample of how it's done:
> 127.0.0.1  ad.3ad.doubleclick.net
127.0.0.1  ad.3au.doubleclick.net
127.0.0.1  ad.ae.doubleclick.net
127.0.0.1  ad.ar.doubleclick.net
127.0.0.1  ad.au.doubleclick.net
127.0.0.1  ad.be.doubleclick.netWhen your browser gets a URL it looks first in the "hosts" file. If it finds the IP address listed there it uses that address. In the above example, the IP address is listed as 127.0.0.1 which is my computer. So instead of accessing doubleclick.net it connects to 127.0.0.1 and gets nothing back. The ads and any tracking are eliminated. You can get a premade host file here:
> This MVPS HOSTS file is a free download from:           #

# [http://www.mvps.org/winhelp2002/](http://www.mvps.org/winhelp2002/)  I just copy and paste it underneath the existing lines in the hosts file. You need to sudo to do this. Windows and Linux use the same format for the hosts file so using a windows version isn't a problem.

You can also enter often used URLs with the correct IP address. That will speed up site access since the computer has the IP address stored locally and doesn't need to go to a DNS server.

---

