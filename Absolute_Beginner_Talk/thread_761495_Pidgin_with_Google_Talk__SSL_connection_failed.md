---
title: "Pidgin with Google Talk : SSL connection failed"
date: 2008-04-21
forum: Absolute Beginner Talk
---

### Post by kaanstiklix on 2008-04-21
Hi,
I'm using gutsy and i'm unable to use pidgin to log on to google talk. My account settings are as follows,

Basic:
Protocol: XMPP
Screen Name:Gmail id(without @gmail.com)
Domain:gmail.com
Resource:Home
Password:*********
Local Alias:---

Option remember password-checked

Advanced:
Require SSL/TLS: Checked
Force old(port 5223) SSL: Checked
Allow plaintext authorization over unencrypted streams: Checked

Connect Port:433
Connect Server:talk.google.com

Proxy Options:

Proxy Type: HTTP
Host: 127.0.0.1
Port:5865

i'm behind a proxy server and i'm using cntlm for authorization. I dont' think there's anything wrong with my proxy settings as i'm using the same for firefox and it's working fine. 
The error I get is : 

[email]username@gmail.com[/email]/Home disconnected
SSL Connection Failed

Any help would be appreciated..
Thanks in advance.

---

### Post by aktiwers on 2008-04-21
Get the latest version of Pidgin
[http://www.getdeb.net/app/Pidgin](http://www.getdeb.net/app/Pidgin)

It has Google Talk integrated so you just pick it like you pick MSN or whatever.. lot easier. :)

---

### Post by kaanstiklix on 2008-04-22
I tried that and i'm still getting the same error. The proxy I'm behind doesn't allow 5222 tunneling. The same settings seem to work for everyone else.:confused:

---

### Post by meditatingfrog on 2008-04-22
I'm using pidgin ver 2.2.1 on google talk, but I'm not behind a proxy.  I just did a google search, and it says you can use port 443 instead of port 5222.  Here's the link:  [URL="http://www.google.com/support/talk/bin/answer.py?hl=en-au&answer=27930"]
[/URL]

Hope it helps!

MeditatingFrog

---

### Post by kaanstiklix on 2008-04-22
It's been sorted out.. the connect port was 443
not 433, d'oh! 
the noob apologizes.

---

### Post by kaanstiklix on 2008-04-22
and many thanks, meditating frog.:)

---

