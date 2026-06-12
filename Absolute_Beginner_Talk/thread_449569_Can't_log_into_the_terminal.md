---
title: "Can't log into the terminal"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by bws on 2007-05-20
Everytime I try to open the $ terminal in Xubuntu Feisty Fawn, I get a black screen and some script appears for a couple of seconds, then it takes me back to the main Xubuntu log-in screen.  After I log in **again** it takes me right back to the desktop.  It just will not open a terminal box for me.

Is this by design or is it a bug?        

Thanks.

---

### Post by taurus on 2007-05-20
Do you happen to catch what it says on the terminal before it closes?

---

### Post by bws on 2007-05-20
No, it goes by so fast I can't catch what it says.  

Sometimes there's no script at all, just a black screen then it takes me back to log-in

---

### Post by taurus on 2007-05-20
Did this happen after you installed something or updated something on your machine?

---

### Post by bws on 2007-05-20
> **taurus said:**
> Did this happen after you installed something or updated something on your machine?

No, nothing.  I just installed the .iso image and that's it.

---

### Post by taurus on 2007-05-20
Press <Ctrl><Alt>F2 and login with your username and password.  Then, look in ~/.xsession-errors to see what the problem is.

```
tail -24 ~/.xsession-errors
```

---

### Post by Nikron on 2007-05-20
What happens when you log into a tty?

---

### Post by bws on 2007-05-20
> **taurus said:**
> Press <Ctrl><Alt>F2 and login with your username and password.  Then, look in ~/.xsession-errors to see what the problem is.

```
tail -24 ~/.xsession-errors
```

"No Symbols defined for <I7A> (keycode 230)"
"No Symbols defined for <I7B> (keycode 231)"
"No Symbols defined for <I7C> (keycode 232)"
"No Symbols defined for <I7D> (keycode 233)"

And so on and so on, all down the page in alpha and numerical order all the way to "keycode 255"

---

### Post by bws on 2007-05-21
Bump.  

Sorry I didn't get back with you earlier.  This issue has been happening ever since I installed Xubuntu

---

### Post by Airais on 2007-05-22
I have the same thing happening with the same errors

---

