---
title: "Installing non-package programs. (other noobie questions)"
date: 2007-02-14
forum: Absolute Beginner Talk
---

### Post by Axis on 2007-02-14
I was wondering how you install programs that are non included in the package manager? Is there a general rule of thumb or is it different for every program you are trying to install (please note I am referring to linux programs)

Also I need a program to stream mp3 audio aswell as other audio. If I can avoid armarok that would be best. (I would prefer a graphical interphase)

Thanks,
Axis

---

### Post by bodhi.zazen on 2007-02-15
For streaming you can check out streamtuner ( + xmms) or songbird.

songbird : [http://doc.gwos.org/index.php/SongBird](http://doc.gwos.org/index.php/SongBird)

for installation, first check the repositories, you may need to enable some repositories :

[http://ubuntuguide.org/wiki/Dapper#Repositories](http://ubuntuguide.org/wiki/Dapper#Repositories)

Then use synaptic, update, and search for your package ...

Outside of that see this link : [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by ramjet_1953 on 2007-02-15
Yes, you can install packages that are not in the Synaptic lists.
However, have a good look in Synaptic before going down this road, as it can save you a lot of time.

If you do need to install some software that you can't get through Synaptic, there are a few options:

Firstly, if it's already a package, but not a .deb package, you can convert it using a program called alien.

If however, you can only get source code, you will need to learn how to "roll your own", using the command line.

./compile
make
sudo make install

Going down this road can be both rewarding and frustrating. You need to fully understand that you must do all of the legwork with satisfying dependancies, which can in some cases involve downloading heaps of extra files and loading them.

If you want to learn how to do this, you can tailor software to your particular setup, which will mean that it will run very efficiently. However, be prepared for hair-pulling frustrations, as part of the learning process.

Enjoy!

Regards,
Roger :cool:

---

