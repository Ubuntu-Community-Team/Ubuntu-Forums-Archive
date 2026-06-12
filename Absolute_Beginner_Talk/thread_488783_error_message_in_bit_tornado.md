---
title: "error message in bit tornado"
date: 2007-06-30
forum: Absolute Beginner Talk
---

### Post by Hranj on 2007-06-30
i got about a third of the way through this torrent and i had to pause it, i came back later to restart, and it was trying to connect to peers again and it came up with this error message
```
ERROR (6/30/2007) 4:14:56 PM) - 
Problem connecting to tracker - timeout exceeded
```

Whats going on? Will i have to start this torrent over again or will i just have to wait until i can connect again?

---

### Post by zarathustra on 2007-06-30
Are you sure it's your end and not the tracker that is having problems?

---

### Post by keithacole on 2007-08-03
i am having the same issue, none of my bit torrent clients work, but uTorrent via wine works

---

### Post by atomkarinca on 2007-08-03
have you tried forwarding the outgoing port of bittornado? (i don't remember what it is, let me have a look)

edit: i found these: [http://guides.radified.com/magoo/guides/bittorrent/bittorrent_03.html](http://guides.radified.com/magoo/guides/bittorrent/bittorrent_03.html)
[http://portforward.com/cportsnotes/bittornado/BitTornado.htm](http://portforward.com/cportsnotes/bittornado/BitTornado.htm)

---

### Post by Hallvor on 2007-08-03
> **Hranj said:**
> i got about a third of the way through this torrent and i had to pause it, i came back later to restart, and it was trying to connect to peers again and it came up with this error message
```
ERROR (6/30/2007) 4:14:56 PM) - 
Problem connecting to tracker - timeout exceeded
```

Whats going on? Will i have to start this torrent over again or will i just have to wait until i can connect again?


Probably just an overloaded tracker: 

> Usually you can ignore this, it seems to happen when the tracker is overloaded or otherwise flaky. 
Problem connecting to tracker - timeout exceeded 
Problem connecting to tracker - HTTP Error 503: Connect failed 
Problem connecting to tracker - [Errno socket error] (10061, "Connection refused") 
Problem connecting to tracker - (111, 'Connection refused') 
There was a problem contacting the tracker. Trackers tend to be heavily loaded, and connections sometimes fail. The best thing to do is just be patient and leave the client open. If you find you're getting this a lot, you can try increasing the HTTP request timeout by adding the parameter "--http_timeout 120" (the default is 60, unit is seconds.) See the FAQ section How do I change the command line parameters in Windows? if you need help doing this. 

[http://btfaq.com/serve/cache/35.html](http://btfaq.com/serve/cache/35.html)

---

