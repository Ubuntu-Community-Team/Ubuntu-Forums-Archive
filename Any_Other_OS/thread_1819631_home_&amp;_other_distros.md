---
title: "/home &amp; other distros"
date: 2011-08-06
forum: Any Other OS
---

### Post by zami on 2011-08-06
I have / and /home partitions, and did okay with switching between LMDE and Ubuntu on the / directory, while keeping /home intact.

Will this work with non-Debian based distros as well?

And if not, what are the other Debian based distros that are lazy-friendly?

Debian
Debian Mint
Ubuntu & family
Elementary OS (I think?)
any others?

And by "lazy" I mean, I don't want to spend an hour hunting down dependencies, and I like having a *big* repository.

-zami

edit - oh yeah, I forgot Mepis!

---

### Post by XubuRoxMySox on 2011-08-06
It didn't work for me between Mint Xfce 9 and Xubuntu 10.04, even though the former is based on the latter! Default settings from one to the other conflict.

It was even worse when I tried it in Debian. Ubuntu, though Debian based, is just too different these days.

If I hop, I do complete backups of important stuff and format the /home partition (leaving it the same size, but formatted) to avoid those issues.

---

### Post by zami on 2011-08-06
> **dixiedancer said:**
> It didn't work for me between Mint Xfce 9 and Xubuntu 10.04, even though the former is based on the latter! Default settings from one to the other conflict.

It was even worse when I tried it in Debian. Ubuntu, though Debian based, is just too different these days.

If I hop, I do complete backups of important stuff and format the /home partition (leaving it the same size, but formatted) to avoid those issues.

Thanks!  That does help.

I went from LMDE to Ubuntu 11.04, and had only a few minor problems with specific programs.  Well, that I was aware of anyhow... now I'm wondering if this has something to do with my three minute start-up time, which is why I'm considering another distro.

I guess I've got some backing-up to do!

-zami

---

### Post by el_koraco on 2011-08-06
Of course it's gonna work, you just need to make a new user for every distro you install, so as not to have config conflicts.

---

### Post by NightwishFan on 2011-08-08
> **el_koraco said:**
> Of course it's gonna work, you just need to make a new user for every distro you install, so as not to have config conflicts.

This will work.

Though sharing homes rarely causes major issues you might end up with grey gtk themes on boot or missing configuration files and other weirdness. Just not worth it.

Now what I do is have a 'data' partition I mount to /mnt/data during install in every OS. Then I link my folders from /mnt/data into home in each system. As long as one OS doesnt want to change the permissions to user 500 (I am looking at you Fedora) it works ok. :)

Edit: Dual booting is overrated. Virtualbox/Live CD is better. =) /opinion

---

