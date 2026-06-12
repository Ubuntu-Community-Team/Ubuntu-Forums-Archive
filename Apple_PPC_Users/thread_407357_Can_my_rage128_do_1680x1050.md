---
title: "Can my rage128 do 1680x1050?"
date: 2007-04-12
forum: Apple PPC Users
---

### Post by justin@kelly.org.au on 2007-04-12
Hi All,

im looking to buy a nice new 22" LCD monitor for my powermac 400 but not sure if its rage128 card can support a resolution of 1680x1050 using the standard driver

anyone know?

Cheers

Justin

---

### Post by Spr0k3t on 2007-04-12
There's no reason why it can't.  You may need to install/update the drivers, but I doubt it.  I'm thinking you can add the resolution to your xorg.conf and it will work, but make sure you backup your xorg.conf file prior to.

---

### Post by heimo on 2007-04-12
My guess is that it can do 1680x1050, but it may need some work in xorg.conf - probably not going to work out of the box - that's because it's a widescreen. No reason why it couldn't go so high in resolution - probably can do even higher.

---

### Post by justin@kelly.org.au on 2007-04-12
Thanks guys,

has anyone actually used a 22" with a rage128?

just wasnt sure that such an old card could handle big wide screens - but maybe it can fine - hope so :)

much appreciated

Cheers

Justin

---

### Post by heimo on 2007-04-12
To answer your question, I searched quite a bit, and I remember I found a discussion thread (not in Ubuntuforums) where someone had used this resolution with r128 driver and he was also using Apple hardware (but I think he first had some trouble setting it up, sorry no link now) - and I checked Xorg documentation to see that this driver can handle high resolutions. So, personally I can't guarantee that it'll work, but I'm quite convinced it will. That's the best I can do. (not much, I know) :D

---

### Post by fkdev on 2007-04-12
As far as I know, the only thing you'll lose would be any 3d accel.

---

### Post by justin@kelly.org.au on 2007-04-12
Thanks guys for your posts!!!,

much appreciated, now just gotta decide which 22" :)

Cheers

Justin

---

