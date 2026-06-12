---
title: "how to add CD repository to aptitude?"
date: 2006-06-25
forum: Absolute Beginner Talk
---

### Post by tubunu on 2006-06-25
I'm running Ubuntu but would like to try out Kubuntu alongside. Whenever I type the command to install kubuntu desktop, it starts fetching files off a server repository. I'd like it to install off my Kubuntu CD (I've already added it in Synaptic), but I don't know how to make Aptitude see the Kubuntu CD.. Any help?

---

### Post by deanjm1963 on 2006-06-25
in a terminal just type

sudo apt-cdrom add

that should do it

---

### Post by tubunu on 2006-06-27
Thanks, that did add the Kubuntu CD, but it doesn't solve my problem. When I type 
```
sudo apt-get install kubuntu-desktop
```
it doesn't fetch files from Kubuntu CD, but starts downloading them from some server. 

Does anyone know how to install Kubuntu desktop using Kubuntu CD? ](*,)

---

### Post by drtvasudevan on 2006-06-27
start synaptic package manager.
click settings repositaries.
uncheck all repositories except cdrom.
close.
click apply.
now only the cd is registered as the repository.
so when you execute the comand it will take the files from the cd

but it must be an alternate cd if i remember right. anyway try.

tv

---

### Post by tubunu on 2006-06-27
I did as you've suggested, but now it tells me package kubuntu-desktop cannot be found. Hello?

](*,)

---

### Post by aysiu on 2006-06-27
Any time you add a new repository, you always have to ```
sudo aptitude update
``` to have its contents recognized.

---

### Post by tubunu on 2006-06-27
Thanks, aysiu, 
after updating aptitude it still says it cannot find package kubuntu-desktop.... :confused: 

(the Kubuntu CD is still in the drive)

---

### Post by aysiu on 2006-06-27
Did you add a Kubuntu Desktop CD or a Kubuntu Alternate CD?

The Desktop CD's repository has a very few things on it, like *build-essential*. It does not have the *kubuntu-desktop* metapackage on it.

The Alternate CD has *kubuntu-desktop* on it.

---

### Post by tubunu on 2006-06-30
Yeah, that was Kubuntu Desktop CD that I added. So this means I can't install KDE unless I have Kububtu Alternate or simply download off the Internet, right? :confused:

---

### Post by user1397 on 2006-06-30
[quote=tubunu]Yeah, that was Kubuntu Desktop CD that I added. So this means I can't install KDE unless I have Kububtu Alternate or simply download off the Internet, right? :confused:[/quote]Right!  If you want to install it via the internet, take a look at the first link in my signature.

---

