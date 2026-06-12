---
title: "A newbie's silly question."
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by Tha_Pig on 2007-12-13
I feel silly already, but I got stuck in the installation. 

I'm installing Xubuntu on a Ramline tablet. I know other people have done it and it works, so I'm very enthusiastic about this OS.

My installation worked fine until I was told to remove the CD and restart the computer. It booted and I got prompter for login and password...

And I don't know what I'm supposed to do now. During the installation I was asked to enter a password that I would use later. but what I'm supposed to enter in the login line?

I'm sorry for bothering you all and thanks ins advance for any help.

---

### Post by coolbrook on 2007-12-13
Try root

---

### Post by Rocket2DMn on 2007-12-13
If you haven't been prompted to create a username before, this is probably where you do it.  Insert the username you would like to use as your system login.

Errr, "root" would probably be a bad idea.

---

### Post by spiderbatdad on 2007-12-13
enter the username you were asked to create at the time of installation, then your password

---

### Post by Dr Small on 2007-12-13
You are supposed to enter the username and password that you choose when installing.
If you forget this, you can always boot into recovery mode (from the GRUB boot loader) and then run:
```
ls /home
```
To figure out what your username is, if that is all you do not know.
If you also do not know what your password is, this can also be reset from recovery mode.

Dr Small

---

### Post by Tha_Pig on 2007-12-13
OK! That was easy... 

Now I logged in, but all I get is a command prompt. How do I make the graphic interface work?

---

### Post by Dr Small on 2007-12-13
Was it graphical back where you entered your username & password ?
Well, anyhow, try:
```
startx
```

Of course, you should not be booting from recovery mode when doing this.

Dr Small

---

### Post by Tha_Pig on 2007-12-13
> **Dr Small said:**
> Was it graphical back where you entered your username & password ?
Well, anyhow, try:
```
startx
```

Of course, you should not be booting from recovery mode when doing this.

Dr Small

When I started it I got the Ubuntu logo and the progress bar for a while, but then it went back to text mode.

I tried startx and got a "command not found" message.

Maybe I messed the installation and it's missing files or something?

---

### Post by Tha_Pig on 2007-12-14
Thanks everybody for the help. I got it working!

Looks like I messed up the install the first time, but the second it worked.

---

