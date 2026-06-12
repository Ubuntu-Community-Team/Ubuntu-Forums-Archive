---
title: "Creating a file"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by Ahunt on 2007-04-24
Hi everyone:

How do you use sudo to create a file? I have checked all the documentation and can't find the proper command.

---

### Post by LostShootingStar on 2007-04-24
> **Ahunt said:**
> Hi everyone:

How do you use sudo to create a file? I have checked all the documentation and can't find the proper command.


An empty file?

```

sudo touch filename

```
or

```

sudu echo "" > filename

```

im sure there are a 100 other ways to do it too.

---

### Post by MasonM on 2007-04-24
It would be helpful to know what kind of file you want to create.

---

### Post by Ahunt on 2007-04-24
I am trying to create the file **/etc/udev/rules.d/10-local.rules** to enable a modem as described at:

[https://help.ubuntu.com/community/DialupModemHowto/Lucent](https://help.ubuntu.com/community/DialupModemHowto/Lucent)

Trying to get a dial up modem on your first day on Ubuntu is a fun way to start!

Adam

---

### Post by imspecial on 2007-04-24
I believe this is what you are looking for. It will work as long as the file you are creating will only contain text of some kind.

do a ```
cd /etc/udev/rules.d/
``` and then do ```
sudo gedit 10-local.rules
``` when you save your file after entering what you want it will be created

---

### Post by RedSquirrel on 2007-04-24
Press Alt-F2 or open a terminal.

If you'd like a graphical editor, type:

```
gksudo gedit <filename>
```where <filename> for you is **/etc/udev/rules.d/10-local.rules**


In a terminal, you can also use nano instead of gedit, like this:

```
sudo nano -w <filename>
```

---

### Post by aktiwers on 2007-04-24
or just:
```
gksudo gedit  /etc/udev/rules.d/10-local.rules
```

---

### Post by Ahunt on 2007-04-24
Thank you so much - that has indeed created the file!!

Now to see if it enabled the mome or not and then my next post might be on Ubuntu instead of XP!

Adam

---

