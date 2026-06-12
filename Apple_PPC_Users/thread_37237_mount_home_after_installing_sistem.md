---
title: "mount /home after installing sistem"
date: 2005-05-26
forum: Apple PPC Users
---

### Post by open_flax on 2005-05-26
hello 
i wont mount a partition on /home after installing my system and use this step:
login as root and i modify /etc/fstab adding a string:
/dev/hda4       /home           ext3    rw,auto,user    0       0

hda4 is a partition where mount /home. 

after you change a permission with:
chown user -R /home/user.

may be rebooot a system to create a configuration file of your menager desktop.
 :)

---

