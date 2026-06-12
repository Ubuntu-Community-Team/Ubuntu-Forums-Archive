---
title: "can't connect with GAIM"
date: 2006-04-25
forum: Absolute Beginner Talk
---

### Post by Isoss on 2006-04-25
This is my first time using gaim, but it's not working at all.
I hv a good connection (ADSL) and I use MSN, Yahoo, Google talk, Skype everyday ... now I created my acounts with gaim, but non of them seems to work:

[email]Account@hotmail.com[/email] has been disconnected.

Connection error from Notification server
(messenger.hotmail.com):
Unable to connect

[email]Account@gmail.com[/email]/Gaim has been disconnected

Couldn't connect to host

Why do u think this is happening?

could it be of the internet provider? if not, what could the problem be?

---

### Post by jason.b.c on 2006-04-25
[QUOTE=Isoss]This is my first time using gaim, but it's not working at all.
I hv a good connection (ADSL) and I use MSN, Yahoo, Google talk, Skype everyday ... now I created my acounts with gaim, but non of them seems to work:

[email]Account@hotmail.com[/email] has been disconnected.

Connection error from Notification server
(messenger.hotmail.com):
Unable to connect

[email]Account@gmail.com[/email]/Gaim has been disconnected

Couldn't connect to host

Why do u think this is happening?

could it be of the internet provider? if not, what could the problem be?[/QUOTE]


Try [www.aim.com](www.aim.com), set up an account there .. It works for me..                                     

Then just make sure that **Gaim** is set for   " *Aim/Icq* "

---

### Post by Isoss on 2006-04-25
Hey ... thanks

but will this make me login with msn account, yahoo and google talk acounts?

---

### Post by Lerris on 2006-04-28
I'm having the same issue - I have established accounts with ICQ, Yahoo, MSN, AOL, Google and they work great in Windows. I try to connect in gaim and sometimes they do sometimes they don't - same error message: Couldn't connect to host. If I keep hitting the reconnect button eventually (sometimes) it connects.

---

### Post by Lerris on 2006-04-28
[QUOTE=Lerris]I'm having the same issue - I have established accounts with ICQ, Yahoo, MSN, AOL, Google and they work great in Windows. I try to connect in gaim and sometimes they do sometimes they don't - same error message: Couldn't connect to host. If I keep hitting the reconnect button eventually (sometimes) it connects.[/QUOTE]

I solved my issue - hopefully this will solve yours. It seems to have something to do with the way I had my DNS set up.

I opened up the System | Administration | Networking and clicked on the DNS tab. I then removed all my DNS entries (I had two assigned from my DHCP server). I then added the two DNS servers my router/dsl modem is using on the outside world then my router/modem. I had all those DNS entries in there before but not in that order (if that makes a difference).

Hope this helps.

---

### Post by Isoss on 2006-05-01
I have  a proxy server ... I entered the proxy and the port in the Preferences -> Network with a proxy type HTTP ... 

In the Modify Account, Proxy Options I set it to HTTP, and entered the Host proxy and the port same as the ones entered in the Preferences -> Network.

now as I try to login it tells me: 

Access denied: proxy server  forbids port 1863 tunnelling.

What is that supposed to mean? does it mean that my ISP company forbids this port tunnelling?

is there anther port that would help connecting to messenger.hotmail.com?

---

