---
title: "Host multiple sites on a single pc using apache2"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by pjrodz on 2007-05-17
I'm trying to host 2 different sites on my computer to be accessed only by me (using [http://localhost/](http://localhost/)**site1** and [http://localhost/](http://localhost/)**site2** ). how do i go about it? what do i put in the /etc/apache2/sites-available/ site1 and site2 files? thanks! :)

---

### Post by compmodder26 on 2007-05-17
With that kind of URL structure, you only need one virtual host in your apache config.  You would simply create two folders in your document root.  Each folder would house the files for a different site.

edit: That sounded a little more cryptic than I originally thought it would.  In other words, leave your configuration alone and just place two different folders in your document root.  Place the files for one site in one folder, then place the file for the other site in the other folder.

---

