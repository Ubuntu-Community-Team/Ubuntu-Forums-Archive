---
title: "Tomboy Notes Icon"
date: 2005-08-26
forum: Art &amp; Design
---

### Post by the.tsr on 2005-08-26
Albeit the cutesy Tin-Tin icon for Tomboy Notes is okay at first, I'd love to know how to change it and have not been able to find a solution to said problem. Any suggestions? Any help would be much appreciated.

 ](*,)

---

### Post by m0biu5 on 2005-08-26
I agree, a change in that icon would be refreshing...

---

### Post by Mike Douglas on 2005-08-26
[QUOTE=the.tsr]Albeit the cutesy Tin-Tin icon for Tomboy Notes is okay at first, I'd love to know how to change it and have not been able to find a solution to said problem. Any suggestions? Any help would be much appreciated.

 ](*,)[/QUOTE]
 Tomboy got a new icon awhile ago. The updated version should be in Breezy.

---

### Post by tageiru on 2005-08-27
The tomboy icon is compiled into the binary as a resource. To change it get the source for the debian package (apt-get source tomboy) and change the data/images/tintin.png and recompile the package (dpkg-buildpackage -rfakeroot)

---

### Post by Corey on 2005-09-01
.3.2 has a much more relative icon. And it doesn't suffer from the transparency but that the old one did either.

---

