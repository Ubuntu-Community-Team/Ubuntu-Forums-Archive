---
title: "cant log into root because passwd change is required"
date: 2012-07-13
forum: Any Other OS
---

### Post by z3nhakr on 2012-07-13
i cant change the password and i get "authentication token manipulation error. i just set the hardware clock/time and from googling that seems to be the cause. how can i login?
btw it's debian not ubuntu but i figure the authentication should be pretty much identical.

---

### Post by Kopkins on 2012-07-13
So can you access the system at all?

If you can't, you can use a live cd to chroot into your locked out system. From there you should be able to change whatever password you need using:
```
passwd user
```

Please, anyone correct me if I am incorrect.

---

### Post by z3nhakr on 2012-07-13
its running off a usb on an ARMv11 development board but i can access the system files on my laptop

---

### Post by ijumpship on 2012-07-13
You have to do it from the machine,not through SSH.I
If the Arm board have a next USB boot-able slot.
Just make another USB

---

### Post by z3nhakr on 2012-07-13
it does but i cant boot from it. i can mount the filesystem on my ubuntu machine. can i reset the expiration date from there? maybe /etc/shadow?

---

### Post by ijumpship on 2012-07-13
Well here is where you gonna be surprise,In a linux file system each files depend on another.the mere fact you can see the passwd or /etc/shadow do not mean you can change it.

If you manage to change it,which I am sure it tells you that there is a permission problem,will mean you can hack the encryption or password.Which may brick your box

You have to drop Grub and the Kernel.Grub will rebuild when you restart and recognised the new password.

So if your USB has only system file,start over.Or when you hack the password files let us all know.

---

### Post by coffeecat on 2012-07-14
> **z3nhakr said:**
> 
btw it's debian not ubuntu

*Thread moved to **Other OS/Distro Talk**.*

---

### Post by z3nhakr on 2012-07-15
so if i hack the password it will reset the expiration time? im guessing your talking about a hack where it changes the password instead of brute forcing it like ntpasswd or whatever for reseting windows passwords. i think iv heard of a way to do that on linux systems but it's probably not very straightforward... but would that reset the expiration date? hmmmm.. it seeems waaay to complicated. why won't it let me just change the password? oh and if i made another user and changed the hardware time, would i have this problem with that user too?

---

