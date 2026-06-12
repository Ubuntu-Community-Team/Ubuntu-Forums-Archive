---
title: "Installing a Game.. Directory?"
date: 2007-06-11
forum: Absolute Beginner Talk
---

### Post by LollYouSuckZor on 2007-06-11
Im following, [http://www.mrbass.org/enemyterritory/](http://www.mrbass.org/enemyterritory/) 's instructions, and it wont work..

Im selecting the linux package and all.  What am I doing wrong? Is there something they did not mention?

---

### Post by taurus on 2007-06-11
It would be nice if you include the command and an error message when you run that command.

---

### Post by LollYouSuckZor on 2007-06-11
[code]
nic@nic-desktop:~$ mv et-linux-2.60.x86.run.zip et-linux-2.60.x86.run
mv: cannot stat `et-linux-2.60.x86.run.zip': No such file or directory



---


nic@nic-desktop:~$ mv et-linux-2.60.x86.run.zip et-linux-2.60.x86.run
mv: cannot stat `et-linux-2.60.x86.run.zip': No such file or directory


----

---

### Post by taurus on 2007-06-11
You probably saved it to ~/Desktop.

```
cd ~/Desktop
mv et-linux-2.60.x86.run.zip et-linux-2.60.x86.run 
chmod +x et-linux-2.60.x86.run 
sh ./et-linux-2.60.x86.run
```

---

### Post by LollYouSuckZor on 2007-06-11
Okay, so now it asks the installation path.

its..
/usr/local/games/enemy-territory/

I agree...
it now says

"No write permission to /usr/local/games/"

---

### Post by LollYouSuckZor on 2007-06-11
.. Bump?

---

### Post by H.E. Pennypacker on 2007-06-11
> **LollYouSuckZor said:**
> Okay, so now it asks the installation path.

its..
/usr/local/games/enemy-territory/

I agree...
it now says

"No write permission to /usr/local/games/"

You have no control, by default, of anything outside of your home directory.  Therefore, you will need administrative privileges.  Use the sudo command to receive these privileges, and provide your password when asked.

Try again.  

Have you tried downloading from Synaptic or getdeb.net?  It's easier to use a .deb file than installing something through the terminal.

---

### Post by taurus on 2007-06-11
```
sudo ./et-linux-2.60.x86.run
```

---

