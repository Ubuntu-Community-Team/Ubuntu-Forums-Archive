---
title: "Starting to get frustrated"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by J11Gyro on 2007-04-04
Ok all installed Kmoney after a reboot and machine locked up, restarted and got a sign on to desktop black screen. how do I restart graphic interface? I sign in and put password in but it does nothing. is there anyway to restore thru this login?

---

### Post by laidback on 2007-04-04
If you're at a prompt try startx to get the gui going again.

$startx (return)

---

### Post by mendingo84 on 2007-04-04
have u tried the ctrl+alt+f1 thing? and after that ```
sudo /etc/init.d/kdm start
``` (for KDE) or ```
sudo /etc/init.d/gdm start
``` for Gnome?

---

### Post by J11Gyro on 2007-04-04
Ok tried all three and am getting an error about a module not loading  libpcidata.so unknown module ?

---

### Post by zvacet on 2007-04-04
[http://www.psychocats.net/ubuntu/nox]("http://www.psychocats.net/ubuntu/nox")

---

### Post by J11Gyro on 2007-04-04
:lolflag: thanks but with both systems down at once I could not have read it

---

### Post by J11Gyro on 2007-04-04
This just does not make sense, I took notes every load up and had a very good record from the last successful load. I followed those notes to the tee and kept having lock ups after install or it would go to the black terminal screen. The only thing I can think of would be the updates. They went from 112 to 128 in the last few loads and I was getting an error every time. Any ideas?

---

