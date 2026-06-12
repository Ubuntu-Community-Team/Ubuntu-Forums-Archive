---
title: "[SOLVED] File Server + MythTv?"
date: 2008-04-02
forum: Absolute Beginner Talk
---

### Post by Aysah on 2008-04-02
My tv recently gave out in a storm and well I dont want to buy a new one because I watch tv maybe 4 or 5 times a month.  Being that I just recently bought a rather decent laptop can I transform my desktop to a fileserver and also add the mythtv functionality?  And if I can, how well do you think it can handle the load of traffic between  5 computers? (only my laptop will be streaming the mythtv and the rest will be just storing stuff on the server)

---

### Post by Calash on 2008-04-02
I have a 2gig system that acts as a web server, mythtv backend and frontend, and file server.  It has no issues processing 3 PC's streaming music plus it's own overhead to watch live TV


What are the specs on the system?

---

### Post by Slushdoot on 2008-04-02
Yep, that's a great idea.  You'll need to add a capture card to the server and on the server you'll run your Myth backend.  On the laptop you'll run your myth frontend and stream recorded TV shows and, if you choose, any other media you like using Samba or NFS shares.  A 100 Mbit network, as would be common in a home network, is more than sufficient for these tasks.

---

### Post by Aysah on 2008-04-02
Core 2 Duo running at 3.2Ghz?
4gb DDR2 Ram
3TB Sata Drive (Software Raid)
Dual NIC...

...do you think the router can handle the load or should I add DHCP capability to the server?  (not sure if that would be foolish or not to do)

---

### Post by AusIV4 on 2008-04-02
You should be able to do that with fairly minimal specs.

I set up a similar system with a Pentium D 2.93 Ghz, 512 MB of RAM. I ran a file server (to my laptop and xbox), and had 2 TV tuners for MythTV. One of my tuners did hardware Mpeg4 encoding, the other I had to do software encoding. Software Encoding + watching a show means you can't do much else unless you've got a pretty powerful system.

Let us know what your specs are and we can give you some better info.
[Edit] You posted your specs since I started my post. You should have no problem whatsoever with those specs.

---

### Post by Aysah on 2008-04-02
> **Slushdoot said:**
> Yep, that's a great idea.  You'll need to add a capture card to the server and on the server you'll run your Myth backend.  On the laptop you'll run your myth frontend and stream recorded TV shows and, if you choose, any other media you like using Samba or NFS shares.  A 100 Mbit network, as would be common in a home network, is more than sufficient for these tasks.

I've never actually used MythTv as of yet so when you mean "backend" and "frontend" I'm not quite sure what you are referring to.  Can you point me to a quick article?

So I'm guessing here the easiest setup would be to install Ubuntu Server and then add MythTv on top of it?  Sorry for the noobish questions

---

### Post by Slushdoot on 2008-04-02
The network you have is going to be just fine.  Serving files really is light on hardware requirements.

I run my MythTV backend and fileserver on a machine with waaaay less power than that, an 800 MHz P3 with 512 MiB RAM.

---

### Post by Aysah on 2008-04-02
> **AusIV4 said:**
> You should be able to do that with fairly minimal specs.

I set up a similar system with a Pentium D 2.93 Ghz, 512 MB of RAM. I ran a file server (to my laptop and xbox), and had 2 TV tuners for MythTV. One of my tuners did hardware Mpeg4 encoding, the other I had to do software encoding. Software Encoding + watching a show means you can't do much else unless you've got a pretty powerful system.

Let us know what your specs are and we can give you some better info.
[Edit] You posted your specs since I started my post. You should have no problem whatsoever with those specs.

So you recommend two Capture Cards?  What does hardware and software encoding actually do.  I just want to get a clear understanding so I'm not blindly just setting stuff up.

---

### Post by Slushdoot on 2008-04-02
> **Aysah said:**
> I've never actually used MythTv as of yet so when you mean "backend" and "frontend" I'm not quite sure what you are referring to.  Can you point me to a quick article?

So I'm guessing here the easiest setup would be to install Ubuntu Server and then add MythTv on top of it?  Sorry for the noobish questionsMythTV has a client/server model.  The backend is the server.  It takes care of recroding the shows and storing them in a database.  The frontend is the part the user uses.  It plays the files served by the backend.  You can have both of them on the same machine, or you can split them and have a dedicated backend with one or many frontends.  In even more advanced setups you can have multiple backends doing distributed processing, but that's beyond the scope of this discussion.  Check out the MythTV wiki for a ton of great info about every part of MythTV.

THe easiest thing to do, if you don't already have Linux installed, is to install Mythbuntu, a derivative of 7.10 that comes with a minimal GUI and makes it easier to set up MythTV. :)

---

### Post by Slushdoot on 2008-04-02
> **Aysah said:**
> So you recommend two Capture Cards?  What does hardware and software encoding actually do.  I just want to get a clear understanding so I'm not blindly just setting stuff up.Two capture cards are only necessary if you want to be able to record two streams simultaneously.  You probably don't need that.  A capture card with hardware encoding offloads the conversion from the analog stream into a format your computer can understand, usually MPEG2, from the CPU onto the card itself.  As such these are great for using in old, slow computers such as my own.  A card that needs software encoding is usually cheaper because it does not do its own processing.  Rather, it relies on the CPU to do that.  With a machine as powerful as yours you could go with either, though well-supported hardware encoders are relatively cheap.  I use and recommend the Huappage PVR-150.

---

### Post by Aysah on 2008-04-02
thank you everyone for your help and guidance...

I'm going to start cracking at this tonight

---

### Post by Slushdoot on 2008-04-02
Great!  Let us know how you get on. :)

---

### Post by shaft350x on 2008-04-02
I've been thinking about doing pretty much the exact same thing, so I'll be interested in how you come along with this.  I don't have a video capture card yet though, so this project is a bit further off for me.

---

### Post by Slushdoot on 2008-04-02
I've just done what he's describing as well.  Feel free to ask any question. :)

---

### Post by mikeserv on 2008-04-02
I've done it as well - only without any capture cards.  I've subscribed to rss feeds of divx and x264 files of my favorite shows, which my backend automatically downloads.  Then, thanks to some scripts I found and a bunch more that I wrote, backend catalogues said shows and grabs information about them off of the internet, at which time it adds them to the MythVideo database.  

My setup uses no capture cards whatsoever - just a lot of internet bandwidth.

-Mike

---

### Post by hooligan36 on 2008-04-03
I am wanting to build a machine for this. Should I install Mythbuntu or Mythtv? Is there an advantage of one over the other?

---

### Post by Calash on 2008-04-03
Mythbuntu is a veriant of Ubuntu that has MythTV already installed, along with a very nice control panel.  I would reccomend it as it is easy to get a basic MythTV setup going using it.

---

### Post by Slushdoot on 2008-04-03
Yep, MythTV is just a set of programs.  Mythbuntu is a variant of Ubuntu with an eye toward setting up a dedicated Myth system.  If you already have an Ubuntu system you can use many of the Mythbuntu packages. :)

---

