---
title: "Music Server questions"
date: 2008-04-09
forum: Absolute Beginner Talk
---

### Post by billgoldberg on 2008-04-09
I followed this [easy how-to]("http://tuxtraining.com/2008/03/05/gnump3d-mp3-server/") to install a music server (gnump3d) on my pc.

I can access the server @ [http://localhost:8888](http://localhost:8888)

I made it so I can access my music collection from my laptop.

How would I connect from my laptop to this music server ?

The laptop is in the shop right now so I can't test it.

Would I just browse to localhost:8888 ?

Will I have to change stuff in my router, or in firestarter?

Will friends who have xp or vista be able to access it the same way I would access it from my laptop?

Will streaming this audio to other computers have any impact on my internet bandwith consumption (35gb limit :( )?

And the final question:

Is this hooked to the internet? I don't want it to be hooked to the internet.

---

### Post by buried on 2008-04-09
First of all to help you, you gotta help me help you..lol
Are all the PC's/Laptops connected to one same LAN/Router if so, the music server can be accessed via localhost, if it is in different places then It's complicated.

---

### Post by billgoldberg on 2008-04-09
They are all on the same router.

So it would just be going on any of the computers and browsing to localhost:8888 ?

---

### Post by billgoldberg on 2008-04-09
Will streaming music in the network affect my internet bandwith consumption?

I think not, but I'm not 100% sure.

Will I need to open up ports on the router, or change settings in the firewalls?

---

### Post by DigitalDuality on 2008-04-10
> **billgoldberg said:**
> I followed this [easy how-to]("http://tuxtraining.com/2008/03/05/gnump3d-mp3-server/") to install a music server (gnump3d) on my pc.

I can access the server @ [http://localhost:8888](http://localhost:8888)

I made it so I can access my music collection from my laptop.

How would I connect from my laptop to this music server ?

The laptop is in the shop right now so I can't test it.

Would I just browse to localhost:8888 ?

Will I have to change stuff in my router, or in firestarter?

Will friends who have xp or vista be able to access it the same way I would access it from my laptop?

Will streaming this audio to other computers have any impact on my internet bandwith consumption (35gb limit :( )?

And the final question:

Is this hooked to the internet? I don't want it to be hooked to the internet.

Taking that your music server and your laptop are 2 different machines, and that gnump3d is on the pc/music server, if you are on your laptop, localhost will not take you anywhere.]

localhost  or 127.0.0.1 (same thing) point your browser to your own machine taking that you are running a webserver (apache, lighhttp, IIS) on that machine.   


If  you are using the default connection settings (it appears you are), then on the music server your firewall (firestarter or other) must allow incoming traffic on port 8888.   You will also have to forward a port on your router to 8888 as well.

So lets say your external IP address is 61.61.61.210 **(just made it up**), you can see what your external ip is by visiting [www.ipchicken.com](www.ipchicken.com) from your music server (or your laptop if you are hooked to the same connection as your music server)

So when you are not at home (or whererver the music server is) you would go to [http://61.61.61.210:8888](http://61.61.61.210:8888)

So it would go from your laptop to your home connection, the router will see you're hitting the 8888 port and should forward it to the internal  ip/port of the music server.

Anyone on any OS will be able to access this site unless you setup something to block them from doing so.

---

### Post by DigitalDuality on 2008-04-10
> **billgoldberg said:**
> Will streaming music in the network affect my internet bandwith consumption?

I think not, but I'm not 100% sure.

Will I need to open up ports on the router, or change settings in the firewalls?

It will use up some bandwidth but not enough to be noticable.

---

