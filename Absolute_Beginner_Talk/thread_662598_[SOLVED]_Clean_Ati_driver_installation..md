---
title: "[SOLVED] Clean Ati driver installation."
date: 2008-01-09
forum: Absolute Beginner Talk
---

### Post by rhc on 2008-01-09
I'm really confused.
Done something with some written things on some sites but i couldn't managed it i think.
I have some problems with my Ati driver i see.
Some transitions are slow and games for ex. Wolfenstein:enemy territory don't work. Don't start.

Now,how can i make a clean installation.
From zero.
Can someone tell me?
I'm very confused with xgl,fglrx bla bla...
What should i do?
I downloaded "ati-driver-installer-8.443.1-x86.x86_64"...
So then?

---

### Post by talsemgeest on 2008-01-09
Just go System>Administration>Restricted Drivers Manager and tick the ati driver. By far the easiest way. If that doesnt work and you need more help I'll post the harder instructions.

---

### Post by Pevichaey5 on 2008-01-09
save the driver to your desktop

then change to root
su
password

cd Desktop
chmod +x ati*.run
./ati*.run

then follow the wizzard taking all default options 
then still as root
aticonfig --initial

then reboot

if you want the ati catalyst control centre, follow mine, otherwise do what talsemgeest

---

### Post by rhc on 2008-01-09
> **thexero said:**
> save the driver to your desktop

then change to root
su
password

cd Desktop
chmod +x ati*.run
./ati*.run

then follow the wizzard taking all default options 
then still as root
aticonfig --initial

then reboot

Should i untick the restricted driver manager before?

---

### Post by Pevichaey5 on 2008-01-09
yea

i have official ati drivers for my graphics card in my laptop just for the catalyst control centre else using the restricted drivers manager is alot simpler

---

### Post by rhc on 2008-01-09
su
Password: 
su: Authentication failure
Sorry.


ANd what is this?

---

### Post by Pevichaey5 on 2008-01-09
what is the root password for you system?

type that is

else

System>>Administration>>Users and Groups>>root>>Properties

change the password here

---

### Post by rhc on 2008-01-09
Will the restricted manager will stay unticked always from now on after i install driver?

---

### Post by rhc on 2008-01-09
aticonfig --initial
Found fglrx primary device section
Nothing to do, terminating.

ANd this?

---

### Post by Pevichaey5 on 2008-01-09
if doesn't really matter, but mine isn't ticked with the ati driver installed

---

### Post by Pevichaey5 on 2008-01-09
just reboot

then it should be working fine with full 3d support

---

### Post by rhc on 2008-01-09
Does my problem here?,
[http://img137.imageshack.us/img137/1382/screenshot1yy9.png](http://img137.imageshack.us/img137/1382/screenshot1yy9.png)

Because after reboot,still same slowing problems even i m carrying windows.
When i want to clear that thing over in the pic. it gives an error like below.
I can'T reinstall it either.

E: xorg-driver-fglrx: subprocess post-removal script returned error exit status 2

---

### Post by rhc on 2008-01-09
Now i can't tick restricted manager either.
It gives the same error.

---

### Post by Pevichaey5 on 2008-01-09
that is the driver in the restricted drivers manager, do you have other resolutions availabe now

---

### Post by rhc on 2008-01-09
Yes desktop resolutions are there.

[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide#Method_2:_Install_the_Catalyst_7.12_Driver_Manually)
Before i asked here,i tried to do things here.
Manual configuration.
Did i do it wrong?
Maybe somthing that shouldn't be done or deleted?

---

### Post by Pevichaey5 on 2008-01-09
what happens when u type this into terminal

fglrxinfo

can you paste the output here

---

### Post by rhc on 2008-01-09
It turned to a screen like a Dos screen and turned to the logon screen after. :) :)
nothing written in terminal. Enter and logon again :)

---

### Post by rhc on 2008-01-09
> **rhc said:**
> It turned to a screen like a Dos screen and turned to the logon screen after. :) :)
nothing written in terminal. Enter and logon again :)

Did i blacklisted it or something?

---

### Post by Pevichaey5 on 2008-01-09
omg

this is getting confusing lol i never had any of these problems when i installed the driver

sudo gedit
password

file>>open>>/etc/usplash.conf
change the resolution here to like 800x600

---

### Post by rhc on 2008-01-09
> **thexero said:**
> omg

this is getting confusing lol i never had any of these problems when i installed the driver

sudo gedit
password

file>>open>>/etc/usplash.conf
change the resolution here to like 800x600

I did it.

---

### Post by Dreamlocked on 2008-01-09
> **thexero said:**
> save the driver to your desktop

then change to root
su
password

cd Desktop
chmod +x ati*.run
./ati*.run

then follow the wizzard taking all default options 
then still as root
aticonfig --initial

then reboot

if you want the ati catalyst control centre, follow mine, otherwise do what talsemgeest

Running the .run file never worked for me.
If you're having problems with it, try the [unofficial wiki]("http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide").
Method 2 should work, though ati drivers are infamous for their bugs.

---

### Post by rhc on 2008-01-09
This is when i click ati catalyst control center.

[http://img209.imageshack.us/img209/6096/screenshot2cm1.png](http://img209.imageshack.us/img209/6096/screenshot2cm1.png)

---

### Post by rhc on 2008-01-09
As i said before,i think messed up things in that wiki.
in manual installation.
Should i try again?

---

### Post by Dreamlocked on 2008-01-09
> **rhc said:**
> As i said before,i think messed up things in that wiki.
in manual installation.
Should i try again?

Hmm, well, I had to try 3 times before it worked.
Be sure to follow the instructions closely.

Also, in the guide, after the 
```

sudo rm /usr/src/fglrx-kernel*.deb

```

I had to add 
```

sudo dkms remove -m fglrx -v 8.443.1 --all

```
(assuming you are installing 8.443.1 aka 7.12)

---

### Post by rhc on 2008-01-09
I think it s allright.
At least it seems that way.
Thanks both of you very much.

---

### Post by rhc on 2008-01-09
ABout Wolfenstein,

> /Games/Enemy$ ./et.x86
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/furkan/.etwolf/etmain
/home/furkan/Games/Enemy/etmain/pak2.pk3 (22 files)
/home/furkan/Games/Enemy/etmain/pak1.pk3 (10 files)
/home/furkan/Games/Enemy/etmain/pak0.pk3 (3725 files)
/home/furkan/Games/Enemy/etmain/mp_bin.pk3 (6 files)
/home/furkan/Games/Enemy/etmain

----------------------
3763 files in pk3 files
^3WARNING: profile.pid found for profile 'Rhc' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/Rhc/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Received signal 11, exiting...


It gives an error like this.
What is this?
What is missing?

It said "You are using software Mesa (no hardware acceleration)!   " 

?? so

---

### Post by Dreamlocked on 2008-01-09
> **rhc said:**
> ABout Wolfenstein,

It gives an error like this.
What is this?
What is missing?

It said "You are using software Mesa (no hardware acceleration)!   " 

?? so

Did you do ?
```

sudo aticonfig --initial

```

If yes, try this :
Open a terminal and run
```

gksu gedit /etc/X11/xorg.conf

```

Scroll down to :
```

Section "Device"
	Identifier  "aticonfig-Device[0]"
	Driver      "mesa"
        ...
EndSection

```

And replace mesa with fglrx.

Reboot.

---

### Post by rhc on 2008-01-09
When i do this sudo aticonfig --initial
> 
sudo aticonfig --initial
[sudo] password for furkan:
Found fglrx primary device section
Nothing to do, terminating. this is the result.
Is there a problem here?

---

### Post by rhc on 2008-01-09
> Section "Device"
	Identifier	"ATI Technologies Inc RV350 AP [Radeon 9600]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

And this is that.

---

### Post by Dreamlocked on 2008-01-09
What does it say when you type :
fglrxinfo

in a terminal?

---

### Post by rhc on 2008-01-09
> fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI RADEON 9600 Series
OpenGL version string: 2.1.7170 Release


But i wanna say again,when i click ati catalyst control manager from applications,

[http://img209.imageshack.us/img209/6096/screenshot2cm1.png](http://img209.imageshack.us/img209/6096/screenshot2cm1.png)

This is the result

---

### Post by Dreamlocked on 2008-01-09
Hmm, maybe try 

```

sudo mkdir /lib/modules/$(uname -r)/volatile
sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko

```

I'm just re-reading the guide really. Not quite sure what the problem is.

EDIT : You can also try installing with [Envy]("http://www.albertomilone.com/nvidia_scripts1.html"). Supposedly works better for some people. However, I  have never tried it myself, so can't help more with that.

---

### Post by rhc on 2008-01-09
this is the result 
> 
furkan@Furkan:~$ sudo mkdir /lib/modules/$(uname -r)/volatile
[sudo] password for furkan:
mkdir: cannot create directory `/lib/modules/2.6.22-14-generic/volatile': File exists
furkan@Furkan:~$ sudo ln -sf /lib/modules/$(uname -r)/misc/fglrx.ko /lib/modules/$(uname -r)/volatile/fglrx.ko
furkan@Furkan:~$ 


---

### Post by Dreamlocked on 2008-01-09
I take it acceleration still doesn't work after a reboot?

---

### Post by Pevichaey5 on 2008-01-09
there are problems with the ati drivers at the moment, but the restricted drivers manager works ok, the only reason i have the ati driver is for the catalyst control centre, if you aren't going to use it, i would use the restricted drivers manager, its alot simpler to install and you shouldn't be having these problems

---

### Post by Dreamlocked on 2008-01-09
Before doing what the above user suggested, remember that you have blacklisted the restricted-drivers in the wiki, so you'll need to undo that step.

```

DISABLED_MODULES="fglrx"

```
-->
```

DISABLED_MODULES=""

```

---

### Post by rhc on 2008-01-09
I m trying envy now and i ll tell you the result.

---

### Post by rmcder on 2008-01-09
Envy worked ok for me, but I haven't been able to get the 1680x1050 resolution working.  Also, after using Envy, the box in the restricted driver manager should be left unchecked - it says driver is in use (ati), but restricted driver is not.  That's the way it should be.

---

### Post by Dreamlocked on 2008-01-09
You can't use 1680x1050 resolution. It's a known bug for version 7.12 of the ati drivers.
Hopefully they will fix it this month.

---

### Post by rhc on 2008-01-09
> furkan@Furkan:~/game$ ./et.x86
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/furkan/.etwolf/etmain
/home/furkan/game/etmain/pak2.pk3 (22 files)
/home/furkan/game/etmain/pak1.pk3 (10 files)
/home/furkan/game/etmain/pak0.pk3 (3725 files)
/home/furkan/game/etmain/mp_bin.pk3 (6 files)
/home/furkan/game/etmain

----------------------
3763 files in pk3 files
^3WARNING: profile.pid found for profile 'Rhc' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/Rhc/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!   
 Driver DLL used: libGL.so.1
 If this is intentional, add
       "+set r_allowSoftwareGL 1"
 to the command line when starting the game.
***********************************************************
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Xlib:  extension "XFree86-VidModeExtension" missing on display ":1.0".
Received signal 11, exiting...
furkan@Furkan:~/game$ 



Envy made it very easy.
And i think no problem,good program.
But wolfenstein gave the problem above again.
I ll say it s about the game but it s funny that i opened this game this morning.
But it had very poor performance,not poor only also bad graphics and i decided to install newer driver,but i m trying for hours.
Things gone bad.
I love that game so much. :)

---

### Post by Pevichaey5 on 2008-01-09
whats the game, i wanna try it now lol

---

### Post by rhc on 2008-01-09
The game is WOlfenstein:Enemy Territory,
but i love it s mod.
Named true combat elite,

[http://www.truecombatelite.net/component/option,com_remository/Itemid,40/](http://www.truecombatelite.net/component/option,com_remository/Itemid,40/)

it s a very good game like counter-strike but much more realistic.
Not a child game like it :)

---

### Post by Pevichaey5 on 2008-01-09
nice

glad your graphics is working properly now

have fun

---

### Post by rhc on 2008-01-09
Thank you so much but i can't play the game still. :)

---

### Post by rhc on 2008-01-09
I want to try my luck again this evening.
What is the problem here with Wolfenstein Enemy Territory game.

> furkan@Furkan:~/game$ ./et.x86
ET 2.60 linux-i386 Mar 10 2005
----- FS_Startup -----
Current search path:
/home/furkan/.etwolf/etmain
/home/furkan/game/etmain/pak2.pk3 (22 files)
/home/furkan/game/etmain/pak1.pk3 (10 files)
/home/furkan/game/etmain/pak0.pk3 (3725 files)
/home/furkan/game/etmain/mp_bin.pk3 (6 files)
/home/furkan/game/etmain

----------------------
3763 files in pk3 files
^3WARNING: profile.pid found for profile 'Rhc' - system settings will revert to defaults
execing default.cfg
couldn't exec language.cfg
execing profiles/Rhc/etconfig.cfg
couldn't exec autoexec.cfg
Hunk_Clear: reset the hunk ok

------- Input Initialization -------
Joystick is not active.
------------------------------------
Bypassing CD checks
----- Client Initialization -----
----- Initializing Renderer ----
-------------------------------
----- Client Initialization Complete -----
----- R_Init -----
...loading libGL.so.1: Initializing OpenGL display
...setting mode 4: 800 600
Xlib: extension "XFree86-VidModeExtension" missing on display ":1.0".
Using 8/8/8 Color bits, 24 depth, 0 stencil display.
GL_RENDERER: Mesa GLX Indirect


************************************************** *********
You are using software Mesa (no hardware acceleration)! 
Driver DLL used: libGL.so.1
If this is intentional, add
"+set r_allowSoftwareGL 1"
to the command line when starting the game.
************************************************** *********
...WARNING: could not set the given mode (4)
Initializing OpenGL display
...setting mode 3: 640 480
Xlib: extension "XFree86-VidModeExtension" missing on display ":1.0".
Received signal 11, exiting...
furkan@Furkan:~/game$

---

### Post by Pevichaey5 on 2008-01-09
thats a real s**t you got no hardware acceleration

i installed the demo for wolfenstein but it crashes when i try to connect to a server lol so i haven't played it yet lol

---

### Post by rhc on 2008-01-09
:) 
thexero download "true combat:elite" mode.
It's the point :)

---

### Post by rhc on 2008-01-09
GL_RENDERER: Mesa GLX Indirect


***********************************************************
 You are using software Mesa (no hardware acceleration)!  


Why do i have Mesa,i can't find.
Really annoying.
Do i have to reinstall Ubuntu...?
Pff.

---

### Post by Pevichaey5 on 2008-01-09
while u are installin the ati driver, do you get any error message or anything?

i would if i were u

---

### Post by rhc on 2008-01-09
Exactly i think i need to clean the file org-driver-fglrx version 8.443.1 but i can't clean it.
If i can delete it or i can find the version 8.37.6 i will solve this.
Because when i want clean uninstalltion to use the driver from restricted driver manager,i can't clean that file,or install the 8.37 version?
How can i install old file.
I think i have some problems with new ones.

---

### Post by rhc on 2008-01-09
now i'm installing the old ones,driver version 7.10.= 8.37.6
We ll see...

---

