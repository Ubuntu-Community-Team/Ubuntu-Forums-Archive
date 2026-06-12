---
title: "How to install LXDE after base install"
date: 2012-04-19
forum: Any Other OS
---

### Post by asifnaz on 2012-04-19
I have a laptop with only 128MB ram . I want to install base system from  CD1 by uncheckïng "D.E" during installation . I want to install  LXDE  later . The problem is that I have 
lack of CLI experience to install LXDE . I think I will have to install X11 as well (if I am not wrong ) .

I  need help to install LXDE using CLI . And please note that I am an  in-experienced user so please guide me step by step answer .

I will really appreciate your help

---

### Post by sudodus on 2012-04-19
Try
```
sudo apt-get install lxde
```
I think it is enough, that it will install other necessary packages.

---

### Post by IWantFroyo on 2012-04-19
I would do:
```
sudo apt-get install lubuntu-desktop
```

This will give you the customized Ubuntu version of the LXDE. It should handle the dependencies as well.

You could do what sudodus suggested as well.

---

### Post by lykwydchykyn on 2012-04-19
lubuntu-desktop is not available in Debian, AFAIK. 

You may need to install the xorg package as well as LXDE.

---

### Post by IWantFroyo on 2012-04-19
> **lykwydchykyn said:**
> lubuntu-desktop is not available in Debian, AFAIK. 

You may need to install the xorg package as well as LXDE.

Ah, missed the [Debian] tag.

<ot>, if xorg-xinit isn't installed as a dependency, then that should be installed as well, as lykwydchykyn said.

---

### Post by lykwydchykyn on 2012-04-19
> **IWantFroyo said:**
> Ah, missed the [Debian] tag.

<ot>, if xorg-xinit isn't installed as a dependency, then that should be installed as well, as lykwydchykyn said.

It's a recommend, but not a dependency.  It may or may not install automatically, depending on system policy.

---

### Post by dzponce11 on 2012-04-19
sudo apt-get install lxde-desktop

---

### Post by dzponce11 on 2012-04-19
If not, check lxde.org

---

### Post by chrissywissy on 2012-04-23
> **dzponce11 said:**
> If not, check lxde.org
 
Seconded. CD images are available there for LXDE-flavoured Debian.

---

### Post by Erik1984 on 2012-04-24
> **chrissywissy said:**
> Seconded. CD images are available there for LXDE-flavoured Debian.

True. I used the squeeze xfce+lxde CD and it let's you choose between installing the XFCE or LXDE version at boot. it's in here: [http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/](http://cdimage.debian.org/debian-cd/6.0.4/i386/iso-cd/) (this is the list for i386 debian CDs)

---

