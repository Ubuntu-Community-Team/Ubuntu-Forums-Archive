---
title: "Weird Colors - iMac G4 PPC Lamp Model Ubuntu 11.10"
date: 2012-01-29
forum: Apple Hardware Users
---

### Post by larsm on 2012-01-29
What have I done wrong?

I have installed Oneiric on my iMac G4 PPC Lamp Model and I have attached the picture of my awfully  
weird colors I experience with gui.

I use this code to get to the desktop, if I don't, I get a white screen after second yaboot prompt:

```
Linux nouveau.modset=0
```

Thank you, if you need anymore info about my computer, ask me please!

-Lars M.

[IMG]http://img84.imageshack.us/img84/7444/img0613551.jpg[/IMG]

---

### Post by canhoto on 2012-01-29
Hi. 
Look for the [PPC known issues]("https://wiki.ubuntu.com/PowerPCKnownIssues") to see if there's something that matches your case.

If you don't find anything, try to reinstall Ubuntu with a more stable and buggy-free release, like Lucid (10.04) or even Maverick (10.10). If you just installed Ubuntu and haven't done anything important with it, you may try another installation. But with another cd and maybe another release. Then, if you want to upgrade, you can always do it from the update manager. However, there are some problems with both 11.04 and 11.10. So, if I where you I would install 10.04, which is very up-to-date already, then upgrade to 10.10, and wait until the next stable release (12.04) comes out (it will be in April, although you can try unstable versions right now). Skip 11.04 and 11.10.

---

### Post by larsm on 2012-01-29
Thank you.

---

### Post by conal on 2012-01-30
Generally I would say - download an xorg.conf file in the way described in the FAQ or set one up. I always find the legacy nv driver to be more reliable than neaveau on my iLamp, you can specify nv in the xorg.conf file. However 12.04 installed fine on mine with no graphics problems at all.

---

### Post by larsm on 2012-01-30
> **conal said:**
> Generally I would say - download an xorg.conf file in the way described in the FAQ or set one up. I always find the legacy nv driver to be more reliable than neaveau on my iLamp, you can specify nv in the xorg.conf file. However 12.04 installed fine on mine with no graphics problems at all.

Yeah but I could never get the hang of xorg. Wait, you do mintppc?

---

### Post by conal on 2012-01-31
I do both! After install, drop to the command line and downloading a ready made xorg.conf file from the command prompt, e.g: 

```
wget http://mac.linux.be/files/xorg/imac8.txt
```

...to get an xorg.conf file, then to put it in place:

```
mv imac8.txt /etc/X11/xorg.conf
```

....then reboot. If that doesn't work try this one:

```
wget http://mac.linux.be/files/xorg/imac9.txt
```

...if that doesn't work try googling for more xorg.conf files that people have used for iLamps!

---

### Post by rsavage on 2012-01-31
> **conal said:**
> 
...if that doesn't work try googling for more xorg.conf files that people have used for iLamps!
 
The nv driver is not included in 11.10 so none of those xorg.conf files will work straightaway in 11.10 (or 12.04 etc).  Instructions to compile the nv driver are in the PowerPC FAQ!  
 
Some of those xorg.conf files on that site are pretty awful and old.  The PowerPC FAQ tells you all you need to know to configure a successful xorg.conf in the year 2012.

---

### Post by hsiyao on 2012-05-04
[B]Hi everybody, 
[/B]I stumbled upon the same problem, and thought the right channel to hopefully get a solution for everyone would be Ubuntu Brainstorm. If you vote for this idea it'll have a better chance getting implemented.

[[IMG]http://brainstorm.ubuntu.com/idea/29668/image/1/[/IMG]]("http://brainstorm.ubuntu.com/idea/29668/")

---

### Post by conal on 2012-05-11
I don't understand hsiyao- it's marked as not an idea!? So is nv actually supported in 12.04 or not?

---

### Post by hsiyao on 2012-05-11
Hi,

I guess it was marked to fast as not being an idea, and I wanted to write cheesehead a pm to take a second look but didn't find the time yet.

[http://packages.ubuntu.com/hardy/xserver-xorg-video-nv](http://packages.ubuntu.com/hardy/xserver-xorg-video-nv) tells you, that there is no 12.04 version (and no 11.10) so it's not installable from the repositories. 

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=612189](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=612189) says, that xorg-video-nv was in fact discontinued because it wasn't maintained good enough anymore. It was replace by nouveau but the problem is, that nouveau needs kms (modeset=1) to work. Therefore if you boot a system with kms disabled, nouveau can't be used and xorg falls back to fbdev since xorg-video-nv doesn't exist anymore (Xorg still looks for it though)

So in my eyes the only solution would be to compile it for 12.04 and make it installable through the repositories for systems with nvidia cards that can't boot with kms enabled... and that pretty much was my idea ;) gonna write cheesehead now ;)

---

### Post by conal on 2012-05-11
Makes sense to me!

---

### Post by csrunu on 2012-05-12
Indeed, this is what worked for me... [2002 iMAC G4 800mhz with NVidia GeForce2 MX]

I'm a total Linux noob so feel free to correct me if there is/are any easier way to get there.
I just compiled various tutorials accordingly to this thread wich I used to get it working.

>installation with 12.04 ppc live cd from there [alt on boot > select the live cd to boot]

[http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-powerpc.iso]("http://cdimage.ubuntu.com/releases/12.04/release/ubuntu-12.04-desktop-powerpc.iso")

>this leads to a minimal cli interface so boot with this option

```
live-powerpc nouveau.modeset=0
```

[the live cd will boot with the same "strange" colors as yours [screen is still "readable"]

>launch the ubuntu full installer on the desktop and follow the steps as usual

>reboot

>at yaboot type...

```
Linux nouveau.modeset=0
```

>when the mac has finished booting, open the terminal

[I followed this tutorial to compile old nv driver]

[http://ubuntuforums.org/showpost.php?p=11493049&postcount=27]("http://ubuntuforums.org/showpost.php?p=11493049&postcount=27")

>so

```
sudo nano /etc/apt/sources.list
```

>add 

```
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
```

at the end of the file.

>then ctrl+O to save > ENTER to confirm > ctrl+x to close

>then to compile the old nv driver

```
sudo apt-get update
sudo apt-get install build-essential fakeroot dpkg-dev
mkdir nv-build
cd nv-build 
apt-get source xserver-xorg-video-nv
cd xserver-xorg-video-nv-2.1.17                        
sudo apt-get build-dep xserver-xorg-video-nv
dpkg-buildpackage -rfakeroot -b
cd ..
sudo dpkg -i ./*.deb
```

>Then remove the two lines you previously added

```
sudo nano /etc/apt/sources.list
```

```
deb http://ports.ubuntu.com/ubuntu-ports/ natty universe
deb-src http://archive.ubuntu.com/ubuntu natty universe
```

>then ctrl+O > ENTER > ctrl+x

>then

```
sudo apt-get update
```

>old nv driver is now compiled...

I then found an xorg.conf file wich seems to work for me [I hope for you too] there

[http://ubuntuforums.org/showthread.php?t=1444986]("http://ubuntuforums.org/showthread.php?t=1444986")

>so, open a new txt file > paste the following code in it > save it to file_name.txt [file_name=any name you would like]

```
Section "Device"
Identifier "nVidia"
Driver "nv"
BusID "PCI:0:16:0"
Option "FlatPanel" "true"
Option "FPDither" "true"
EndSection

Section "Monitor"
Identifier   "Generic Monitor" 
Option      "DPMS" 
HorizSync     59-63
VertRefresh   50-160
EndSection


Section "Screen"
	Identifier "Screen0"
	Device "nVidia"
	Monitor "Generic Monitor"
	DefaultDepth 24
	Subsection "Display"
	Depth 24
	Modes	"1024x768"
EndSubSection
EndSection

Section "ServerLayout"
Identifier "ilamp"
Screen "Screen0"
#Option "AIGLX" "off"
EndSection

#Section "Extensions"
#	Option "Composite" "enable"
#EndSection

Section "DRI"
	Mode 0666
EndSection
```

>then [depending on the file_name and the location you choose or simply drag the file into the terminal between "mv" and "/etc/X11/xorg.conf"]

```
sudo mv file_name /etc/X11/xorg.conf
```

>the xorg.conf file is now ready and so is the nv driver, you just now need to make the "nouveau.modeset=0" yaboot paramater permanent [[https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F]("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F")]

>to do so []("https://wiki.ubuntu.com/PowerPCFAQ#How_do_I_make_a_yaboot_parameter_permanent.3F")

```
sudo nano /etc/yaboot.conf
```

>add 

```
nouveau.modeset=0
```

in the appends fields [between the quotes and after what is already there [!separated by a space!] if you would not change anything to the way ubuntu boot natively]

>now reboot

```
sudo reboot
```

>everything should now works as it has worked for me...

---

### Post by hsiyao on 2012-05-13
Thx csrunu for your great post with all the little things you have to do to be able to use the nv-driver again! Highly appreciate it!

For the long run: I got a reply from one of the admins at ubuntu brainstorm, that in situations like this you've to file a bugreport against a meta package like xorg-xserver with the plain explanation, that it worked before the upgrade and now doesn't. Maybe in the end there will be some installer, that does all the  steps you listed above, that would be installable through synaptic or even during installation - and all this at own risk. Maybe this could be a solution for the dilemma that nouveau needs kms and reintegrating xorg-xserver-video-nv would need a maintainer....

---

