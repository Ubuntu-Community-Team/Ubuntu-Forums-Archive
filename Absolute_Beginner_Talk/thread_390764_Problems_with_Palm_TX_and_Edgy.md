---
title: "Problems with Palm TX and Edgy"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by mrandersonmd on 2007-03-22
I'm having troubles configuring my Palm TX for synching with Edgy...

I tryed configuring gnome-pilot but my TX is not detected... when I try to Get the ID from my Palm TX and press the hotsync button on the USB cable, nothing happens, and the ID is not retrieved...

I've tryed with /dev/pilot with /dev/ttyUSB0 and /dev/ttyUSB1 but none of these works... even I tryed with various connection speeds... my TX is not detected...

I went to /dev but there's no /pilot subdor or ttyUSB0 or ttyUSB1 subdir... do I have to create them manually??

Hoping someone will help me

Yours MrAnderson from Chile

---

### Post by Ryba on 2007-03-22
I'd also love to know how to fix this problem. It has not worked for me in Edgy or Feisty (and neither has cd burning for that matter) but it worked (as did cd burning) in the Dapper Drake LTS version.

I read the palm problem has something to do with the way that the /dev/ttyUSB0 is not created *until* you push the sync button then it appears through the udev stuff. But the gnome-pilot program seems to try and bind itself to that location before it is created and thus never sees anything coming in on that device and so everything just explodes to high heaven as a result :-(

It seems like it is actually a bug with gnome-pilot (as in it should be listening for a dbus message instead of instantly binding itself???) but then again it seems like a case of chicken and the egg too.

---

