---
title: "[SOLVED] Copy files from USB to Desktop"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by Orcaporka on 2008-04-08
Is there a set of command I can use that will transfer all my mp3s from my usb stick to my desktop?

Thanks

---

### Post by KIAaze on 2008-04-08
The copy command?
```
cp <path_to_usbstick>/*.mp3 ~/Desktop
```

If you have your mp3s scattered in different folders:
```
find <path_to_usbstick> -name *.mp3 | xargs -n1 -i {} ~/Desktop
```
(haven't tested this command, but it should be something like this. See [http://www.linux.com/articles/113662](http://www.linux.com/articles/113662) for more info on xargs)
Note also that this command won't keep the folder structure you had on your USB stick. It will just search for all mp3s and copy them to your Desktop.

A script copying all mp3s while keeping the folder structure is probably also doable somehow by writing a script, but I don't think you need something that advanced.

---

### Post by Orcaporka on 2008-04-08
> **KIAaze said:**
> The copy command?
```
cp <path_to_usbstick>/*.mp3 ~/Desktop
```

If you have your mp3s scattered in different folders:
```
find <path_to_usbstick> -name *.mp3 | xargs -n1 -i {} ~/Desktop
```
(haven't tested this command, but it should be something like this. See [http://www.linux.com/articles/113662](http://www.linux.com/articles/113662) for more info on xargs)
Note also that this command won't keep the folder structure you had on your USB stick. It will just search for all mp3s and copy them to your Desktop.

A script copying all mp3s while keeping the folder structure is probably also doable somehow by writing a script, but I don't think you need something that advanced.

Thanks, but Im really new where would I find what my "path to usb stick"? is?

---

### Post by l0stendeavor on 2008-04-08
the path to the usbstick would be something like /media/whatever_name_usbstick

---

### Post by KIAaze on 2008-04-08
Yes, for me it's /media/disk for example.
You can also see the path when you open it with nautilus (the equivalent of Windows explorer).

Tip: By pressing ctrl+L in nautilus, you can switch to a different location bar which allows you to copy the path to the current directory. ;)

If you want to use the command-line it is essential to know some basic commands like "cd" for navigating.
Go here to learn the basics: [http://www.tuxfiles.org/linuxhelp/cli.html](http://www.tuxfiles.org/linuxhelp/cli.html)

---

### Post by Orcaporka on 2008-04-08
Thanks alot all done.

---

