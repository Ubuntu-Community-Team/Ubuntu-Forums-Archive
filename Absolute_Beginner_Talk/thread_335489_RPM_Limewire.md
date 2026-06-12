---
title: "RPM Limewire"
date: 2007-01-10
forum: Absolute Beginner Talk
---

### Post by loyaleagle on 2007-01-10
Hello everybody;

Thanks again for all the help provided. Just have a quick question. I want to use Limewire. I went to their site and downloaded LimeWireLinux.rpm. Now they have no info on what to do with this once it is downloaded. Could someone help me in installing this rpm package.

Thanks again for this forum and the AWESOME Ubuntu experience,

Loyaleagle:confused: :mrgreen:

---

### Post by loyaleagle on 2007-01-10
Found my answer in a more detailed search of this forum. Downloaded Frostwire instead. Much easier and looks like I have what I wanted.

Sorry for the trouble......

Thanks, Loyaleagle.

---

### Post by ComplexNumber on 2007-01-10
> **loyaleagle said:**
> Hello everybody;

Thanks again for all the help provided. Just have a quick question. I want to use Limewire. I went to their site and downloaded LimeWireLinux.rpm. Now they have no info on what to do with this once it is downloaded. Could someone help me in installing this rpm package.

Thanks again for this forum and the AWESOME Ubuntu experience,

Loyaleagle:confused: :mrgreen:
install a package called alien. then go to the directory where the rpm is located and fire up your terminal in the same directory. then type in the following into the terminal:

sudo alien -d <package name> (package name of the rpm file)

that will create a deb package in the same directory. to install it, type:

sudo dpkg -i <package name> (package name of the deb file)

---

### Post by jvc26 on 2007-01-10
No trouble at all - using frostwire as a .deb is probably more reliable, as the alien package doesnt always convert from .rpm to .deb without any problems and so you could end up with a package which didnt convert properly. Its not too difficult to do (see above) but if theres a .deb there which works then thats the easiest option! :)
Il

---

### Post by loyaleagle on 2007-01-10
Thanks for all the GREAT advice.

As always, this forum kicks ***...

An Ubuntu lover, 

Loyaleagle

---

