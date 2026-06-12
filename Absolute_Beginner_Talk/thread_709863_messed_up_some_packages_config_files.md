---
title: "messed up some packages config files"
date: 2008-02-27
forum: Absolute Beginner Talk
---

### Post by redrocket on 2008-02-27
have been trying to install nagios-pgsql and nagios-text, also apache and apache2. now whatever ive done from the different packages a few times, when i try to install again and get running again there are messed up config files. I would like to remove everything cleanly and install everything cleanly, overwriting any previous config files and leaving me with a clean fresh start. 

in some cases config files arent even there after fresh install!
 * Starting web server apache2
apache2: Could not open configuration file /etc/apache2/apache2.conf: No such file or directory

to remove i have been using apt-get remove --purge apache2, then apt-get autoremove, then apt-get install apache2

have the same problem with nagios. 

Im sure there's something simple that i cant think of to search for solution.

Thanks

---

### Post by Daishiman on 2008-02-27
I suggest you look in Synaptic, in the package options, the "Installed Files" tab and see which configuration files might be there and check for their existence post-removal.

---

### Post by redrocket on 2008-02-27
ok will try that now, completely forgot about synaptic, been using apt-get for a while now

---

