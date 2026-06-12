---
title: "i can't install"
date: 2006-08-04
forum: Absolute Beginner Talk
---

### Post by careca on 2006-08-04
i launched adept but and tried to install something.
While installing I hit 'Show details' and I was asked to reply "Yes" or "No", but the console went crazy and I couldn't hit enter.

Then I closed adept with brute force.

Now I want to re-lauch it but error message come:
```
You will not be able to change your system settings in any way (install, remove or upgrade software), because another process is using the packaging system database (probably some other Adept application or apt-get or aptitude). Please close the other application before using this one.
```

I know there are no other processes running, it's just because I closed brute force adept.

---

### Post by Dinerty on 2006-08-04
```
sudo dpkg --configure -a
```

Originally said by **tcollogne** :)

Think the servers are playing up I had same prob when updating

---

### Post by careca on 2006-08-04
Thank you! It works!

---

