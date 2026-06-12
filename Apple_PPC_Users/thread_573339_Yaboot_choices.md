---
title: "Yaboot choices?"
date: 2007-10-11
forum: Apple PPC Users
---

### Post by Bikerbob on 2007-10-11
In Yaboot.. you can have the choice 

macos

macosX

and it will display linux choices if you enter more Kernal values.

Can I have multi osX partitions? with say 10.3 and 10.4??

If so.. how do I label it?? 

Does the label have to be something already known to the Yaboot program? or can I just do.

Jag=/dev/sdc10
Tiger=/dev/sdb10

ETC????

Thanks

James

---

### Post by allesfresser on 2007-10-12
You might take a look through the yaboot.conf man page, but after reading that, I can't see anything that indicates that there is a way to accomplish what you're looking to do.  :(  It seems like yaboot was written with the assumption that there would only be one OS X boot partition (and possibly one OS 9 partition as well).

Anybody that knows something to the contrary, please post!  I would find this useful as well.

---

