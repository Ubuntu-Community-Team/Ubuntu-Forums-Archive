---
title: "beyrl problem"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by zetsumei on 2007-04-28
I installed beryl and when I start it, it always goes to the fall-back window manager if it fails, which is metacity.  I installed the nvidia drivers and i did this command

```
sudo aptitude install nvidia-glx
```

and restarted my X server crashed.  I restored the xorg.conf from a backup to get X to work again but how do I fix this as I think this is why my beryl won't run properly.

If it helps, I used this guide [http://doc.gwos.org/index.php/BerylOnEdgy](http://doc.gwos.org/index.php/BerylOnEdgy)  for the nvidia drivers...

Please help me.

---

### Post by taurus on 2007-04-28
You can use envy to install nVidia driver for your graphic card first.  

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by Churnd on 2007-04-28
What graphics card do you have?  If nvidia-glx caused your xserver to crash, then you probably need to install nvidia-glx-legacy.  In that case, getting beryl to work might be more difficult than outlined in that article, but not impossible.

The reason it's not working now is because you restored the xorg.conf to it's original nv driver, which doesn't support 3d acceleration.  Once you get the correct nvidia driver installed, then you can try getting beryl to work.

Google "envy ubuntu".  This software includes a way to install a slightly older nvidia driver, but not the legacy one.  If you're not sure which driver your card supports, look it up on Nvidia's website.

---

### Post by zetsumei on 2007-04-28
I installed the nvidia driver via envy just now and it still crashed my X server.  My graphics card is a geforce 6200gt

---

### Post by Churnd on 2007-04-29
nvidia-glx should have worked for that card.  Post your xorg.conf and whatever's in /var/log/ concerning video, such as envy-installer.log, Xorg.0.log, and if there's an nvidia log, that too.

---

### Post by zetsumei on 2007-04-29
heres the files contents:

xorg.conf
> # /etc/X11/xorg.conf (xorg X Window System server configuration file)
took out beginning part...(the comments)

Section "Files"
	FontPath	"/usr/share/X11/fonts/misc"
	FontPath	"/usr/share/X11/fonts/cyrillic"
	FontPath	"/usr/share/X11/fonts/100dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/75dpi/:unscaled"
	FontPath	"/usr/share/X11/fonts/Type1"
	FontPath	"/usr/share/X11/fonts/100dpi"
	FontPath	"/usr/share/X11/fonts/75dpi"
	FontPath	"/usr/share/fonts/X11/misc"
	# path to defoma fonts
	FontPath	"/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
	Load	"i2c"
	Load	"bitmap"
	Load	"ddc"
	Load	"dri"
	Load	"extmod"
	Load	"freetype"
	Load	"glx"
	Load	"int10"
	Load	"type1"
	Load	"vbe"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
	Option		"XkbOptions"	"lv3:ralt_switch"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"		"/dev/input/mice"
	Option		"Protocol"		"ExplorerPS/2"
	Option		"ZAxisMapping"		"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Driver		"nv"
	BusID		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"LCM-19v7"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"NVIDIA Corporation NV40? [Unknown nVidia Card]"
	Monitor		"LCM-19v7"
	DefaultDepth	24
	SubSection "Display"
		Depth		1
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		4
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		8
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		15
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		16
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
	SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
	InputDevice	"Generic Keyboard"
	InputDevice	"Configured Mouse"
	InputDevice     "stylus" "SendCoreEvents"
	InputDevice     "cursor" "SendCoreEvents"
	InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
	Mode	0666
EndSection


---

### Post by zetsumei on 2007-04-29
Sorry for the double post.  It didnt all fit in my first post.  Is there a site I can go to to paste large files because I still have one log Xorg.0.conf.
envy-installer.log
> python pulse.py nvidia
root@desktop:/usr/share/envy# python pulse.py nvidia
Ubuntu Edgy 32bit
Your graphic card has been detected as a GeForce 6200
Your graphic card is supported by the latest driver
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-2.6.17-11-generic is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-kernel-2.6.17-11-generic
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-new
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package nvidia-glx-legacy is not installed, so not removed
Package nvidia-legacy-kernel-source is not installed, so not removed
Package nvidia-settings is not installed, so not removed
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
rm: cannot remove `/usr/src/nvidia*.deb': No such file or directory
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package fglrx-control is not installed, so not removed
E: Couldn't find package fglrx-kernel-2.6.17-11-generic
rm: cannot remove `/usr/src/fglrx*.deb': No such file or directory
rm: cannot remove `/usr/src/*.deb': No such file or directory
rm: cannot remove `/usr/src/modules/nvidia-kernel': No such file or directory
rm: cannot remove `/usr/src/modules/fglrx-kernel': No such file or directory
An installer has been detected
md5new: d41d8cd98f00b204e9800998ecf8427e
md5sumold: 991e03ceaff94fa8113ac04a541ec576
ENVY ERROR: md5 Error! Trying to fetch the driver from the website
No installer detected
Download of the driver in progress, please wait
--11:50:24--  [http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run)
           => `NVIDIA-Linux-x86-1.0-9755-pkg0.run'
Resolving us.download.nvidia.com... 195.27.11.136, 195.27.11.150
Connecting to us.download.nvidia.com|195.27.11.136|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 7,750,628 (7.4M) [application/octet-stream]
100%[====================================>] 7,750,628    528.80K/s    ETA 00:00

11:50:38 (552.19 KB/s) - `NVIDIA-Linux-x86-1.0-9755-pkg0.run' saved [7750628/7750628]
md5new: 991e03ceaff94fa8113ac04a541ec576
md5sumold: 991e03ceaff94fa8113ac04a541ec576
dpkg-buildpackage: source package is nvidia-graphics-drivers
dpkg-buildpackage: source version is 1:1.0.9756
dpkg-buildpackage: source changed by Alberto Milone (tseliot) <albertomilone@alice.it>
dpkg-buildpackage: host architecture i386
dpkg-buildpackage: source version without epoch 1.0.9756
debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp build-kernel-stamp configure-stamp
dh_clean
rm -fr NVIDIA-Linux-x86-1.0-9755-pkg0  nvidia-kernel-source.tar.gz
 debian/rules build
rm -f debian/nvidia-kernel-source.README.Debian debian/control debian/copyright debian/nvidia-glx.links debian/nvidia-glx-dev.links debian/nvidia-glx.override debian/nvidia-glx.docs debian/nvidia-glx.examples debian/nvidia-glx.postrm debian/nvidia-glx.init debian/nvidia-glx-ia32.override debian/nvidia-glx-ia32.links debian/nvidia-kernel-source.docs debian/nvidia-glx-dev.preinst || true
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-kernel-source.README.Debian.in > debian/nvidia-kernel-source.README.Debian
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/control.in > debian/control
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/copyright.in > debian/copyright
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx.links.in > debian/nvidia-glx.links
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx-dev.links.in > debian/nvidia-glx-dev.links
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx.override.in > debian/nvidia-glx.override
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx.docs.in > debian/nvidia-glx.docs
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx.examples.in > debian/nvidia-glx.examples
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx.postrm.in > debian/nvidia-glx.postrm
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx.init.in > debian/nvidia-glx.init
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx-ia32.override.in > debian/nvidia-glx-ia32.override
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx-ia32.links.in > debian/nvidia-glx-ia32.links
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-kernel-source.docs.in > debian/nvidia-kernel-source.docs
perl -p \
        -e 's{#BASE_VERSION#}{1.0}g;' \
        -e 's{#RELEASE#}{9755}g;' \
        -e 's{#VERSION#}{1.0.9755}g;' \
        -e 's{#NEXTVER#}{1.0.9757}g;' \
        -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
        -e 's{#DIRNAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0}g;' \
        -e 's{#FILENAME#}{NVIDIA-Linux-x86-1.0-9755-pkg0.run}g;' \
        -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
        < debian/nvidia-glx-dev.preinst.in > debian/nvidia-glx-dev.preinst
dh_testdir
./NVIDIA-Linux-x86-1.0-9755-pkg0.run --extract-only
Creating directory NVIDIA-Linux-x86-1.0-9755-pkg0
Verifying archive integrity... OK
Uncompressing NVIDIA Accelerated Graphics Driver for Linux-x86 1.0-9755.........
................................................................................
......................................
if test -d /usr/share/envy/nvidia-graphics-drivers/patches; \
        then \
                pwd; \
                ls -al; \
                cd NVIDIA-Linux-x86-1.0-9755-pkg0/usr/src/nv; \
                for i in /usr/share/envy/nvidia-graphics-drivers/patches/*; \
                        do patch -p3 <$i; \
                done; \
        fi
sed 's/^nvidia-graphics-drivers/nvidia-kernel/g'  debian/changelog > debian.binary/changelog
touch configure-stamp
touch build-stamp
 debian/rules binary
touch build-stamp
dh_testroot
dh_testdir
# build kernel module source tarball
mkdir -p /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian
mkdir -p /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/nv
cp -r /usr/share/envy/nvidia-graphics-drivers/debian.binary/* /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian
for f in `ls /usr/share/envy/nvidia-graphics-drivers/debian.binary` ; do \
                perl -p \
                -e 's{#BASE_VERSION#}{1.0}g;' \
                -e 's{#RELEASE#}{9755}g;' \
                -e 's{#VERSION#}{1.0.9755}g;' \
                -e 's{#UPSTREAMVERSION#}{1.0-9755}g;' \
                -e 's{#URL#}{ftp://download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg0.run}g' \
                < /usr/share/envy/nvidia-graphics-drivers/debian.binary/$f >   /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/$f ; \
                chmod 0644 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/$f ; \
            done
/bin/sh: cannot create /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patches: Is a directory
chmod 755 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/patches          
cp /usr/share/envy/nvidia-graphics-drivers/NVIDIA-Linux-x86-1.0-9755-pkg0/usr/src/nv/* /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/nv || true
chmod 755 /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules/nvidia-kernel/debian/rules
chown -R root:src /usr/share/envy/nvidia-graphics-drivers/debian/temp/modules
tar -zcvf /usr/share/envy/nvidia-graphics-drivers/nvidia-kernel-source.tar.gz -C /usr/share/envy/nvidia-graphics-drivers/debian/temp modules
modules/
modules/nvidia-kernel/
modules/nvidia-kernel/debian/
modules/nvidia-kernel/debian/README.Debian
modules/nvidia-kernel/debian/changelog
modules/nvidia-kernel/debian/control.template
modules/nvidia-kernel/debian/copyright
modules/nvidia-kernel/debian/devfs.devices
modules/nvidia-kernel/debian/dirs.template
modules/nvidia-kernel/debian/override.template
modules/nvidia-kernel/debian/patches/
modules/nvidia-kernel/debian/patches/01_sysfs
modules/nvidia-kernel/debian/patches/00list
modules/nvidia-kernel/debian/patches/03_pci_get_class
modules/nvidia-kernel/debian/patches/02_pcialias
modules/nvidia-kernel/debian/patches/04_minion
modules/nvidia-kernel/debian/postinst
modules/nvidia-kernel/debian/postrm
modules/nvidia-kernel/debian/rules
modules/nvidia-kernel/nv/
modules/nvidia-kernel/nv/Makefile.kbuild
modules/nvidia-kernel/nv/Makefile.nvidia
modules/nvidia-kernel/nv/README
modules/nvidia-kernel/nv/conftest.sh
modules/nvidia-kernel/nv/cpuopsys.h
modules/nvidia-kernel/nv/gcc-version-check.c
modules/nvidia-kernel/nv/makefile
modules/nvidia-kernel/nv/nv-i2c.c
modules/nvidia-kernel/nv/nv-kernel.o
modules/nvidia-kernel/nv/nv-linux.h
modules/nvidia-kernel/nv/nv-memdbg.h
modules/nvidia-kernel/nv/nv-misc.h
modules/nvidia-kernel/nv/nv-vm.c
modules/nvidia-kernel/nv/nv-vm.h
modules/nvidia-kernel/nv/nv.c
modules/nvidia-kernel/nv/nv.h
modules/nvidia-kernel/nv/nvreadme.h
modules/nvidia-kernel/nv/nvtypes.h
modules/nvidia-kernel/nv/os-agp.c
modules/nvidia-kernel/nv/os-agp.h
modules/nvidia-kernel/nv/os-interface.c
modules/nvidia-kernel/nv/os-interface.h
modules/nvidia-kernel/nv/os-registry.c
modules/nvidia-kernel/nv/pat.h
modules/nvidia-kernel/nv/rmretval.h
rm -rf debian/temp
touch build-kernel-stamp
dh_testdir
dh_testroot
dh_clean -k
dh_installdirs
install -m 644 /usr/share/envy/nvidia-graphics-drivers/nvidia-kernel-source.tar.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-kernel-source/usr/src
install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/X11R6/lib/modules/drivers/nvidia_drv.so \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/drivers
install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/X11R6/lib/libXvMCNVIDIA.a /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/libXvMCNVIDIA.a;
install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/X11R6/lib/libXvMCNVIDIA.so.1.0.9755 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/libXvMCNVIDIA.so.1.0.9755;
install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/include/GL/gl.h \
/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/include/GL/glext.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/include/GL/glx.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/include/GL/glxext.h \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/include/GL
install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/libGL.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/libGLcore.so.1.0.9755 \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
sed "s/__GENERATED_BY__/Debian nvidia-graphics-drivers/" NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib/" > /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/libGL.la
# install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/libGL.la /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/libGL.la
# TLS (nvidia-tls new for 6106)
install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/libnvidia-tls.so.1.0.9755 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/
install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/tls/libnvidia-tls.so.1.0.9755 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
#sed "s/__GENERATED_BY__/Debian nvidia-graphics-drivers/" NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/tls/libGL.la | sed "s/__LIBGL_PATH__/\/usr\/lib\/tls/" > /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-dev/usr/lib/nvidia/libGL.la
# install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/tls/libGL.la /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia/libGL.la
install -m 0644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib/libnvidia-cfg.so.1.0.9755 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia/
install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/X11R6/lib/modules/extensions/libglx.so.1.0.9755 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/extensions/
install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/X11R6/lib/modules/libnvidia-wfb.so.1.0.9755 /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/xorg/modules/
install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/tls_test /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/tls_test_dso.so /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib/nvidia
install -d /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/lintian/overrides
install -m 0644 debian/nvidia-glx.override \
                /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/lintian/overrides/nvidia-glx
if [ "i386" == "amd64" ] ; then \
                install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib32/libGLcore.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib32/libGL.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib32/libnvidia-tls.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib32/tls/libnvidia-tls.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib/tls ; \
        fi
[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs
dh_installdocs -s
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 122052 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_1.0.9756_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-kernel-source:
 nvidia-kernel-source depends on dpatch (>= 2.0.0); however:
  Package dpatch is not installed.
dpkg: error processing nvidia-kernel-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-kernel-source
rm: cannot remove `/usr/src/nvidia-kernel*.deb': No such file or directory
rm: cannot remove `/usr/src/nvidia-new-kernel*.deb': No such file or directory
Getting source for kernel version: 2.6.17-11-generic
Kernel headers available in /lib/modules/2.6.17-11-generic/build
Creating symlink...
apt-get install build-essential
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  nvidia-kernel-source: Depends: dpatch (>= 2.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Done!

install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib32/libnvidia-tls.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib32/tls/libnvidia-tls.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib/tls ; \
        fi
[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install 
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs 
dh_installdocs -s 
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian 
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 122052 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_1.0.9756_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-kernel-source:
 nvidia-kernel-source depends on dpatch (>= 2.0.0); however:
  Package dpatch is not installed.
dpkg: error processing nvidia-kernel-source (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 nvidia-kernel-source
rm: cannot remove `/usr/src/nvidia-kernel*.deb': No such file or directory
rm: cannot remove `/usr/src/nvidia-new-kernel*.deb': No such file or directory
Getting source for kernel version: 2.6.17-11-generic
Kernel headers available in /lib/modules/2.6.17-11-generic/build
Creating symlink...
apt-get install build-essential 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
build-essential is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  nvidia-kernel-source: Depends: dpatch (>= 2.0.0) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Done!

Updated infos about 83 packages
Extracting the package tarball, /usr/src/nvidia-kernel-source.tar.gz, please wait...

/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib32/tls/libnvidia-tls.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib/tls ; \
        fi
[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install 
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs 
dh_installdocs -s 
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian 
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 122052 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_1.0.9756_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-kernel-source:
 nvidia-kernel-source depends on dpatch (>= 2.0.0); however:
  Package dpatch is not installed.

/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib ; \
                install NVIDIA-Linux-x86-1.0-9755-pkg0/usr/lib32/tls/libnvidia-tls.so.1.0.9755 \
                        /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx-ia32/emul/ia32-linux/usr/lib/tls ; \
        fi
[: 10: ==: unexpected operator
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-bug-report.sh /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate package
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-xconfig /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
# use separate source package instead
install -m 755 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/bin/nvidia-settings /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/bin/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/doc/nvidia-settings-user-guide.txt /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/man/man1/nvidia-settings.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install -m 644 NVIDIA-Linux-x86-1.0-9755-pkg0/usr/share/man/man1/nvidia-xconfig.1.gz /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/man/man1/
install /usr/share/envy/nvidia-graphics-drivers/script /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/share/bug/nvidia-glx
dh_install 
/usr/bin/make -f debian/rules binary-common
make[1]: Entering directory `/usr/share/envy/nvidia-graphics-drivers'
dh_testdir
dh_testroot
dh_installchangelogs 
dh_installdocs -s 
dh_installexamples
dh_installdebconf
dh_installinit
dh_installman
dh_link
dh_compress -X.h -X README.Debian 
dh_fixperms
dh_makeshlibs
dh_installdeb
dh_shlibdeps  -Xia32 -Xtls -l/usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx/usr/lib
# quickhack! remove me :-/
perl -pi.bak -e 's/,\s+nvidia-glx-ia32//;' /usr/share/envy/nvidia-graphics-drivers/debian/nvidia-glx.substvars
dh_gencontrol -s
dh_md5sums
dh_builddeb -s
dpkg-deb: building package `nvidia-glx' in `../nvidia-glx_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-glx-dev' in `../nvidia-glx-dev_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
dpkg-deb: building package `nvidia-kernel-source' in `../nvidia-kernel-source_1.0.9756_i386.deb'.
tar: -: file name read contains nul character
make[1]: Leaving directory `/usr/share/envy/nvidia-graphics-drivers'
 dpkg-genchanges -b
dpkg-genchanges: binary-only upload - not including any source code
dpkg-buildpackage: binary only upload (no source included)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
Selecting previously deselected package nvidia-kernel-source.
(Reading database ... 122052 files and directories currently installed.)
Unpacking nvidia-kernel-source (from nvidia-kernel-source_1.0.9756_i386.deb) ...
dpkg: dependency problems prevent configuration of nvidia-kernel-source:
 nvidia-kernel-source depends on dpatch (>= 2.0.0); however:
  Package dpatch is not installed.
Done with /usr/src/nvidia-kernel-2.6.17-11-generic_1.0.9756+2.6.17.1-11.37_i386.deb .
Selecting previously deselected package nvidia-kernel-2.6.17-11-generic.
(Reading database ... 122060 files and directories currently installed.)
Unpacking nvidia-kernel-2.6.17-11-generic (from .../nvidia-kernel-2.6.17-11-generic_1.0.9756+2.6.17.1-11.37_i386.deb) ...idia-kernel*.deb': No such file or directory
Setting up nvidia-kernel-2.6.17-11-generic (1.0.9756+2.6.17.1-11.37) ...ectory
Getting source for kernel version: 2.6.17-11-generic
Reading package lists... Donelib/modules/2.6.17-11-generic/build
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  dpatchstate information... Done
Suggested packages:already the newest version.
  curlght want to run `apt-get -f install' to correct these:
Recommended packages:s have unmet dependencies:
  patchutilsnel-source: Depends: dpatch (>= 2.0.0) but it is not going to be insThe following NEW packages will be installed:
  dpatch dependencies. Try 'apt-get -f install' with no packages (or specify a s
0 upgraded, 1 newly installed, 0 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 84.1kB of archives.
After unpacking 319kB of additional disk space will be used.
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main dpatch 2.0.20 [84.1kB]
Fetched 84.1kB in 0s (110kB/s)  /usr/src/nvidia-kernel-source.tar.gz, please wai
Selecting previously deselected package dpatch.
(Reading database ... 122067 files and directories currently installed.)
Unpacking dpatch (from .../archives/dpatch_2.0.20_all.deb) ...
Setting up dpatch (2.0.20) ...
Setting up nvidia-kernel-source (1.0.9756) ...
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package nvidia-glx-new
(Reading database ... 122111 files and directories currently installed.)
Preparing to replace nvidia-glx 1.0.9746+2.6.17.7-11.1-9746 (using nvidia-glx_1.0.9756_i386.deb) ...
dpkg-divert: `diversion of /usr/lib/xorg/modules/extensions/libglx.so to /usr/lib/nvidia/libglx.so.xlibmesa by nvidia-glx' clashes with `diversion of /usr/lib/xorg/modules/libglx.so to /usr/lib/nvidia/libglx.so.xlibmesa by nvidia-glx'
dpkg: error processing nvidia-glx_1.0.9756_i386.deb (--install):
 subprocess pre-installation script returned error exit status 2
Errors were encountered while processing:
 nvidia-glx_1.0.9756_i386.deb
rm: cannot remove `*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.deb': No such file or directory
rm: cannot remove `/usr/share/envy/*.asc': No such file or directory
rm: cannot remove `/usr/share/envy/*.changes': No such file or directory
ENVY: Operation Completed


there was no nvidia log in /var/log...

---

### Post by Churnd on 2007-04-29
Try this:

[LIST=1]
[*]Restore the original Xorg.conf
[*]Install nvidia-glx
[*]When the install is finished, run " sudo nvidia-glx-config enable"
[*]Take a look at the xorg.conf it wrote for you and see if it varies from the one you had been using
[/LIST]

Sometimes, it doesn't configure the "BusID" option correctly.  You can comment it out and see what happens.

---

### Post by zetsumei on 2007-04-29
Someone in #ubuntu helped me.  I upgraded and it all worked fine LOL

---

