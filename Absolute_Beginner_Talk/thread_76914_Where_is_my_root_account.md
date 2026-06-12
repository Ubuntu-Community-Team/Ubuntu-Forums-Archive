---
title: "Where is my root account?"
date: 2005-10-15
forum: Absolute Beginner Talk
---

### Post by mog27 on 2005-10-15
I just clean installed Breezy and it did not ask me for a root password during install.  Now I have no idea what the root password is, if there is even one.  How would I go about creating a root passwd?

---

### Post by adwait on 2005-10-15
Root account is by default disabled in Ubuntu. You can use sudo and the password of the first user created
```
sudo <command>
```
This will run any command as the root user. Although it is not reccomended, if you want to enable the root account you can do that with
```
sudo passwd 
```

This has been discussed n number of times on the forums, so please search them before posting questions.

---

### Post by aysiu on 2005-10-15
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by mog27 on 2005-10-15
[QUOTE=adwait]Root account is by default disabled in Ubuntu. You can use sudo and the password of the first user created
```
sudo <command>
```
This will run any command as the root user. Although it is not reccomended, if you want to enable the root account you can do that with
```
sudo passwd 
```

This has been discussed n number of times on the forums, so please search them before posting questions.[/QUOTE]

root was enabled in Hoary when I used that.

---

### Post by adwait on 2005-10-15
That is impossible, out of the box root has always been disabled. And if you enabled it later, and then performed a clean install........you can't expect your tweaks to be present right?

---

### Post by mog27 on 2005-10-15
[QUOTE=adwait]That is impossible, out of the box root has always been disabled. And if you enabled it later, and then performed a clean install........you can't expect your tweaks to be present right?[/QUOTE]

I am telling you.  When I had Hoary I was able to "su -" and be root.  I did no tweaks or modifications at all. This was like this by default.

---

### Post by aysiu on 2005-10-15
[QUOTE=mog27]I am telling you.  When I had Hoary I was able to "su -" and be root.  I did no tweaks or modifications at all. This was like this by default.[/QUOTE] You may have done an expert install. I think in an expert install you can enable root. In regular installs for Hoary and Breezy there is no root.

---

### Post by mog27 on 2005-10-15
[QUOTE=aysiu]You may have done an expert install. I think in an expert install you can enable root. In regular installs for Hoary and Breezy there is no root.[/QUOTE]

Ah gotcha.  I guess that explains it then.  Thanks

---

### Post by majikstreet on 2005-10-15
sudo su
then enter your password for your account and you are root.
to get out just type exit


majikstreet

---

### Post by learner on 2005-10-18
hi,does anyone know how to disable root, if the root is enabled, i know this might sound a bit weird.

---

### Post by the_clown on 2005-10-18
[QUOTE=learner]hi,does anyone know how to disable root, if the root is enabled, i know this might sound a bit weird.[/QUOTE]
sudo passwd -l root

---

