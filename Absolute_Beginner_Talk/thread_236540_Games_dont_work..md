---
title: "Games dont work."
date: 2006-08-14
forum: Absolute Beginner Talk
---

### Post by jasonpeinko on 2006-08-14
I installed several games like xmoto, tuxracer, scroched3d and none ofthem work.

---

### Post by zxee on 2006-08-14
> **jasonpeinko said:**
> I installed several games like xmoto, tuxracer, scroched3d and none ofthem work.

Perhaps you don't have a 3D video driver installed/enabled?
What video card does your computer use? 
If you don't know do lspci -v from a terminal and post the output.

---

### Post by jasonpeinko on 2006-08-14
ati radeon 9200 
when i run fglrxinfo
i get this error
fglrxinfo: symbol lookup error: /usr/lib/libglide3.so.3: undefined symbol: __LINE__

---

### Post by jasonpeinko on 2006-08-14
how do i fix this problem?

---

### Post by Pipone on 2007-01-18
> **jasonpeinko said:**
> ati radeon 9200 
when i run fglrxinfo
i get this error
fglrxinfo: symbol lookup error: /usr/lib/libglide3.so.3: undefined symbol: __LINE__

I got the same error after removing Beryl. I fix it after re-installing ati radeon drivers etc..
System>>Administrasion>>Symnatic package manager; Search: ati radeon install or reinstall all except gatos.
After doing this when running fglxinfo you should be with mesa drivers. Reinstall ati drivers and all should be fine [http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Installation_Guide) ;)

---

