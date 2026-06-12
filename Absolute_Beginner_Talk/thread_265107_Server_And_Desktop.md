---
title: "Server And Desktop"
date: 2006-09-25
forum: Absolute Beginner Talk
---

### Post by W2UOS on 2006-09-25
hi, i have a question, what is the difference between the server and the desktop download? i have the server version and dont know the difference =?

and another question: do you need to dual boot to run UBUNTU? cause when i booted my empty hard drive i didnt get a desktop, i logged in and then it gave me a screen with all these command lines and other stuff....can anyone help?

---

### Post by bodhi.zazen on 2006-09-25
LOL :lol:

The server is a minimal install with no GUI.

If you want:```
sudo aptitude install ubuntu-desktop
```
Will give you a GUI.

The rest is beyond this post.

---

### Post by lamego on 2006-09-25
> and another question: do you need to dual boot to run UBUNTU? cause when i booted my empty hard drive i didnt get a desktop, i logged in and then it gave me a screen with all these command lines and other stuff....can anyone help?
If you have installed the desktop version you may need to reconfigure the graphical manager, login and type:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by W2UOS on 2006-09-25
so do i type that in as a command?

---

### Post by bodhi.zazen on 2006-09-25
Please advise```
sudo dpkg-reconfigure **-phigh** xserver-xorg
```
It is much easier.

---

### Post by bodhi.zazen on 2006-09-25
> **W2UOS said:**
> so do i type that in as a command?

If you installed the server, as you stated in your first post, type in ```
sudo aptitude install ubuntu-desktop
```
As a command.

It will as you for a password, input you user (log in) password. You will not see anything on the screen when you type your password.

---

