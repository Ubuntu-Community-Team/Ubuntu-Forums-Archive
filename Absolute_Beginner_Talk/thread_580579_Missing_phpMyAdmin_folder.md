---
title: "Missing phpMyAdmin folder"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by mevets on 2007-10-18
I always apt-get phpmyadmin. In earlier releases of ubuntu phpmyadmin would just show up when [http://localhost](http://localhost) was served. Now I notice I am prompted to determine what apache should be configured when  I apt-get phpmyadmin, under gutsy. The first time I selected apache2 only since I have apache2 install. But it did not show up after installation. The next time i reinstalled I selected all four checkboxes for apache2, apache, apache-ssl, apache-perl. It is still not there.

What am I doing wrong?

---

### Post by don durito on 2007-10-19
same problem here
don't know what to do but i realy need phpmyadmin

---

### Post by saj0577 on 2007-10-21
Anyone got this important as this is really important to my work and I dont want to have to downgrade to 7.04. Is this a bug do you think?

Saj

---

### Post by xxzeenoxx on 2007-10-22
Hey guys i was having the same issues, but all I did was completely remove 'phpmyadmin' from synaptic, then i installed phpmyadmin from the terminal:

sudo apt-get install phpmyadmin



You'll get a blue display asking you which apache servers you want it to configure it on, and I just selected all of them by clicking the space bar.  It only did it for apache2 because it didn't find the other 3 apache servers which were listed.  I then tabbed over to OK and hit enter.  Then go to [http://localhost/phpmyadmin]("http://localhost/phpmyadmin")  to see if it worked.



...hope this helps.

---

### Post by mevets on 2007-10-23
yeah I still can goto localhost/phpmyadmin but it doesnt show up when i goto localhost. wonder why this is

---

### Post by saj0577 on 2007-10-23
Yeah that worked still does not appear in my file structure though?

Saj

---

