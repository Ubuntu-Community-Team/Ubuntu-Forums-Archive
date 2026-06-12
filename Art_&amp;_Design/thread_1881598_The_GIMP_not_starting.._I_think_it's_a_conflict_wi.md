---
title: "The GIMP not starting.. I think it's a conflict with GLib"
date: 2011-11-15
forum: Art &amp; Design
---

### Post by PayPaul on 2011-11-15
I had just put up an update to a RAW processing program today called Darktable from a Deb file. After that I've been having a sudden problem opening up Gimp. When I typed in "gimp" in terminal I get the following message:

(gimp:25542): GLib-WARNING **: /build/buildd/glib2.0-2.28.6/./glib/goption.c:2132: ignoring no-arg, optional-arg or filename flags 8 on option of type 0
paulw@ubuntu:~$ 



It seems to me, a noob when it comes to these dependencies that there is a conflict of some kind going on. I can only at this point attribute it to my Darktable update. How do I find out what that programs dependencies are and if they are in conflict with GIMP in any way?:confused:

---

### Post by desktorp on 2011-11-17
[https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/775586](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/775586)

seems to address something similar if not the same thing (?)

it seems like the ultimate solution/workaround was to make a hidden directory for gimp.. didn't really read the whole thing but there were other relevant results on google, when I just searched for the bulk of your error message.

---

### Post by PayPaul on 2011-11-17
> **desktorp said:**
> [https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/775586](https://bugs.launchpad.net/ubuntu/+source/gimp/+bug/775586)

seems to address something similar if not the same thing (?)

it seems like the ultimate solution/workaround was to make a hidden directory for gimp.. didn't really read the whole thing but there were other relevant results on google, when I just searched for the bulk of your error message.

It apparently corrected itself on reboot. This was almost giving me a deja vu experience ala Microsoft.

---

