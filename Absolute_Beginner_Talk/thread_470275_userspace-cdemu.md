---
title: "userspace-cdemu"
date: 2007-06-10
forum: Absolute Beginner Talk
---

### Post by danny_kay1710 on 2007-06-10
This is my first post here. A little background i am not a complete novice altho still dont know a lot about it especially when it comes to compiling programs

I am trying to get the userspace-cdemu installed as cdemu0.8 corrupts all my images.

So i have managed to get three of the 5 packages these are

cdemu-daemon
libmirage
cdemu-module

i installed them using the commands:
```

./configure
sudo make
sudo make install

```
but i can not get gcdemu or cdemu-client to install - they both error on the exact same thing

```

Making all in pixmaps
make[1]: Entering directory `/home/daniel/Desktop/cdemu/gcdemu-1.0.0/pixmaps'
make[1]: Nothing to be done for `all'.
make[1]: Leaving directory `/home/daniel/Desktop/cdemu/gcdemu-1.0.0/pixmaps'
Making all in po
make[1]: Entering directory `/home/daniel/Desktop/cdemu/gcdemu-1.0.0/po'
file=`echo sl | sed 's,.*/,,'`.gmo \
          && rm -f $file &&  -o $file sl.po
/bin/sh: -o: not found
make[1]: *** [sl.gmo] Error 127
make[1]: Leaving directory `/home/daniel/Desktop/cdemu/gcdemu-1.0.0/po'
make: *** [all-recursive] Error 1
```

thats all the output made by the sudo make command

i dont know what else to do and can not get it installed - you can get userspace-cdemu from [http://kabelkaos.net/cdemu/](http://kabelkaos.net/cdemu/) i used the experimental version but if u can get any others of the userspace-cdemu working and installed i would be most grateful

I dont think it will have any relevance but i am using the latest version of wubi (7.04-test3) cos i couldn't get it booting with a stripe for windows - wasnt to bothered about putting ubuntu on the stripe but as soon as i renabled the raid for windows grub wont work anymore :(

hope someone can help
danny_kay1710

---

### Post by danny_kay1710 on 2007-06-13
sorry for double posting and probably bumping the thread but has anyone got this to work its really bugging me now lol

The only thing left i need is a daemon tools clone for linux and i can switch and get rid of windows for good lol and i really can't wait until i can do that 

thanks
danny_kay1710

---

### Post by Trail on 2007-11-09
Run:
sudo apt-get install gettext
And then reconfigure.

And by the way, you can use 'make' instead of 'sudo make'

---

### Post by denar on 2007-11-10
After I suffered from the same problem,after one day from the search i find the Solution.
to install:
1-
zgrep CONFIG_BLK_DEV_SR /proc/config.gz
CONFIG_BLK_DEV_SR=y

2-
mkdir ~/cdemu_src && cd ~/cdemu_src
tar -xf userspace-cdemu-2007-08-23.tar && for x in *.tar.gz; do tar -xf $x; done

3-
cd libmirage-1.0.0/
./configure --prefix="$HOME/apps/cdemu"
make install

cd ../vhba-module/
make
sudo make install # zavrsice u /lib/modules/`uname -r`/extra/vhba.ko

cd ../cdemu-daemon-1.0.0/
PKG_CONFIG_PATH="$HOME/apps/cdemu/lib/pkgconfig/" ./configure --prefix="$HOME/apps/cdemu" --with-distro=none
make install
sudo cp ~/apps/cdemu/etc/dbus-1/system.d/cdemud-dbus.conf /etc/dbus-1/system.d/
sudo cp ~/apps/cdemu/etc/udev/rules.d/cdemud-udev.rules /etc/udev/rules.d/cdemud-udev.rules

cd ../cdemu-client-1.0.0/
./configure --prefix="$HOME/apps/cdemu"
make install

4-Test run
cd ~/apps/cdemu/bin
sudo modprobe vhba
sudo ./cdemud -d
export PYTHONPATH="$HOME/apps/cdemu/lib/python2.4/site-packages/:${PYTHONPATH}"
./cdemu status
+/+ and now you will see same this:
Devices status:
DEV LOADED TYPE FILENAME
0 0 N/A N/A
+/+ to load example this file 111111111111111.iso
./cdemu load 0 111111111111111.iso
./cdemu status
Devices status:
DEV LOADED TYPE FILENAME
0 1 IMAGE-ISO 111111111111111.iso

finally  after every restart to load "mount" any file you must repeat the step 4

---

