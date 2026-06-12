---
title: "Program to connect my ipod nano"
date: 2007-12-26
forum: Absolute Beginner Talk
---

### Post by nflynn2k7 on 2007-12-26
hi please can some tell a program to put music on my ipod

---

### Post by mellowd on 2007-12-26
Which version and model of ipod?

---

### Post by nflynn2k7 on 2007-12-26
latest 1

---

### Post by Samhain13 on 2007-12-26
Try GTKPod.

---

### Post by dashnak on 2007-12-26
Try gtkpod, yamipod or floola

---

### Post by nflynn2k7 on 2007-12-26
where can i get it

---

### Post by Samhain13 on 2007-12-26
GTKPod is available through Synaptic. Just search for it.

---

### Post by nflynn2k7 on 2007-12-26
i'm i complete novice with this please help

---

### Post by Samhain13 on 2007-12-26
Type this in a terminal.

```
 sudo apt-get install gtkpod
```

It's going to install gtkpod, and you have to supply your password. :)

After installation, it's going to appear in Applications > Sound & Video

---

### Post by nflynn2k7 on 2007-12-26
i have installed but when i try to put music on it says its putting it on but when i eject there is nothing on my ipod

---

### Post by dreadlord_chris on 2007-12-26
I use Amarok - never really ha any problems with adding music to either of the Nano's I have available...

That said - you do need to make sure that you unmount the device before removing it - this allows all the writes to be sync'd

You should be able to do this by right-clicking the device icon (on your Desktop) and selecting Safely Remove

---

### Post by siwilson on 2007-12-26
The newer Nano's are tricky to get working. You need a later iPod library.

There are some simple to follow instructions here: [http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

Good luck!

/Simon

---

### Post by dashnak on 2007-12-26
You have to his "save changes" before ejecting

---

### Post by Samhain13 on 2007-12-27
> **dashnak said:**
> You have to his "save changes" before ejecting

nflynn2k7: Sorry it took so long for me to reply (I'm in a different timezone). But yeah, you need to save the changes before ejecting your iPod. And from experience, this may take a few minutes. Don't be surprised if the application greys-out a few times, it just really takes some time to save your changes especially if you've downloaded many songs to your iPod.

---

### Post by nflynn2k7 on 2007-12-27
hi i did eject and wait still no luck

---

### Post by siwilson on 2007-12-27
See my earlier post. You need to update libgpod and libgpod2 for the latest nano to work.

/Simon

---

### Post by davidgutu on 2007-12-27
try installinu ipod linux on your nano

---

### Post by mathnerd314 on 2007-12-27
What about Rhythmbox (which is installed by default on Ubuntu)? Doesn't it have an iPod support plugin?

---

### Post by nflynn2k7 on 2007-12-27
i have now got music on using amarok but how do i get the cd cover to go on

---

### Post by adam.tropics on 2007-12-27
In the device section of amarok, you will see the ipod menu with a little drop down arrow. Click that and you can copy over the artwork from there. (can't remember the name of the option off the top of my head)

Before you do that though, run Cover manager from the main Tools menu, and fetch missing covers.

---

### Post by nflynn2k7 on 2007-12-27
> **adam.tropics said:**
> In the device section of amarok, you will see the ipod menu with a little drop down arrow. Click that and you can copy over the artwork from there. (can't remember the name of the option off the top of my head)

Before you do that though, run Cover manager from the main Tools menu, and fetch missing covers.


hi i done the tools thing but there is know artwork option

---

### Post by adam.tropics on 2007-12-27
See the attached pic to check we're talking about the same thing. Also by the way, make sure (again from that menu) you are connected as the correct model of ipod.

---

### Post by nflynn2k7 on 2007-12-27
> **adam.tropics said:**
> See the attached pic to check we're talking about the same thing. Also by the way, make sure (again from that menu) you are connected as the correct model of ipod.

mine dont have that what version of amarok u on

---

### Post by adam.tropics on 2007-12-27
version1.4.8

---

### Post by nflynn2k7 on 2007-12-27
> **adam.tropics said:**
> version1.4.8

i download that i dont know how to install it could you help please

---

### Post by adam.tropics on 2007-12-27
Sent you a message, but anyway, to install it, you can just use synaptic. Make sure the gutsy-backports repo is enabled, reload, and search for amarok.

---

### Post by pseudosero on 2007-12-29
I have a 3rd generation ipod nano, and I am experiencing the same problem, using gtkpod.  I read one article that said apple is trying to prevent anything but itunes from working.  Sounds like a challenge.  It seems at this point it is a problem of early adoption, and we'll have to wait for gen 3 nano support.

---

### Post by gerbman on 2008-01-01
> **pseudosero said:**
> I have a 3rd generation ipod nano, and I am experiencing the same problem, using gtkpod.  I read one article that said apple is trying to prevent anything but itunes from working.  Sounds like a challenge.  It seems at this point it is a problem of early adoption, and we'll have to wait for gen 3 nano support.

The above posters seemed to have success with Gutsy's Amarok and the 3rd generation IPod Nano. Did you try Amarok?

---

### Post by dylgod on 2008-01-02
Just wanted to post a big thank you to the advice on this thread.. I've been trying to get my nano to work since xmas (new to Ubuntu :) )

Finally getting somewhere due to this thread... so big thanks !

---

### Post by uncannybuzzard on 2008-01-03
go here:
[http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/](http://lilserenity.wordpress.com/2007/12/22/virgin-mobile-praise-ubuntu-and-ipod-nano-3g/)

update the libgpod libraries and use gtkpod. there is also a bug in gtkpod that won't allow you to add media to the local repository. i'll post the link to the updated .deb if i can find it again.

---

### Post by uncannybuzzard on 2008-01-03
ahhh ... here's a link to the source

[https://launchpad.net/ubuntu/+source/gtkpod-aac/](https://launchpad.net/ubuntu/+source/gtkpod-aac/)

this does video as well. once you get it running it beat everything hands down.

---

