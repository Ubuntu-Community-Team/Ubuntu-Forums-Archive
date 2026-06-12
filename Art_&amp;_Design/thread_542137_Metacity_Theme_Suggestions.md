---
title: "Metacity Theme Suggestions?"
date: 2007-09-03
forum: Art &amp; Design
---

### Post by DM was on fire! on 2007-09-03
I'm wanting a theme with rounded window borders like here:

[[IMG]http://img208.imageshack.us/img208/9822/windowborderlw6.th.png[/IMG]](http://img208.imageshack.us/my.php?image=windowborderlw6.png)

The theme I'm using now is nice, but I'm wanting some more.
And just so I'm clear on something...I don't have the Murrine engine installed because I don't know how, so I can't use the configurator to configure a Murrine theme the way I want it to be.

EDIT - I totally realised this is in the wrong section. I'm sorry. D:

---

### Post by FuturePilot on 2007-09-04
If you're using Feisty you can install the Murrine engine by doing
```
sudo apt-get install gtk2-engines-murrine
```
If you're not using Feisty I can post instructions on how to build it from source.

---

### Post by DM was on fire! on 2007-09-04
I'm using Dapper.
I **wish** I was using Feisty, though.

---

### Post by FuturePilot on 2007-09-04
Ok, here's how to build the Murrine engine from source.
First let's get all the dependencies
```
sudo apt-get install build-essential libgtk2.0-dev
```
Now download the tarball to your Desktop
[http://cimi.netsons.org/media/download_gallery/murrine/murrine-0.53.1.tar.bz2]("http://cimi.netsons.org/media/download_gallery/murrine/murrine-0.53.1.tar.bz2")
Extract it, then in a terminal
```
cd Desktop/murrine-0.53.1/
```
```
./configure --prefix=/usr --enable-animation
make
sudo make install
```

Now for the Murrine Configurator. Download the archive to your Desktop
[http://murrine.netsons.org/files/nmc.tar_3.bz2]("http://murrine.netsons.org/files/nmc.tar_3.bz2")
Then extract it. And then extract the archive that you just extracted. It's an archive inside an archive:p
Now
```
cd Desktop/newmurrineconfigurator/
sudo ./install.sh
```
It will be available under System>Preferences>New Murrine Configurator
And you're done!:D

---

### Post by DM was on fire! on 2007-09-14
Woot! :D It worked! Thanks a bunch! <3

---

### Post by FuturePilot on 2007-09-14
No problem:) I had to do that myself when I was still using Dapper.

---

