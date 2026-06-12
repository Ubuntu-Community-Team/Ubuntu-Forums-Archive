---
title: "[SOLVED] why my firefox browser 2.0 aways get crush?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by tuts69 on 2007-12-19
hello guys hope i can get solution for this 1 everytime i open my firefox browser and i type like http.www name of website and i hit enter my browser get crush 2 to 3 times before i can go to that website that i like to visit? what it cause of this problem? and how i can fix this? thanks in advance. im using  ubuntu 7.10 gutsy

---

### Post by bump_ on 2007-12-19
It crashes? What happens? Does it just close or what?

Also, just in case this wasn't a typo, if you want to use the full website name, it is [http://www.website.com](http://www.website.com)

not

> http.www name of website

---

### Post by rickycodie on 2007-12-19
yeah could you write a little clearer? does crush mean crash?

---

### Post by kevindubrow on 2007-12-19
Hit enter? He probably means he has to hit enter a couple of times before the website loads.

---

### Post by rickycodie on 2007-12-19
i don't know, he says that he gets crush,......so ......yeah

---

### Post by jan quark on 2007-12-19
Sometimes when I am on a site with many videos like youtube firefox just starts to load extremely slow and freezes while loading. Bang white page and I have to restart. Sometimes have also to restart the networking via sudo /etc/init.d/networking restart.Any ideas how I could specify the problem? Or any solutions? Seems similar to the problem mentioned above.

---

### Post by bump_ on 2007-12-19
> **jan quark said:**
> Sometimes when I am on a site with many videos like youtube firefox just starts to load extremely slow and freezes while loading. Bang white page and I have to restart. Sometimes have also to restart the networking via sudo /etc/init.d/networking restart.Any ideas how I could specify the problem? Or any solutions? Seems similar to the problem mentioned above.

I believe this happens because of an issue with flash. Check this out:
[http://ubuntuforums.org/showthread.php?t=590242&highlight=flash+problem+firefox](http://ubuntuforums.org/showthread.php?t=590242&highlight=flash+problem+firefox)

---

### Post by markyb86 on 2007-12-19
> **tuts69 said:**
> get crush 2 to 3 times before i can go to that website that i like to visit? 

You have to drink 2 or 3 cans of crush to get it to work?

---

### Post by rickycodie on 2007-12-19
> **markyb86 said:**
> You have to drink 2 or 3 cans of crush to get it to work?


hahahahaha lol

---

### Post by Hospadar on 2007-12-19
It sounds like maybe you need some video drivers.  try going to System->Administration->Restricted Driver Manager.  Flash and videos can really slow down a machine without proper graphics hardware or the right drivers for aforementioned video hardware.

---

### Post by jan quark on 2007-12-19
Hm... there are currently some posts dealing with the flash problem but this is history for me:) flash problem solved, videos on youtube run flawlessly, but the crushes:) still crop up sporadically. Is there a way to monitor the process of firefox to report the problem more accurately
 than crush bang boom

---

### Post by Palmyra on 2007-12-19
You guys...I think it's pretty obvious that crush means crash.  We're not all fluent in English.

Anyway, I suggest you either compile Firefox from scratch (I am not even sure that this works at all) or that you use another browser like Flock.  Flock caused serious problems for me, but it might work for you.

---

### Post by tuts69 on 2007-12-19
it suddenly close the browser. sorry if i didnt give the specific problem.

---

### Post by tuts69 on 2007-12-20
Thanks palmyra:KS

---

### Post by tuts69 on 2007-12-20
thanks sto markyb86 for funny suggestion!\\:D/

---

### Post by philinux on 2007-12-20
open a terminal and use 

```
firefox -safe-mode
```

When it crush see if there is error message.

---

