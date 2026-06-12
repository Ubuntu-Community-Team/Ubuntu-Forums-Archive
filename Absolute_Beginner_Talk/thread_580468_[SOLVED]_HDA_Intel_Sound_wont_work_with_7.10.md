---
title: "[SOLVED] HDA Intel Sound wont work with 7.10"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Amarasu on 2007-10-18
I have a HDA Intel soundcard on my laptop and just clean installed 7.10 (I have 7.04 on another partition)

Ordinarily I just have to fix the sound with the instructions in this guide: 

[http://ubuntuforums.org/showthread.php?t=539595&highlight=headphones]("http://ubuntuforums.org/showthread.php?t=539595&highlight=headphones")

With gutsy gibbon, this doesn't work and there is an error message when I try to do sudo make with the alsa driver

Does anyone know what is happening?

I'm willing to provide information on demand

---

### Post by Amarasu on 2007-10-18
Anyone have any idea?

---

### Post by Technoviking on 2007-10-18
Check out this wiki page.
[https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768?highlight=%28lenovo%29](https://wiki.ubuntu.com/LaptopTestingTeam/Lenovo3000N100_0768?highlight=%28lenovo%29)

---

### Post by Amarasu on 2007-10-19
According to the guide, this is what I should do:

```

sudo apt-get install libc6-dev 
sudo apt-get install libc6-dev 

mkdir alsa-fix && cd alsa-fix 

wget ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.15.tar.bz2
wget ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.15.tar.bz2
wget https://bugtrack.alsa-project.org/alsa-bug/file_download.php?file_id=2233&type=bug

tar -xvf alsa-driver-1.0.15.tar.bz2
tar -xvf alsa-lib-1.0.15.tar.bz2
tar -xvf alsa-utils-1.0.15.tar.bz2

cd alsa-driver-1.0.15
patch -p1 < ../hdaintel-laptop-eapd-hg20070908.patch
./configure --with-cards=hda-intel --with-sequencer=yes --with-oss=yes
make
sudo make install
cd ..

cd alsa-lib-1.0.15
./configure
make
sudo make install
cd ..

cd alsa-utils-1.0.15
./configure
make
sudo make install
cd ..
```

But I'm stuck when I make install command the patched alsa driver. This is what happens:

```
if [ -L /usr/include/sound ]; then \
                rm -f /usr/include/sound; \
                ln -sf /home/henry/alsa-fix/alsa-driver-1.0.15/include/sound /usr/include/sound; \
        else \
                rm -rf /usr/include/sound; \
                install -d -m 755 -g root -o root /usr/include/sound; \
                for f in include/sound/*.h; do \
                        install -m 644 -g root -o root $f /usr/include/sound; \
                done \
        fi
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'snd*.*o.gz' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o' | xargs rm -f
find /lib/modules/2.6.22-14-generic/kernel/sound -name 'ac97_bus.*o.gz' | xargs rm -f
make[1]: Entering directory `/home/henry/alsa-fix/alsa-driver-1.0.15/acore'
mkdir -p /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp snd-hwdep.ko snd-page-alloc.ko snd-pcm.ko snd-rtctimer.ko snd-timer.ko snd.ko /lib/modules/2.6.22-14-generic/kernel/sound/acore
cp: cannot stat `snd-hwdep.ko': No such file or directory
cp: cannot stat `snd-page-alloc.ko': No such file or directory
cp: cannot stat `snd-pcm.ko': No such file or directory
cp: cannot stat `snd-rtctimer.ko': No such file or directory
cp: cannot stat `snd-timer.ko': No such file or directory
cp: cannot stat `snd.ko': No such file or directory
make[1]: *** [modules_install] Error 1
make[1]: Leaving directory `/home/henry/alsa-fix/alsa-driver-1.0.15/acore'
make: *** [install-modules] Error 1
henry@henry-laptop:~/alsa-fix/alsa-driver-1.0.15$ 


```

I don't know what this means so any help would be greatly appreciated.

---

### Post by Amarasu on 2007-10-19
Anyone have an idea of whats wrong?

---

### Post by Amarasu on 2007-10-20
bump

---

### Post by muzakman on 2008-03-06
bump

---

### Post by igknighted on 2008-03-06
Updated drivers were backported... install the "linux-backports-modules-generic" package and try that.  You may need to tweak a setting in the "/etc/modprobe.d/alsa-base" file to add something specific your model needs, this varies though so we would need to know exactly what soundcard/laptop you have.

---

### Post by Amarasu on 2008-03-08
It was solved on my Toshiba A135-S4527 by adding:
options snd-hda-intel model=auto

To alsa-base

---

