---
title: "python install 2.3"
date: 2006-01-27
forum: Absolute Beginner Talk
---

### Post by xstation on 2006-01-27
I just installed a a frash 5.10

now I need to uninstall pyhon 2.4 which is the default
now last time I did this I lost my ubuntu desktop.

I want to install python 2.3. as THE programs I am to install
later are written in python.

please tell me how to proceed please.

xstation:)

---

### Post by ubuntumaneh on 2006-01-27
I think that 2.4 can handle any work that 2.3 does.
I don't advice you to drop 2.4 off, for many things in ubuntu depends on it. However, 2.3 and 2.4 can coexist.

sudo apt-get install python2.3

---

### Post by Jucato on 2006-01-27
Isn't Python 2.4 backward compatible? I mean won't programs using python 2.3 run in 2.4 as well?

---

### Post by xstation on 2006-01-27
some of the programmes I will install will accept 2.4 others will not.

what about installing 2.3 then uninstalling 2.4?

xstation:) :)

---

### Post by ubuntumaneh on 2006-01-27
It is not a good idea to unistall 2.4
You can install 2.3 and use this program with it. I have both in my box.
Perhaps you have to make a symbolic link to 2.3 at some point, but it is hardly necessarily.

---

### Post by Jucato on 2006-01-27
yes, I think ubuntumaneh's suggestion is better. It's quite dangerous to modify some of the default libraries/installations, such as Python, because the system is configured to work with the default Python version (2.4). Uninstalling it might break dependencies and wreak havoc on your system.

---

