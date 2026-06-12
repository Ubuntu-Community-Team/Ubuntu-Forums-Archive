---
title: "3D Rendering Questions. Wings3D. Blender. Server"
date: 2009-03-11
forum: Art &amp; Design
---

### Post by justin_c18 on 2009-03-11
I'm curious to see if anyone has another machine they model, or render with with Wings3D or Blender. I'm asking because my laptop isn't at all powerful, and I want a something that will render with a bit more power. Is it possible to have some sort of external machine on a local network, and do 3D graphic stuff from say a laptop, and render/ model through vnc, or something else? 

How would one do it? I don't have any cash to get a really nice laptop, or Desktop, or computer. But I do have a couple desktops that I can either leave as desktops or turn into servers for this purpose and are way more powerful than my laptop, but I don't have any room in my house set it up proper. It'd be nice to set them up as servers and just model through the network. 

It may not make much sense, that's why I'm asking for feedback to get my stuff straight. 

If there's a solution, let me know. I need some details what to do.

One desktop: (not doing anything with it atm)
Dual Core, 2GB RAM, etc..

The other: (not doing anything with it atm)
P4 @ 3GHz, 512mb RAM, 160GB HDD, nvidia card

LAMP server: 
PIII @ 1GHz, 512mb RAM, 20GB HDD

Laptop: 
C2d @ 2.0GHz, 2GB RAM, 80GB HDD

Leave some feedback!
Thanks

---

### Post by MooseDog on 2009-03-11
modeling is typically done on a one-machine basis.  since you've got a dual-core desktop, that's plenty powerful enough right there.

rendering animations (or better frame sequences)is usually where the render farm concept comes into play, and there, while big and powerful is great, it's not at all necessary, as a collection of weak machines still gets you to the end quicker than one machine.

i'm pretty sure there's an open source render farm tool out there for blender, i just forget what it's called.

---

### Post by chmasy on 2010-12-01
Yes, Blender can be run command line with no GUI, I set up a ubuntu 10.10 file server (No GUI) I installed telnet and blender on the server (apt-get install telnetd apt-get install blender). I then work with windows blender from my windows machine and save the .blend files on the shared drive. I then telnet into the server from my windows machine and run blender command line on the server to render images and movies.

[http://wiki.blender.org/index.php/Doc:Manual/Render/Command_Line_Options](http://wiki.blender.org/index.php/Doc:Manual/Render/Command_Line_Options)


Blender 2.49 on both windows and server. I tried to run a 2.5 blend file on the 2.49 server and got a bunch of errors.

---

