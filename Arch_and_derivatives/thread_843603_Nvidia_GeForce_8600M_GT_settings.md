---
title: "Nvidia GeForce 8600M GT settings"
date: 2008-06-28
forum: Arch and derivatives
---

### Post by ruffEdgz on 2008-06-28
I didn't know if anyone who installed arch linux had a GeForce 8600M GT as their GPX card.

I have installed what was said at the beginning guide from the arch wiki page which was helpful but I don't think the nvidia card is actually working. I can't really figure it out but I just wanted some more advise on this.

I know Ubuntu and Arch are different distro's but when viewing Ubuntu with this laptop, it just looks 'better' but with Arch, I feel like I'm looking at everything with 1024x768.

Below you will see what I got when I ran the command: lspci | grep VGA and a picture of what my desktop looks like (.png).

```

01:00.0 VGA compatible controller: nVidia Corporation GeForce 8600M GT (rev a1)

```

If you need me to show you my xorg.conf file, I can do that as well. As a side note, I checked out the arch linux wiki and found a page that talked about this GPX card but didn't work that well: [http://wiki.archlinux.org/index.php/Dell_Inspiron_1520](http://wiki.archlinux.org/index.php/Dell_Inspiron_1520)

Thanks for any help but just thought I would ask :D

---

### Post by ruffEdgz on 2008-06-30
Well, it was my fault on this one but I just felt that my settings in the xorg.conf

I was also trying to find the version that was installed for:

```

pacman -S nvidia

```

The version that is being used is v173.14.05 and I just couldn't find it on the site ([http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)) and I was convincing myself that it wasn't that good of a version. I searched and searched and just started playing with it and just found ways to get this OS a lot better.

The config was the default on that was given to me during the starting installation. I used the:
```

nvidia-xconf --composite --add-argb-glx-visuals

```

All in all, I have a better looking Arch and I'm happy!

Sorry for the post but it helped me since after posting it, I wanted to figure this more out :D

-Ruff

---

### Post by mips on 2008-07-01
Moral of the story? Follow the Beginners Guide as that information was in there :)

Something else you might want to look into is anti aliasing of fonts in your kde control center.

---

### Post by ruffEdgz on 2008-07-01
Well that is the moral of the story and I followed it all the time for all my installs ([http://wiki.archlinux.org/index.php/Beginners_Guide](http://wiki.archlinux.org/index.php/Beginners_Guide)) but I just thought the version of the nvidia card wasn't the newest so I did some more research.

The beginners guide is nice but people need to really read it carefully to understand which step they need to follow.

:D

---

