---
title: "Titlebar Missing from Applications"
date: 2008-04-06
forum: Absolute Beginner Talk
---

### Post by quddusaliquddus on 2008-04-06
Hi all :),
             I followed the following tutorial:

[http://ubuntuforums.org/showthread.php?t=580748](http://ubuntuforums.org/showthread.php?t=580748)

to install the fancy graphics. But now the titlebar is missing in every application. How can i get back the title bars?

Thanks :D

Regards

Q

---

### Post by quddusaliquddus on 2008-04-06
anyone? ... bump ... btw mods - are we allowed to bump threads?

---

### Post by quddusaliquddus on 2008-04-06
someone please help!! -bump

---

### Post by Daveg4otu on 2008-04-06
Go here and scroll down to about Forestpixies(hope I got the name right) posts - works for me

[http://ubuntuforums.org/showthread.php?t=734001](http://ubuntuforums.org/showthread.php?t=734001)

---

### Post by quddusaliquddus on 2008-04-06
thanks for the input but i dont have an nividia card.

---

### Post by Mazza558 on 2008-04-06
Press Alt + F2 and type in 

> compiz --replace

---

### Post by quddusaliquddus on 2008-04-06
ok. i tried that. there dont seem to be any changes. thanks for suggestion.

---

### Post by autocrosser on 2008-04-06
sudo apt-get fusion-icon

If you are using Gutsy--this will give you more control over Compiz---You might also do  sudo apt-get emerald  to be able to run a different window-decorator.

---

### Post by quddusaliquddus on 2008-04-06
When i run:
```

sudo apt-get fusion-icon

```
I get the error:
```

E: Invalid operation fusion-icon

```
When i run:
```

sudo apt-get emerald

```
i get the following error
```

E: Invalid operation emerald

```

Where am i going wrong?...or is there something else i can do to fix this?

BTW im using restricted drivers manager to run my graphics card which is a ati radeon 9550 (256 mb).

---

### Post by alexforcefive on 2008-04-06
You actually want to install the compiz config settings manager, then run it and make sure window decoration is enabled

---

### Post by autocrosser on 2008-04-06
Have you opened up all your repos?  Menu>System>Administration>Software Sources & check all boxes in the first tab....Yes, also install settings-manager too, but Fusion-Icon allows a single place to access your Compiz & Emerald settings---puts it in the notification area.

---

### Post by quddusaliquddus on 2008-04-06
alex - how would i install compiz config settings manager? im sorry - im a noob to ubuntu or anything linux related. 

auto - all the checkboxes in the first tab are checked.

---

### Post by autocrosser on 2008-04-06
HMMMM--open up Synaptic & search for emerald & fusion-icon--You are using Gutsy? Have you added the Medibuntu sources?

---

### Post by quddusaliquddus on 2008-04-06
im using gutsy. i dont know if i have added medibuntu sources. i will now search for emerald and fusion icon

---

### Post by quddusaliquddus on 2008-04-06
btw - thank u sooo much for your help!

---

### Post by quddusaliquddus on 2008-04-06
i just found that emerald isnt installed.....and there is no package called fusion icon.

shall i install emerald?

---

### Post by Mazza558 on 2008-04-06
> **quddusaliquddus said:**
> When i run:

When i run:
```

sudo apt-get emerald

```
i get the following error
```

E: Invalid operation emerald

```

Where am i going wrong?...or is there something else i can do to fix this?



He made a mistake. It should be

```
sudo apt-get install emerald
```

After you've done this, try

```
emerald --replace
```

---

### Post by autocrosser on 2008-04-06
Medibuntu is the repository that has several "additional" things---like codecs & other "needful" things--I'll run you thru the drill...

Open Software Sources & in the second tab (third-party) Add the following:

deb [http://packages.medibuntu.org/](http://packages.medibuntu.org/) gutsy free non-free

And then save it--software sources will update...then try searching for all of it again..

---

### Post by quddusaliquddus on 2008-04-06
mazza - i did:

```

sudo apt-get install emerald

```
it installed fine
then i did this:
```

emerald --replace

```
 and this time nothing happens. the cursor just blink in the next line which is blank without any dirtectories.

---

### Post by quddusaliquddus on 2008-04-06
auto ... ill do that right now.

---

### Post by autocrosser on 2008-04-06
Sorry 'bout the missing "install"  In any case--you will find the fusion-icon in the medibuntu sources.......I've found it very handy to turn Compiz on/off & gain access to all the settings in one place.

---

### Post by quddusaliquddus on 2008-04-06
so..auto - i still cant find fusion-icon in synaptic even after doing what u said.

---

### Post by Mazza558 on 2008-04-06
> **quddusaliquddus said:**
> mazza - i did:

```

sudo apt-get install emerald

```
it installed fine
then i did this:
```

emerald --replace

```
 and this time nothing happens. the cursor just blink in the next line which is blank without any dirtectories.

Have you tried logging out and logging in again after doing this?

---

### Post by quddusaliquddus on 2008-04-06
mazza - i will try that now

---

### Post by quddusaliquddus on 2008-04-06
didnt work im afraid. :(

Oh man ... ubuntu is more buggy than i initially thought.

---

### Post by Mazza558 on 2008-04-06
> **quddusaliquddus said:**
> didnt work im afraid. :(

Oh man ... ubuntu is more buggy than i initially thought.

You're just having a very bad/unlucky experience. It honestly isn't buggy for most people.

what does the output of 

> glxinfo

show?

---

### Post by autocrosser on 2008-04-06
Compiz is still "experimental" software--it is the most advanced eye-candy on the planet, but it's a bit "fun" getting it all setup--Please don't judge Linux by one piece of flashy stuff---I've watched Linux evolve into the best the software world has to offer---You have to remember that Linux assumes you are smart--unlike a "other" OS that assumes you are stupid......

You can find a fair amount of the info you need here: [http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)

And for more answers (including Fusion-icon): [http://wiki.compiz-fusion.org/](http://wiki.compiz-fusion.org/)

---

### Post by quddusaliquddus on 2008-04-06
ok. its wrong to judge the softwre based on my experience alone- i guess other poeople have had a better time with it than me.

ok.... ill try glxinfo command now and see.

here is the result:

```

name of display: :1.0
Xlib:  extension "XFree86-DRI" missing on display ":1.0".
display: :1  screen: 0
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)
server glx vendor string: SGI
server glx version string: 1.2
server glx extensions:
    GLX_ARB_multisample, GLX_EXT_visual_info, GLX_EXT_visual_rating, 
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_OML_swap_method, 
    GLX_SGI_make_current_read, GLX_SGIS_multisample, GLX_SGIX_hyperpipe, 
    GLX_SGIX_swap_barrier, GLX_SGIX_fbconfig
client glx vendor string: ATI
client glx version string: 1.3
client glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_get_proc_address, GLX_SGI_video_sync, GLX_ARB_multisample, 
    GLX_ATI_pixel_format_float, GLX_ATI_render_texture
GLX version: 1.2
GLX extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_EXT_import_context, 
    GLX_ARB_multisample
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: ATI Radeon 9550 / X1050 Series
OpenGL version string: 1.2 (2.0.6473 (8.37.6))
OpenGL extensions:
    GL_ARB_multitexture, GL_ARB_texture_border_clamp, GL_ARB_texture_cube_map, 
    GL_ARB_texture_env_add, GL_ARB_texture_env_combine, 
    GL_ARB_texture_env_dot3, GL_ARB_transpose_matrix, GL_EXT_abgr, 
    GL_EXT_blend_color, GL_EXT_blend_minmax, GL_EXT_blend_subtract, 
    GL_EXT_texture_env_add, GL_EXT_texture_env_combine, 
    GL_EXT_texture_env_dot3, GL_EXT_texture_lod_bias

   visual  x  bf lv rg d st colorbuffer ax dp st accumbuffer  ms  cav
 id dep cl sp sz l  ci b ro  r  g  b  a bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------
0x2c 24 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 None
0x2d 24 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 None
0x2e 32 tc  0 32  0 r  y  .  8  8  8  8  0 24  8  0  0  0  0  0 0 Ncon
0x2f 32 tc  0 32  0 r  .  .  8  8  8  8  0  0  0  0  0  0  0  0 0 Ncon


```

---

### Post by autocrosser on 2008-04-06
I'm sure that Mazza will concur--you don't have accelerated drivers installed & that is why Compiz is giving you problems---we need to know your graphics card info....

---

### Post by quddusaliquddus on 2008-04-06
ok. i know that my graphics card is ati radeon 9550 (256 MB) thats all. if you need more info where would i go to find out the info in ubuntu?

---

### Post by Mazza558 on 2008-04-06
> **quddusaliquddus said:**
> ok. i know that my graphics card is ati radeon 9550 (256 MB) thats all. if you need more info where would i go to find out the info in ubuntu?

Go to System > Administration > Restricted Drivers, select the ATI one, restart and all will be well.

---

### Post by quddusaliquddus on 2008-04-06
mazza - ive done that along time ago. thanks for the suggestion though.

---

### Post by fitzman49 on 2008-04-06
I t looks like something is messed up with the settings in your xorg.conf.  Could you post it please?

sudo gedit /etc/X11/xorg.conf

---

### Post by quddusaliquddus on 2008-04-06
```

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
	Option		"XkbLayout"	"gb"
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
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"RM170"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"RM170"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
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
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

---

### Post by Mazza558 on 2008-04-06
I know why!

> sudo apt-get install xserver-xgl

Restart after doing this (unless you've already done this before)

Just to note, if you install Hardy (the new release), you don't have to follow this step.

Also, if you don't like emerald (when you get everything working), you can remove it with

> sudo apt-get remove emerald 

---

### Post by quddusaliquddus on 2008-04-06
thanks. il try that now

---

### Post by quddusaliquddus on 2008-04-06
i just tried:

sudo apt-get install xserver-xgl

it says that its already installed.

---

### Post by SunnyRabbiera on 2008-04-06
You might not be able to use desktop effects, maybe if you turn them off you might have your titlebar back.
sometimes stuff like this happens, sometimes the desktop effects simply dont work.

---

### Post by Mazza558 on 2008-04-06
> **quddusaliquddus said:**
> i just tried:

sudo apt-get install xserver-xgl

it says that its already installed.

Damn. 

I don't think Xgl is loading properly. Can you log out and go to options > choose a session (or similar), and see if there's an "xgl" option?

If you just want your titlebars back for now (with no effects), you can run

> metacity --replace

---

### Post by quddusaliquddus on 2008-04-06
i know its petty of me - but one of the main reasons for installing ubuntu was because of the desktop effects (and its immunity to viruses and bugs)....so i was hoping there was a solution out there somewhere.

---

### Post by autocrosser on 2008-04-06
OK--ATI is a bit harder that nVidia--I'm not a guru about ATI---but--

First--you need the ATI accelerated drivers
In Gutsy you can goto Add/Remove & after "show all available"--search for fglrx.
install the ATI hardware driver & the catalyst control centre.

next you will need to do a edit to your xorg.conf (/etc/X11/xorg.conf) as root user. Open a terminal & do  sudo gedit /etc/X11/xorg.conf
this will open the text editor with root permissions. Look for the area "Device" & change the "driver" to fglrx. Save & close the file. Your old xorg.conf will be saved as: /etc/X11/xorg.conf~

Next log out or reboot--your choice...after you log in, check the glxinfo again---you should now have DRI

Crud--I see I type too slow.......

---

### Post by quddusaliquddus on 2008-04-06
there was no xgl option

---

### Post by fitzman49 on 2008-04-06
> **quddusaliquddus said:**
> ```

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
	Option		"XkbLayout"	"gb"
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
	Identifier	"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection

Section "Monitor"
	Identifier	"RM170"
	Option		"DPMS"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc RV350 AS [Radeon 9550]"
	Monitor		"RM170"
	Defaultdepth	24
	SubSection "Display"
		Modes		"1280x1024"	"1024x768"	"832x624"	"800x600"	"720x400"	"640x480"
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
EndSection
Section "Module"
	Load		"glx"
EndSection
Section "Extensions"
	Option		"Composite"	"0"
EndSection

```

OK think I may have found an issue.  Looks like you do not have direct rendering enabled.  I used to have the same problem when I had ATI a long time ago.  Pretty simple fix.

```
sudo gedit /etc/X11/xorg.conf
```

Then look at the bottom for the extensions group.\

Add this line inside the extensions group:
```
Option "Composite" "Enable"
```

All you should need to do is reboot X by doing CTRL+ALT+BACKSPACE.

Let me know how that goes.

---

### Post by SunnyRabbiera on 2008-04-06
> **quddusaliquddus said:**
> didnt work im afraid. :(

Oh man ... ubuntu is more buggy than i initially thought.

well if you are using Gutsy, yeh it is buggy as heck.
My suggestion personally is to hold off for a bit and wait for hardy or use another distro, I know Gusty has had issues for me.
I really dont like Ubuntu Gutsy, or Feisty, both were buggy and unstable in my experience...
I preferred Ubuntu Dapper and edgy, far more stable in my experience.

---

### Post by Mazza558 on 2008-04-06
> **autocrosser said:**
> OK--ATI is a bit harder that nVidia--I'm not a guru about ATI---but--

First--you need the ATI accelerated drivers
In Gutsy you can goto Add/Remove & after "show all available"--search for fglrx.
install the ATI hardware driver & the catalyst control centre.

next you will need to do a edit to your xorg.conf (/etc/X11/xorg.conf) as root user. Open a terminal & do  sudo gedit /etc/X11/xorg.conf
this will open the text editor with root permissions. Look for the area "Device" & change the "driver" to fglrx. Save & close the file. Your old xorg.conf will be saved as: /etc/X11/xorg.conf~

Next log out or reboot--your choice...after you log in, check the glxinfo again---you should now have DRI

His Xorg is already using fglrx.

---

### Post by quddusaliquddus on 2008-04-06
ok auto . ill try that

---

### Post by autocrosser on 2008-04-06
Hardy is doing very well--I've been with it testing from repos opening. I'd wait til the dist settles after release & move to it...My experences have been very positive (but I have contributed to it so maybe I'm biased :)  )


I added a note to last post--I'm late :)

---

### Post by quddusaliquddus on 2008-04-06
ok fitzman. i did what u said and no difference :(.

---

### Post by Mazza558 on 2008-04-06
Well, I can do no more. There is, provided all the info you gave us is correct, NO reason why it's not working now. I'm stumped. I recommend waiting 19 days for the release of Hardy Heron and doing a clean install then.

---

### Post by quddusaliquddus on 2008-04-06
thanks for al the help. :)

---

### Post by autocrosser on 2008-04-06
Sounds like it's time to send you to this forum:  Desktop effects & customization

[http://ubuntuforums.org/forumdisplay.php?f=223](http://ubuntuforums.org/forumdisplay.php?f=223)

---

### Post by quddusaliquddus on 2008-04-06
thanks guys for **all** the help guys.

---

