---
title: "problem with bluetooth"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by snake444 on 2007-11-20
i bought bluetooth dongle today here is a picture of it
[http://img253.imageshack.us/img253/9835/bluetoothqb0.jpg](http://img253.imageshack.us/img253/9835/bluetoothqb0.jpg)
and when i try to connect to my mobile nokia6288 i get this error
[img]http://img151.imageshack.us/img151/9149/errorgp5.png[/img]
how to fix this?
if it cannot be fixen ill switch the bluetooth to the second computer wich is windows
but i prefer the ubuntu computer so help me fix it:)

---

### Post by por100pre1 on 2007-11-21
If using Gnome try gnome-obex-server:

```
sudo apt-get install gnome-bluetooth
```

```
gnome-obex-send -d 00:1B:AF:0E:89:F6 */path/to/any/file*
```

Try send a file to your PC too, sometimes that does the trick.

---

