---
title: "Package manager install location"
date: 2007-12-02
forum: Absolute Beginner Talk
---

### Post by siddthekidd on 2007-12-02
Hi

To set up partitions for the root and usr directory, I need to know which requires more space.
Where do Ubuntu's package managers (Synaptic, apt-get, etc.) install packages by default, in /root or in /usr?

Thank You

---

### Post by monktbd on 2007-12-02
well there is / which is called the root directory and /root which is kinda the /home of the root user.
programs get all installed somewhere in /usr, a few also in /opt (if you download them not via synaptic). so /usr needs more space than /, /root does not need much at all and is usually just a folder on the / partition.
keept in mind that / also holds all other folders besides the ones you make partitions for (/home should clearly have its own partition and probably be as large as the data you want to hold in your personal files).
also / holds folders like /var where log messages are stored and if you run a webserver/database on your comp their data are stored. also there is /tmp which is often used as temporary space when burning cds or dvds which might need the appropriate free space too.

---

### Post by monte48lowes on 2007-12-02
The package managers download packages to /var/cache/apt when you add new software to your system. When the packages are installed most of the files within the package are installed into /usr.

Mike

---

