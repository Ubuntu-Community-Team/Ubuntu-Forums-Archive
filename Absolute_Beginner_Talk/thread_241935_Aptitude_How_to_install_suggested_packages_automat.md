---
title: "Aptitude: How to install suggested packages automatically?"
date: 2006-08-23
forum: Absolute Beginner Talk
---

### Post by Akhran on 2006-08-23
I've added the following line ```
APTITUDE::Keep-Suggests "true";
``` into /etc/apt/apt.conf.

However, when I install a package, the suggested packages are not automatically installed.

Any help would be appreciated.

Thanks !

---

### Post by bodhi.zazen on 2006-08-23
```
sudo aptitude --with-recommends
```

Or

```
sudo aptitude --with-suggests
```

---

### Post by Akhran on 2006-08-23
--wish-suggests seems to be a invalid switch. When I I tried ```
sudo aptitude --with-suggests install somepackage
```, it displays a whole list of options.

Is ```
APTITUDE::Keep-Suggests "true";
``` the right statement to put in /etc/apt/apt.conf for suggested packages to be installed as dependencies?

Thanks.


> **bodhi.zazen said:**
> ```
sudo aptitude --with-recommends
```

Or

```
sudo aptitude --with-suggests
```

---

### Post by Akhran on 2006-08-24
I'll put in the url that provides me with the info, in case I miss out something:

[http://people.debian.org/~dburrows/aptitude-doc/en/ch02s04s05.html#configKeepSuggests](http://people.debian.org/~dburrows/aptitude-doc/en/ch02s04s05.html#configKeepSuggests) 

And scrolling down we have 

Option: Aptitude::Keep-Suggests 
Default: false 
Description: If this option is true, aptitude will keep automatically installed packages on the system as long as any installed package suggests them. For more information, see the section called &#8220;Managing automatically installed packages&#8221;. 

Somehow adding Aptitude::Keep-Suggest "true"; into /etc/apt/apt.conf doesn't work for me.

Does it work for you?

Thanks.

---

### Post by bodhi.zazen on 2006-08-24
Honestly, I do not use this setting. I prefer to review the suggested packages and install only if I need them. They are not needed and can clutter your system (with increasing packages you increase dependencies and upgrading is more likely to become problematic). The last time I did this was in Debian some time ago and I have already told you more then I know (--with suggests worked in Debian the last time I tried).

Not sure why this is not working for you. Just answering so you do not feel ignored.

---

### Post by harisund on 2006-08-24
I know I sound stupid, but perhaps it might be a difference between APTITUDE and aptitude or Aptitude?

---

### Post by Akhran on 2006-08-24
Tried that, doesn't seem to make a difference.

Thanks :)

> **harisund said:**
> I know I sound stupid, but perhaps it might be a difference between APTITUDE and aptitude or Aptitude?

---

### Post by msak007 on 2006-08-24
> **Akhran said:**
> Option: Aptitude::Keep-Suggests 
Default: false 
Description: If this option is true, aptitude will keep automatically installed packages on the system as long as any installed package suggests them. For more information, see the section called “Managing automatically installed packages”. 

Is it just me, or am I understanding that to mean that with that option when you do an uninstall, aptitude won't remove packages that are still "suggested" by other packages. I'm not seeing anything about automatically installing packages that are recommended, only *not* *uninstalling* ones that are already installed and suggested by another installed package when you do an uninstall.

If you want to automatically install everything, you could try a 

```
sudo aptitude -r
``` or ```
sudo aptitude --with-recommends
``` which will treat recommended or suggested packages as dependencies and install them.

---

