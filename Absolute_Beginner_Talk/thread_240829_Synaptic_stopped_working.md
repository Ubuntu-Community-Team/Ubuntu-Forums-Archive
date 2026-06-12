---
title: "Synaptic stopped working"
date: 2006-08-21
forum: Absolute Beginner Talk
---

### Post by Djieff on 2006-08-21
Hi,

I'm kind of new in the community, so if somebody know that my question has already been talked about, please relink me ;) thanks!


So i've installed Ubuntu 6.06, and I began having a lot of fun using it. Installing software via synaptic and automatix. I installed XGL also and a lot of things. However now I do not understand because when I start synaptic, I get a prompt to enter my root password. I enter it. then... nothing... Synaptic do not start anymore!:confused: 

I tried reinstalling it, reinstall XGL, start synpatic in Gnome. Nothing works, do somebody got an idea?

thanks,
djieff

---

### Post by taner on 2006-08-21
try to install something with terminal and it will let u the error why synaptic isn't work

like this
sudo apt-get install yakuake

---

### Post by arnieboy on 2006-08-21
> **Djieff said:**
> Hi,

I'm kind of new in the community, so if somebody know that my question has already been talked about, please relink me ;) thanks!


So i've installed Ubuntu 6.06, and I began having a lot of fun using it. Installing software via synaptic and automatix. I installed XGL also and a lot of things. However now I do not understand because when I start synaptic, I get a prompt to enter my root password. I enter it. then... nothing... Synaptic do not start anymore!:confused: 

I tried reinstalling it, reinstall XGL, start synpatic in Gnome. Nothing works, do somebody got an idea?

thanks,
djieff

just do this:
```
sudo ln -s /usr/lib/libvte.so.9 /usr/lib/libvte.so.4
```
and synaptic will work again

---

### Post by Djieff on 2006-08-22
Thanks!

it works again! but why I had to create a symbolic link in       order to make it work again?

anyway it is working, this is the important!=D>

---

### Post by mostwanted on 2006-08-22
> **Djieff said:**
> Thanks!

it works again! but why I had to create a symbolic link in       order to make it work again?

anyway it is working, this is the important!=D>

You're using the unofficial Compiz repos which are causing this problem (library versioning issues).

---

