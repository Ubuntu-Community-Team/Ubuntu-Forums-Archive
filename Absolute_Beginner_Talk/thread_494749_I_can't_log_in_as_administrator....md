---
title: "I can't log in as administrator..."
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by Game_boy on 2007-07-07
I open the terminal, type su, press enter, and then try and type my password in.

However, after I press enter on su, the terminal freezes up and doesn't display characters when I type!

The, after entering my password (which I know is correct) and nothing changing on the screen, I press enter and it says "authentication failed".

There's no way I can have root access now!

---

### Post by lisati on 2007-07-07
It is normal for nothing to show on your screen when typing in your password. I put in "su" and got "authentication failed" too. There are alternatives to the "su" command..... Ubuntu uses the "sudo" command, which roughly translates to "Super User Do".

---

### Post by RomeReactor on 2007-07-07
Hi. I don't think it's a good idea to log in as root in a terminal; it's easier to break your system. I suggest you use **sudo** to issue commands that require administrator privileges. However, if you're determined to use root in the terminal, press ALT+F2 and enter:
```
gksu /usr/bin/x-terminal-emulator
```
Just remember to close it after you're done.

---

### Post by Malibu Illusion on 2007-07-07
I suggest trying this to invoke a root prompt:

```
sudo -s
```

and

```
exit
```

When done to be returned to a normal prompt.

Take care.

---

