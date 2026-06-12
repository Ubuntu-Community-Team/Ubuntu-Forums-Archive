---
title: "p2p messenger clients for Linux and Windows users?"
date: 2006-11-22
forum: Absolute Beginner Talk
---

### Post by gresses1 on 2006-11-22
Hello,
I am a nube to LInux.  I am looking for an I.M. client that can be used between ip addresses that will allow p2p messages (file transfer not necessary) without the need to use a server.  Can someone suggest clients that would be useful for this and a location for a nube to use in installing same?

Thank you.:-?

---

### Post by haxer on 2006-11-22
Maybe frostwire? sudo apt-get install frostwire?

---

### Post by gresses1 on 2006-11-22
Thank you for your response.  I am not familiar with frostwire.  Is there a link that you can send me which would allow me to educate myself on this app?
Is it already packaged with 6.06?

Thank you.

---

### Post by gresses1 on 2006-11-22
I have found a site for LICQ, for Linux.  Does anyone know anything about this?
THanks.

[http://www.freeos.com/articles/4205/www.licq.org/www.licq.org/](http://www.freeos.com/articles/4205/www.licq.org/www.licq.org/)

---

### Post by Rhubarb on 2006-11-22
Frostwire is a p2p file transerring program.  It's not designed to send IM around.

There is a promising Program called CSpace.  You will need to compile it yourself (for linux, not for the windows version).
It's completely p2p, uses 2048 bit encryption, uses the kademlia network, supports IMing and file transfer.
It works much like a normal IM client like GAIM or aMSN.

CSpace website:
[http://cspace.in/](http://cspace.in/)

Linux version:
[http://www.aabdalla.com/cspace/](http://www.aabdalla.com/cspace/)

I'm a bit of a newb here too, so I haven't compiled the programme yet.  But I do know a few linux users that have, and everything works successfully.

---

### Post by Rhubarb on 2006-11-22
Licq is not p2p, it still has to talk to the ICQ server on the 'net.
... Are you sure you want proper a proper p2p IM (Instant Messenger)?

Because if you don't, then I'd recommend you sign up on yahoo or icq then use GAIM as your IM.
By default GAIM is already installed in Ubuntu.
Windows clients can just use GAIM for windows, or use the "proper" IM program for icq / yahoo / whatever.

---

### Post by gresses1 on 2006-11-22
Thanks.  I want to avoid the hastle of our IT police.  I just want to IM inside our firewall without having to go outside and open myself up to hacking.

---

### Post by gresses1 on 2006-11-22
In addition, I do not know how to compile something for Linux.  A little help in the right direction would be great. :neutral:

---

### Post by gresses1 on 2006-11-22
Went to Cspace.  Would this be the compile syntax?
Thanks.
Installing the ebuild

NOTE: This requires ncrypt to be installed

Set up a portage overlay:

# mkdir /usr/local/portage

# echo "/usr/local/portage >> /etc/make.conf

Create portage directories:

# mkdir /usr/local/portage/app-crypt

# mkdir /usr/local/portage/app-crypt/cspace

Download the ebuild (or move it to this directory)

# cd /usr/local/portage/app-crypt/cspace

# wget [http://www.aabdalla.com/cspace.com/cspace-0.1_alpha.ebuild](http://www.aabdalla.com/cspace.com/cspace-0.1_alpha.ebuild)

Digest the ebuild:

# ebuild cspace-0.1_alpha.ebuild digest

Emerge cspace:

# emerge -av cspace

Run cspace:

# cspace

---

### Post by Rhubarb on 2006-11-22
I don't know how to compile myself, there should be some threads here that'll help you out.
I do know that you'll need a program called "gcc", and that you need to use "make install", but that's about it.

If it's a really simple one small sentance that you typically need to send around, you could use a program called linpopup.
It works with the windows' "net send" inbuilt program.
But I must warn you, it's not user friendly, it's just designed so sysadmins can broadcast a simple message to the network.

I do recommend you try out CSpace.  At the very least get the windows version installed on a few pc's to see if it'll all work for you.  Then you can try your hand at compiling the linux version.
I think CSpace is still in development, so maybe in a year's time it should all be pretty and come with .deb linux install packages for you (it might even end up in the Ubuntu repositories).

---

### Post by gresses1 on 2006-11-22
Thanks.  Sounds too involved for me. :-? 

I do have a copy of Netsend which I have used on my Windows boxes.  It is simplistic and just shows a pop-up screen...not historical GUI from which to copy and paste.

---

### Post by Rhubarb on 2006-11-22
> **gresses1 said:**
> Went to Cspace.  Would this be the compile syntax?
Thanks...

Arrrghghhghghgghgh, I don't know.  It could be.
I'm not the one here to ask.  Is there anyone else out there they might know?

Ask me again in a month or so and I should be able to help you out :)

---

### Post by Rhubarb on 2006-11-22
> **gresses1 said:**
> Thanks.  Sounds too involved for me. :-?

It shouldn't be to hard to figure out, should only take an hour or so to figure out how to compile it.
Perhaps start a new post (or look for an existing post) of how to compile a program from source.

As I said before, try the CSpace windows client first on your windows boxes, if everything works, then you can consider diving in to compile the linux CSpace client.

---

