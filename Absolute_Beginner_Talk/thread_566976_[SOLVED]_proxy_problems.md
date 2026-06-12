---
title: "[SOLVED] proxy problems"
date: 2007-10-04
forum: Absolute Beginner Talk
---

### Post by simon303 on 2007-10-04
I have just arrived at uni and they have proxies to access the internet from your room
I got it working in firefox using their Automatic Proxy Configuration and in synaptic using a proxy server and port
But I cant get gaim to connect to the internet, even by setting global network proxies (system --> preferences --> network proxies)
I would appreciate any suggestions to get this working

---

### Post by izhar81 on 2007-11-30
why not you share how to solve the problems on Synaptic + Automatic Configuration Url to us..

 because i'm stuck with the same problem too...

---

### Post by vikramsharma on 2007-11-30
> **izhar81 said:**
> why not you share how to solve the problems on Synaptic + Automatic Configuration Url to us..

 because i'm stuck with the same problem too...

Launch "Synaptic Package Manager" in there goto the "Settings" in there goto "Preferences" in there click on "Network" tab enter in your http and ftp proxy..  That should do it.

---

### Post by izhar81 on 2007-11-30
but it is not Automatic Proxy configuration..

if i have just Automatic Proxy Configuration url...

what i should key in there?

---

### Post by simon303 on 2007-12-03
sorry, haven't been on here for a while.
for automatic proxy go to system --> prefecences --> network proxy
it should be the bottom option

---

### Post by izhar81 on 2007-12-06
thank for your help,

but i already done that..

my synaptic still not working... my default firefox also not working eventhogh i already put Automatic Proxy Configuration in firefox menu.

The only thing which working for me is only Opera...

---

### Post by simon303 on 2007-12-06
what worked fo me with synaptic was to open synaptic and change the network setting in preferences. for this unfortunately you need a http proxy. not sure with firefox, mine worked when i put in the auto config url

---

### Post by batty007 on 2007-12-06
Hi

New to this but we use a proxy at my work

Aside from putting the proxy in the system > preferences> network proxy:
Firefox Proxy

You need to go you your terminal and do the following commands

sudo export http_proxy=http://<proxy address>:<port>

Then refresh the network with the following command

sudo /etc/init.d/networking restart

Thats how i've managed to get mine working!

Hope it Helps!

---

