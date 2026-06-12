---
title: "Help installing!"
date: 2006-09-03
forum: Absolute Beginner Talk
---

### Post by MaLaKa on 2006-09-03
I have just got Cedega and now I have two files and have no idea what to do with them :-\" 

cedega-small-5.2.3-1.i386.rpm
cedega-engine-5.2.5-local-update.i386.cpkg

help!

---

### Post by Klaidas on 2006-09-03
Hmm, an RPM.
Well, if there is no .deb, it's not in repos, it's not availible to compile from source, you'll have to use alien to convert it to a .deb
> sudo apt-get install alien
> sudo alien filename.rpm
> sudo dpkg -i filename.deb

---

