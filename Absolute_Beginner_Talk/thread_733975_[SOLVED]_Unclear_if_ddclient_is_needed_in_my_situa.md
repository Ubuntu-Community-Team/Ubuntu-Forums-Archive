---
title: "[SOLVED] Unclear if ddclient is needed in my situation"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by BlizzofOZ on 2008-03-24
I have Ubuntu 7.10 server installed, which is working behind a Linksys WRT45GL router.

I had noticed that my IP kept changing as I had removed power to the router.

I then got myself a DNS name from dyndns.com.

I reflashed the routers's firmware with DD-WRT and added the MAC addresses of the computers that will be on that router.

What I am unclear about is if I need install and use ddclient on the server.  Is it necessary with this router/firmware version?

---

### Post by teaker1s on 2008-03-24
if your router supports dyndns or similar then that is all you need to set up. you need ddclient if you are hosting multiple sites off one server as most routers I've come across only support one instance. 

After setting up dyndns on router you will need a static ip address and set up http port forwarding

---

### Post by BlizzofOZ on 2008-03-24
> **teaker1s said:**
> if your router supports dyndns or similar then that is all you need to set up. you need ddclient if you are hosting multiple sites off one server as most routers I've come across only support one instance. 

After setting up dyndns on router you will need a static ip address and set up http port forwarding

Just to make sure I understand... when you say "supports dyndns", do you support the site dyndns where I setup my dns name?

If so, how do I tell that?

---

### Post by BlizzofOZ on 2008-03-24
Bump...

---

### Post by louieb on 2008-03-24
Go into your routers configuration. typically 192.168.1.1 in your browsers address bar.  See if you have an option to put in you dyndns user name and password. Can't tell you about your router I use a netgear.

If your router doesn't support dyndns then you will have to use ddclient.

---

### Post by BlizzofOZ on 2008-03-24
> **louieb said:**
> Go into your routers configuration. typically 192.168.1.1 in your browsers address bar.  See if you have an option to put in you dyndns user name and password. Can't tell you about your router I use a netgear.

If your router doesn't support dyndns then you will have to use ddclient.

Thanks for the response!

I guess I'm unclear then as to where I would put in my dyndns user name and password.   What section/heading/name would I find this?

Again, using DD-WRT firmware.

---

### Post by teaker1s on 2008-03-24
may be under dns settings, i use alternative firmware in my wag200

---

### Post by BlizzofOZ on 2008-03-27
Yes, I found it in the DD-WRT firmware on my WRT54GL router... and yes it supports Dyndns.org

Thanks!!!

---

### Post by teaker1s on 2008-03-28
:KS so you have a server/website up and running yet? mine just family photo's and thinking of joining folding at home with it on idle time

---

### Post by BlizzofOZ on 2008-03-28
> **teaker1s said:**
> :KS so you have a server/website up and running yet? mine just family photo's and thinking of joining folding at home with it on idle time

I've had my server up and running... what I was trying to do was be able to remote into the server from my Win machine as I didn't want a monitor, keyboard, etc attached to the server.  I am able now use Putty and TightVNC to do so... I was also trying to able remote in from work, but work must block ports as I can't do that.

Additionally, I have Samba up and running so I file share between machines.

But,  website/webserver sounds interesting... would this allow others (that I would allow) to be able to download stuff from my server?  Can you point me to some on this?

---

