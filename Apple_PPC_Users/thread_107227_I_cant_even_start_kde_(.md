---
title: "I cant even start kde :("
date: 2005-12-22
forum: Apple PPC Users
---

### Post by T31 on 2005-12-22
I got this error all the time :(

ERROR: KUniqueApplication: Can't setup DCOP communication

and the same if I try to start any kde app from any other desktop :(

Ive been trying everything Ive seen in the forums and no success chown .kde, deleting .kde socket tmp cache deleting iceauthority and nothing, one thing is I miss the file .DCOPserver_XXX__0 may be this can help to solve my problem?

(edit) one more thing I got as well "segmentation fault"

---

### Post by T31 on 2005-12-30
Ok dudes, this is how I fixed, maybe not the best way but now it works

go to synaptic (yeah yeah I prefer aptitude as well but a graphic interface always helps) and look for any kde thing, and just... get rid of it completely

and now k3b kmag and the rest is working :) I know is not an elegant way to fix it but... it does work :)

---

