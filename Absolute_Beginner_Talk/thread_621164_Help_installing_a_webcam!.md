---
title: "Help installing a webcam!"
date: 2007-11-23
forum: Absolute Beginner Talk
---

### Post by RobotoWorks on 2007-11-23
Im running Ubuntu 7.10, and I just bought a Logitech QuickCam Communicate STX, similar to this one,  [http://www.sybaritic.co.za/store/images/WC-LQCSs.jpg](http://www.sybaritic.co.za/store/images/WC-LQCSs.jpg)  with these specs,

    *  Sensor - High quality VGA
    * Video Capture - Up to 640 x 480 pixels 30 frames per second AVIs
    * Still Image Capture - 1.3 mexapixels (interpolated) BMP, JPEG
    * Field of View - 42 degrees horizontal
    * USB 2.0 and 1.1 compliant


How do I install this on my laptop?

---

### Post by spiderbatdad on 2007-11-23
there is a program called camorama web cam viewer under Applications->Add/Remove.
make sure you enable all available application in the search at top right of the window.

---

### Post by RobotoWorks on 2007-11-23
Where exactly would the program be located in Add/Remove?

---

### Post by spiderbatdad on 2007-11-23
when you open Add/Remove, you may have to choose preferences to enable third party software. Then there is a small dialogue window that defines your search parameters. use the drop down menu to select All Available Applications. Camorama is listed alphabetically

---

### Post by spiderbatdad on 2007-11-23
here's a screenshot:

---

### Post by RobotoWorks on 2007-11-23
3rd party is enable and I typed the name exactly how you wrote it, but here what I got:

There is no matching application available.
To broaden your search, choose "All available applications" or "All Open Source applications".
To broaden your search, choose 'All' categories.

And I did go to "All applications"

---

### Post by spiderbatdad on 2007-11-23
your preferences should look like this:

---

### Post by RobotoWorks on 2007-11-23
They do, so I dont see why Im experiencing this problem.  Do I need to download anything first?

---

### Post by spiderbatdad on 2007-11-23
idk, Bro. Try Sudo apt-get update in a terminal now that you have enabled all the repositories, but I thought Add/Remove auto-updated itself.

you see the first screenshot i posted in post #5?

---

### Post by RobotoWorks on 2007-11-23
My dad has the webcam installed on a Vista computer, he downloaded the software from the Logitech site, would that work for Ubuntu?

Btw, I found a way to install Camorama Webcam Viewer, how do I use my webcam from there?

---

### Post by spiderbatdad on 2007-11-23
negative, though logitech might offer a .tar you could use.

---

### Post by LordKthulhu on 2007-11-23
On a related topic... is it possible to have a video chat with someone running YM? Pidgin does not seem to support video, and I couldn't get YM to run under Wine. Any suggestions, or am I SOL? Thanks!

---

### Post by RobotoWorks on 2007-11-23
So I found away to get Camorama Webcam Viewer, how do I use my webcam from it?

---

### Post by spiderbatdad on 2007-11-23
it should appear somewhere in your Applications. maybe under Sound Video or Accessories

---

### Post by spiderbatdad on 2007-11-23
> **LordKthulhu said:**
> On a related topic... is it possible to have a video chat with someone running YM? Pidgin does not seem to support video, and I couldn't get YM to run under Wine. Any suggestions, or am I SOL? Thanks!

Pidgin is planning to include video support soon I hope, as I've been wanting this a long time too.There are solutions I think if you're chatting with someone running windows, unfortunately my gf has an older mac (pre-tiger) and we have not had any luck. Of course there is Ekiga which is now available to windows. It may take a little work but I think you can do it.

---

### Post by RobotoWorks on 2007-11-23
Okay well It appeared under Graphics for some reason any way, I plugged in the web cam and tryed to load the web cam view when I was prompted with the following  "could not connect to video device (/dev/video0) please check connection"

---

### Post by spiderbatdad on 2007-11-23
> **spiderbatdad said:**
> it should appear somewhere in your Applications. maybe under Sound Video or Accessories


sorry for re-posting. didn't want you to miss this.

---

### Post by RobotoWorks on 2007-11-23
> **RobotoWorks said:**
> Okay well It appeared under Graphics for some reason any way, I plugged in the web cam and tryed to load the web cam view when I was prompted with the following  "could not connect to video device (/dev/video0) please check connection"

Sorry for re=posting just want you to see

---

### Post by spiderbatdad on 2007-11-23
hmmm? not sure. I have used this before with my logitech quickcam. Your cam may be too new or require drivers not included in the program camorama. I know there is a solution, but I think it is beyond my abilities at this point. If you could get just the drivers and run them from the appropriate file, for example. You would have to point your /dev file to it and include it, and all that jazz. Sorry I can't help anymore with this.

---

### Post by LordKthulhu on 2007-11-23
Thanks, Spider, I guess I am SOL for the time being. Will be looking forward to the added capability, then.

---

### Post by asmiller-ke6seh on 2007-11-23
You might want to try searching this forum for **EasyCam**. If you webcam is supported, this could make your setup easier.

---

### Post by RobotoWorks on 2007-11-23
I got the webcam about a month ago, do I have any other options?

---

### Post by spiderbatdad on 2007-11-23
maybe try running Ekiga, too, to see if it detected.

---

### Post by RobotoWorks on 2007-11-23
Where do I find Ekiga?

---

### Post by spiderbatdad on 2007-11-23
should be under Applications->Internet. Else it's in Synaptic.

---

### Post by RobotoWorks on 2007-11-23
Ekiga is setup now, how does it realate to a web cam?

---

### Post by philinux on 2007-11-23
you need a driver like qc-usb-messenger-source_1.1-2_all.deb

Not sure if this one is the right one for your cam, will have a look for you. BRB.

---

### Post by philinux on 2007-11-23
Looks like someone cracked this cam here.

[http://ubuntuforums.org/showthread.php?t=299210&highlight=Logitech+QuickCam+Communicate+STX](http://ubuntuforums.org/showthread.php?t=299210&highlight=Logitech+QuickCam+Communicate+STX)

---

### Post by RobotoWorks on 2007-11-23
So matter reading this I should have it working, does it matter that I have 7.10 and not 6.06?

---

### Post by philinux on 2007-11-23
Should work fine

---

### Post by RobotoWorks on 2007-11-23
It doesnt work, must be becuase the thread is over a year old and my cam is only about a month old, any other solutions?

---

### Post by philinux on 2007-11-23
The instruction looked a little hard for me too. I looked at the list of supported webcams and bought the quickcam messenger found the .deb file which is easy to install, only needs double click on it and away it goes.

I'll have another poke around see if there's anything like it for yours.

---

### Post by philinux on 2007-11-23
According to the guru of webcams 

[http://mxhaard.free.fr/spca5xx.html](http://mxhaard.free.fr/spca5xx.html) it is supported and the driver required is this one 

[http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz](http://mxhaard.free.fr/spca50x/Download/gspcav1-20070508.tar.gz)

[http://mxhaard.free.fr/download.html](http://mxhaard.free.fr/download.html)

You download the tar file save to your desktop. Double click to extract it then run the script for gspca_build

---

### Post by RobotoWorks on 2007-11-23
Thanx so much! Btw, how do I install these?

---

### Post by philinux on 2007-11-23
Like I said previous download the tar file and select save to your Desktop.

Double click it then to extract it. It's like a zip file in windoze thats all. It will create a folder on your desktop. Now I've never done this before but you need to open a terminal and type

sudo /Desktop/gspcav1-20070508/gspca_build

Copy and paste it into the terminal. That runs the script that creates the driver for you. Hope it works.

---

### Post by RobotoWorks on 2007-11-23
Kk, I extracted the file ran the code in terminal and this came up "sudo: /Desktop/gspcav1-20070508/gspca_build: command not found"

---

### Post by philinux on 2007-11-23
Bump

I said I'd not done this before.

Anyone know how to get this script or make thingy to go.

---

### Post by RobotoWorks on 2007-11-23
Bump...


Yeah anyone know?

---

### Post by philinux on 2007-11-23
[http://monkeyblog.org/ubuntu/installing/#source](http://monkeyblog.org/ubuntu/installing/#source)

I'd read through carefully, and dont bump too often it gets some folk annoyed. Dont forget all this help is free too.

---

### Post by RobotoWorks on 2007-11-23
Will this help me install the drivers?

---

### Post by spiderbatdad on 2007-11-23
have you rebooted since installing camorama, and tried it again to see if your cam is detected?

---

### Post by RobotoWorks on 2007-11-23
No I havent....I need to install the driver that Philinux gave me, but I dont know how to do that

---

### Post by spiderbatdad on 2007-11-23
sorry I missed a lot. was it a tar ball? It should have an install file with instructions for installing it, or a readme file. Click on it to open it up and look for the instructions. You may need additional packages to make the build...like buildessential from synaptic

---

### Post by RobotoWorks on 2007-11-23
Well here the makefile:

# Makefile.kld to build a driver with linux emulation.
# $Id: Makefile.kld,v 1.13 2007/01/29 19:04:29 luigi Exp $
#
# Here you should set the following:
#	.PATH:	driver-specific paths
#	SRCS=	list of (driver) source files that we want to compile.
#	KMOD=	driver name (one word, will be used also elsewhere).
#	CFLAGS=	any driver-specific flags you might need. Often
#		-Ixyz listing all directories with include files.
#	KLINPATH= path of linux_compat relative to .CURDIR
#
#	Any other driver-specific variables.

.PATH: ${.CURDIR} ${.CURDIR}/decoder 

# sources for the linux driver
SRCS= gspca_core.c gspcadecoder.c

KMOD=gspca

CFLAGS+= -ISunplus -ISunplus-jpeg -ISonix -IConexant
CFLAGS+= -IVimicro -Idecoder
CFLAGS+= -DUSB_DEBUG

#DEBUG_FLAGS=-g

#--- Here are the driver-specific variables

VERSION    = 01.00.18

###
# The following flags enable experimental features.
# By default, these are enabled for development versions of the driver, and
# disabled for release versions.

# Optional: Enable driver debugging
CFLAGS   += -DGSPCA_ENABLE_DEBUG

# Optional: Enable direct register read/write for PAC207 development
#CFLAGS   += -DGSPCA_ENABLE_REGISTERPLAY

###
# The following flags enable features that aren't yet implemented, and
# therefore are disabled by default.

# Optional: Enable compression
CFLAGS   += -DGSPCA_ENABLE_COMPRESSION

###
# Rest of Makefile follows here. You probably won't need to touch this.

# Setup defines
CFLAGS   += -DCONFIG_USB_GSPCA_MODULE=1 -D__KERNEL__
#CFLAGS   += -DCONFIG_USB_GSPCA_MODULE=1 -DMODULE -D__KERNEL__
CFLAGS   += -DVID_HARDWARE_GSPCA=0xFF -DGSPCA_VERSION=\"$(VERSION)\"

.include <linux_compat/bsd.linux_kmod.mk>

---

### Post by RobotoWorks on 2007-11-23
Can someone tell me what that makefile means?

---

### Post by spiderbatdad on 2007-11-23
you're looking for install or readme. usually a tar.gz is installed something like this, assuming the package is on your desktop:

open terminal:

```
cd Deskt
``` then tab to auto complete the line and enter

now:
```
tar -xvf (begin typing the package name and hit tab)
```

then:
```
cd (name of new directory created on desktop
```

then:
```
./configure
           make
           make install
```

but the commands will vary depending on the package. If you can find .deb packages the are self extracting in ubuntu. If you are stuck with tar balls, you need the proper tools installed from synaptic to handle the tar ball...like make1.4, build essential...etc. the terminal should tell you if you have unmet dependencies.

---

### Post by RobotoWorks on 2007-11-23
Its a tar.gz file, but when I enter those codes it gives me "Bash:Command not found."

---

### Post by spiderbatdad on 2007-11-23
heres a how to for ya:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by spiderbatdad on 2007-11-23
```
cd D(tab key)
```

gives you bash command not found?

---

### Post by RobotoWorks on 2007-11-23
> **spiderbatdad said:**
> ```
cd D(tab key)
```

gives you bash command not found?

No that one works.

---

### Post by spiderbatdad on 2007-11-23
then:

```
tar -xvf name of packge, begin as named and use tab key to complete and make sure your doing it right
```
heh.

---

### Post by RobotoWorks on 2007-11-23
Heres what that gives me:

gspcav1-20070508/
gspcav1-20070508/decoder/
gspcav1-20070508/decoder/gspcadecoder.c
gspcav1-20070508/decoder/gspcadecoder.h
gspcav1-20070508/decoder/gspcadecoder-OSX.c
gspcav1-20070508/decoder/gspcadecoder-OSX.h
gspcav1-20070508/Makefile
gspcav1-20070508/Vimicro/
gspcav1-20070508/Vimicro/vc032x_sensor.h
gspcav1-20070508/Vimicro/zc3xx.h
gspcav1-20070508/Vimicro/cs2102.h
gspcav1-20070508/Vimicro/vc032x.h
gspcav1-20070508/Vimicro/pas106b.h
gspcav1-20070508/Vimicro/icm105a.h
gspcav1-20070508/Vimicro/hv7131b.h
gspcav1-20070508/Vimicro/hv7131c.h
gspcav1-20070508/Vimicro/pb0330.h
gspcav1-20070508/Vimicro/ov7630c.h
gspcav1-20070508/Vimicro/tas5130c_vf0250.h
gspcav1-20070508/Vimicro/tas5130c.h
gspcav1-20070508/Vimicro/hdcs2020.h
gspcav1-20070508/Etoms/
gspcav1-20070508/Etoms/et61xx51.h
gspcav1-20070508/Sonix/
gspcav1-20070508/Sonix/sn9cxxx.h
gspcav1-20070508/Sonix/sonix.h
gspcav1-20070508/utils/
gspcav1-20070508/utils/spcagamma.h
gspcav1-20070508/utils/spcausb.h
gspcav1-20070508/utils/spcaCompat.h
gspcav1-20070508/Conexant/
gspcav1-20070508/Conexant/cx11646.h
gspcav1-20070508/Conexant/cxlib.h
gspcav1-20070508/Pixart/
gspcav1-20070508/Pixart/pac207-OSX.h
gspcav1-20070508/Pixart/pac7311.h
gspcav1-20070508/Pixart/pac207.h
gspcav1-20070508/changelog
gspcav1-20070508/gspca_core.c
gspcav1-20070508/Transvision/
gspcav1-20070508/Transvision/tv8532.h
gspcav1-20070508/Makefile.kld
gspcav1-20070508/gspca.h
gspcav1-20070508/Sunplus/
gspcav1-20070508/Sunplus/spca501.dat
gspcav1-20070508/Sunplus/spca505.dat
gspcav1-20070508/Sunplus/spca508.dat
gspcav1-20070508/Sunplus/spca561-OSX.h
gspcav1-20070508/Sunplus/spca506.h
gspcav1-20070508/Sunplus/spca561.h
gspcav1-20070508/Sunplus/spca501_init.h
gspcav1-20070508/Sunplus/spca508_init-OSX.h
gspcav1-20070508/Sunplus/spca508_init.h
gspcav1-20070508/Sunplus/spca501_init-OSX.h
gspcav1-20070508/Sunplus/spca505_init.h
gspcav1-20070508/Sunplus-jpeg/
gspcav1-20070508/Sunplus-jpeg/spca500.dat
gspcav1-20070508/Sunplus-jpeg/jpeg_qtables.h
gspcav1-20070508/Sunplus-jpeg/sp5xxfw2.h
gspcav1-20070508/Sunplus-jpeg/sp5xxfw2.dat
gspcav1-20070508/Sunplus-jpeg/spca500_init.h
gspcav1-20070508/gspca_build
gspcav1-20070508/Mars-Semi/
gspcav1-20070508/Mars-Semi/mr97311.h

---

### Post by spiderbatdad on 2007-11-23
it will also have placed a new file on your desktop with the same name as the tar.gz package.
at the prompt in the terminal:
```
cd name of new file
```

thats change directory into the new file. cd then the name of the file. begin typing name and use tab to auto complete the line.

Then at the prompt:
```
./configure
```

when that finishes:

```
make
```

finally:

```
make install
```

---

### Post by RobotoWorks on 2007-11-23
No new file was created.

---

### Post by spiderbatdad on 2007-11-23
no folder was created after untarring the package? That is strange. maybe the options in the code were not all correct.
my bad. try:

```
tar -zxvf (tarball)
```

of course you have to open a terminal and cd to Desktop again.

---

### Post by RobotoWorks on 2007-11-23
It works better only:  robotoworks@robotoworks-laptop:~$ /home/robotoworks/Desktop/gspcav1-20070508.tar.gz
bash: /home/robotoworks/Desktop/gspcav1-20070508.tar.gz: Permission denied

---

### Post by spiderbatdad on 2007-11-23
you may also need to be root while configuring and making.

thats: sudo ./configure
          sudo make
          sudo make install

this all after you have sucessfully untarred the package and cd into the directory.
yup permission denied because you need to be root.

---

### Post by RobotoWorks on 2007-11-23
Hmm, none of this is working, either Im not doing it right or I just dont know, Im giving up, I'll just let my dad use the webcam on his Vista computer (A computer that he wont let me use) Thanx for all the help even if it didnt work and well yeah.....

---

### Post by spiderbatdad on 2007-11-23
one more try for me at explaining how to unpack a tar.gz from your desktop.
open terminal and enter:
```
cd D(tab key)
```

then:
```
tar -zxvf (name of tarball)
```
begin typing name and use tab to auto complete helps eliminate typos and is faster.

new directory having a name similar to the tar.gz is placed on desktop

```
cd (name of new directory)
```

then:
```
./configure
```

not all tar.gz have a configure. if you get an error or not proceed with:

```
make
```

finally:

```
sudo make install
```

best of luck. Your best chance of success is in reading the readme or install file that comes with the tarball to tell you how to install it. These files are archived in the tarball and can be extracted by right clicking on the package and selecting extract here.

---

### Post by RobotoWorks on 2007-11-23
My final question, what do you mean by the name of the tar ball?

---

### Post by spiderbatdad on 2007-11-23
whatever the package tar.gz is called: the whole name of the package including tar.gz. It is best to just type the first couple of characters (case sensitive) and use the tab key.

sorry I'm so clumsy giving help.

---

### Post by Frak on 2007-11-23
> **RobotoWorks said:**
> It works better only:  robotoworks@robotoworks-laptop:~$ /home/robotoworks/Desktop/gspcav1-20070508.tar.gz
bash: /home/robotoworks/Desktop/gspcav1-20070508.tar.gz: Permission denied
```
**tar -zxvf** /home/robotoworks/Desktop/gspcav1-20070508.tar.gz
```

---

### Post by Frak on 2007-11-23
> **spiderbatdad said:**
> you may also need to be root while configuring and making.

thats: sudo ./configure
          sudo make
          sudo make install

this all after you have sucessfully untarred the package and cd into the directory.
yup permission denied because you need to be root.
You **NEVER** use ./configure or make as root. Unless you want to risk screwing up your system.
Only
./configure
make
sudo make install

---

### Post by RobotoWorks on 2007-11-23
> **Frak said:**
> ```
**tar -zxvf** /home/robotoworks/Desktop/gspcav1-20070508.tar.gz
```

Do I press tab after that?

---

### Post by spiderbatdad on 2007-11-23
> **Frak said:**
> You **NEVER** use ./configure or make as root. Unless you want to risk screwing up your system.
Only
./configure
make
sudo make install

thank you. another of many things I didn't know.

---

### Post by RobotoWorks on 2007-11-23
Okay so right now in terminal I have:  cd D tar -zxvf /home/robotoworks/Desktop/gspcav1-20070508.tar.gz

What do I press?

---

### Post by spiderbatdad on 2007-11-23
no that code isnt right cd D(tab key) then enter
then tar -zxvf (package) then enter
then cd (new directory) then enter
then ./configure 
enter
make
enter
sudo make install.

check post 59 again. you need to enter after each code line.

---

### Post by RobotoWorks on 2007-11-23
"no that code isnt right cd D(tab key) then enter"

I press tab and it works then I press enter and it says "Bash:no such file in directory"

---

### Post by spiderbatdad on 2007-11-23
cd D(tab key) where tab key is actually the tab key on your keyboard, used to auto-complete the line for you

---

### Post by spiderbatdad on 2007-11-23
make sure capitol D
```
cd Desktop/
```

---

### Post by RobotoWorks on 2007-11-23
Okay finally I got all that coding finished and working, what is the next time, if there is any?

---

### Post by spiderbatdad on 2007-11-23
try your webcam. if it works jump for joy.

---

### Post by RobotoWorks on 2007-11-23
IT WORKS!!!!  *A little laggy and not as cool and it is on Windows but IT WORKS!!!!

---

### Post by philinux on 2007-11-23
Well done you learnt something on the way.

It may be the light level causing the lag.

---

### Post by RobotoWorks on 2007-11-23
Thanx for all the help guy, I have successfully installed a webcam on Ubuntu and learned something at the same time!

---

### Post by spiderbatdad on 2007-11-23
omg! I'm going to celebrate.

---

### Post by philinux on 2007-11-23
Linus is not windows.

However not many peeps installed windoze themselves and got everything to work, it usually comes pre-installed.

---

### Post by RobotoWorks on 2007-11-23
One thing though, how do I install effects on the effects tab?

---

### Post by philinux on 2007-11-23
before you get into another post try Kopete from synaptic. great im with webcam support

---

### Post by Frak on 2007-11-23
> **RobotoWorks said:**
> One thing though, how do I install effects on the effects tab?
Post the output of this command
```
glxinfo | grep direct
```

---

### Post by Marianne_S on 2007-11-25
i tried posting about this before here: [http://ubuntuforums.org/showthread.php?p=3812997#post3812997](http://ubuntuforums.org/showthread.php?p=3812997#post3812997)

but since i didnt get any replies, and it looks like people are onto some of the same things i struggle with here, i'll try to post here. i got the gspca-source from synaptic, and i need to unpack it. it  is placed in /usr/src, and its name is gspca-source.tar.bz2.

i tried following the instructions - but changing it so it would unpack a .bz2 (I'm really new to ubuntu and dont know much about using the terminal ) - anyways here's how it went: 

cd /usr/src/
m@m-desktop:/usr/src$ tar  xfj gspca-source.tar.bz2
tar: modules: Cannot mkdir: Permission denied
tar: modules/gspca: Cannot mkdir: No such file or directory
tar: modules/gspca/debian: Cannot mkdir: No such file or directory
tar: modules/gspca/debian/rules: Cannot open: No such file or directory
tar: modules/gspca/debian/control.modules.in: Cannot open: No such file or directory
tar: modules/gspca/debian/postinst.modules.in: Cannot open: No such file or directory
tar: modules/gspca/debian/control: Cannot open: No such file or directory
tar: modules/gspca/debian/compat: Cannot open: No such file or directory
tar: modules/gspca/debian/copyright: Cannot open: No such file or directory
tar: modules/gspca/debian/changelog: Cannot open: No such file or directory
tar: modules/gspca/utils: Cannot mkdir: No such file or directory
tar: modules/gspca/utils/spcausb.h: Cannot open: No such file or directory
tar: modules/gspca/utils/spcaCompat.h: Cannot open: No such file or directory
tar: modules/gspca/utils/spcagamma.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro: Cannot mkdir: No such file or directory
tar: modules/gspca/Vimicro/ov7630c.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/vc032x_sensor.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/hv7131c.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/tas5130c.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/hdcs2020.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/icm105a.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/pb0330.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/cs2102.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/hv7131b.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/tas5130c_vf0250.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/zc3xx.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/vc032x.h: Cannot open: No such file or directory
tar: modules/gspca/Vimicro/pas106b.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus: Cannot mkdir: No such file or directory
tar: modules/gspca/Sunplus/spca506.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca505.dat: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca508_init.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca501_init-OSX.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca501.dat: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca561-OSX.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca561.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca501_init.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca508.dat: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca505_init.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus/spca508_init-OSX.h: Cannot open: No such file or directory
tar: modules/gspca/Conexant: Cannot mkdir: No such file or directory
tar: modules/gspca/Conexant/cxlib.h: Cannot open: No such file or directory
tar: modules/gspca/Conexant/cx11646.h: Cannot open: No such file or directory
tar: modules/gspca/gspca_core.c: Cannot open: No such file or directory
tar: modules/gspca/decoder: Cannot mkdir: No such file or directory
tar: modules/gspca/decoder/gspcadecoder-OSX.h: Cannot open: No such file or directory
tar: modules/gspca/decoder/gspcadecoder-OSX.c: Cannot open: No such file or directory
tar: modules/gspca/decoder/gspcadecoder.h: Cannot open: No such file or directory
tar: modules/gspca/decoder/gspcadecoder.c: Cannot open: No such file or directory
tar: modules/gspca/Sonix: Cannot mkdir: No such file or directory
tar: modules/gspca/Sonix/sn9cxxx.h: Cannot open: No such file or directory
tar: modules/gspca/Sonix/sonix.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus-jpeg: Cannot mkdir: No such file or directory
tar: modules/gspca/Sunplus-jpeg/sp5xxfw2.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus-jpeg/spca500_init.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus-jpeg/sp5xxfw2.dat: Cannot open: No such file or directory
tar: modules/gspca/Sunplus-jpeg/jpeg_qtables.h: Cannot open: No such file or directory
tar: modules/gspca/Sunplus-jpeg/spca500.dat: Cannot open: No such file or directory
tar: modules/gspca/changelog: Cannot open: No such file or directory
tar: modules/gspca/Transvision: Cannot mkdir: No such file or directory
tar: modules/gspca/Transvision/tv8532.h: Cannot open: No such file or directory
tar: modules/gspca/Etoms: Cannot mkdir: No such file or directory
tar: modules/gspca/Etoms/et61xx51.h: Cannot open: No such file or directory
tar: modules/gspca/Pixart: Cannot mkdir: No such file or directory
tar: modules/gspca/Pixart/pac207.h: Cannot open: No such file or directory
tar: modules/gspca/Pixart/pac207-OSX.h: Cannot open: No such file or directory
tar: modules/gspca/Mars-Semi: Cannot mkdir: No such file or directory
tar: modules/gspca/Mars-Semi/mr97311.h: Cannot open: No such file or directory
tar: modules/gspca/gspca.h: Cannot open: No such file or directory
tar: modules/gspca/Makefile: Cannot open: No such file or directory
tar: modules/gspca/Makefile.kld: Cannot open: No such file or directory
tar: modules/gspca/gspca_build: Cannot open: No such file or directory

what happened here? 

grateful for any help i can get

---

### Post by Marianne_S on 2007-11-25
ha fixed it by copying the gspca-source from usr/src to Desktop and then following the instructions here (changing tar -zxvf  to tar xfvj ) - and now my camera sort of works in camorama (showing upside down - but at least showing a picture) - but i can't make it work with skype beta - which is what i wanted in the first place. anybody knows how to do that? (my camera is philips spc315)

---

### Post by philinux on 2007-11-25
Try it in kopete

---

### Post by Marianne_S on 2007-11-25
installed it and the camera works nicely in kopete - cept the picture is still upside down though. - anyways - thank you :D - it is a great start hooray!

but i still would love to be able to make it work in skype beta - so if anyone knows how to i'd be super happy

also if anyone knows why the picture is showing upside down and how to fix that i'd be super super grateful!

---

### Post by philinux on 2007-11-25
you could turn the camera upside down. :lolflag:

No seriously I treid to get kopete to do the mirror image thing and it just ignores me.

---

### Post by Marianne_S on 2007-11-25
haha funny ... ;P

---

### Post by defenestratos on 2008-05-27
have a look under troubleshooting

[https://help.ubuntu.com/community/Spca5xx#head-032065f8a5fb6a485a7985ddb3a40262a0629fe5](https://help.ubuntu.com/community/Spca5xx#head-032065f8a5fb6a485a7985ddb3a40262a0629fe5)

---

