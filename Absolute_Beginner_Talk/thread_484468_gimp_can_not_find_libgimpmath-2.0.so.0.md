---
title: "gimp can not find libgimpmath-2.0.so.0"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Innova on 2007-06-25
Subject pretty much sums it up.  I haven't installed anything outside of Synaptic, but I am still getting this error:

gimp: error while loading shared libraries: libgimpmath-2.0.so.0: cannot open shared object file: No such file or directory


Any idea how to correct it?

---

### Post by muguwmp67 on 2007-06-25
Have you tried reinstalling the library?

To do this, open synaptic and do a name search for libgimp. Right-click on it and select mark for reinstallation.  Then select apply.

---

### Post by Innova on 2007-06-25
libgimpmath does not show up in synaptic.

---

### Post by muguwmp67 on 2007-06-25
search for 'libgimp2.0'

I checked the manifest and your library is one of the modules it installs.

---

### Post by Innova on 2007-06-25
Thanks.  That worked!

Sorry I didn't read your first message completely.  I have been working on this for a while and was getting frustrated.

Thanks again for your help!

---

