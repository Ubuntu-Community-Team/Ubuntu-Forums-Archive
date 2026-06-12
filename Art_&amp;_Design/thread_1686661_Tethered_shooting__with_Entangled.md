---
title: "Tethered shooting  with Entangled"
date: 2011-02-12
forum: Art &amp; Design
---

### Post by ElSlunko on 2011-02-12
Hello Ubuntu / Linux photographers.

Just wanted to bring up a piece of software I found out about today but couldn't find mentioned here in the forums (Maybe under it's former named capa).

From the website :

> Entangle provides a graphical interface for “tethered shooting”, aka taking photographs with a digital camera completely controlled from the computer.

Using Entangle is as easy as 1,2,3…

    Connect camera
    Launch Entangle
    Shoot photos

With a sufficiently capable digital SLR camera Entangle allows:

    Trigger the shutter from the computer
    Live preview of scene before shooting
    Automatic download and display of photos as they are shot
    Control of all camera settings from computer

Entangle is Open Source software licensed under the GNU GPL v3+. It is built on top of libgphoto using GTK-2 for its interface. It is fully colour managed, auto-detecting system monitor profile and applying the neccessary transforms when displaying images.


[http://entangle-photo.org](http://entangle-photo.org)

Live view works on my D90. Very useful if you're looking for just a tethering option and no asset manager behind it.

---

### Post by robert shearer on 2011-02-13
Fine for canikon users.
Here's one for  Pentax DSLRs

[http://sourceforge.net/projects/pktriggercord/](http://sourceforge.net/projects/pktriggercord/)

---

### Post by juilen_perth on 2011-05-16
Hi,
Ive been trying to install this software for a couple of weeks on Natty.
I can ./configure (after installing the required packages)

But when I sudo make  I get the following error

make  all-recursive
make[1]: Entering directory `/home/robin/Downloads/entangle-0.1.0'
Making all in src
make[2]: Entering directory `/home/robin/Downloads/entangle-0.1.0/src'
make  all-am
make[3]: Entering directory `/home/robin/Downloads/entangle-0.1.0/src'
g-ir-compiler \
        --includedir=. \
        --includedir=. \
        -o GPhoto-2.0.typelib GPhoto-2.0.gir
/bin/bash: line 1: g-ir-compiler: command not found
make[3]: *** [GPhoto-2.0.typelib] Error 127
make[3]: Leaving directory `/home/robin/Downloads/entangle-0.1.0/src'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/robin/Downloads/entangle-0.1.0/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/robin/Downloads/entangle-0.1.0'
make: *** [all] Error 2
robin@netbook:~/Downloads/entangle-0.1.0$ 

Anyone able to assist or identify what is wrong?

I have tried to install everything related g-ir-compiler that I could find.

---

### Post by BLTicklemonster on 2011-07-13
I have installed pktriggercord, but I have no idea how to bring it up. I entered pktriggercord into the terminal, and nothing happens.

I don't see it in applications menu - graphics. 

Wonder what I do?

---

### Post by robert shearer on 2011-07-13
pktriggercord,  have a look in your home folder and see if there is a pktriggercord folder then click on that.

Edit, ignore the above in light of the following posts.
run using command ```
pktriggercord
``` or ```
sudo pktriggercord
``` if your camera is not recognised by the program but does show if you run ```
lsusb
```

---

### Post by BLTicklemonster on 2011-07-13
I checked back, it won't compile because I don't have libglade2 or something. Bah.

---

### Post by robert shearer on 2011-07-13
Keep at it as it does work. :)
I had the same problems and contacted the developer who provided this info to get it running .....

Install the package    **libglade2-dev**  from the Ubuntu repositories and compile again.

Once installed you **may** have to run it using sudo as it may not recognise your camera otherwise.

---

### Post by BLTicklemonster on 2011-07-14
Well, I got this,

```
bill@bill:~/pktriggercord$ make 
cc -O3 -g -Wall -fPIC -c pslr_scsi.c
In file included from pslr_scsi.c:29:
pslr_scsi_linux.c: In function &#8216;get_drive_info&#8217;:
pslr_scsi_linux.c:96: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
pslr_scsi_linux.c:104: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
cc -O3 -g -Wall -fPIC -c pslr.c
cc -O3 -g -Wall -fPIC -c pslr_lens.c
cc -O3 -g -Wall pktriggercord-cli.c pslr.o pslr_scsi.o pslr_lens.o  -DVERSION='"0.76.00"' -o pktriggercord-cli -L. 
pktriggercord-cli.c: In function &#8216;save_buffer&#8217;:
pktriggercord-cli.c:482: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
Package libglade-2.0.1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0.1' found
Package libglade-2.0.1 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libglade-2.0.1.pc'
to the PKG_CONFIG_PATH environment variable
No package 'libglade-2.0.1' found
cc -O3 -g -Wall   -DVERSION='"0.76.00"' -DDATADIR=\"/usr/local/share/pktriggercord\" pktriggercord.c pslr.o pslr_scsi.o pslr_lens.o  -o pktriggercord -L. 
pktriggercord.c:29: fatal error: gtk/gtk.h: No such file or directory
compilation terminated.
make: *** [pktriggercord] Error 1
```

but sudo make install didn't give me any errors.

But when I try to run it from the command line, I get this:

```
bill@bill:~$ pktriggercord
pktriggercord: command not found
```


and

```
bill@bill:~$ pktriggercord-cli
Segmentation fault
```

So something ain't jiving.

I wish there were more documentation, or a list of specific dependencies. I tried installing gtk2hsbuildtools, and gtkam, etc, but to no avail.

I'm running 64 bit, but I don't think that's the problem, is it?

---

### Post by robert shearer on 2011-07-14
from your output...
> Package libglade-2.0.1 was not found in the pkg-config search path.

If you have installed libglade2-dev as per my last post then reboot and compile again.
(looks like the package hasn't yet been added to the software list)

cheers, Bob.

what version of Ubuntu are you running ?

O.K.... I just re-downloaded pktriggercord from their sourceforge page  and moved it to a folder on  the desktop then cd to that folder  (read the install file....  > /ppkTriggerCord installation (you need root privileges for 'make install')

make clean
make
make install
so for Ubuntu the last command is ```
sudo make install
```

all compiles (I have libglade2-dev installed)
(can pm you the full output if that would help ?)

Then start the app by alt+F2 and typing pktriggercord

Just done now all ok using Ubuntu natty 32-bit.
Have it on another machine under 10.10
haven't tried with 10.04.

cheers, Bob

---

### Post by BLTicklemonster on 2011-07-14
Sorry, when I first tried, I downloaded the latest libglade, and it was 2.0.1, so I edited makefile (I'd done that before to get stuff to compile). 

I just edited it back to 2.0 and did it all again, and voila!!! No error.

Until ...

```
bill@bill:~$ pktriggercord
/usr/share/themes/exotic/gtk-2.0/gtkrc:336: error: invalid string constant "theme-menu-

widget_class ", expected valid string constant
Segmentation fault
```

Durnit. 

Looked great for a second there!

**And I do appreciate your help! Thank you!!** We're running a photo business, sort of, on the side, and I don't want to ever use Windows for the business, only Ubuntu. We use gimp, I downloaded darktable and am checking it out (really cool) and though we have a new laptop and I could easily run stuff on it in windows, I'd rather run stuff in ubuntu when we ever have to turn it on and use it.

So I wonder what that widget class was, and why it caused a segmentation fault? :(


OH, and I'm running 10.10 64 bit on this machine, and 32 bit on the laptop and the other desktop.

---

### Post by BLTicklemonster on 2011-07-14
Don't tell me the theme I'm using is stopping me from using it... I'll change and see.

Nope, that's not it, I just get a plain old segmentation fault now.

---

### Post by robert shearer on 2011-07-14
Hmmm, now I am about at the limit of my knowledge with this app and I am afraid I do not know what may be giving you trouble.

I do know that on my vanilla installs of 10.10 and 11.04 it works fine.

Perhaps the time has come for you to contact Andras the developer...
[http://sourceforge.net/project/memberlist.php?group_id=394488](http://sourceforge.net/project/memberlist.php?group_id=394488)

cheers, Bob.

Great to hear you are running a studio with opensource software !.
What pentax camera ? and are you a member of the Pentax forums...[http://www.pentaxforums.com/forums/](http://www.pentaxforums.com/forums/)
(search for 'tethering' there)

Depending on camera model you may be able to run the other apps that have the same functionality...
pkremote... [http://pkremote.sourceforge.net/](http://pkremote.sourceforge.net/)

---

### Post by BLTicklemonster on 2011-07-14
I'm using the K-x, my wife has a Canon Xsi and a T2i (no idea why I bought her a T2-i for Valentine's, other than she's cute wearing it around her neck...).

I have gotten PK Tether.exe to run in Wine, yay!

But nothing happens.

I wish fspot or whatever would tether....

I'll contact Andras, see what he has to say.

Thanks for all your help. Maybe it's just a 64 bit problem.

and I know PK stuff is only for pentax, I was just mentioning her cameras, too.

---

### Post by jelina on 2011-07-14
I have installed pktriggercord, but I have no idea how to bring it up. I  entered pktriggercord into the terminal, and nothing happens. We're running a photo business, sort of, on the side, and I don't want  to ever use Windows for the business, only Ubuntu. We use gimp, I  downloaded darktable and am checking it out (really cool) and though we  have a new laptop and I could easily run stuff on it in windows, I'd  rather run stuff in ubuntu when we ever have to turn it on and use it.

---

### Post by BLTicklemonster on 2011-07-14
> **jelina said:**
> I have installed pktriggercord, but I have no idea how to bring it up. I  entered pktriggercord into the terminal, and nothing happens. We're running a photo business, sort of, on the side, and I don't want  to ever use Windows for the business, only Ubuntu. We use gimp, I  downloaded darktable and am checking it out (really cool) and though we  have a new laptop and I could easily run stuff on it in windows, I'd  rather run stuff in ubuntu when we ever have to turn it on and use it.

??? I've met my doppelganger!!! Good luck with your business!

---

### Post by BLTicklemonster on 2011-07-14
Robert, I just downloaded and rebooted, and started over again. 

make clean
make
sudo make install

I got this when I ran make:

```
bill@bill:~/pktriggercord-0.76.00$ make
cc -O3 -g -Wall -fPIC -c pslr_scsi.c
In file included from pslr_scsi.c:29:
pslr_scsi_linux.c: In function &#8216;get_drive_info&#8217;:
pslr_scsi_linux.c:96: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
pslr_scsi_linux.c:104: warning: ignoring return value of &#8216;read&#8217;, declared with attribute warn_unused_result
cc -O3 -g -Wall -fPIC -c pslr.c
cc -O3 -g -Wall -fPIC -c pslr_lens.c
cc -O3 -g -Wall pktriggercord-cli.c pslr.o pslr_scsi.o pslr_lens.o  -DVERSION='"0.76.00"' -o pktriggercord-cli -L. 
pktriggercord-cli.c: In function &#8216;save_buffer&#8217;:
pktriggercord-cli.c:482: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result
cc -O3 -g -Wall -pthread -I/usr/include/gtk-2.0 -I/usr/lib/gtk-2.0/include -I/usr/include/atk-1.0 -I/usr/include/cairo -I/usr/include/gdk-pixbuf-2.0 -I/usr/include/pango-1.0 -I/usr/include/gio-unix-2.0/ -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include -I/usr/include/pixman-1 -I/usr/include/freetype2 -I/usr/include/libpng12 -I/usr/include/libglade-2.0 -I/usr/include/libxml2   -pthread -lglade-2.0 -lgtk-x11-2.0 -lxml2 -lgdk-x11-2.0 -latk-1.0 -lgio-2.0 -lpangoft2-1.0 -lpangocairo-1.0 -lgdk_pixbuf-2.0 -lm -lcairo -lpng12 -lpango-1.0 -lfreetype -lfontconfig -lgobject-2.0 -lgmodule-2.0 -lgthread-2.0 -lrt -lglib-2.0   -DVERSION='"0.76.00"' -DDATADIR=\"/usr/local/share/pktriggercord\" pktriggercord.c pslr.o pslr_scsi.o pslr_lens.o  -o pktriggercord -L. 
pktriggercord.c: In function &#8216;auto_save_check&#8217;:
pktriggercord.c:1028: warning: ignoring return value of &#8216;chdir&#8217;, declared with attribute warn_unused_result
pktriggercord.c: In function &#8216;save_buffer&#8217;:
pktriggercord.c:1929: warning: ignoring return value of &#8216;write&#8217;, declared with attribute warn_unused_result

```

That was the only place I saw any errors or warnings whatsoever. 

I still get the segmentation fault.

Here's debug:

```
bill@bill:~/pktriggercord-0.76.00$ pktriggercord --debug
/usr/share/themes/exotic/gtk-2.0/gtkrc:336: error: invalid string constant "theme-menu-

widget_class ", expected valid string constant
Create glade xml
init_preview_area
bufferwindow expose
Checking drive: ATA     
&#65533;)&#65533; WDC WD6401AALS-0

Checking drive: HL-DT-ST
&#65533;)&#65533; DVD-RAM GH22NS30

Segmentation fault

```

---

### Post by robert shearer on 2011-07-14
The 'errors' during make seem the same as I have had each time I compiled but do not affect the outcome so I have ignored them.
Will check the output (I saved it last night) when I get home today but I think you can safely ignore those.
)**Edit:** checked my output and it is the same as yours.)

As far as the segmentation fault it does seem to involve your theme.
I take it you are using a theme other than the official one ?

Again I would point out that I have no idea if pktriggercord works with 10.04 but as it makes ok then perhaps it has all dependencies satisfied.

Do you have spare space on drives in either of your machines ?

If so consider installing 11.04 **alongside** your existing install then add libglade2-dev and download and compile pktriggercord as I know that works . 
This would rule out all variables we know not of that may be affecting its execution in your current install.

Alternatively if you have enough ram you could run 11.04 in a virtual machine and try installing  pktriggercord there.
Virtualbox should do it.

---

### Post by BLTicklemonster on 2011-07-15
Bleh. I'll test it on the laptop and the other desktop first. If nothing works, I'll try 11. Thanks for the support, Robert.

Oh, and check this, I changed themes, and all I get now is 

bill@bill:~$ pktriggercord
Segmentation fault

---

### Post by BLTicklemonster on 2011-07-15
Ugh, it's early.

I forgot, I now get this when I debug:

```
bill@bill:~$ pktriggercord --debug
Create glade xml

(<unknown>:4897): libglade-WARNING **: could not find glade file 'pktriggercord.glade'
init_preview_area
bufferwindow expose
Checking drive: ATA    
&#1350;&#65533;j WDC WD6401AALS-0

Checking drive: HL-DT-ST
&#1350;&#65533;j DVD-RAM GH22NS30

Segmentation fault

```

But pktriggercord.glad is right there in the directory. Why can't it find it? Is there something I can edit to point straight to it? Could this be what's causing the problem?

---

### Post by robert shearer on 2011-07-15
try installing this package....
libgtk2-gladexml-perl
and if you can find something like libgtk2-dev then that too. 
(don't know if the second one exists it is not here on 11.04 but rereading Andras' email he makes mention of a gtk2 package though does not name it)
libgtk2-gladexml-perl looks to address several of the errors you are getting and specifically the xml file creation.

You probably need to install it and recompile so there is a make clean to remove the old configs.

hope this helps.
cheers, bob.

about to leave for work.
Will be a couple of days before I can check back.

---

### Post by BLTicklemonster on 2011-07-15
No -dev file, but I did install, and I still get the segfault. :(

Got to go to work, I'll work on this this weekend. Thanks for your help Robert.

---

### Post by JackDeth on 2011-08-20
I ran across this thread by accident while doing a Google search. I just got done installing Entangle and after a very long time I finally got it up and running. 

I am not a programmer so if you feel like a newbie with all this (like me) I will try to put this in layman's terms and spell it all out. If something is still not clear, I apologize.

What I will tell you folks having problems with installation is to keep your terminal window open but also have Synaptic open as well.

During the ./configure phase it will most likely fail several times. When it fails, usually just look a few lines up from the bottom and it will tell you the name of the package that it needs that is missing. Then go over to Synaptic and search for it. In the list of results the package should show up under it's own name, or it may be part of another package in the list. Mark it for installation plus any other packages of the same name that also end in -dev.  So, for example, if it asks for a package called "xyz" and you find both xyz and xyz-dev, install both of them. Then try your ./configure again.

The next time around it may crash again saying it's looking for another missing package. Basically it's missing several dependencies that most people won't have after a regular install of Ubuntu. So just keep going through this process until it works without errors near the end.

After that part works you need to run "make". Mine also crashed at this point a couple times due to missing -dev packages, etc. Once I installed those, did ./configure over again, and ran "make" again, it worked fine.

If this is clear as mud, I'm sorry. Just post another question if you want further clarification.

---

### Post by VeeDubb on 2011-09-13
The trouble I'm having with entangle is that it locks up almost every time I click on anything.  It looks like a very interesting program, but either it's wildly unstable, or gphoto2 doesn't like my Nikon D300s

---

### Post by BLTicklemonster on 2011-10-09
I installed again since then, and now have pktriggercord installed and it will load up without any errors. 


```
bill@bill-GF6100-M754:~/pktriggercord$ sudo make install
[sudo] password for bill: 
install -d /usr/local/bin
install -s -m 0755 pktriggercord-cli /usr/local/bin/
install -d /etc/udev/rules.d
install -m 0644 pentax.rules /etc/udev/
install -m 0644 samsung.rules /etc/udev/
cd /etc/udev/rules.d;\
	ln -sf ../pentax.rules 025_pentax.rules;\
	ln -sf ../samsung.rules 025_samsung.rules
install -d -m 0755 /usr/local/share/man/man1
install -m 0644 pktriggercord-cli.1 pktriggercord.1 /usr/local/share/man/man1
if [ -e ./pktriggercord ] ; then \
	install -s -m 0755 pktriggercord /usr/local/bin/; \
	install -d /usr/local/share/pktriggercord/; \
	install -m 0644 pktriggercord.glade /usr/local/share/pktriggercord/ ; \
	fi
bill@bill-GF6100-M754:~/pktriggercord$ pktriggercord
bill@bill-GF6100-M754:~/pktriggercord$ pktriggercord
bill@bill-GF6100-M754:~/pktriggercord$ 

```



But I can't get it to detect my camera in msc or ptp.

---

### Post by BLTicklemonster on 2011-10-09
Woo hoo, rebooted, and it works!!!

---

### Post by robert shearer on 2011-10-09
> But I can't get it to detect my camera in msc or ptp.

> Woo hoo, rebooted, and it works!!!

Yep, reboot after install when devices need to be recognised. Glad to hear that it is running.

Out of interest, when you say you "installed again" do you mean reinstalled pktriggercord (ie new version) or reinstalled the o/s and if the latter did you install the same or a newer version..?  Curious.

---

### Post by BLTicklemonster on 2011-10-09
> **robert shearer said:**
> Yep, reboot after install when devices need to be recognised. Glad to hear that it is running.

Out of interest, when you say you "installed again" do you mean reinstalled pktriggercord (ie new version) or reinstalled the o/s and if the latter did you install the same or a newer version..?  Curious.

No sorry, fresh install of Ubuntu 11.04. :O)

---

### Post by BLTicklemonster on 2011-10-09
By the way, I'm using version 0.77.02. I'd be interested to know if the author would be able to create a version that gave the user the ability to take a photo every so many minutes, like if you were wanting to take a 25 second exposure every 3 minutes or something like that. Set it up so you can take one shot (at settings already predetermined) every 3 minutes or so. So you could do time lapse photos. Man, I wish I knew programming. My mind is always working a mile a minute thinking of what if stuff.

---

### Post by arron on 2011-12-23
I would like to chime in on what I had to do do get entangle installed and working.  I had some help from the developer, Daniel Berrange who was quick to get back to me and helpful.

Webpage with source and info:
[http://entangle-photo.org/](http://entangle-photo.org/)

These are the packages needed:

```

libgtk-3-dev
libglade2-dev
libgphoto2-2
libgphoto2-2-dev
libgudev-1.0-dev
libdbus-glib-1-dev
liblcms-dev
libgexiv2-dev
libffi-dev
libpeas-dev
gobject-introspection
```

Commands from source folder:
```

sudo apt-get install libgtk-3-dev libglade2-dev libgphoto2-2 libgphoto2-2-dev libgudev-1.0-dev libdbus-glib-1-dev liblcms-dev libgexiv2-dev libffi-dev libpeas-dev gobject-introspection
./configure --prefix=$HOME/usr
make
make install
### this was a line not documented, the dev says it will be a part of the next release, so may become outdated after release 0.3.0 ###
glib-compile-schemas /home/yourname/usr/share/glib-2.0/schemas

```

And add these lines to your ~/.bashrc, with your proper user name put in:
```

export XDG_DATA_DIRS="/usr/share:/usr/local/share:/home/*username*/usr/share"

```

Log out, then in, and bingo, ~/usr/bin/entangle should work.

Hope this helps someone, seems to be a good app so far with my Canon T6i (600d).

---

### Post by lalelale on 2012-01-27
Nice software, works quite well with my Canon 1000D aka Rebel XS
The instructions above by arron worked perfectly to install the software from source on a freshly installed 11.11
A proper binary package would be very appreciated though :-)

---

### Post by Ubiquitousuk on 2012-02-04
For those who aren't aware, you can get good tethered shooting functionality at the command line using the gphoto2 package. For a broad range of [supported cameras]("http://gphoto.sourceforge.net/proj/libgphoto2/support.php") you can capture a frame and download it to the current directory with the command

```
gphoto2 --capture-image-and-download
```

To shoot a time-lapse with a frame every 45 seconds use
```
gphoto2 --capture-image-and-download --interval 45
```

More commands can be found [here]("http://gphoto.sourceforge.net/doc/manual/ref-gphoto2-cli.html").

---

### Post by dhor on 2012-02-09
Great application...

For those, who wants install in easy way Entangle - use my PPA:

```
sudo add-apt-repository ppa:dhor/myway
sudo apt-get update
sudo apt-get install entangle
```

There's package for Ubuntu 11.10 Oneiric (64/32bit) so far.

---

### Post by rojaasensei on 2012-02-15
> **dhor said:**
> Great application...

For those, who wants install in easy way Entangle - use my PPA:

```
sudo add-apt-repository ppa:dhor/myway
sudo apt-get update
sudo apt-get install entangle
```

There's package for Ubuntu 11.10 Oneiric (64/32bit) so far.

Yes, great PPa

BUT, this morning's entangle update won't install, conflict with, I believe, shotwell as I recall from the error message.

---

### Post by dhor on 2012-02-16
> **rojaasensei said:**
> 
BUT, this morning's entangle update won't install, conflict with, I believe, shotwell as I recall from the error message.

Indeed...  Fix should be available in PPA in two/three hours. ('gschemas.compiled' overwrite curse).

---

### Post by rojaasensei on 2012-02-17
> **dhor said:**
> Indeed...  Fix should be available in PPA in two/three hours. ('gschemas.compiled' overwrite curse).

Just updated entangle.  It was error free!:D

Thank you for your prompt response and action.

Yours is a superb ppa.  Keep up the fantastic efforts.:)

---

