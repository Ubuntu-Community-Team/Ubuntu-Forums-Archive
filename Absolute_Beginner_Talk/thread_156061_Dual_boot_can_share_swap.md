---
title: "Dual boot can share swap?"
date: 2006-04-06
forum: Absolute Beginner Talk
---

### Post by echo $USER on 2006-04-06
Im going to install Ubuntu and Fedora on my IBM T21 as soon as it gets here.  And I was wondering can I just use one swap space for both OS?  Or do they both need there own?

---

### Post by taurus on 2006-04-06
They both can share the same swap partition.  No need to create an extra one...  Just point it to the right partition when you install but chances are each would know because it has the ID of 82--Linux swap...

---

### Post by echo $USER on 2006-04-06
Thanks!  If I had /home on it's on partition, could they both share it?

---

### Post by echo $USER on 2006-04-06
bump

---

### Post by htinn on 2006-04-06
Probably not a good idea. Fedora uses different versions of a lot of applications, so their configs will likely have conflicts. Plus, Fedora expects to have different permissions on the /home folder, etc. There's probably a few other problems I'm not thinking of. Sharing swap should be fine though. :)

---

### Post by echo $USER on 2006-04-06
Thanks for the info.  Guess I just need to get a bigger HD.

---

### Post by taurus on 2006-04-06
[QUOTE=echo $USER]Thanks for the info.  Guess I just need to get a bigger HD.[/QUOTE]
Harddrives are so dirt cheap right now so get yourself as large as you can afford.  I always have a good experience with [http://www.newegg.com/](http://www.newegg.com/).

---

