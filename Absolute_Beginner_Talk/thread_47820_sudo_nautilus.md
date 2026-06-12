---
title: "sudo nautilus?"
date: 2005-07-10
forum: Absolute Beginner Talk
---

### Post by gammyhand on 2005-07-10
I need to be able to delete stuff from /var/ etc through nautilus. How do I enable this without running into lack of permission errors?

---

### Post by nemin on 2005-07-10
[QUOTE=gammyhand]I need to be able to delete stuff from /var/ etc through nautilus. How do I enable this without running into lack of permission errors?[/QUOTE]
I guess the title of this topic is the only solution. Or you should chmod 777 /var/ etc. first, but I don't think that's a good idea ;)

---

### Post by gammyhand on 2005-07-10
[QUOTE=nemin]I guess the title of this topic is the only solution. Or you should chmod 777 /var/ etc. first, but I don't think that's a good idea ;)[/QUOTE]
 I should have elabourated...I don't want sudo permissions everywhere....but I think that is not possible....If /var/www/ is not 777 though I can't save pages to it in Nvu or Anjuta :(

---

### Post by rider343 on 2005-07-10
sudo nautilus --browser

---

### Post by gammyhand on 2005-07-10
[QUOTE=rider343]sudo nautilus --browser[/QUOTE]
 where does that command go?

---

### Post by jasplund on 2005-07-10
in a terminal "sudo nautilus /var"

or in Application --> Run Application and then type gksudo nautilus

---

### Post by Kvark on 2005-07-10
Use gksudo for GUI apps, using sudo for GUI apps may mess things up.

As for /var/www/, The best option IMO is to reconfigure apache to use a directory inside your home.

---

