---
title: "updates get failed to fetch error"
date: 2007-01-18
forum: Absolute Beginner Talk
---

### Post by carloslosgrande on 2007-01-18
Hi Everyone.
Some days ago I got some new updates ready to be downloaded, 7 of them. On trying to do this I got the error
> W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20061205_all.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-en/language-pack-gnome-en_6.06+20061205_all.deb)
  404 Not Found

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_6.06+20061130_all.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-gnome-zh/language-pack-gnome-zh_6.06+20061130_all.deb)
  404 Not Found

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en/language-pack-kde-en_6.06+20061201_all.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-en/language-pack-kde-en_6.06+20061201_all.deb)
  404 Not Found

W: Failed to fetch [http://cn.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-zh/language-pack-kde-zh_6.06+20061130_all.deb](http://cn.archive.ubuntu.com/ubuntu/pool/main/l/language-pack-kde-zh/language-pack-kde-zh_6.06+20061130_all.deb)
  404 Not Found


I kept trying from time to time and after a few days 3 of these updates did thier thing. The other 4 are steadfastly refusing.
aptitude update runs fine with the result that these 4 are 'held back'
I'm running Dapper. I searched the posts and the only thing I saw related to this was a problem resolved thru resetting the proxy. I don't run a proxy, but anyway I ran these
> buddha@Rubaiyat-desktop:~$ cat /etc/apt/apt.conf
Acquire::http::Proxy "false";
buddha@Rubaiyat-desktop:~$ cat /etc/environment
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games"
LANG="en_AU.UTF-8"
LANGUAGE="en_AU:en"
buddha@Rubaiyat-desktop:~$

I assume the Proxy "false" means that I don't have one.
Its a little thing and may only relate to these language updates, but still a little annoying.
The language settings as "en-AU:en" wouldn't be behind this??
Any ideas?

---

### Post by taurus on 2007-01-18
Edit /etc/apt/sources.list and remove the **cn.** from your repos.

```
gksudo gedit /etc/apt/sources.list
```
Save it and run

```
sudo aptitude update
sudo aptitude upgrade
```

---

### Post by jvc26 on 2007-01-18
Can you post the output of your sources.list file? The cn. in your address search looks odd.
```

gksudo gedit /etc/apt.sources.list

```
It may be that there is an error in the list which is stopping it downloading files.

Edit:: man.. once again taurus' lightening speed beats me ;)
Il

---

