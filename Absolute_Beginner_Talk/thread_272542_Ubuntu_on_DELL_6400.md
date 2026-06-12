---
title: "Ubuntu on DELL 6400"
date: 2006-10-06
forum: Absolute Beginner Talk
---

### Post by madhurjain on 2006-10-06
Hi people,

i read the thread i had to before posting and most of the others but still could not find the solution to my problem, maybe coz i'm absolutely new to ubuntu, i could not figure it out.

Its like, i installed ubuntu onmy dell 6400 laptop but i cant get it to detect my wireless card, which is dell 1390, i downloaded the files u suggested there to download but i could not get the rpm's to install as it says "make" command is not supported, also "install" command is no use, even using the GUI to do it was no good,
so i would be grateful if anyone could give me a stepwise method to get my wireless network up and running on ubuntu.

Madhur

---

### Post by Kateikyoushi on 2006-10-06
I think you downloaded a wrong file.
RPM is Red hat Package Manager, similar to deb you can not compile it.
You need a tar.gz version untar it and follow the instructions.

I found a some info on installing it under ubuntu.

[How to install BCM1390]("http://www.ubuntuforums.org/showthread.php?t=193350")

[URL="http://http://unia.ual.es/socios/pexi//?q=node/8"]Ubuntu Dapper Beta on Dell Inspiron 6400 or E1505
[/URL]

---

### Post by madhurjain on 2006-10-06
Ok but can u also tell me what to do once i get the tar file,

i mean how do i install it from there, as i got one and it said use the command "make", but that does not work for me :confused:

---

### Post by Kateikyoushi on 2006-10-06
Follow this guide. [LINK]("http://www.ubuntuforums.org/showthread.php?t=193350")
It is a step by step installation of your wireless card.

---

### Post by madhurjain on 2006-10-06
Thanks man,
i hope it works,
as i am really interested in dumping windows for good,
am sick n tired of it

---

### Post by madhurjain on 2006-10-06
Well when i try installing wine.deb,
it says dependencies not satisfied,
what do i do???

Also when i try the drapper, it says cant find build-essential package???

---

### Post by DSn0wMan on 2006-10-06
Try installing build-essentials with synaptic package manager, or apt-get

```
sudo apt-get install build-essential
```

---

