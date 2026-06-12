---
title: "Insatlling lm sensors"
date: 2006-05-22
forum: Absolute Beginner Talk
---

### Post by meniscus on 2006-05-22
Hi every1, im tryin to install lm-sensors from this link 
[http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sen](http://www.ubuntuforums.org/showthread.php?t=2780&highlight=lm-sen)


and im on step 3 after answering yes to all the qs.


On step 3 when it asks me 

Do you want to add these lines to /etc/modules automatically? (yes/NO)YES

I say yes!

But after it says manually add the lines to /etc/modules in the reverse order. I cant because modules has only root permissions and wont allow me to.

Does any1 know a way around this?

Thanks
meniscus

---

### Post by Klaidas on 2006-05-22
Are you the administrator of you computer and you don't know how to gain root acces? Then see [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)
If you are a regular user, that I don't think that it is possible :-k

---

### Post by Ecthelion on 2006-05-22
doesn't
```
sudo gedit /etc/modules
```
work?

With sudo you get the root permissions so it shouldn't cause any trouble

---

### Post by Ecthelion on 2006-05-22
[QUOTE=Klaidas]Are you the administrator of you computer and you don't know how to gain root acces? Then see [http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)
If you are a regular user, that I don't think that it is possible [/QUOTE]

He does know the root password otherwise he couldn't do 
>  1. Install lm-sensors using apt-get or the Synaptic GUI.

sudo apt-get install lm-sensors
So he can gain root acces

---

### Post by nocturn on 2006-05-22
Deleted the double (empty) thread in the Desktop support thread.

---

