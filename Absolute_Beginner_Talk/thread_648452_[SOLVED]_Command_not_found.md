---
title: "[SOLVED] Command not found?"
date: 2007-12-23
forum: Absolute Beginner Talk
---

### Post by hilariousness16 on 2007-12-23
I am trying to install my ATI driver ( ATI RADEON XPRESS 200M )

My installer is located in /home/linux/documents/ati-driver-installer-8.41.7-x86.x86_64.run

In the terminal, when i type in  /home/linux/documents/ati-driver-installer-8.41.7-x86.x86_64.run , it's fine, but I need to be the " Super-user "

So I did 

sudo  /home/linux/documents/ati-driver-installer-8.41.7-x86.x86_64.run

and it said the command was not found.

---

### Post by dward526 on 2007-12-23
> **hilariousness16 said:**
> I am trying to install my ATI driver ( ATI RADEON XPRESS 200M )

My installer is located in /home/linux/documents/ati-driver-installer-8.41.7-x86.x86_64.run

In the terminal, when i type in  /home/linux/documents/ati-driver-installer-8.41.7-x86.x86_64.run , it's fine, but I need to be the " Super-user "

So I did 

sudo  /home/linux/documents/ati-driver-installer-8.41.7-x86.x86_64.run

and it said the command was not found.

Try sudo sh ati-driver-installer-8.41.7-x86.x86_64.run from your /home/linux/documents/ directory.

---

### Post by shareMenaPeace on 2007-12-23
Hi i exactly have the same card ... i didnt used this way ... i used ENVY, but im not sure what is the best way as compiz works ..but not 100% .... you can get envy from [http://albertomilone.com/wordpress/?cat=12](http://albertomilone.com/wordpress/?cat=12)

But im intrested to hear what is the best way ... you could use restricted drivers too, but currently i got those disabled also catalyst setup isnt working....

---

### Post by hilariousness16 on 2007-12-23
> **dward526 said:**
> Try sudo sh ati-driver-installer-8.41.7-x86.x86_64.run from your /home/linux/documents/ directory.

I am a major noob at this... sorry lol

Do i type in the terminal  sudo  /home/linux/documents/sh ati-driver-installer-8.41.7-x86.x86_64.run

---

### Post by shareMenaPeace on 2007-12-23
Note if you run into startup trouble you can fix this with backing up 

/etc/X11/xorg.conf

todo this you need to open a terminal session from login ..just incase :)

liek 

open terminal than type

cd /etc/X11

than to edit the xorg.conf type

gksudo gedit xorg.conf

now save under a diffrent name ....

---

### Post by jkblacker on 2007-12-23
Try this:
```
sudo sh /home/linux/documents/ati-driver-installer-8.41.7-x86.x86_64.run
```
It should work; you were missing the 'sh' which needs to come after the sudo (sh is the command which was missing).

---

### Post by hilariousness16 on 2007-12-23
I tried ENVY, but when I try to install the package it says 

Error: Dependency is not satisfiable: xserver-xorg-dev

---

### Post by hilariousness16 on 2007-12-23
Ok ty i just forgot the sh part

it's installing now


random questions..

whats the beans
it says i got 1 bean?

---

### Post by GrumpyBob on 2007-12-23
xserver-xorg-dev is in the repos - you could install that first via synaptic

Robert

---

### Post by dward526 on 2007-12-23
1 bean = 1 post :)

---

### Post by shareMenaPeace on 2007-12-23
If you get all running please post later your xorg.conf, thanx

---

### Post by hilariousness16 on 2007-12-23
Ok i finished installing the driver, but when I when to System/Admin/Restriced Driver Manager, I tried to enable my graphics card, it says 

The software source for the package 
xorg-driver-fglrx
is not enabled

Huh :confused:

How do I get the xorg.conf 
lol..

---

### Post by hilariousness16 on 2007-12-23
The card is the only thing not working on my laptop.

---

### Post by hilariousness16 on 2007-12-23
anyone here?

---

### Post by rzrgenesys187 on 2007-12-23
> **hilariousness16 said:**
> Ok i finished installing the driver, but when I when to System/Admin/Restriced Driver Manager, I tried to enable my graphics card, it says 

The software source for the package 
xorg-driver-fglrx
is not enabled

Huh :confused:

How do I get the xorg.conf 
lol..

Give this a shot
```
 sudo apt-get install xorg-driver-fglrx
```

---

### Post by hilariousness16 on 2007-12-23
linux@linux-laptop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists...Done
Building dependency tree
Read state information...Done
E: Couldn't find package xorg-driver-fglrx 

huh what?

---

### Post by OldTimeTech on 2007-12-23
you need to make sure all your repositories are checked.

Go to System->administration->synaptic package manager
then go to settings in Synaptic and open repositories and check 
make sure all are checked.

Then in search of synaptic, type xorg-driver-fglrx and it should find that command or go back to terminal and type in sudo apt-get install xorg-driver-fglrx.

---

### Post by shareMenaPeace on 2007-12-23
You do not need ATI accelerated graphics driver .... at least i dont have this checked...onyl got Atheros Hardware Access Layer ... maybe this is wrong but i remeber havening problem using this ATI accelerateddriver ....

I got everythign working and its very nice :)

---

### Post by shareMenaPeace on 2007-12-23
Do you also use an asus notebook v50 with this ati xpress card? I mean i coudl sent you my xorg.conf ... this file is teh configutation file for your desctop environment....loads all the hardware and acceleration stuff and options

---

### Post by hilariousness16 on 2007-12-23
yay it works now thank you all who had helped :)

Ubuntu Forever!

---

### Post by shareMenaPeace on 2007-12-23
Do you use the restricted driver?

---

### Post by hilariousness16 on 2007-12-23
i don't know if you need the accerlated driver either, but just in case...:lolflag:

---

### Post by hilariousness16 on 2007-12-23
no actually i got a HP dv8000

i didn;'t have internet on my laptop so i think that was the problem... but it's all good now since i've gotten internet

---

### Post by hilariousness16 on 2007-12-23
the driver requires restart

now i can't log onto ubuntu using my username and password :mad:

---

### Post by shareMenaPeace on 2007-12-23
Yes this happen dto me too... this is because of this restricted driver you turned on ... what you need todo is ...

boot and choose recovery mode ... i think this gives you a comman dprompt ... login and 

do 

cd /etc/X11

than 

sudo nano xorg.conf_bak*

Note 
You nee dto load a backuped xorg.conf

because the default corg.conf is configured wrong ... 

Than open this bakuped xorg and save it ... just rename it to xorg.conf and overwrite the default (errorness) xyorg.conf

---

### Post by hilariousness16 on 2007-12-23
ok i think every is working fine but how come when I try to enable desktop effects i get a message 

"The composite extension is not available"

and how do i get my xorg.conf that you asked for mena, i still don't get it

---

### Post by shareMenaPeace on 2007-12-23
ok 

go to the menu panel on top of the screen

click 

Application - Accesoires - here RIGHT click Temrinal and choose display on panel

Now

click the new icon on the panel which launches the TERMINAL

here enter

cd /etc/X11

now BACKUP xorg.conf do this by right click and copy somewhere to your hoem directory.

Now  enter again itno the TEMRINAL

gksudo gedit xorg.conf

Scroll down to the bottom and change

composite extension ="1"  
(it is now "0"

...
NOTE because of the restricted driver ( I belive) you coudl still ahve issues later but this setting is for haveing compiz desktop visualisations.

---

### Post by hilariousness16 on 2007-12-23
I  am still getting that same message and changed the composite to 1

Look...


# xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
EndSection

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"CoreKeyboard"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
	Option		"Device"	"/dev/input/mice"
	Option		"Protocol"	"ImPS/2"
	Option		"ZAxisMapping"	"4 5"
	Option		"Emulate3Buttons"	"true"
EndSection

Section "InputDevice"
	Identifier	"Synaptics Touchpad"
	Driver		"synaptics"
	Option		"SendCoreEvents"	"true"
	Option		"Device"	"/dev/psaux"
	Option		"Protocol"	"auto-dev"
	Option		"HorizEdgeScroll"	"0"
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"stylus"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"stylus"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"eraser"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"eraser"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
	Driver		"wacom"
	Identifier	"cursor"
	Option		"Device"	"/dev/input/wacom"
	Option		"Type"	"cursor"
	Option		"ForceDevice"	"ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
	Identifier	"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Driver		"fglrx"
	Busid		"PCI:1:5:0"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc Radeon XPRESS 200M 5955 (PCIE)"
	Monitor		"Generic Monitor"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1440x900"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
  screen "Default Screen"
	Inputdevice	"Generic Keyboard"
	Inputdevice	"Configured Mouse"
	
	# Uncomment if you have a wacom tablet
	#	InputDevice     "stylus"	"SendCoreEvents"
	#	InputDevice     "cursor"	"SendCoreEvents"
	#	InputDevice     "eraser"	"SendCoreEvents"
	Inputdevice	"Synaptics Touchpad"
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"1"
EndSection

---

### Post by shareMenaPeace on 2007-12-23
Did you restarted (booted) ?

---

### Post by hilariousness16 on 2007-12-23
oops :p

---

### Post by shareMenaPeace on 2007-12-23
And did thuis fixd it?

btw

Mark the topic as SOLVED (top of page under topic tools)


Cheers

---

### Post by jaybombalous on 2007-12-23
> **shareMenaPeace said:**
> Did you restarted (booted) ?

not needed, anything u change in xorg.conf can just be restarted by reloading X server. Try ctrl+alt+backspace and log back in and see if the error still exist.

---

### Post by hilariousness16 on 2007-12-23
Ok, I restarted, Logged on fine, went to Appearance Preferences ( Right-click ) and selected "Normal" for desktop effects and got a message...

"Desktop effects could not be enabled"

I did the composite thing already:confused::confused::confused:

---

### Post by shareMenaPeace on 2007-12-23
Do you have the restricted driver checked?

Try uncheck it and restart again ...

---

### Post by hilariousness16 on 2007-12-23
Still got same message 


argggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggggg

---

### Post by shareMenaPeace on 2007-12-23
can you click extra?

Than make sure
that you updated gutsy allready (update manager from administration drop down)
that you have enabled the repos in (administration 3rd party - check all)
and check in ubuntu software verythign except source code.

or try this

open from administration - synaptic package manager and search for

compizconfig-setting

install it but beware this can cause freezes and hangds of your system if you configure wrong so make first a new theme ... and you could always reset to default settings)....ask me away if you have more qestions :)


on the bottom line i woner why you didnt could used envy ... are you sure you tried the right script?

(try again if you got the repos checked)

---

### Post by hilariousness16 on 2007-12-23
im downloading like 165 stuff for the update hopefully it will work. i will imform you how it went

so stick around lol, it says 25minutes remaining
:popcorn:

---

### Post by shareMenaPeace on 2007-12-23
yes, dont give up ... i try around with nearly everything but im close to get what i want :)

basicly beware to make compiz settings these can be tuff to find later when you have problems... but envy should fix it ... you enabled the repos, and in the first tab there all except for source code, right?

Oh, and i suggest when you get the ati card and compiz running to create a second asminsitration user ... and keep on working with this one, just in case you mess around ... :)

cheers


:popcorn:

---

### Post by hilariousness16 on 2007-12-23
i did everything u said and guess what

i got nothing

roarr -.-

---

### Post by shareMenaPeace on 2007-12-23
DId you tried to use envy?

[http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu3_all.deb](http://albertomilone.com/ubuntu/nvidia/scripts/ubuntu/envy_0.9.9-0ubuntu3_all.deb)

---

### Post by hilariousness16 on 2007-12-23
i did

---

### Post by hilariousness16 on 2007-12-23
My ATI accerlated graphics card is not in use like you told me by the way

---

### Post by shareMenaPeace on 2007-12-23
hmmm

---

### Post by shareMenaPeace on 2007-12-23
I said i would uncheck it ... here i unchecked it moment i try something....

---

### Post by shareMenaPeace on 2007-12-23
So i checked mine it still works now :)

But i used envy to install the drivers ... so what error do you get when you try to run envy?

And first try uninstall drivers (ATI) and than install ATI drivers.... with GUI (when on desktop).

---

### Post by hilariousness16 on 2007-12-23
> **shareMenaPeace said:**
> So i checked mine it still works now :)

But i used envy to install the drivers ... so what error do you get when you try to run envy?

And first try uninstall drivers (ATI) and than install ATI drivers.... with GUI (when on desktop).


whats GUI lol

I installed Envy fine, should I reinstall it?

or should i get a new graphics card?

---

### Post by shareMenaPeace on 2007-12-23
no no no :)

all is ok ..but strange ... so under restricted driver syou got both checked?

I have a last trywhen this is still not working .. so your error message is coul dnot enable compiz or asomething ...oh and gui does mena GENERAL USER INTERFACE ... something opposite to terminal stuff...

---

### Post by hilariousness16 on 2007-12-23
[http://i215.photobucket.com/albums/cc239/hilariousness16/Screenshot.png](http://i215.photobucket.com/albums/cc239/hilariousness16/Screenshot.png)


take a look

so fustracting

---

### Post by shareMenaPeace on 2007-12-23
So it should work ... maybe reinstall envy ... i got the same card as you 

What i did diffrent AND what made me problems is, i installed

GL Desktop, if i remember right after this  i was able to enable compiz, but after this you shiould uninstall GL Desktop again, because its bad and conflicting with compizconfig-settings-manager


GL Desktop 
And
compizconfig-settings-manager

and both be found via the synaptic package manager ...

Try to first install compizconfig-settings-manager

If this also fails, than look search somewhere else, but please try this first and also post here if yoxu not succeed as im curious :)

Cheers + GL

---

### Post by hilariousness16 on 2007-12-23
whats GL desktop?

and i already installed the conpiz manager thingy

---

### Post by shareMenaPeace on 2007-12-23
oops i think GU means GRAPHICAL USER INTERFACE ... :)
:popcorn:

---

### Post by shareMenaPeace on 2007-12-23
its another tool to configurate compiz ... try install it and try than to enable compiz... if this works ... after this uninstall it ...its bad software ...it lack smost compoiz features and conflicting with compizconfig-settings-manager

---

### Post by hilariousness16 on 2007-12-23
sorry for delay
when i searched for gui on the symnatic thing, i got like 100 results, didn'y no which one to pick:confused::confused::confused:

---

### Post by hilariousness16 on 2007-12-23
how come urs works and mine doesn't:-|:-|:-|

---

### Post by hilariousness16 on 2007-12-24
nvm i didn't get a new graphics card, still my old ati rademon 200m

---

### Post by hilariousness16 on 2007-12-24
bump:popcorn::popcorn::popcorn::popcorn:

---

### Post by Majorix on 2007-12-24
> **hilariousness16 said:**
> Ok ty i just forgot the sh part

it's installing now


random questions..

whats the beans
it says i got 1 bean?

It can't say you got 1 bean. You have more than 1 posts preceding this one. Can you probably post a screenshot or something?

---

### Post by steinkaare on 2007-12-28
edit forgot the "sh"

---

