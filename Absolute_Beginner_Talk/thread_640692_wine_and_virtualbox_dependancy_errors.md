---
title: "wine and virtualbox dependancy errors"
date: 2007-12-14
forum: Absolute Beginner Talk
---

### Post by faraz_k86 on 2007-12-14
ok so while i try to configure my dial up i still need wine and virtual box on my laptop.

before i post my problem i want to make it clear that the laptop on which ubuntu is installed cannot connect to the internet.


ok so i downloaded wine and virtualbox installers (.deb)


when installing wine, i get the following error:

Eroor: dependancy is not satisfiable: binfmt-support


and when installing virtualbox, i get the following error:

Eroor: dependancy is not satisfiable: libqt3-mt

so what now??

---

### Post by faraz_k86 on 2007-12-14
ok so i even downloaded the file libqt3-mt but i still get the same error

---

### Post by faraz_k86 on 2007-12-15
bump

---

### Post by faraz_k86 on 2007-12-15
and another bump, after 5 hours.  can no one help?

---

### Post by Paqman on 2007-12-15
You're stuck in dependency hell! Basically, the packages you're trying to install need other packages in order to work. If you had an internet connection, the system would automatically download and install those extra packages to satisfy the dependency. Since it can't gte them your install fails and spits out those errors.

Have you tried using the install CD as a repo? Got to System > Administration > Software Sources and add the CD as a repo. Refresh Synatpic or sudo apt-get update and try again. I can't guarantee those packages will be on the CD, but it might be a quick win if they are.

---

### Post by faraz_k86 on 2007-12-15
thx for the reply paqman.

the cd is already added as a repo, but i get the same error.

any other ideas? can any1 else help me out?

---

### Post by n0t5ew on 2008-02-24
Go to:

System->Administration->Software Sources

After you have opened that, make sure that you have all your Downloadable From The Internet checkboxes checked.

Then try installing the package and it will install all necessary packages.

I understand this thread is dead, but I hope it will help someone (like me) who used the search button later.

---

