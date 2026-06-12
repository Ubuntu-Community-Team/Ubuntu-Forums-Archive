---
title: "XGL/Compiz installation - ATIx1400/Dapper686"
date: 2006-10-08
forum: Absolute Beginner Talk
---

### Post by Edowardo on 2006-10-08
I'm currently having difficulties in installing, configuring and running Xgl's awesome gui interface. Before I continue I'll explain what I have.

IBM T60 Laptop
Intel Duo 2GHz
2GB DDR2 Ram
ATI Mobile x1400
Ubuntu, Kernel 2.6.15-27-686 & fully updated

I'm the freshest meat you can buy when it comes to being new to linux. So please be patient with me. With that said, I have gone through about 10 or so guides on how to install and run Xgl properly. So far each has failed for me, or I am terrible with instructions, or a combo of both. There is one guide that has worked half way through; so I'll post what I've done so far.

**STEP 1:**
_Installed and updated ATI x1400 - Method 2_:
[http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_new_8.29.6_drivers_in_Ubuntu_Dapper_Manually)

fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Mobility Radeon X1400 Generic
OpenGL version string: 2.0.6065 (8.29.6)

fgl_glxgears [COLOR="Red"][this won't work under Xgl session][/COLOR]
average 230FPS @ full screen 1400x1050

[COLOR="Red"]Note:[/COLOR]
Under Xgl sesison ATI Control gives an error message:
*“Driver does not provide the FireGL X11 extensions! Panel components will operate only partially”*
In fact, no components are available....

**STEP 2:**
_Installed Xgl - Method A_:
[https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)

**STEP 3:**
_Compiz [COLOR="Red"][Nothing works, far as i got][/COLOR]_
[https://help.ubuntu.com/community/CompositeManager/InstallingCompiz](https://help.ubuntu.com/community/CompositeManager/InstallingCompiz)

After installing Xgl and logging into the Xgl session I attempted to apt-get install compiz. They installed, I think, but that's it. They will not update, nor start up. I tried everything in the above link, word for word.

Any idea what maybe the problem?

Thank you for your help.

-Edo

---

### Post by jordanmthomas on 2006-10-08
If you've tried all that and still are having trouble you may want to wait for Edgy to come out, upgrade to it, and then install beryl.

[http://wiki.beryl-project.org](http://wiki.beryl-project.org)  has some instructions, but they won't work for Dapper any more.

---

### Post by redDEADresolve on 2006-10-08
Can't use compiz guides anymore, use this Beryl guide I made. It's pretty similar to ones on the net but it's completely idiot proof. You got the ATI driver part right...

Update System
Code:
sudo apt-get update
sudo apt-get dist-upgrade


-Prepare and update repositories:
Code:
sudo gedit /etc/apt/sources.list


-Add quinstorms' and reggaemanus' repositories to /etc/apt/sources.list
Code:
deb [http://www.beerorkid.com/compiz/](http://www.beerorkid.com/compiz/) dapper main
deb [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main
deb-src [http://xgl.compiz.info/](http://xgl.compiz.info/) dapper main


-Download and import the gpg key for quinnstorms repository
Code:
wget [http://www.beerorkid.com/compiz/quinn.key.asc](http://www.beerorkid.com/compiz/quinn.key.asc) -O - | sudo apt-key add -

-update your sources
Code:
sudo apt-get update

-Install Packages
Code:
sudo apt-get install  xserver-xgl libgl1-mesa xserver-xorg libglitz-glx1 beryl beryl-core beryl-manager beryl-plugins beryl-plugins-data beryl-settings emerald emerald-themes

-Modify /etc/gdm/gdm.conf-custom
Code:
sudo gedit /etc/gdm/gdm.conf-custom

-look for [servers] and paste this under it:
# Override display 1 to use Xgl (DISPLAY 1 IMPORTANT FOR ATI FGLRX). 
1=Xgl 

[server-Xgl] 
name=Xgl server 
command=/usr/bin/Xgl :1 -fullscreen -ac -accel glx:pbuffer -accel xv:pbuffer
flexible=true

-Modify /etc/gdm/gdm.conf 
Code:
sudo gedit /etc/gdm/gdm.conf
From:
0=Standard
#1=Standard
To:
#0=Standard
1=Standard

In same document:
-Go to line 198 and change GdmXserverTimeout=10 to  (this one is very important!!!)
and change it to"
GdmXserverTimeout=50

-add "/usr/bin/beryl-manager" to gnome session startup programs ( go to system , preferences , sessions and select the startup programs tab.)

-or make a launcher with the command "beryl-manager" and you can lauch Beryl at any time if you don't always want to load into Beryl and tax your system resources. (right click Ubuntu's menu bar aka the Ubuntu start menu, find the system tools icon, click it, go to file, selcet new entry, and create your launcher)

Update System
Code:
sudo apt-get update
sudo apt-get dist-upgrade

Enjoy the eyecandy

---

### Post by Edowardo on 2006-10-09
It installed! Finally! But it won't work..? Everything launches, but I see no cube or any of the pretty effects. I reinstalled linx just for the heck of it, to see if anything changes, nothing.

At the moment the operating system is very slow and is very choppy. When things load or move too fast across the desktop, the windows are slashed diagonally for a second or so. I also tried turning off _all_ effects in the Beryl Manager; nothing changes. I assume this has something to do with the video drivers?

It appears that everything is being software rendered.... One hint of this is I see both my CPU cores spike when anything requires rendering.

This is what I got:

**fglrxinfo**
Error: unable to open display :0

**fgl_glxgears**
Using GLX_SGIX_pbuffer
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
Error: couldn't get fbconfig

Also under the ATI controls I get this warning window:

*[COLOR="Red"]"Driver does not provide the FireGL X11 extensions! Panel components will operate only partially."[/COLOR]*

Once in the ATI controls nothing is available not even the informaiton on the card. Everything is unavailable.


Thank you again for your help!

---

### Post by Edowardo on 2006-10-12
I figured I'd revive this thread at least once to see if anyone else may have an answer. If not within 48 hours I'll remove this.

Thank you.

---

### Post by richtl on 2006-10-29
I'm having the same problem. DRI (and acceleration) works fine on screen 0, but fglrxinfo yields the following on screen 1:

Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI MOBILITY FireGL V5200 Pentium 4 (SSE2) (FireGL) (GNU_ICD)
OpenGL version string: 2.0.6011 (8.28.8)

---

### Post by Danyl on 2006-10-30
Hi guys/gals

I'm a noob having troubles with this How To.

I was following everything fine until this point:

"In same document:
-Go to line 198 and change GdmXserverTimeout=10 to (this one is very important!!!)
and change it to"
GdmXserverTimeout=50"

In my "gdm.conf" document, it doesn't go as far as line 198. My line's end at 72.

Where have I gone wrong?

I basically skipped this step to see what would happen, now when I boot up, it doesn't log into Gnome, it just keeps sending me back to the login screen.

Help!

---

### Post by Lunar_Lamp on 2006-10-31
I think you will just need to find the line that says "GdmXserverTimeout" and edit that.

---

### Post by GeneM on 2006-11-19
Try the command 

fgl_glxgears -display :0.0

and see if it doesn't work for you.  It worked for me.

---

