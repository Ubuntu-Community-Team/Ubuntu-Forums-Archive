---
title: "Airport problems"
date: 2008-01-25
forum: Apple Intel Users
---

### Post by robscheflo on 2008-01-25
I recently bought a intel macbook pro over the summer and I've installed Ubuntu 7.10 but it won't recognize my airport card and I can't seem to fix it. I'm reasonably new to linux and coding as well so please make instructions easy if you can.

---

### Post by cyberdork33 on 2008-01-25
> **robscheflo said:**
> I recently bought a intel macbook pro over the summer and I've installed Ubuntu 7.10 but it won't recognize my airport card and I can't seem to fix it. I'm reasonably new to linux and coding as well so please make instructions easy if you can.

I am pretty sure you have an Atheros card. There is a link in the FAQ to how to compile the madwifi driver.
[http://ubuntuforums.org/showpost.php?p=2731459&postcount=25](http://ubuntuforums.org/showpost.php?p=2731459&postcount=25)

---

### Post by robscheflo on 2008-01-25
will@will-laptop:~/Desktop$i svn checkout [http://svn.madwifi.org/trunk](http://svn.madwifi.org/trunk) madwifi
svn: URL 'http://svn.madwifi.org/trunk' doesn't exist


When I get to a certain point this happens

---

### Post by cyberdork33 on 2008-01-25
you don't have to checkout the svn source. Just get the lastest source from the site:
[http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz](http://downloads.sourceforge.net/madwifi/madwifi-0.9.3.3.tar.gz)

extract that and build in the resulting directory

---

