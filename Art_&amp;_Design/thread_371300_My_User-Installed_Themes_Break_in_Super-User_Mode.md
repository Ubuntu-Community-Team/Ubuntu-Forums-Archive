---
title: "My User-Installed Themes Break in Super-User Mode"
date: 2007-02-26
forum: Art &amp; Design
---

### Post by smultronstallet on 2007-02-26
I've noticed that the themes *I've* installed (as opposed to the ones that came default on the system) break apart to an ugly theme whenever I run an application in super-user mode (i.e. any administrative task). For instance, the Human theme works fine, but an [[COLOR="Orange"]altered Human version[/COLOR]]("http://gnome-look.org/content/show.php?content=53558") off of GNOME-Look.org breaks apart in su mode. Same thing happens with Murrine-based themes, too. The attached screenshot should give a better explanation. Any help to resolve this would be much appreciated.

---

### Post by smultronstallet on 2007-02-27
Figured it out. I had to manually install the new themes into */usr/share/themes/* rather than *~/.themes/*
Not sure why it would act this way to begin with, but maybe this will help someone else having a similar problem.

---

### Post by v8YKxgHe on 2007-02-27
> **smultronstallet said:**
> Figured it out. I had to manually install the new themes into */usr/share/themes/* rather than *~/.themes/*
Not sure why it would act this way to begin with, but maybe this will help someone else having a similar problem.

Thats because there a different themes set for each user. Root can have a different theme to you're normal User, and so to make sure when you run programs as root they have the same theme, you can do these commands in terminal:

```
sudo ln -s /home/USERNAME/.themes /root/.themes
sudo ln -s /home/USERNAME/.icons /root/.icons
sudo ln -s /home/USERNAME/.fonts /root/.fonts
```

Regards,

---

### Post by smultronstallet on 2007-02-28
> **AlexC_ said:**
> Thats because there a different themes set for each user. Root can have a different theme to you're normal User, and so to make sure when you run programs as root they have the same theme, you can do these commands in terminal:

```
sudo ln -s /home/USERNAME/.themes /root/.themes
sudo ln -s /home/USERNAME/.icons /root/.icons
sudo ln -s /home/USERNAME/.fonts /root/.fonts
```

Thanks for the tip. Everything is running smoothly now. :)

---

