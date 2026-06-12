---
title: "rolling back drivers?"
date: 2007-08-02
forum: Absolute Beginner Talk
---

### Post by superbungalow on 2007-08-02
how do I roll back the drivers for my graphics card?

---

### Post by asmoore82 on 2007-08-02
what type of card is it and post the output of running this in a terminal ...

```
~$ grep Driver /etc/X11/xorg.conf
```

---

### Post by superbungalow on 2007-08-02
```
        Driver          "kbd"
        Driver          "mouse"
        Driver          "synaptics"
        Driver          "wacom"
        Driver          "wacom"
        Driver          "wacom"
        Driver  "fglrx"
```

It's ATI (I installed them using envy, and It's mucked up my sound)

---

### Post by superbungalow on 2007-08-02
?

---

### Post by asmoore82 on 2007-08-02
edit the file with root priviledge and change "fglrx" to "ati"

```
~ $ gksudo gedit /etc/X11/xorg.conf
```
and change the line
```
        Driver      "fglrx"
```
to this
```
        Driver      "ati"
```

save the changes and restart the PC to make sure the ATI kernel modules get unloaded.

---

### Post by superbungalow on 2007-08-02
umm, how do I do that with root privileges?

---

### Post by asmoore82 on 2007-08-02
the 'gksudo' part of the command takes care of that.

even better idea ... back up the file before you edit it like this...

```
~ $ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
~ $ gksudo gedit /etc/X11/xorg.conf
```

---

### Post by superbungalow on 2007-08-02
Oh, don't worry about that, I've got a backed up version from ages ago.

---

### Post by Inxsible on 2007-08-02
> **superbungalow said:**
> Oh, don't worry about that, I've got a backed up version from ages ago.

That necessarily wont be updated to reflect all the changes you would have made.

And if it does, why not simply replace your xorg.conf and you would be good to go.

---

