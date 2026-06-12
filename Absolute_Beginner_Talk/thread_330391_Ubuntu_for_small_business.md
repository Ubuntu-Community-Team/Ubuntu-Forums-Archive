---
title: "Ubuntu for small business"
date: 2007-01-03
forum: Absolute Beginner Talk
---

### Post by Jupio on 2007-01-03
Hello, 

Just new here and want to say hello to everybody.

I have a question i want to setup Ubuntu for a small business, can you guide me to some more relevant info on this subject here?

I did a search but not much result.

thx
Jupio

---

### Post by Sasa_Ivanovic on 2007-01-03
define small business...

---

### Post by rbalfour on 2007-01-03
> **Jupio said:**
> Hello, 

Just new here and want to say hello to everybody.

I have a question i want to setup Ubuntu for a small business, can you guide me to some more relevant info on this subject here?

I did a search but not much result.

thx
Jupio

Define your requirements. 

Example:

1) File sharing with Windows Client
2) Mail server
3) Print Server
4) Web Server
5) Soft PBX

---

### Post by Jupio on 2007-01-03
Sorry, i want to run accounting- and stockadministration software. 

The business will be with two persons. 

There is a office and an place to put stocks. The office and stockplace must be connected (by computers) regarding the relevant stock position etc (so we both can see what the level is.

and the things you mentioned:

1)File sharing with Windows Client
2) Mail server
3) Print Server
4) Web Server
5) Soft PBX (what is this...?)

will be glad if you could point me to the relevant info, especially the stockadministration software.

Thx
Jupio

---

### Post by rbalfour on 2007-01-03
> **Jupio said:**
> 

1)File sharing with Windows Client

Samba for file sharing
> 
2) Mail server

(I know the hardcore will flame/shootme) But I use Kerio Mail server. Good groupware for all. I use Linux, but my Partners use Windows (outlook) So calendar sharing is a big thing.
> 
3) Print Server

Samba again
> 
4) Web Server

On server install, if you use Ubuntu, choose LAMP. That will give you the Apache (web server) and MySQL (database)
> 
5) Soft PBX (what is this...?)

[www.asterisk.org](www.asterisk.org) , Telephones via Internet / POTS / GTALK and many more
> 
will be glad if you could point me to the relevant info, especially the stockadministration software.

In my experience, this is a custom application. I have built a few for Fund management / Stock and bond trading / Stock execution here in Tokyo. So you will want to shop around. I am sure you know your business, Open Source just doesn't have anything for this type of business, YET! Hopefully in the near future we will. If you keep your base open source, this will keep your options open. A build I use alot is Ubuntu 6.06.1LTS Server with LAMP option / Samba / IPtables / Asterisk.

---

### Post by magicfab on 2007-01-29
For asterisk you can try to see this guide:
[https://wiki.ubuntu.com/AsteriskOnUbuntu](https://wiki.ubuntu.com/AsteriskOnUbuntu)

Be warned, however, that the FreePBX part has not been tested. The document is work in progress.

---

