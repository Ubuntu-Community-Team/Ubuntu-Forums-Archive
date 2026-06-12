---
title: "Where do I get codecs?"
date: 2006-08-06
forum: Absolute Beginner Talk
---

### Post by vaazu on 2006-08-06
When I try to play an .avi file in movie player it just wont work no sound no picture. Am I missing some codecs because I havent any of them. And If I do have to install them Where do I get them?

---

### Post by lamego on 2006-08-06
Use [http://easyubuntu.freecontrib.org/](http://easyubuntu.freecontrib.org/) .

---

### Post by vaazu on 2006-08-06
Ok I´ll try it

---

### Post by richbarna on 2006-08-06
And :-
[http://doc.gwos.org/index.php/DapperGuide#How_to_install_Multimedia_Codecs](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Multimedia_Codecs)

---

### Post by Buffalo Soldier on 2006-08-06
Go through the [Restricted Format](https://help.ubuntu.com/community/RestrictedFormats) wiki.

---

### Post by vaazu on 2006-08-06
Ok, but I have a question If I download package files or for example easyubuntu downloads them automatilcay then are they restored or deleted after installation? And if they are restored then can I delete them and if I can form where?

---

### Post by xmastree on 2006-08-06
> **Buffalo Soldier said:**
> Go through the [Restricted Format](https://help.ubuntu.com/community/RestrictedFormats) wiki.

Hmm... is this correct?
```
wget -c http://packages.freecontrib.org/ubuntu/plf/pool/dapper/i386/non-free/w32codecs/w32codecs_20060611-[COLOR="Red"]**1plf1_i386**[/COLOR].deb
sudo dpkg -i w32codecs_20060611-[COLOR="Red"]**0.0_i386**[/COLOR].deb
```
Surely they should be the same filename?

---

