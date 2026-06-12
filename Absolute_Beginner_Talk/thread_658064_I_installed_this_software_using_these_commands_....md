---
title: "I installed this software using these commands ...how can i uninstall it?"
date: 2008-01-04
forum: Absolute Beginner Talk
---

### Post by hopelessone on 2008-01-04
Hi,

i did:
**wxWidgets-2.8.7**
./configure --enable-mem_tracing --enable-debug --disable-optimise --enable-debug_flag --enable-debug_info --enable-debug_gdb --with-opengl --enable-gtk2 --enable-unicode --enable-largefile --prefix=/home/firebox/usr/local/wxWidgets-2.8.7/ && make && make install

**aMule**
./configure --enable-ccache --with-denoise-level=3 --enable-debug --disable-optimize --enable-verbose --enable-geoip --enable-cas --enable-wxcas --enable-amule-gui --enable-webserver --enable-amulecmd --enable-amule-daemon --with-wx-config=/home/firebox/usr/local/wxWidgets-2.8.7/bin/wx-config --prefix=/home/firebox/usr/local/amule && LD_LIBRARY_PATH=/home/firebox/usr/local/wxWidgets-2.8.7/lib/ make && LD_LIBRARY_PATH=/home/firebox/usr/local/wxWidgets-2.8.7/lib/ make install

to uninstall this do i just delete the folders that's it? What do i do?

thanks

---

### Post by skymera on 2008-01-04
go into the directories you compiled them in.
where you entered ./configure, make, make install

then once your there type

```
 sudo make uninstall 
```

---

### Post by spiderbatdad on 2008-01-04
```
sudo apt-get remove --purge amule
```
```
sudo dpkg -r wxWidget2.87
```or whatever it was

---

### Post by NilsE on 2008-01-04
They may show up in Synaptic or add&remove so check there and do a complete removal.  

If not you can just delete the folders that the install created and also look in /usr/bin/ to see if an executable was created there.

---

### Post by mike^_^ on 2008-01-04
*solution stated earlier*

---

### Post by hopelessone on 2008-01-04
ok...

thanks a bunch you guys...

will remember this next time...

cheers..

---

