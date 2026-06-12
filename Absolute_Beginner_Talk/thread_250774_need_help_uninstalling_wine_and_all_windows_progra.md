---
title: "need help uninstalling wine and all windows programs"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by baylorbear on 2006-09-04
How do I uninstall WINE and all of the crappy software I installed in the fake windows environment?  Ugh... never should have installed that to begin with!

---

### Post by bodhi.zazen on 2006-09-04
Just delete your ~/.wine folder (fake_c_drive) and remove wine via synaptic or apt-get.

---

### Post by JNowka on 2006-09-04
To uninstall it goto System->Administration->Synaptics.  Once there search for Wine.  This sould bring up libwine, libwine-dev, wine, and wine-dev.  click each of these and select "Mark for Removal".  After this click the apply button at the top.  This will Uninstall Wine.  Next you will need to use the File Browser to goto your home folder.  Once there goto View->Show Hidden Files and now you should see many folders.  Scroll down to .wine and delete the folder.

Everthing is uninstalled.

But to be honest wine is great for getting things in Internet Explorer and Microsoft Office to work thought there are some other programs to install first.  I would suggest downloading winetools and installing it.  A link can be found at [www.winehq.com](www.winehq.com) in the downloads section.  If you want to be a gamer I would suggest Paying for Cedega, It plays about 220 differant Windows games right now. You have to pay for it though.  As for Wine and Games I would have to admit it isn't as good on games based on the DirectX engine, but works remarkable better on games that work on OpenGl.  There are some games that windows has that runs on this.

Hopes this helps. :)

---

### Post by baylorbear on 2006-09-04
> **JNowka said:**
> To uninstall it goto System->Administration->Synaptics.  Once there search for Wine.  This sould bring up libwine, libwine-dev, wine, and wine-dev.  click each of these and select "Mark for Removal".  After this click the apply button at the top.  This will Uninstall Wine.  Next you will need to use the File Browser to goto your home folder.  Once there goto View->Show Hidden Files and now you should see many folders.  Scroll down to .wine and delete the folder.

Everthing is uninstalled.

But to be honest wine is great for getting things in Internet Explorer and Microsoft Office to work thought there are some other programs to install first.  I would suggest downloading winetools and installing it.  A link can be found at [www.winehq.com](www.winehq.com) in the downloads section.  If you want to be a gamer I would suggest Paying for Cedega, It plays about 220 differant Windows games right now. You have to pay for it though.  As for Wine and Games I would have to admit it isn't as good on games based on the DirectX engine, but works remarkable better on games that work on OpenGl.  There are some games that windows has that runs on this.

Hopes this helps. :)

Thanks for the help!  Truth be told, however, is that I've had nothing but problems with WINE since installing it a few days ago.  I used WineTools right from the start and followed the instructions on how to use it.  Once I finished the steps, however, IE wouldn't run anymore... and half of the programs I installed wouldn't work -- even tho they're on the "tested / working" list.

---

