---
title: "system restarts when i log on"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by astathios on 2008-01-08
hello ,
i need help , when i log on my system by giving username and password it restarts.
this happend after an attempt to make enable the compiz. i use an ati x1400 card , i found in a forum this code   
 sudo apt-get install xserver-xgl
and since the time i run it on a terminal i cant log in my desktop.now i log in failstart system.
what can i do to repair it?
i dont have any knowlege in linux i am a new user 
thank you very much

---

### Post by philinux on 2008-01-08
At the log in screen there is an options button. Maybe choose failsafe mode i think it's called.

---

### Post by astathios on 2008-01-08
yes i log in failsafe sorry my mistake
so can i do something to repair it ?
or is ok now?

---

### Post by astathios on 2008-01-08
i run again this command in terminal sould i remove this package?sudo apt-get install xserver-xgl

as i remember when i install it ,it automatic remove some packages that was in my system
but i dont remember which was .
any help?

---

### Post by astathios on 2008-01-08
please any help ?
i dont know what to do

---

### Post by stump138 on 2008-01-08
my suggestion at this point would be to re-install your desktop.  May be a bit heavy-handed, but at least it will reset you to a default setup where you can start working again perhaps
```
sudo aptitude reinstall ubuntu-desktop
```

---

### Post by LowSky on 2008-01-08
if you want your ATI graphics to work try a program named Envy [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu5_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu5_all.deb)

---

### Post by astathios on 2008-01-08
> **LowSky said:**
> if you want your ATI graphics to work try a program named Envy [http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu5_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu5_all.deb)

didnt solve my problem but it update my card software thnx

---

### Post by astathios on 2008-01-08
any other sugestion?
i update my ati
i reinstall desktopi 
i removed xserver-xgl but when i install this first time it removed some files then was when my problem began.

---

