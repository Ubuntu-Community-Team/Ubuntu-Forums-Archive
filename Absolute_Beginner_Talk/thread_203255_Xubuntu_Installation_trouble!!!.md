---
title: "Xubuntu Installation trouble!!!"
date: 2006-06-24
forum: Absolute Beginner Talk
---

### Post by Xanthus on 2006-06-24
When installing the burned iso of Xubuntu 6.06 the process stops at the "Adding live CD user" stage.  Shortly afterwards the screen goes black and the disk drive stops running.  I could use some help ](*,) .  If you think you know what's wrong I would greatly appreciate any replys or E-mails to [email]xanthus.alias@gmail.com[/email].  Thanks.

---

### Post by cleverselfreferentialname on 2006-06-24
Maybe you have a bad disk. We can do an md5sum to check. Otherwise, can you tell us your hardware, specifically the monitor and graphics card?

---

### Post by Xanthus on 2006-06-25
I thought the disk may be bad so I downloaded the alternative but I have no idea of which option to choose, server or OEM... I have no idea what these mean.

---

### Post by taurus on 2006-06-25
OEM will do a normal install but you need to run an extra command at the end to create a user.  The screen will tell you what to run and when to run it.

The server will only install a minimal OS and if you want to use Gnome, KDE, or even XFce4, you have to install it later as
```

sudo apt-get install ubuntu-desktop <- for Gnome
sudo apt-get install kubuntu-desktop <- for KDE
sudo apt-get install xubuntu-desktop <- for XFce4

```

---

