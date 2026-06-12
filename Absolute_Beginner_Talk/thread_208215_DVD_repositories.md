---
title: "DVD repositories"
date: 2006-07-03
forum: Absolute Beginner Talk
---

### Post by vinodis on 2006-07-03
Fed up with the installation problems(dependencies etc), on a non-internet machine at home, i downloaded all the ubuntu dapper DVDs from here:-
[ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/](ftp://ftp.leg.uct.ac.za/pub/linux/ubuntu-unofficial-packages-dvd/)

Now how can I add these 4 .ISO files as local repositories in my ubuntu pc?
I have 80GB hard disk space. The mounting of ISO files as /cdrom would allow only one right?.

How can I have all these 4 .ISO files serving as local repositories?

Thanks many.

---

### Post by simone.brunozzi on 2006-07-03
Not completely sure, but I think you can use a symbolic link... I'm pretty sure there is a better way, though.

Cheers,

---

### Post by lamego on 2006-07-03
Copying all the .deb files from the DVDs to /var/cache/apt/archives should work fine.

Even with the repositories pointed to the network it would use the local var packages as long the version matches.

---

### Post by vinodis on 2006-07-03
I bought a new DVD Writer (LG) and wrote those .iso to 4 DVD-Rs. Now I think it is a good investment on a DVD Writer.

---

