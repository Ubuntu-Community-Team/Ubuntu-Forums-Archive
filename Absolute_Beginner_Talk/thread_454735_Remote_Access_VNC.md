---
title: "Remote Access VNC"
date: 2007-05-25
forum: Absolute Beginner Talk
---

### Post by Mazen on 2007-05-25
I would like to remote access my laptop from other locations, and i've been told that i should use VNC, i installed the Server on my ubuntu but from there on i don't know how to open the ports, get the IP or anything,
Anyone has an idea?or a HOWTO?
Thanks

---

### Post by Mazen on 2007-05-25
anyone?

---

### Post by Inxsible on 2007-05-25
you need to keep the VNCServer running on your ubuntu machine.

Then from a client machine (any machine with which you want to access your ubuntu machine ) you need to connect to it. For this you will need the IP address of your ubuntu machine.

on your client machine
```

sudo aptitude install xvnc4viewer

```

Then start the viewer like so
```

xvnc4viewer <IP address of your ubuntu machine>

```

It will ask for the password that you have set up and will allow you to connect.

As for the opening of ports, you need to open port 5900 on your router and/or firewall(s) that you have installed on the ubuntu machine


Hope that helps

---

### Post by Mazen on 2007-05-25
but first i have to set up a Dynamic DNS? or that's totally unrelated?

---

### Post by Mazen on 2007-05-25
?!

---

### Post by owise1 on 2007-05-25
Have a look at [http://www.cs.vu.nl/~eliens/documents/vnc/start.html](http://www.cs.vu.nl/~eliens/documents/vnc/start.html)

Suggest that reading some of the material / documenation is the best way to go.  There are also several other posts in this forum about VNC.  Google around.

cheers

---

### Post by Mazen on 2007-05-25
10x!!

---

### Post by lazyart on 2007-05-25
It helps to have a dynamic dns account-- that way you can access your computer by name instead of a constantly changing IP address.

I use [http://www.dyndns.org]("http://www.dyndns.org") but there are others.  Once you've set up an account there you'll need to install a dynamic dns client on your server (or any machine on your network that is on 24/7).  There are some in the repositories.  The client periodically checks your ip address and if it has changed, will report it to the site where you have your account.

When you are away from home, fire up a VNC client and put the name you designated in as the server name.  Provided you have opened port 5900 at home you should be greeted with your desktop.

You will want to password protect your VNC access if you are exposing it to the world.  I'm not sold that it's totally safe that way (I watched someone come thru my password protected windows box, but that might be apples to oranges).

---

