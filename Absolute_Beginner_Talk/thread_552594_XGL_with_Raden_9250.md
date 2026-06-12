---
title: "XGL with Raden 9250?"
date: 2007-09-16
forum: Absolute Beginner Talk
---

### Post by sccrstvn93 on 2007-09-16
Is there a way to make XGL work with my graphics card. Should i use AXGL instead? What drivers  do i need?

---

### Post by master_kernel on 2007-09-16
> **sccrstvn93 said:**
> Is there a way to make XGL work with my graphics card. Should i use AXGL instead? What drivers  do i need?

Just follow this guide up to the installation of Compiz Fusion
[http://ubuntuforums.org/showthread.php?t=488385](http://ubuntuforums.org/showthread.php?t=488385)

---

### Post by master_kernel on 2007-09-16
> **sccrstvn93 said:**
> Is there a way to make XGL work with my graphics card. Should i use AXGL instead? What drivers  do i need?

Also, there is a script to automatically install the LATEST driver from ATi's site [here.]("http://ubuntuforums.org/showthread.php?p=3376011")

---

### Post by sccrstvn93 on 2007-09-16
when i follow the guide i cannot get to the desktop with the session with xgl and gnome. When i try and login the screen reamins that yellowish orange color and then after 10 seconds it goes back to the login screen. After that i just login using just Gnome. Should i have tried again?

---

### Post by sccrstvn93 on 2007-09-16
Here is what i get when i try to run envy: Envy Erro: Ati's Legacy Driver does not support your operative system"

---

### Post by w4ett on 2007-09-16
The 9250 IS NOT supported by the proprietary driver fglrx...see:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

The native xorg-driver-ati  (included in Feisty) supports your card.

---

