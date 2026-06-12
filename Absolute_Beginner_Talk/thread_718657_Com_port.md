---
title: "Com port?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by Ken101 on 2008-03-08
I'm trying to get mgetty voice running.
How can I check which com port my modem is installed on and test if it's communicating with my PC? (query modem)

---

### Post by Diabolis on 2008-03-11
You can communicate through serial ports with minicom. You can get it from the repositories.
```
sudo apt-get install minicom
```

Then run:
```
dmesg | grep tty
```
That will tell you which are your serial ports.

```
minicom -s
```
Will open minicom in configuration mode.

There you'll have options for modems and dialing or serial port communication. I have used only serial communication with routers.

If what you need is to check serial communication, what you got from "dmesg" is what you need to put into "Serial Device".

You can read a lot more about how to use it here: [http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html](http://www.cyberciti.biz/tips/connect-soekris-single-board-computer-using-minicom.html)

---

### Post by Ken101 on 2008-04-05
I found the answer on another forum:

Simply run   sudo wvdialconf

---

