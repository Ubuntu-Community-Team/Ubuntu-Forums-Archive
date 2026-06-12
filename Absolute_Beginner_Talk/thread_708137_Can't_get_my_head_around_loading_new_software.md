---
title: "Can't get my head around loading new software"
date: 2008-02-26
forum: Absolute Beginner Talk
---

### Post by Tony_photoplus on 2008-02-26
No matter how I try to sort out how to load up software that is not on Synaptic I just can't seem to find the right terminal or what ever is needed.  The software I have found that I need is
[http://www.nongnu.org/mailnotify/]("http://www.nongnu.org/mailnotify/")

I have read the 'How to install anything' web site and quite frankly it is easy when there appears to be a 'Debain' or is on the list  of downloads.  Any pointers here please, in simple language.


Tony

---

### Post by jan quark on 2008-02-26
extract the package to the desktop 

just drag and drop the folder form where it is now to the desktop

right click and select extract here

now open the terminal

applications > accessories > terminal

and navigate to the folder on the desktop
```

cd /home/user/Desktop/mail-notification-5.0
```

change user to your username

now run in this order

```
./configure
```

```
make 
```

```
sudo make install
```

---

### Post by ramjet_1953 on 2008-02-26
Before attempting the above, make sure that you have installed[COLOR="Blue"] build-essential[/COLOR]

In a terminal type this in:

[COLOR="Red"]sudo apt-get install build-essential[/COLOR]

Or, if you prefer, use the Synaptic Package Manger to install it.

Regards,
Roger :)

---

### Post by Tony_photoplus on 2008-02-26
Many thanks for your kind help.  Have it downloaded and working.

Tony

---

