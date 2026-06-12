---
title: "Ubuntu server security"
date: 2007-03-20
forum: Absolute Beginner Talk
---

### Post by fatphilthethird on 2007-03-20
Hi

I am trying to set up an old box to use as a development web server and it's connected to my desktop via a router (Netgear DG834). I've installed ubuntu server and upgraded to apache2 and I can connect to the ip address through the browser on the desktop (edgy-eft). 

Complete newbie question: As the box is behind my router, can only the LAN see it? I'm assuming yes, but if someone could either confirm it, or point me in the direction of some information, I'd be very thankful. All the stuff I've found so far seems to be aimed at something far more complicated than my simple set up. 

I'm happy to play about with anything else until it breaks, just didn't want to mess around with it wide open.

Thanks; sorry; feel free to chuckle away at the poor fool...

Fat

---

### Post by h0ax on 2007-03-21
If port 80 is not open on your router, nothing can come in on port 80 (ie, to your webdev server)

Look at your router as a filtering device, which it is as a Layer 3 smart switching device.  If you have nothing open on your router, Looking IN from the OUTSIDE will be fruitless, therefore your server is not visible.

If you open 80 on the machine of your webdev... then it will be visible to the outside world.

No need to chuckle - we're here to help - I hope you have a better understanding now

---

### Post by scxtt on 2007-03-21
yeah, like h0ax said, you have to allow people to see your webserver when your box is on a router ... if i was to view your website, it'd be like this

my browser --> internet --> your ip --> your modem --> your router (192.168.1.1) --> your webserver (192.168.1.100)

so if your router doesn't say "any request for port 80 (HTTP) goes to 192.168.1.100" - then no one can see your website ... and all modern routers allow you to forward requests for common and specified ports ...

---

### Post by fatphilthethird on 2007-03-21
That's great, many thanks to you both for replying and setting my mind at ease

Had terrible visions of turning my dev box into a wide open server and my ISP kicking my ar*e ; )

Cheers

Fat

---

