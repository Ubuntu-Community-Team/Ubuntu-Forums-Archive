---
title: "Ubuntu V's Edubuntu"
date: 2006-05-03
forum: Absolute Beginner Talk
---

### Post by jethro10 on 2006-05-03
Hi,
I'm a new linux user and could not get V5 to install so tried 6 testing, with Gnome and its been ok now for weeks.
However i've just noticed, Ubuntu startup screen has somehow changed to edubuntu !
Honest it definatley was ubuntu at first cos i've booted from the disk I made to check!
I've no idea how it happened, but is it going to make any difference?
If so how can I go back without a full re-install ?

Ta
Jeff

---

### Post by zxcvbnm on 2006-05-03
It means you must of downloaded the package  desktop of Edubuntu.....Don't worry, You can change it back if you uninstall the package...It's just a different theme

---

### Post by halfvolle melk on 2006-05-03
No, it just means that the Ubuntu boot splash somehow got replaced by the Edubuntu splash, but other than that it should be a perfectly good Ubuntu install. For some reason this can occur sometimes when the kernel is replaced. If you want you can put the Ubuntu splash back, but I can't remeber how nor can I find it through a forum search. Anyway, no need to reinstall.

---

### Post by jethro10 on 2006-05-03
Thanks,
it seems like its not serious so I wont worry....

J

---

### Post by makhand on 2006-06-24
I have this same problem. it was my own doing. I would like to get rid of the edubuntu boot splash, but havent been able to figure out how to do this. Anyone?

---

### Post by uzi09 on 2006-06-24
paste this in a terminal: 
```

 sudo update-alternatives --configure usplash-artwork.so

```

Choose usplash-default.so for the brown Ubuntu splash.

Then, paste this in a terminal: 
```

sudo dpkg-reconfigure linux-image-`uname -r`
```

---

### Post by makhand on 2006-06-24
perfect! Thanks uzi.

except i think ```
sudo update-alternatives --configure usplash-artwork.so
```
should be ```
sudo update-alternatives --config usplash-artwork.so
```

---

