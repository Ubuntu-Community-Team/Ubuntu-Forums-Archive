---
title: "Volume prob. PCM keeps resetting to low level."
date: 2007-09-05
forum: Absolute Beginner Talk
---

### Post by philinux on 2007-09-05
When I listen to different stuff the pcm slider keeps going low it wont stay where I set it.

Anyone else had this? :confused:

{edit] I think it happens when I reboot.

---

### Post by philinux on 2007-09-05
k bump

---

### Post by mridkash on 2007-09-06
This happened with me when I tried to fix the no sound issue in fiesty for my laptop.
followed some commands given by somebody and after every reboot the volume controls were muted.

try this, download latest alsa drivers from [http://www.alsa-project.org/main/index.php/Main_Page]("http://www.alsa-project.org/main/index.php/Main_Page")

extract the folder in home folder.
in terminal:
```
cd alsa-driver-1.0.14
```

then type
```
./configure
```

if you see no errors then proceed.
```
make
```

then finally
```
sudo make install
``` This is the general way to complie software from source code!


after process completes, reboot. And see if the problem exists.

---

