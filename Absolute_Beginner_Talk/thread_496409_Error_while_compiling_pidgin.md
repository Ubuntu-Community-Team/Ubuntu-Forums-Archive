---
title: "Error while compiling pidgin"
date: 2007-07-09
forum: Absolute Beginner Talk
---

### Post by vniles on 2007-07-09
Hello

I have pidgin tar ball. While compiling it, i get error as '**error: C compiler cannot create executable**

Need help urgently

Please help
Thanks in advance

Niilesh

---

### Post by meborc on 2007-07-09
you can get the pidgin deb file for feisty here - [http://www.getdeb.net/release.php?id=1045](http://www.getdeb.net/release.php?id=1045)

download both to your home folder, then
```
cd
sudo dpkg -i pidgin*
sudo apt-get -f install
sudo rm pidgin*
```

the -f install bit downloads the extra dependencies... so don't be afraid when the dpkg -i fails... :)

---

### Post by FNM on 2007-07-21
Is there a package compiled for PowerPC?

---

### Post by ramjet_1953 on 2007-07-21
Have you installed build essential?

If not:

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Regards,
Roger :cool:

---

