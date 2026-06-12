---
title: "skype for ubuntu"
date: 2006-05-15
forum: Absolute Beginner Talk
---

### Post by s_raghu20 on 2006-05-15
Hi Guys,

Just wondering, if someone can point to a version of skype that is known to work good on Ubuntu dapper beta (6.06)

Just checked their web page (skype) and it mentions some distributions, but not U Ubuntu... 

[http://www.skype.com/download/skype/linux/](http://www.skype.com/download/skype/linux/)

Looking forward to your response.

regards
raghav..

---

### Post by Jagot on 2006-05-15
[https://wiki.ubuntu.com/SkypeHowto#head-8729b3df199dd7c4591bc717d35ae4c3b40ef5a0](https://wiki.ubuntu.com/SkypeHowto#head-8729b3df199dd7c4591bc717d35ae4c3b40ef5a0)

You need to get the Debian package on that page, which should work with Ubuntu as it states there.

---

### Post by macdo on 2006-05-15
The debian package on the skype website should work. Download it to your Desktop, then ```
cd Desktop
sudo dpkg -i skype_1.2.0.18-2_i386.deb
```

Sorted!

---

### Post by richbarna on 2006-05-15
Or put this in your sources.list
> ## Skype
 deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

---

### Post by nalmeth on 2006-05-15
You'll soon find that skype linux doesn't support video yet..
:rolleyes:

boo

It's still good, but lame that they haven't given us video capability

---

### Post by telepheedian on 2006-05-15
You should also try EasyUbuntu or Automatix, A lot of beginner's slip-ups can be sloved using these.

---

### Post by aysiu on 2006-05-15
[QUOTE=telepheedian]You should also try EasyUbuntu or Automatix, A lot of beginner's slip-ups can be sloved using these.[/QUOTE] I don't think those have been adapted for Dapper yet.

---

