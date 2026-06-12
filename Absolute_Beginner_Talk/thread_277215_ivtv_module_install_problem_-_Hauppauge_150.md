---
title: "ivtv module install problem - Hauppauge 150"
date: 2006-10-14
forum: Absolute Beginner Talk
---

### Post by Episteme on 2006-10-14
I've been working on installing the ivtv modules for my Hauppauge 150 following this guide:

[http://ubuntuforums.org/showthread.php?t=186747](http://ubuntuforums.org/showthread.php?t=186747)

I've merged althepcman's alterations with the original, and edited in my specifics so that the instructions look like this.

```


I will not be putting the "sudo" in front of all of my commands in this HOWTO, since I find that to be overly laborious. For normal use, I am fine with sudo here and sudo there; but, when doing a large number of commands as we will be doing here, it gets a little tiring. 
First, type the following, and remember the output. 
uname -r
For my system, the output is 
2.6.15-27-amd64-generic
It is important to remember both parts. The 2.6.15 is the kernel version, and the -27-amd64-generic part is the extra tag. This will be important later. Now, to install the proper kernel source, execute the following command: 
apt-get install linux-source-2.6.15 linux-headers-`uname -r`
where 2.6.15 is replaced with your current kernel version that you found out from the uname -r command above. And notice the backticks in the above command!  The tick used here is the one next to your 1 key, not the quote next to your Enter key.
Now that we have the source, we need to unpack it and configure its pseudo-location: 
tar xvjf /usr/src/linux-source-*.tar.bz2 -C /usr/src/
ln -s /usr/src/linux-source-2.6.15 /usr/src/linux
ln -s /usr/src/linux /lib/modules/`uname -r`/build
Now switch to the /usr/src/linux directory: 
cd /usr/src/linux
We need to make sure to remember our extra "tag" in the kernel source Makefile. Edit /usr/src/linux/Makefile with your favorite editor, and set the variable EXTRAVERSION (about the fourth line of the Makefile) to your "tag" that we found out from the uname -r command above. My tag was -10-686, for example. Therefore, the line in the Makefile should read something similar to: 
EXTRAVERSION = -27-amd64-generic
Now lets configure the source tree to get it ready for compiling, without actually compiling it: 
cp /boot/config-`uname -r` /usr/src/linux/.config
make oldconfig
make prepare0
make scripts
Lastly, do the following:
cd /lib/modules/`uname -r`/
ls -l build
If this symbolic link points to /usr/src/linux, we don't have to do anything.  However, if it does not, manually delete it and make the link yourself:
rm build
ln -s /usr/src/linux build
Yay! We finally have our build environment ready. Now on to the compilation and installation of the ivtv drivers. 
Let's go the the ivtvdriver.orgsite and download the latest stable 0.4.x version of the ivtv drivers, and extract them (as of now, this is version 0.4.7). 
cd /usr/src
wget http://dl.ivtvdriver.org/ivtv/archive/0.4.x/ivtv-0.4.7.tar.gz
tar xvfz ivtv-0.4.7.tar.gz
Before you compile your ivtv source, edit the file ivtv-firmware.c in /usr/src/ivtv-0.4.7/driver/. Change memcpy to memcpy_toio on lines 112 and 115 (it's in the load_fw_direct function).

Now, compile your ivtv drivers and utilities: 

make
make install
During your make install, it could be that the installer reports that there are conflicts for the files that it is trying to install. IMPORTANT: do not ignore these conflicts! After each conflict, it will tell you exactly the command to issue to "hide" the offending file. Execute each command it tells you, and rerun "make install" until there are no more conflicts. 
In some rare cases (I don't believe that this will happen to you, but I am leaving this bit here just in case) the drivers end up installed in the wrong place; they land in /lib/modules/2.6.15/ivtv rather than /lib/modules/`uname -r`/ivtv. So, check on this. If they are installed incorrectly, you can fix this just by copying 
cp -r /lib/modules/2.6.15/ivtv /lib/modules/`uname -r`/
The Hauppauge cards require firmware files, as the firmware is not stored in the ROMs on the card.  We must download and install these properly now.  To do this, 
wget ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip
wget ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip
unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /lib/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /lib/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /lib/firmware/
mv /lib/modules/ivtv-fw-enc.bin /lib/firmware/
cp ../v4l-cx2341x-init.mpg /lib/firmware/
ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw

After this set of commands, if you execute
ls -ltra /lib/firmware/
You should see
drwxr-xr-x 3 root root 4096 2005-12-18 10:04 ..
-rw-r--r-- 1 root root 262144 2005-12-23 20:05 ivtv-fw-enc.bin
-rw-r--r-- 1 root root 262144 2005-12-23 20:05 ivtv-fw-dec.bin
-r--r--r-- 1 root root 14264 2005-12-23 20:08 v4l-cx25840.fw
-r--r--r-- 1 root root 376836 2005-12-23 20:08 v4l-cx2341x-enc.fw
-rw-r--r-- 1 root root 155648 2005-12-24 13:33 v4l-cx2341x-init.mpg
lrwxrwxrwx 1 root root 41 2006-01-03 00:40 v4l-cx2341x-dec.fw -> /usr/lib/hotplug/firmware/ivtv-fw-dec.bin
drwxr-xr-x 2 root root 4096 2006-01-03 00:40 .
Now lets tell Ubuntu that we have ivtv modules. Edit /etc/modules, and just stick "ivtv" at the end of the file. Also edit /etc/modprobe.d/aliases, and put the following line in where it fits: 
alias char-major-81-0 ivtv
Then, do the following: 
depmod
modprobe ivtv
dmesg
If, at the end of the output of dmesg, you see a section starting with ==START INIT IVTV== and ending with ==END INIT IVTV==, you are in good shape, as long as the text in between these markers is not filled with errors. Mine wasn't, so it was time to write this up and take a break. 
5.3 Verification of IVTV drivers
This section is not meant to be exhaustive, but to cover a couple of steps that you can do to make sure that your ivtv drivers are working properly.  First, capture a raw MPG stream to a file:
cat /dev/video0 > /tmp/test.mpg
 (hit Ctrl+C to stop the capturing)
and play the file using mplayer:
mplayer -vo xv /tmp/test.mpg
If you get a picture, that's great; time to move on to the MythTV install.  If not, it could be that the tuner is just not tuned to a viewable channel.  Shut down mplayer, and while that is running, let's use the command line utility ivtv-tune to change channels: 
mplayer -vo xv /dev/video0
ivtv-tune -c # -d /dev/video0 (in a separate terminal/konsole)
Where "#" is replaced by the channel that you want to tune to.  If you have a PVR-500, you might want to try the same steps above, but with /dev/video0 replaced with /dev/video1.  If you are able to watch TV in this way, great! Ivtv is working just fine.


```

When I got to  “Before you compile your ivtv source, edit the file ivtv-firmware.c in /usr/src/ivtv-0.4.7/driver/. Change memcpy to memcpy_toio on lines 112 and 115 (it's in the load_fw_direct function).” I noticed that memcpy doesn't seem to be a part of ivtv-firmware.c for version 4.7, so I ignored this step.

When I got to:

“Now, compile your ivtv drivers and utilities: 
make
make install”
I got this:
```

sean@Pantheon:/usr/src/ivtv-0.4.7/driver$ sudo make install
make -C /lib/modules/2.6.15-27-amd64-generic/build M=/usr/src/ivtv-0.4.7/driver modules
make[1]: Entering directory `/usr/src/linux-source-2.6.15'

  WARNING: Symbol version dump /usr/src/linux-source-2.6.15/Module.symvers
           is missing; modules will have no dependencies and modversions.

  Building modules, stage 2.
  MODPOST
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
make INSTALL_MOD_PATH= INSTALL_MOD_DIR=ivtv \
                -C /lib/modules/2.6.15-27-amd64-generic/build M=/usr/src/ivtv-0. 4.7/driver modules_install
make[1]: Entering directory `/usr/src/linux-source-2.6.15'
  INSTALL /usr/src/ivtv-0.4.7/driver/cx25840.ko
  INSTALL /usr/src/ivtv-0.4.7/driver/ivtv-fb.ko
  INSTALL /usr/src/ivtv-0.4.7/driver/ivtv.ko
  INSTALL /usr/src/ivtv-0.4.7/driver/saa7127.ko
  INSTALL /usr/src/ivtv-0.4.7/driver/tda9887.ko
  INSTALL /usr/src/ivtv-0.4.7/driver/tuner.ko
  INSTALL /usr/src/ivtv-0.4.7/driver/tveeprom.ko
make[1]: Leaving directory `/usr/src/linux-source-2.6.15'
/sbin/depmod -a
Module /lib/modules/2.6.15-27-amd64-generic/kernel/drivers/media/video/cx25840/c x25840.ko conflicts with the ivtv module of the same name -- please hide or dele te it.
To hide:  mv /lib/modules/2.6.15-27-amd64-generic/kernel/drivers/media/video/cx2 5840/cx25840.ko /lib/modules/2.6.15-27-amd64-generic/kernel/drivers/media/video/ cx25840/cx25840.ko.HIDE
You will then need to run depmod.
Module /lib/modules/2.6.15-27-amd64-generic/kernel/drivers/media/video/saa7127.k o conflicts with the ivtv module of the same name -- please hide or delete it.
To hide:  mv /lib/modules/2.6.15-27-amd64-generic/kernel/drivers/media/video/saa 7127.ko /lib/modules/2.6.15-27-amd64-generic/kernel/drivers/media/video/saa7127. ko.HIDE
you will then need to run depmod.
v4l-cx2341x-init.mpg needs copying to the hotplug firmware directory if needed for PVR350 mpeg initialization

```
I removed both those files and make install again – this time with no conflicts. I'm presuming all is well there.
However, it's this part I'm stuck on...
“wget [ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip](ftp://ftp.shspvr.com/download/wintv-pvr_150-500/inf/pvr_2.0.24.23035.zip)
wget [ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip](ftp://ftp.shspvr.com/download/wintv-pvr_250-350/inf/pvr_1.18.21.22254_inf.zip)
unzip pvr_2.0.24.23035.zip 
./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
cp HcwMakoA.ROM /lib/firmware/v4l-cx25840.fw
cp HcwFalcn.rom /lib/firmware/v4l-cx2341x-enc.fw
mv /lib/modules/ivtv-fw-dec.bin /lib/firmware/
mv /lib/modules/ivtv-fw-enc.bin /lib/firmware/
cp ../v4l-cx2341x-init.mpg /lib/firmware/
ln -s lib/firmware/ivtv-fw-dec.bin /lib/firmware/v4l-cx2341x-dec.fw”

For some reason, bash can't find ./ivtvfwextract.pl

```

sean@Pantheon:/usr/src/ivtv-0.4.7/driver$ ./ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
bash: ./ivtvfwextract.pl: No such file or directory
sean@Pantheon:/usr/src/ivtv-0.4.7/driver$

```

What am I doing wrong?](*,)

---

### Post by Episteme on 2006-10-14
ok, I found the pl script, and did this...

sean@Pantheon:/usr/src/ivtv-0.4.7/driver$ sudo /usr/src/ivtv-0.4.7/utils/ivtvfwextract.pl pvr_1.18.21.22254_inf.zip
sean@Pantheon:/usr/src/ivtv-0.4.7/driver$

I'm just getting concerned that I'm not extracting these files into the right directory.

---

### Post by Episteme on 2006-10-14
Grrr...

sean@Pantheon:/usr/src/ivtv-0.4.7/driver$ sudo modprobe ivtv
FATAL: Module ivtv not found.

ok, this is getting beyond me.

---

### Post by Episteme on 2006-10-16
Hi, I'm episteme and I've got a module problem... <sigh> ](*,) 


Right - so the problem was that i needed to:

cp -r /lib/modules/<kver>/ivtv /lib/modules/`uname -r`/

I can cat /dev/video0 > /tmp/test.mpg and it works fine. 

But, now ivtv-tune and ivtvctl return :command not found. 

I've obviously messed up somewhere, and would grately appreciate some help... or maybe an encouraging word to keep my now dismal moral up.

---

### Post by Episteme on 2006-10-16
riiiiiiight....

So, I went back to the ivtv-0,4,whatever folder and make and make install.

---

