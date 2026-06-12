---
title: "totem xine ogg vorbis plugin?"
date: 2007-11-01
forum: Absolute Beginner Talk
---

### Post by robulus on 2007-11-01
Hi Folks,
I've compiled and installed the most recent version of xine and am using totem as it's front-end.
Everything I throw at it works great - even .rm with the w32codecs package.
But....
When I try and open a .ogg file(audio or video) I get this error:

'Totem could not play 'whateverITWas.ogg'
'There is no plugin to handle this movie.'

Can anyone help me out by showing me where the .ogg plugin for totem-xine is?
Cheers!
Rob.

---

### Post by Hospadar on 2007-11-01
have you tried using the xine out of the repos?  I would bet that if you compiled it yourself you might have missed a switch to get ogg support.

Maybe not, but it might be worth a try

---

### Post by robulus on 2007-11-02
Hi Hospadar,
cheers - that was exactly what caused it - I was missing the libogg and libvorbis dev header files when I originally compiled xine.  Reconfiguring and making did the rest once I install them.

I used to use the repos for totem with the xine backend, but subsequently I changed to the most recent version (with all the corresponding configuring/making etc) since I was trying to find a way to get real media .rm files to work.  (I didn't know about w32codecs at the time).

In any case, it's been a great way to learn about using the command line/dev headers/installing manually etc.

enjoy the weekend!
Rob.

---

