---
title: "dual boot ubuntu and kubuntu"
date: 2007-04-16
forum: Absolute Beginner Talk
---

### Post by mojo123 on 2007-04-16
how do i do this?

---

### Post by NeoLithium on 2007-04-16
You don't need to dual boot; you can just install the missing desktop environment. If you have Ubuntu, install the kubuntu-desktop packages, or vice versa.  You can then click on sessions at your login, and select either KDE or GNOME :)
```

sudo aptitude install kubuntu-desktop 
or
sudo aptitude install ubuntu-desktop

```

I'd recommend you leave your login manager as is, should you decide to remove the added environment later on; but that's just my way I do things :)

---

### Post by soapytheclown on 2007-04-16
> **mojo123 said:**
> how do i do this?

originally i did this installed on 2 separate partitions and it appears in your grub menu however theres a much simpler way if all you're trying to do is try  them both out, in terminal

sudo apt-get install kubuntu-desktop

at one point it will ask if you want to use gdm or kdm, choose which ever you like its the login screen manager (i always choose gdm). Then when thats done, Alt+ctrl+backspace. to take you to the login screen. press "sessions" and choose either kde or gnome then login as normal :D

hope that helped you

---

### Post by soapytheclown on 2007-04-16
> **NeoLithium said:**
> You don't need to dual boot; you can just install the missing desktop environment. If you have Ubuntu, install the kubuntu-desktop packages, or vice versa.  You can then click on sessions at your login, and select either KDE or GNOME :)
```

sudo aptitude install kubuntu-desktop 
or
sudo aptitude install ubuntu-desktop

```

I'd recommend you leave your login manager as is, should you decide to remove the added environment later on; but that's just my way I do things :)

doh you beat me to it lol

---

### Post by mojo123 on 2007-04-16
th guys this is awsome

---

