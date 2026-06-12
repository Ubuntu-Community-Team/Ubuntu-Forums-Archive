---
title: "Only boots in Terminal Mode"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by johnfarrow on 2007-10-29
I was checking some tips on how to improve Fiesty and I think I installed Xfce.  Anyway now when I start Ubuntu it gives me a lot of error messasges. I can get to the terminal , but when I type exit or Press Alt-F1 or Alt f2 it just stays at the login screen and will not go back to the desktop.  I also tried to install ATI viedo drivers.  Can anyone tell me how to get my desktop back?

Do I need to  uninstall Xfce and if so what is the code to enter in terminal mode?

Big Dummy

---

### Post by taurus on 2007-10-29
Were you using Gnome before you installed XFce?  If you need to reconfigure X again, just run

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by mali2297 on 2007-10-29
Write down and post some of the error messages, they will make it easier for us to help.

You might have removed some packages when you installed Xfce, try
```

sudo apt-get install ubuntu-desktop

```
to get them back.

Also, try starting X from the terminal with the command
```

startx

```

---

### Post by johnfarrow on 2007-10-29
Taurus,
   That did it.  Many thanks for you help.
How do you get SOLVED put on the original post?

---

