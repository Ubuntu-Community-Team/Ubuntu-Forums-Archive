---
title: "logitech mx5000 no num lock"
date: 2007-10-25
forum: Absolute Beginner Talk
---

### Post by bigmonmulgrew on 2007-10-25
I have a logitech mx 5000 keyboard. it does not have a num lock key, the number pad functions as arrows etc. it there a way to force num lock on without the key.

---

### Post by mikeyphi on 2007-10-25
> **bigmonmulgrew said:**
> I have a logitech mx 5000 keyboard. it does not have a num lock key, the number pad functions as arrows etc. it there a way to force num lock on without the key.

Have a look at your BIOS - I seem to recall there was an option for num lock at boot.

---

### Post by joop905 on 2007-10-25
> **bigmonmulgrew said:**
> I have a logitech mx 5000 keyboard. it does not have a num lock key, the number pad functions as arrows etc. it there a way to force num lock on without the key.

sudo apt-get install numlockx
sudo gedit /etc/gdm/Init/Default

Edit this file by adding the following lines at the end before the line “exit 0”:

if [ -x /usr/bin/numlockx ]; then
/usr/bin/numlockx on
fi

Save the file, reboot, and numlock should be on.

---

