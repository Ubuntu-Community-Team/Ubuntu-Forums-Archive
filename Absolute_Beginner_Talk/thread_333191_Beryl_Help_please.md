---
title: "Beryl Help please"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by ajmorris on 2007-01-07
I have just installed beryl. The beryl forums aren't much help so i though i would try here. Beryl is installed and everything, the red diamond is in the system tray but when i choose it as the window manager all the title bars disapear so there are no minimize maxamize or close buttons.
Any help is appreciated.
If it helps i get this error:

beryl: glXBindTexImageEXT is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

---

### Post by Rory_O on 2007-01-07
I just ran into this problem.  You need to add the line

Option "AddARGBGLXVisuals" "True"

Under the Device section in xorg.conf.  Kill X and everything is good to go.

Those errors are normal if you're running an nVIdia card.

---

### Post by ajmorris on 2007-01-07
thanks but i alread had that line added.

I rebooted the system and now gnome won't start. I had beryl-xgl on startup which crashes i think that i what is causing it either that it i the xorg.conf file. Anyway, can someone please tell me where the gnome config file is that sets what starts on startup?

---

### Post by ajmorris on 2007-01-07
> **Rory_O said:**
> I just ran into this problem.  You need to add the line

Option "AddARGBGLXVisuals" "True"

Under the Device section in xorg.conf.  Kill X and everything is good to go.

Those errors are normal if you're running an nVIdia card.

[PHP]Section "Device"
	Identifier	"Intel Corporation 82852/855GM Integrated Graphics 
Device"
	Driver		"i810"
	BusID		"PCI:0:2:0"
	Option  "XAANoOffscreenPixmaps"
	Option "AddARGBGLXVisuals" "True"[/PHP]
is what it looks like

---

### Post by ajmorris on 2007-01-07
> **ajmorris said:**
> thanks but i alread had that line added.

I rebooted the system and now gnome won't start. I had beryl-xgl on startup which crashes i think that i what is causing it either that it i the xorg.conf file. Anyway, can someone please tell me where the gnome config file is that sets what starts on startup?

nvm i found the startup file (~/.config/autostart) however gnome still won't start
.

---

### Post by pissedoffdude on 2007-01-07
> **ajmorris said:**
> thanks but i alread had that line added.

I rebooted the system and now gnome won't start. I had beryl-xgl on startup which crashes i think that i what is causing it either that it i the xorg.conf file. Anyway, can someone please tell me where the gnome config file is that sets what starts on startup?

Have you tried using AIGLX instead of xgl, a friend of mine had a laptop with intel integrated graphics and AIGLX worked fine.

---

### Post by ajmorris on 2007-01-07
please look at the attatchment, it shows the error. The title bars are there in that one because i cant take a screenshot while using beryl. or for that matter change the open window.

---

### Post by pissedoffdude on 2007-01-07
> **ajmorris said:**
> please look at the attatchment, it shows the error. The title bars are there in that one because i cant take a screenshot while using beryl. or for that matter change the open window.

How exactly did you install beryl?  Do you have a link to a howto that you followed?

---

### Post by ajmorris on 2007-01-07
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu)

:)

---

### Post by ajmorris on 2007-01-07
sorry this is it

[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Feisty_with_AIGLX)

---

### Post by housam on 2007-01-07
Using the terminal type ```
startx
```
it will start the Gnome display manager and after that try to update the xorg files through the update manager . it may help solving the problem.

---

### Post by pissedoffdude on 2007-01-07
you did edit ur xorg.conf file properly right?  Try right clicking the beryl icon>advanced beryl options>Rendering platform and select force AIGLX.  This might actually be a feisty problem though.

---

### Post by ajmorris on 2007-01-07
thanks for both suggestions but neither worked.

Attatched is my xorg.conf file (only xorg.txt for the purpose of uploading)

---

### Post by ajmorris on 2007-01-07
could this error have something to do with it?


(heliodor:6982): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",

this was after i set it to use heliodor instead of emerald.

(emerald:7057): Gtk-WARNING **: Unable to locate theme engine in module_path: "murrine",
 
this was after i set it to use emerald.

Sorry if any of my questions are nooby. I am new to beryl

---

### Post by ajmorris on 2007-01-07
> **pissedoffdude said:**
> you did edit ur xorg.conf file properly right?  Try right clicking the beryl icon>advanced beryl options>Rendering platform and select force AIGLX.  This might actually be a feisty problem though.

i don't think its a feisty problem because i could never get it to work on 6.06 either.

---

### Post by ajmorris on 2007-01-07
l337h4x0r@l337h4x0r-Ubuntu:~$ beryl --display 0
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl: Couldn't open display 0



Could this be a problem?

and also this happens

beryl-xgl --replace settings
XGL Absent, checking for NVIDIA
Nvidia Absent, checking for texture_from_pixmap
texture_from_pixmap Present
beryl-xgl: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
Reloading all options.


beryl: GLX_EXT_texture_from_pixmap is missing
beryl: Using non-tfp mode
beryl: GLX_SGIX_fbconfig is missing
beryl: Failed to manage screen: 0
beryl: No manageable screens found on display :0.0

so there is a problem with the display.

---

### Post by STREETURCHINE on 2007-01-07
i just fixed this problem by 
 adding   

 user/bin/beryl-manager   

to the start up menu it fires up when i log in

system >preferances > sessions>start up programs 

click on add and type it in

---

### Post by ajmorris on 2007-01-07
> **STREETURCHINE said:**
> i just fixed this problem by 
 adding   

 user/bin/beryl-manager   

to the start up menu it fires up when i log in

system >preferances > sessions>start up programs 

click on add and type it in

nah didn't work. It starts but the title bar and minimize maxamize and close buttons aren't there still. Is my graphics chipset capable of running beryl?

---

### Post by ajmorris on 2007-01-07
ok one more question before i give up.

[PHP]beryl-settings
beryl-settings: symbol lookup error: beryl-settings: undefined symbol: beryl_settings_set_codeset[/PHP]


whats with that?

---

### Post by STREETURCHINE on 2007-01-07
that happened to me and i typed metacity in terminal
that was dapper and it fixed it

have you chosen a theme frome emerald yet.?

i know there have been some fixes to this in the forums ,
try a search there

---

### Post by xpod on 2007-01-07
Try changing the "select window manager" setting in beryl settings over to gnome then hitting ctr-alt-backspace..
Once it restarts start beryl again then switch the window manager back to beryl....

I dont know why but sometimes my title bars and min\max etc are all missing too.....that seems to fix it if and when it does happen.

Just something else to mabey try

---

### Post by ajmorris on 2007-01-07
> **xpod said:**
> Try changing the "select window manager" setting in beryl settings over to gnome then hitting ctr-alt-backspace..
Once it restarts start beryl again then switch the window manager back to beryl....

I dont know why but sometimes my title bars and min\max etc are all missing too.....that seems to fix it if and when it does happen.

Just something else to mabey try

thanks, that sorta worked. the title bars are there with using beryl but the emerald themes won't work it just uses the one i set in "system - preferences - Theme" and i still can't open beryl-settings.

---

### Post by ajmorris on 2007-01-07
oh well looks like i can't do it. Thanks for trying guys.

---

### Post by xpod on 2007-01-07
The fact that your using feisty might explain stuff although i would`nt know for sure.....

I know i did`nt go near Edgy until the week or 2 before it was due and i certainly wont be going near feisty until then either....if at all.

Mabey it`s feisty itself you should give up on for the time being;)

---

### Post by Bigbluecat on 2007-01-07
Click on the diamond and select reload window decorator. See if that helps

---

### Post by bulldog on 2007-01-07
Maybe you have to use a standard Gnome theme.
I get the impression it can't find some murrine stuff or what ever.
As I remember correctly was murrine not a sort of window manager too?
Correct me if I'm wrong though :D

---

### Post by ajmorris on 2007-01-07
i tried using the default theme as well but still no luck. Does anyone know what the murrine thing is ?

---

### Post by ajmorris on 2007-01-07
i just realised that it comes up with the murrine error when i switch it back to Metacity.

---

### Post by clothrh on 2007-01-08
I just got beryl working with a 7 year old nVidia card with similar problems as yours.  I got mine going by installing newer nVidia drivers, and the part about the min-max buttons dissapearing happens every time beryl starts up. Click the Emerald and select Reload Window Decorator and the buttons should reappear.

---

