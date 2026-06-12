---
title: "Can't Get Repository Listing"
date: 2005-08-11
forum: Bug Reports / Support
---

### Post by Olrich on 2005-08-11
I have all the other Ubuntu repositories enabled, and when I try to retrieve the new listings everything works just fine.  I tried to add the backports repositories but Synaptic always fails to get a listing.  I tried using all of the available mirrors but they all fail.  However, if I type the URL of one of the repositores in to Firefox, I am able to connect and browse through the files just fine. I am certain I have the APT lines right as I copied them straight out of the Unofficial Starter Guide.

deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

Does anyone know of what could be causing this problem, and a possible solution?  Thank you for your help.

---

### Post by bjweeks on 2005-08-12
Have you tried "sudo apt-get update"?

---

### Post by Xk2c on 2005-08-20
yesterday I had the same problem with:
[http://public.planetmirror.com/pub/ubuntu-backports/](http://public.planetmirror.com/pub/ubuntu-backports/)

after changing to:
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/)


everything worked fine again. Hmm u told u had Problem THIS server.

hmm
Maybe some should check this, seems s.th. doesn't work right
(s.o. on the irc channel had the same behavior, as mine)

---

