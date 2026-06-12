---
title: "Customize desktop with my own packages"
date: 2014-09-17
forum: Any Other OS
---

### Post by redprive2 on 2014-09-17
Hi at all!

I have installed in my student's school network Ubuntu 12.10 kiosk mode.

I would like to change some configurations like entries menu, wallpapers, icon desktop, etc... but I would prefer don't it computer by computer, else I would like to learn to create a package where I can configure these things, and then, distribute it from my server to rest of the computers...

Anybody could help me please?

Thanx

---

### Post by Bucky Ball on 2014-09-17
Not a good start. 12.10 is no longer supported (and hasn't been for some time) and therefore receives no updates and probably shouldn't be online as it has had no security updates for quite some time either. It is not supported by Canonical or these forums, sorry. Too old and things change. People forget. Please read this:

EOL release recommendations:
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

Advise you start again with a supported release. 12.04 LTS is supported until 2017 and 14.04 LTS til 2019. Both are stable and LTS releases are intended for production/work machines, which these appear to be. If you persist with 12.10 you are going to run into some brick walls as far as getting support goes I would imagine, unless you can hunt down some answers through researching existing literature pertaining to 12.10. Good luck.

* The short answer to your actual question, though, and the way I would go (using 14.04 LTS, I will add :)) would be to:

- Do [a minimal install ]("https://help.ubuntu.com/community/Installation/MinimalCD")on one computer and customise as you want;
- Create an ISO of that install (think you can do that with [Clonezilla]("https://rbgeek.wordpress.com/tag/using-clonezilla-to-create-iso-image/"));
- Netinstall to the other computers from the ISO.

Why Kiosk mode, incidentally? :-k

---

### Post by redprive2 on 2014-09-17
Excuse me,

error is mine. I have installed a distribution called Vitaliux ([www.vitalinux.org](www.vitalinux.org)) and this distribution is based on Ubuntu 12.04 ;)

I did all things you recommend me: minium install, create iso and distribute it with clonezilla server ... but time past, and now I would like to do new small changes in all computers and It not good idea repeat all process for it... Too many time. I have 80 cloned computers ...

Best way to apply these changes is installing packages. I can distribute them because all these computers, when they are turn on, looking for new packages to install from server.

Kiosk mode was installed because all these computer are used by students, from 5 years... and they give me too many problems to my department :-)

Exists any manual where I can learn how to create packages with this purpose?

Thanx

---

### Post by slickymaster on 2014-09-17
*Moved to the ***Other Operating Systems and Projects*** sub-forum.*

---

