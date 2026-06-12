---
title: "malicious individual to damage or take control of your system (solved)"
date: 2006-10-25
forum: Absolute Beginner Talk
---

### Post by wadehel on 2006-10-25
My update summary show something like this:

You are about to install software that cant be authenticaded! doing this could allow a malicious individual to damage or take control of your system.

I think this happen after i add Trevino's repository ([http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0) Into my /etc/apt/sources.list in order to install flash 9. Beside flash, there are stardict, stardict-tools, and xserver-xorg-input-synaptics updates offered by the rep.

The question:
Is it safe to add [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0 to my list?
How can i know if it malicious or not?
Where can we check if a source is safe or not?

Thanks.

---

### Post by Bachstelze on 2006-10-25
Where did you get the URL from ? It should be OK but you never know...

If you feel the repo can be trusted, run that command to get rid of the messages :

```
wget http://3v1n0.tuxfamily.org/EDD1E155.gpg -O- | sudo apt-key add -
```

---

### Post by wadehel on 2006-10-25
i get it from here:

[http://everythingelse.wordpress.com/2006/10/23/howto-install-flash-9-beta-on-ubuntu-the-easy-way/](http://everythingelse.wordpress.com/2006/10/23/howto-install-flash-9-beta-on-ubuntu-the-easy-way/)

---

### Post by Bachstelze on 2006-10-25
I guess it should be fine then.

---

### Post by wadehel on 2006-10-25
**I have enter this:**
```
 wget [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg) -O- | sudo apt-key add -

```**then it show this:**
```
 --01:49:13--  [http://3v1n0.tuxfamily.org/EDD1E155.gpg](http://3v1n0.tuxfamily.org/EDD1E155.gpg)
           => `-'
Resolving 3v1n0.tuxfamily.org... 212.85.158.4
Connecting to 3v1n0.tuxfamily.org|212.85.158.4|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,374 (2.3K) [text/plain]

100%[===========================================================>] 2,374          1.72K/s

01:49:19 (1.72 KB/s) - `-' saved [2374/2374]

OK
```I guess that means ok, then i do this:
```
 sudo apt-get update
```then some of those line show this message:

```
Hit [http://3v1n0.tuxfamily.org]("http://3v1n0.tuxfamily.org/") dapper Release
Err [http://3v1n0.tuxfamily.org]("http://3v1n0.tuxfamily.org/") dapper Release

Hit [http://security.ubuntu.com]("http://security.ubuntu.com/") dapper-security/universe Sources
Get:8 [http://3v1n0.tuxfamily.org]("http://3v1n0.tuxfamily.org/") dapper Release [2995B]
Ign [http://3v1n0.tuxfamily.org]("http://3v1n0.tuxfamily.org/") dapper Release
Hit [http://3v1n0.tuxfamily.org]("http://3v1n0.tuxfamily.org/") dapper/3v1n0 Packages
Fetched 3570B in 24s (145B/s)
Reading package lists... Done
W: GPG error: [http://3v1n0.tuxfamily.org]("http://3v1n0.tuxfamily.org/") dapper Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
W: You may want to run apt-get update to correct these problems
```

What is wrong, is the server dead?

Btw, is this flash 9 (beta?) worth the pain?

---

### Post by aidanr on 2006-10-25
why not just grab it from the adobe site, it's a piece of cake to install it manually, it's just copying 1 file into your mozilla plugins directory

---

### Post by barkej on 2006-10-25
Just grab it from adobe. It's a cinch to install.

---

### Post by wadehel on 2006-10-26
thankyou, i never think about that, silly me :P

thankyou verymuch

---

