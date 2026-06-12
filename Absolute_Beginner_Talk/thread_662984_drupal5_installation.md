---
title: "drupal5 installation"
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by observ8 on 2008-01-09
i installed drupal after the installation of LAMP and phpmyadmin

how i can run drupal?
i found that drupal files rests on /etc/drupal/5

---

### Post by stalker145 on 2008-01-09
> **observ8 said:**
> i installed drupal after the installation of LAMP and phpmyadmin

how i can run drupal?
i found that drupal files rests on /etc/drupal/5

You're looking at the wrong files. Configure your web server to host **/usr/share/drupal5**, restart your server, and point your browser to **[www.yourdomain.tld](www.yourdomain.tld)** and set it up. I'm assuming that you already have MySQL and PHP installed.

---

### Post by observ8 on 2008-01-12
i unistalled the drupal5 version through synaptic and i nstalled it again there seem to be a problem with this version and synaptic installation
after that i downloaded the last version of drupal through drupal site i installed it and everything is ok now :)

---

### Post by comandrei on 2008-01-12
You can always install drupal "from sources". Just download the installation kit, and it has an installer.
The installer should notify you if you have some disabled modules on your server ( e.g. mod_rewrite).

---

