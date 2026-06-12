---
title: "force mount hard drive"
date: 2008-02-11
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-02-11
running the live cd, ubuntu won't mount my hard drive. i get an error basically telling me that windows is still using it, and that i can either go to windows and disconnect the device (via the 'safely remove hardware' icon on the system tray) or i can force mount it.

i can't continue with a full wipe-out installation because the installer is stuck on the part with formatting the drive, because it's not mounted.

does anyone know a command i can use to force mount my hard drive, or an alternate solution?

---

### Post by Sinkingships7 on 2008-02-11
bump. anyone?

---

### Post by Rocket2DMn on 2008-02-11
You gotta give longer than 8 minutes to get a response man, it's rude to bump that early :(
In any case, you can force it to mount with
```
sudo mkdir /media/windows
sudo mount /dev/(yourdevice) /media/windows -o force
```
Then unmount and let the installer deal with it
```
sudo umount /media/windows
```

---

### Post by oedha on 2008-02-11
if windows still using it....you have to make sure that you have shutdown windows properly before get to ubuntu

---

