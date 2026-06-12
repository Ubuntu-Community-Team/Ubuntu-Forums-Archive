---
title: "PHP and MySQL support in Ubuntu"
date: 2006-12-11
forum: Absolute Beginner Talk
---

### Post by 4xmadeeasy on 2006-12-11
HI, I'm Dan. I am a beginner using Ubuntu and I would like to know if it has included support for PHP and MySQL(if this comes with the distribution).
   Regards,
     Dan - 4x made easy

---

### Post by tribaal on 2006-12-11
Hum well PHP and MySQL are most famous for running on linux (via the LAMP stack).

There are packages for Apache, PHP and MySQL in the repositories, just open up Synaptic.

More info [Here]("https://help.ubuntu.com/community/ApacheMySQLPHP").

Hope this helps

- trib'

---

### Post by beefcurry on 2006-12-11
It dosnt COME with the Standard Ubuntu but COMES with Ubuntu Server Edition. However it is easy to ADD PHP and MySQL support to the standard Ubuntu from the repository via synaptic.

---

### Post by bill123 on 2006-12-11
i have installed php5 and its working from command line 
but when i hit a php page from browser it gives me pop-up for file download. 
i believe this is the problem with apache2 configuration or could be some thing else. please need help

any help would be appreciated

---

### Post by bill123 on 2006-12-11
i have even reinstalled the libapache2-mod-php5 
but the point is 
it is working fine on the command line 
but asking for open or save through browser
it was working fine actually.. i did some updates and not remember what were those cuz just hit the "updates available" icon on top and ruined my system.

---

### Post by hyper_ch on 2006-12-11
try in the command line:

```

a2enmod php5

```

---

### Post by az on 2006-12-11
> **bill123 said:**
> i have even reinstalled the libapache2-mod-php5 
but the point is 
it is working fine on the command line 
but asking for open or save through browser
it was working fine actually.. i did some updates and not remember what were those cuz just hit the "updates available" icon on top and ruined my system.

What versions of apache, mysql and php do you have running?

---

### Post by bill123 on 2006-12-11
i m running apache2 php5 and mysql5
my problem has been solved already 
by "a2enmod php5"
thnaks

---

### Post by hyper_ch on 2006-12-11
That's the new great thing about apache2... you can easily de/activate modules in there :)

---

