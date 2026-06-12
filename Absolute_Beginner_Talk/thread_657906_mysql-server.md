---
title: "mysql-server"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by rene53 on 2008-01-04
In synaptek i have the choice of 3 pakkets.
mysql-server, mysql-server4 and mysql-server5
can any-one tell me what is the difference between all the mysql-server pakkets?
I work with ubuntu 7.04 ad have installed Apache2, php5-mysql and php5-gd, does that mean that i have ti install mysql-server5  for better implantation, or does'nt it matter wich pakket i install?
Thanks, rene53

---

### Post by hyper_ch on 2008-01-04
well, the mysql-server4 and -5 package will install that specific version. The "mysql-server" package is a meta-package which always points to the most recent version (in this case mysql-server5).

So assuming you install now mysql-server and you do 3-4 upgrades from Gutsy to .... and assuming that meanwhile there is mysql-server6, then, because of the selection of mysql-server it will also upgrade it to mysql-server6.

P.S.: I'd also install mysql-client

---

### Post by rene53 on 2008-01-04
Thank you for the answer, i will do that.
;-)

---

