---
title: "Can I recover passwords with LiveCd"
date: 2006-12-03
forum: Absolute Beginner Talk
---

### Post by Leed on 2006-12-03
Hi 

After several install attempts I've finally set up Ubuntu on one of my younger brothers pc's. Strange enough the login won't work, I guess I must have slipped my finger on the keyboard during the double password entry on install. Also I cannot check the password in tty1 because his ATI card craps up in text mode, it only does graphical mode... hopefully some better drivers will solve that, but for now I have no console. 

I can however still boot up with the LiveCd and mount the FileSystem... question now is, can I recover the password this way? If not I'll have to reinstall Ubuntu. 

Best regards
Dave

---

### Post by d3v1ant_0n3 on 2006-12-03
If it's a very fresh install, you might be as well reinstalling as waiting for an answer- an edgy install takes me about 30 mins. How on earth did you mistype the password twice??:p

---

### Post by taurus on 2006-12-03
Reinstalling is always the last solution!  

Boot into recovery mode from GRUB menu and at the prompt, type

```
passwd leed
(assuming leed is your username...)
shutdown -r now
```

---

### Post by lamego on 2006-12-03
Yes, you can use the LiveCD to reset user's password.
Boot from the live cd, mount your installed partition and chroot to it.
You can then use passwd or any other root related command that you may need...

---

### Post by ibanez on 2006-12-03
Did you use any special characters in the set up of password  Ive installed before with them i.e @password@  can become "password" I use a gb keyboard setup btw . 
Just a thought as its happened to me before Just I'm aware of it now.
It does indeed seem strange you can mistype the same password twice.

---

