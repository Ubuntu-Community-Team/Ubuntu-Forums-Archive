---
title: "chmod/usermod problems"
date: 2007-05-30
forum: Absolute Beginner Talk
---

### Post by jcolo on 2007-05-30
Permissions problem chmod/usermod

Hi I have a recently installed a version of ubuntu server/LAMP. Everything is fine, up and running.

 Under /var/www (www-data/www-data) there are all my web files but they appear either with rw-r--r-- permissions or rwx-rx-rx ( dirs).

 I want to strip our our permissions to "other" as I use a separate user "myuser" in order to maintain and browse the files. For that I wan to to include "myuser" within the "www-data" group and use group level permissions.

In effect I want to be able to do an ls or edit any file within the directory with this user but not expose all configuration files ( with db passwds ) to the rest of the world.

I issue a "sudo usermod -a -G www-data myuser" and then "id myuser" which reports that myuser is now part of www-data.

However it does not appear to work. I cannot edit files no do "cd" into those directories.

What am I missing ???

Thanks.

JCG

---

### Post by jcolo on 2007-05-30
my fault.... I have to logout/login to activate the membership .... same session is not effective

---

