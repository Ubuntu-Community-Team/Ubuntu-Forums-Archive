---
title: "failed to fetch from http://bg.archive.ubuntu.com"
date: 2007-04-29
forum: Absolute Beginner Talk
---

### Post by shadowboxer_k on 2007-04-29
hi,

i have a problem downloading updates or any installation files needed. i first noticed it yesterday, when i tried downloading the 6 new updates for feisty - only one loaded and for the rest i got this notice:

> W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_0.76.1_all.deb](http://bg.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-problem-report_0.76.1_all.deb)
  Could not connect to bg.archive.ubuntu.com:80 (195.69.109.181). - connect (111 Connection refused)


W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_0.76.1_all.deb](http://bg.archive.ubuntu.com/ubuntu/pool/main/a/apport/python-apport_0.76.1_all.deb)
  Could not connect to bg.archive.ubuntu.com:80 (195.69.109.181). - connect (111 Connection refused)


W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_0.76.1_all.deb](http://bg.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport_0.76.1_all.deb)
  Could not connect to bg.archive.ubuntu.com:80 (195.69.109.181). - connect (111 Connection refused)


W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_0.76.1_all.deb](http://bg.archive.ubuntu.com/ubuntu/pool/main/a/apport/apport-gtk_0.76.1_all.deb)
  Could not connect to bg.archive.ubuntu.com:80 (195.69.109.181). - connect (111 Connection refused)


W: Failed to fetch [http://bg.archive.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.5.0-1ubuntu1_i386.deb](http://bg.archive.ubuntu.com/ubuntu/pool/main/r/rdesktop/rdesktop_1.5.0-1ubuntu1_i386.deb)
  Could not connect to bg.archive.ubuntu.com:80 (195.69.109.181). - connect (111 Connection refused)




same thing happens when i try to install a program via terminal. does anyone have any idea why this happen and how it can be fixed?

any help kindly appreciated.

---

### Post by starcraft.man on 2007-04-29
Server might be down for maintenance or for some other reason. A simple easy way to check is to use another countries server.

System -> Administration -> Software Sources

Look at the drop down menu (I guess bg is bulgaria) and pick another country, US or Canada should be up. 

Then just reload your sources with "sudo aptitude update". 

Hope that helps, you can always switch back later.

---

### Post by yabbadabbadont on 2007-04-29
EDIT:  What the previous poster suggested is the easier course.

---

### Post by shadowboxer_k on 2007-04-29
thanks a lot to both of you! i went for the solution offered by starcraft.man, as it looked easier indeed. it seems to work. thanks again!

---

