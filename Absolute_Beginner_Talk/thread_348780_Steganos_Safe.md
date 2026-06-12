---
title: "Steganos Safe"
date: 2007-01-29
forum: Absolute Beginner Talk
---

### Post by Norfolk 'n' Good on 2007-01-29
Hi,

Does anyone know if there is a version of Steganos Safe or a similar product that will run on linux?  Preferably not through Wine.

Thanks.

---

### Post by BarfBag on 2007-01-29
What is Steganos Safe?  Can you post a link to the website?

---

### Post by an.echte.trilingue on 2007-01-29
I looked up their website, and I am not sure what exactly that piece of software is supposed to do.

There are a wide variety of encryption tools in Ubuntu, you can even encrypt the entire hard drive (no need for the 256MB limit that this piece of software seems to impose).  There are also a variety of secure delete tools, and you can easily annonymize your web surfing.  Linux is a privacy freak's dream, so to speak.

If you let us know more precisely you want to do, we can probably help you select the tool(s) that are right for you.

Beware, though, you are going to have to face a learning curve.

Take care,
-mat

---

### Post by an.echte.trilingue on 2007-01-29
> **BarfBag said:**
> What is Steganos Safe?  Can you post a link to the website?

I think the OP was talking about [this]("http://www.steganos.com/?product=safe8&layout=web2005&language=en")

---

### Post by Norfolk 'n' Good on 2007-01-29
Thank you for your swift replies.

In answer to the question above... I'm looking for a piece of software to create an encrypted virtual drive, preferably with a GUI.  Any information on anonymous surfing will be helpful too and software that allows for secure deleting.

Kind regards.

---

### Post by an.echte.trilingue on 2007-01-29
I don't think that you are are going to find this in GUI form.  If you are serious about keeping your data private, you don't want that anyway; GUIs will hide things from you that you might want to know about.

So, Encryption:
[1.  Your entire harddrive including the OS]("http://www.debianhelp.org/node/1116")
[2.  Single partitions]("http://www.debian-administration.org/articles/469")
[3.  Creating encrypted folders within your partition]("http://www.debian-administration.org/articles/204")

Secure delete:
The package secure-delete (sudo aptitude install secure-delete) contains two commands that you probably care about: 
1.  srm: is used just like the command line tool rm (delete), except that srm overwrites the file upwards of 32 times with a pattern designed to make the file unrecoverable.  It is the best tool available today.
2.  sfill: sfill overwrites all of the empty space with the same pattern as srm, thus obliterating any unsecurely deleted files.  You can run this at any time.  
The two tools in tandem are ideal for overwriting your drive before selling your computer.  When I was in the military we occasionally used these to wipe drives on old life-cycle replacement computers before turning them into the re-usage guys.  The package also contains tools to overwrite swap space and your RAM.

Anonymous surfing:
The [Tor onion network]("http://en.wikipedia.org/wiki/Tor_%28anonymity_network%29") keeps you anon.
Here are the [install instructions.]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian")  Don't use the version that comes with ubuntu.  You will need to add a line to your sources.list.
Here are the [usage instructions.]("http://tor.eff.org/docs/tor-doc-unix.html.en")

Let me know if this helps!
Take care
-mat

---

### Post by Norfolk 'n' Good on 2007-01-29
Thanks very much for the information Mat, I'll have a play later and let you know how I get on.

Kind Regards. 

Mark.

---

