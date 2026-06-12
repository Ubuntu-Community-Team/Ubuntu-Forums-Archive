---
title: "Newbtastic"
date: 2007-05-08
forum: Absolute Beginner Talk
---

### Post by Lurthor on 2007-05-08
Ok well i am beginner as beginner can be.  i just install ubuntu.  and it load but loads to a command prompt how do i load a desktop. is there one on the cd already that i just need to learn how to load. and is there a good place for super new users can get the basic gist of this?   Thanks in advance to anyone who reply s =)

---

### Post by taurus on 2007-05-08
Did you use the server version or the desktop version?  What happens if you type in this command from a prompt?

```
startx
```

---

### Post by Lurthor on 2007-05-08
Server edition..   after typing that is says "The program startx is currently not installed

---

### Post by lukew on 2007-05-08
> **Lurthor said:**
> Server edition..   after typing that is says "The program startx is currently not installed


You need to install a desktop environment. 

Try either 

sudo apt-get install kde
sudo apt-get install kde-core
sudo apt-get install gnome
sudo apt-get install gnome-core

---

### Post by taurus on 2007-05-08
With server version, you only get a console.  If you want a window manager, you need to install it.

```
sudo aptitude update
sudo aptitde install ubuntu-desktop gdm
sudo /etc/init.d/gdm start
```

---

### Post by Lurthor on 2007-05-08
THanks guys.. maybe i should  not kid myself and just start with a desktop version till i get the hang of it.  what do you all think. would that be my best bet?

---

### Post by LaRoza on 2007-05-08
You should start with a desktop version, you can dual boot them so you can switch back when you learn more.

You can use a variety of desktop environments. Ubuntu defaults to Gnome, but you can add others.

---

### Post by Lurthor on 2007-05-08
Got desktop installing now =)  thanks again

---

