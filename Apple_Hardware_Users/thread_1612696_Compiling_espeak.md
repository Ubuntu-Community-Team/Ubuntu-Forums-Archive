---
title: "Compiling espeak"
date: 2010-11-03
forum: Apple Hardware Users
---

### Post by UndiFineD on 2010-11-03
I need someone with a powerpc to compile a big-endian G3 compatible espeak application for Ubuntu 10.04.1
This is for a blind person which depends on it.

espeak can be found  here:
[http://sourceforge.net/projects/espeak/files/espeak/espeak-1.44/espeak-1.44.05-source.zip/download](http://sourceforge.net/projects/espeak/files/espeak/espeak-1.44/espeak-1.44.05-source.zip/download)

---

### Post by paultag on 2010-11-03
I know we talked over IRC, but for the Google-bots and future hackers:

Try getting in touch with the PowerPC folks, it's not official anymore, but they still work on it, IIRC.

[https://launchpad.net/~ubuntu-powerpc](https://launchpad.net/~ubuntu-powerpc)

Much Love.

---

### Post by UndiFineD on 2010-11-03
found them, thank you JanC

[http://ports.ubuntu.com/pool/main/e/espeak/](http://ports.ubuntu.com/pool/main/e/espeak/)

---

### Post by UndiFineD on 2010-11-03
How to make it easy for a blind person ?

well what about this:
```

cat > get-espeak.sh <<"EOF"
wget http://ports.ubuntu.com/pool/main/e/espeak/espeak-data_1.44.05~really-1.44.04-0ubuntu1_powerpc.deb
wget http://ports.ubuntu.com/pool/main/e/espeak/libespeak1_1.44.05~really-1.44.04-0ubuntu1_powerpc.deb
wget http://ports.ubuntu.com/pool/main/e/espeak/espeak_1.44.05~really-1.44.04-0ubuntu1_powerpc.deb
pause 'the following three commands use sudo and require the admin passwword, press any key to continue'
sudo dpkg --install espeak-data_1.44.05~really-1.44.04-0ubuntu1_powerpc.deb
sudo dpkg --install libespeak1_1.44.05~really-1.44.04-0ubuntu1_powerpc.deb
sudo dpkg --install espeak_1.44.05~really-1.44.04-0ubuntu1_powerpc.deb
EOF

bash get-espeak.sh

```

I will not let him type that, instead I refer to this:
[http://dl.dropbox.com/u/7607669/get-espeak.sh](http://dl.dropbox.com/u/7607669/get-espeak.sh)

---

### Post by WitchCraft on 2011-04-21
Try this:

```

apt-get build-dep espeak
apt-get source espeak

```

[change to directory of espeak]

```

./configure
make 
make install

```

Then you still need espeak big-endian data.
Little endian won't do the trick.

---

### Post by Alvasin on 2011-04-22
To compile the eSpeak Emacspeak server (tclespeak.cpp) under Debian Sid, I had
to make the changes below. These are not intended for inclusion; they are just
quick fixes designed to make it compile. The location of the tcl.h header
should also be set by the Emacspeak configure process, if possible, as it is
different under Debian (i.e., /usr/include/tcl8.3/tcl.8 for tcl 8.3, and
mutatis mutandis for tcl 8.4).The compiler gives numerous warnings about type conversions throughout
tclespeak.cpp; I have fixed only those which give fatal errors, and by the
brute force method, not the proper method of understanding the code and
correcting it.

---

