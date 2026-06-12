---
title: "need help"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by barpat96 on 2007-03-10
I am totally new to the Linux based systems. after downloading 3 different versions of ubunu and trying to install it on an older Dell Desktop PC, i finally got the 6.06 alternate to install. Now i am confused. When the system is bting up, it asks for usernam and password then it goes to:
bb@ubuntu:~$
I am not sure what to do from here, I have searched for hours for an answer with no luck.
can anyone please tell me what I need to do from here?
Thanks

---

### Post by v8YKxgHe on 2007-03-10
It appears X/Gnome isn't loading (basically you're **G**raphical **U**ser **I**nterface). What graphics card do you have?

---

### Post by barpat96 on 2007-03-10
this is what it is showing in the computer manual:

A 66-MHz accelerated graphics port (AGP) video card with its own graphics
bus enhancing 3D performance, or a high-speed, high-resolution
33-MHz PCI video card. The selected video card is installed in an expansion-
card slot, rather than an integrated video controller, to provide video
flexibility for customers.

---

### Post by taurus on 2007-03-10
What is the error message when you run this command at a prompt, after you log in?

```
startx
```

---

### Post by barpat96 on 2007-03-10
I will have to get back to you on that one. I am not at home right now but will try that when i get there... Thanks
:)

---

### Post by barpat96 on 2007-03-10
after I log in and put the command startx it says
-bash: startx: command not found

---

### Post by barpat96 on 2007-03-10
> **AlexC_ said:**
> It appears X/Gnome isn't loading (basically you're **G**raphical **U**ser **I**nterface). What graphics card do you have?

How can i get the GUI to load?

---

### Post by barpat96 on 2007-03-10
i just wanted to add that this computer was running Win XP wioth no problems. I did a complete reformat when i installed ubuntu. would installing XP back on it help?

---

### Post by taurus on 2007-03-10
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
sudo /etc/init.d/gdm start
```

---

### Post by barpat96 on 2007-03-11
Thanks That FIxed it :)

---

