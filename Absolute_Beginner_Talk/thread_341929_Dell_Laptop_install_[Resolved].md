---
title: "Dell Laptop install [Resolved]"
date: 2007-01-19
forum: Absolute Beginner Talk
---

### Post by kensmith on 2007-01-19
I wanted to put Ubuntu 6.06 on a dell inspiron 8000 laptop. It a 698 Mhz processor with 128 meg of memory and 20 g Hard drive. However the live CD has been running for about 55 minutes and its loading very slow. Does this mean it will not work on this computer as being too old. I have also tried the safe mode and still doing the same thing. I do not want dual boot only linux for this machine.

---

### Post by je1117 on 2007-01-19
it's taken 55 minutes to just boot up the livecd? Or the install is taking 55 minutes?

---

### Post by kensmith on 2007-01-19
Just booting up the live CD.

---

### Post by davebgimp on 2007-01-19
You might have a bad CD burn. You try redownloading and burning a new copy and checking the MD5 to make sure it's cool.

You could also try using the alternate install ISO.

---

### Post by kensmith on 2007-01-19
I know the CD is good as this is what I used to install the one I have. I will locate the alternate One. Never had this trouble before.

---

### Post by kensmith on 2007-01-19
I installed the alternate CD and it loaded but took 3 hours. I am now up to trying to edit the Xorg.conf file and am getting Error: No permission to write to the file. I have tried everything I know and have looked up on the forums.

---

### Post by davebgimp on 2007-01-19
> **kensmith said:**
> I installed the alternate CD and it loaded but took 3 hours. I am now up to trying to edit the Xorg.conf file and am getting Error: No permission to write to the file. I have tried everything I know and have looked up on the forums.

You need to use the sudo command.

For example:
sudo gedit /etc/X11/xorg.conf

---

### Post by aysiu on 2007-01-19
128 MB of RAM isn't enough for the Desktop CD.

Use the Alternate CD instead.

---

### Post by kensmith on 2007-01-19
Ok tried that but it does not open to edit it.
I used the GUI editor and edited it but then it would not save it. Just getting confused. Ben on this thing for 12 hours.

---

### Post by aysiu on 2007-01-19
If you're using Ubuntu, press Alt-F2 and type ```
gksudo nautilus
``` Then you can navigate to /etc/X11 and edit the xorg.conf file. Make sure you make a backup copy first, though!

If you're using Kubuntu, you want Alt-F2 and ```
kdesu konqueror
```

If you're stuck at the command-line, log in, and type ```
sudo nano -B /etc/X11/xorg.conf
```

---

### Post by kensmith on 2007-01-19
Thanks. That worked.

---

