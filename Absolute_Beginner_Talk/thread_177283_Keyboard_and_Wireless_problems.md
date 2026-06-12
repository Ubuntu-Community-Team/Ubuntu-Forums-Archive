---
title: "Keyboard and Wireless problems"
date: 2006-05-16
forum: Absolute Beginner Talk
---

### Post by ahlandberg on 2006-05-16
After installing and activating my wlan PCI card my keyboard has gone spastic:

When typing, it does this to me:

cd ...............................

i.e. a key simply 'gets stuck'!?

Also, when re-booting my computer, the wlan0 disappears. A thread suggested to have the appropriate code to start it in the /etc/module file. However, when I tried to edit it, it said cannot write to file. I couldn't even get around it with :w!

Please help, everything is going pear shaped!

Cheers, Anders

---

### Post by Moebius on 2006-05-16
To edit a file in /etc/module section you will need to use the sudo command.

Something like this:
```
sudo gedit /etc/module/file
```

Explaning it would be.
sudo - Super User Do, gives you some high privileges to edit the file
gedit - the editor of "choice" of Gnome
/etc/module/file - the path to the file, this one is an example.

---

