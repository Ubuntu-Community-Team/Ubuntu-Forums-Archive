---
title: "Nvidia legacy driver help!"
date: 2006-10-19
forum: Absolute Beginner Talk
---

### Post by yellow beard on 2006-10-19
Im trying to install the nvidia legacy driver for my vanta lt on dapper. Ive followed this tut [here]("http://doc.gwos.org/index.php/Latest_Nvidia_Dapper#METHOD_1") precisely but when i restart x im left with a black screen and cant switch to a console. To fix it i have to resort to my xorg.conf.backup. Im running this kernel 2.6.15-27-386. I also tried downloading the driver package from the nvidia site but when i run that i get this error:```
no precompiled kernel interface was found to match your kernel
```Some one please help!

---

### Post by bulldog on 2006-10-19
Just search in synaptic nvidia legacy and they will pop-up.

```
sudo aptitude install nvidia-glx-legacy
```should do it.

---

### Post by yellow beard on 2006-10-19
I already have that. Im going to try download the nvidia-legacy-kernel-source and see if that fixes it.

---

### Post by yellow beard on 2006-10-19
Ok i installed that but it didn't help. I'm still getting a black screen when I reboot. Any ideas?

---

