---
title: "404 during apt-get update"
date: 2012-03-27
forum: Any Other OS
---

### Post by yuhanz on 2012-03-27
Hi all,

I reached an error with a apt-get update on an Amazon Hadoop node, which was showing 404 during downloading some of the packages.

Could someone give some suggestion on how to fix the problem? (I am guessing the urls to the repositories in /etc/apt/sources.list, but I don't know where to point to.)


Thank you.

Yuhan

There is the error log:


 sudo DEBIAN_FRONTEND=noninteractive apt-get update
W: Failed to fetch [http://http.us.debian.org/debian/dists/lenny/main/binary-i386/Packages](http://http.us.debian.org/debian/dists/lenny/main/binary-i386/Packages)  404 Not Found [IP: 64.50.236.52 80]

W: Failed to fetch [http://http.us.debian.org/debian/dists/lenny/contrib/binary-i386/Packages](http://http.us.debian.org/debian/dists/lenny/contrib/binary-i386/Packages)  404 Not Found [IP: 64.50.236.52 80]

W: Failed to fetch [http://http.us.debian.org/debian/dists/lenny/non-free/binary-i386/Packages](http://http.us.debian.org/debian/dists/lenny/non-free/binary-i386/Packages)  404 Not Found [IP: 64.50.236.52 80]

E: Some index files failed to download, they have been ignored, or old ones used instead.



Ign [http://http.us.debian.org](http://http.us.debian.org) lenny/non-free Packages
Err [http://http.us.debian.org](http://http.us.debian.org) lenny/main Packages
  404 Not Found [IP: 64.50.236.52 80]
Err [http://http.us.debian.org](http://http.us.debian.org) lenny/contrib Packages
  404 Not Found [IP: 64.50.236.52 80]
Err [http://http.us.debian.org](http://http.us.debian.org) lenny/non-free Packages
  404 Not Found [IP: 64.50.236.52 80]

---

### Post by Krytarik on 2012-03-27
Debian Lenny has reached its End of Life in February this year:

[http://wiki.debian.org/DebianLenny#Release_and_updates](http://wiki.debian.org/DebianLenny#Release_and_updates)

Regards.

---

### Post by QIII on 2012-03-27
Implicit in the reply, if not obvious, is that you will have to see if the packages exist in the Debian Squeeze repos.  If so and you need help with your sources, just ask.

---

### Post by dcstar on 2012-03-27
> **Krytarik said:**
> Debian Lenny has reached its End of Life in February this year:


As well this has **absolutely nothing** to do with Ubuntu, and should have been posted in a Debian forum and not the Ubuntu forums.

---

### Post by Krytarik on 2012-03-28
> **dcstar said:**
> As well this has **absolutely nothing** to do with Ubuntu, and should have been posted in a Debian forum and not the Ubuntu forums.
You should tell that the OP, not me. ;-)

EDIT: I figure you may have meant it like that, the start of your sentence didn't make that obvious to me.

---

### Post by QIII on 2012-03-28
A haggard, bone-thin man with a whispy white beard comes to the door with an empty bowl asking for rice.

I notice that he has a Debian pin on his shirt ...

---

### Post by Krytarik on 2012-03-28
> **QIII said:**
> A haggard, bone-thin man with a whispy white beard comes to the door with an empty bowl asking for rice.

I notice that he has a Debian pin on his shirt ...
:popcorn: Great! :D

---

### Post by oldos2er on 2012-03-28
Thread moved to Other OS/Distro Talk.

---

### Post by aykoola on 2012-04-02
Maybe this would be best put here.

If i install the 6.0.1 DVD, will it update to version 6.0.4 or do i have to burn the 6.0.4 DVD?

Thank you!

---

