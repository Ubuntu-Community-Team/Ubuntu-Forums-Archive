---
title: "Install Ubuntu Studio"
date: 2007-05-10
forum: Absolute Beginner Talk
---

### Post by LE CHARBON on 2007-05-10
Couple questions. Can someone breakdown how to install it?  Also, is it a complete program inside feisty or a seperate OS?

---

### Post by 65536 on 2007-05-11
It is a complete OS so you can install it like you did feisty. But you can also just install its packages from your current install.

---

### Post by mrmonday on 2007-05-11
You can install it from Applications> Add/Remove Applications in GNOME, not sure about KDE.

---

### Post by stylofone on 2007-05-11
At [http://ubuntustudio.org/downloads](http://ubuntustudio.org/downloads) they suggest you do this:
sudo su -c 'echo deb [http://archive.ubuntustudio.org/ubuntustudio](http://archive.ubuntustudio.org/ubuntustudio) feisty main >> /etc/apt/sources.list'
wget -q [http://archive.ubuntustudio.org/ubuntustudio.gpg](http://archive.ubuntustudio.org/ubuntustudio.gpg) -O- | sudo apt-key add - && sudo apt-get update

Can anyone tell me what that will do to my existing Ubuntu Feisty installation? Will it mess with anything else I've got set up already? Or is it safer to do a clean install of Studio on a separate partition?

---

### Post by ticopelp on 2007-05-11
It shouldn't mess with your existing installation, but it will add a TON of programs to your menu. It will also change your splash screen and such if you install the desktop package (which, of course, you needn't do, I suppose).

---

### Post by rajputrajat on 2007-05-11
if anyone has intalled it...
plz tell me, can it be use like normal ubuntu.?
i mean its features and other softwares...
or it's suitable only for audio video professionals.....

---

### Post by qiemem on 2007-08-06
It will be exactly the same except for the extra themes and a whole bunch of sweet multimedia programs. Oh, and a kernel designed for low latency.

---

### Post by por100pre1 on 2007-08-06
> **LE CHARBON said:**
> Couple questions. Can someone breakdown how to install it?  Also, is it a complete program inside feisty or a seperate OS?

Both. There is a Ubuntu Studio audio applications launcher:

```
sudo apt-get install ubuntustudiolauncher
```

and there is the [COLOR="RoyalBlue"]Ubuntu Studio[/COLOR] OS that you can install over Ubuntu **Feisty**:
```

sudo su -c 'echo deb http://archive.ubuntustudio.org/ubuntustudio feisty main >> /etc/apt/sources.list'

```
```

wget -q http://archive.ubuntustudio.org/ubuntustudio.gpg -O- | sudo apt-key add - && sudo apt-get update

```
```
sudo aptitude install ubuntustudio-desktop ubuntustudio-audio ubuntustudio-audio-plugins ubuntustudio-graphics ubuntustudio-video
```

---

