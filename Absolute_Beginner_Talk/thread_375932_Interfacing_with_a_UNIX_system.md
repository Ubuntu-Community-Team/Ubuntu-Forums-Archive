---
title: "Interfacing with a UNIX system"
date: 2007-03-04
forum: Absolute Beginner Talk
---

### Post by plastic96 on 2007-03-04
I have a computer with 6.06 running in my office (and quite well I might add:) ). Our billing and scheduling system (CMEDS) is a UNIX based system. Our Windows boxes communicate using a translation program called FacetWin. I would like to be able access CMEDS from the Ubuntu computer. I thought about trying to run FacetWin under WINE, but I don't know anything about WINE and I would rather access CMEDS directly from Linux if at all possible.

Can anyone help?:(

---

### Post by chggr on 2007-03-04
CMEDS is a program running on a server? Give us some more info concearning the program and the network topology you are using...

---

### Post by plastic96 on 2007-03-04
Well, I'm not 100% sure what you are looking for, but here's what I can tell you.
CMEDS is an SCO UNIX based scheduling and billing system running on a standalone Acer server. As to network topology, I think you are asking the following:
I have a 48 port switch that all of the computers including the windows boxes, Linux box and the server all hook up to, as well as accessing the internet via a broadband cable connection.

Thanks

---

### Post by chggr on 2007-03-05
Ok, that was the information I was looking for.

If the CMEDS is a command line program, you can set up the acer server to act as a SSH server. Then you can permit only your linux box IP address to connect to it using the ssh program. 

If the CMEDS is a GUI program, then you can set up X-Window to remotely log in into the acer server and run the program. I haven't tried this thing in the past, so my knowledge on that stops here...

---

### Post by plastic96 on 2007-03-05
Thanks. Looks like I have a lot to learn about this. The SSH program looked really intimidating at the newbie level(that's me all the way, but learning)

---

