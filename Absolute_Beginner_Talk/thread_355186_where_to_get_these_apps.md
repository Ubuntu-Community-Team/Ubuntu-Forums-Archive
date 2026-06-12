---
title: "where to get these apps"
date: 2007-02-06
forum: Absolute Beginner Talk
---

### Post by sankarv on 2007-02-06
Softwares like Wine, Real Player cannot be found in the Synaptic for download/install. Are there any alternatives or from where can we get this?. Also Synaptic download these files and then installs them. Do the downloaded files exist in our system. If so what is the path where they are?

---

### Post by nhandler on 2007-02-06
Have you enabled all the repositories? If not, check out the Ubuntu Guide for info on how to do that.

Ubuntu Guide: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)


After you enable all the repositories, try installing the apps again.

---

### Post by ComplexNumber on 2007-02-06
wine is in the repos, but i don't think realplayer is. 

i suspect that the reason why you can't see wine in synaptic is because you haven't enabled the multiverse and universe repositories. to enable them, fire up synaptic. then go to the menu, select 'settings', then 'repositories'. click on them all. then reload. you should now see wine in there.

you can get real player from [here]("http://www.real.com/linux?pcode=rn&am"). NOTE: i had a not too easy time uinstalling it, so just be aware. there is a script that is available to uninstall it (i had to google for it), but its not supported by real.com.

---

### Post by nhandler on 2007-02-06
> **ComplexNumber said:**
> wine is in the repos, but i don't think realplayer is. 

i suspect that the reason why you can't see wine in synaptic is because you haven't enabled the multiverse and universe repositories. to enable them, fire up synaptic. then go to the menu, select 'settings', then 'repositories'. click on them all. then reload. you should now see wine in there.

you can get real player from [here]("http://www.real.com/linux?pcode=rn&am"). NOTE: i had a not too easy time uinstalling it, so just be aware. there is a script that is available to uninstall it (i had to google for it), but its not supported by real.com.

[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

RealPlayer is in the PLF Repository.

---

### Post by ComplexNumber on 2007-02-06
> **Cheater said:**
> [http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Multimedia_Player_.28RealPlayer_10.29)

RealPlayer is in the PLF Repository.
ahhh well, i hadnt seen that.

---

### Post by nalioth on 2007-02-06
You can get Opera, Realplayer and a few other proprietary programs from the dapper commercial repository (it works on edgy too)
```

deb http://archive.canonical.com/ubuntu dapper-commercial main

```

Add the above to your sources.list and update your apt-get/synaptic.  You should then have some "commercial" programs available.

---

### Post by sankarv on 2007-02-06
Thanks,



>  Do the downloaded files exist in our system. If so what is the path where they are?


and on this...?

---

### Post by nalioth on 2007-02-08
Any application that synaptic/apt/adept installs will be in /usr/bin/

Be careful modifying anything not in your home directory.

---

