---
title: "Installation of Ubunto with winxp and the problem of gurb boot loader"
date: 2006-05-05
forum: Absolute Beginner Talk
---

### Post by true_friend on 2006-05-05
Hi Folks.
i m new in linux. i have installed the ubunto but the problem i faced was the boot loader does not woeked.i wroked for once only and next time when i statred my pc i was giving error 17.I had to reformate my C: to enable the windows xp boot.now i have ubunto installed but running xp,linux one is not in the boot list.
An other the main error is this i can not see the display correctly.my graphic card is supported with linux 5.10.  I had confirmed it from the site but my monitor is very old an analog monitor it does not supporting the resolution.the same was the problem with live cd i changed the resolution to lovest level but could not got it.tell me what i do to correct the resolution and the boot loader problem also.
Shall i to uninstall the ubunto or any other solution is there.
thnx .

---

### Post by Sef on 2006-05-05
1) Did you install Ubuntu or XP first?

2) Start a new thread for your monitor problem.  That way you are more likely to get a fix for it.

---

### Post by true_friend on 2006-05-06
i had installed xp first.then in after distributing D in two parts by ubnuto partitionar i installed it.But the loader is creating problem.i still have ubunto in system.it can be recovered in boot list i know by the installation cd but the problem may arise again i want its permanent solution.

---

### Post by Jose Catre-Vandis on 2006-05-06
Are you installing grub to the mbr during installation (this is the default) ? If you don't do this you don't get grub on boot up and won't get into ubuntu. This thread should help you get grub up and running:

[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+howto](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=grub+howto)

There are two methods, using either the install or live cd, for recovering grub. You may need to re-install grub

Also root access on the live cd is accessed by typing "sudo su"

---

### Post by true_friend on 2006-05-07
yes it was, i installed it during installation.
now tell me if i got same problem what would be the remedy.what does mean by  error 17.i shall wait for ur instructions to remove gurb after recreating the same problem to got to my default windows boot.

---

