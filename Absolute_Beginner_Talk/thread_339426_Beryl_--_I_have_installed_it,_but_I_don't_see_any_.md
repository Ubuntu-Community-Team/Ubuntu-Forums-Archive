---
title: "Beryl -- I have installed it, but I don't see any difference"
date: 2007-01-15
forum: Absolute Beginner Talk
---

### Post by Charlie Wilkes on 2007-01-15
:confused: I followed the instructions to install. configure and activate beryl, and everything seemed to go just fine.  Now I have a little red gemstone in the bar at the top of my screen, and that is the only difference in the appearance of my desktop.

I tried the beryl theme manager, clicking on various themes, but nothing changed.  When I choose "Import" it throws up a box in which I have to identify the location of the themes... I guess maybe I don't know where they are.

Maybe I haven't installed beryl at all... I just don't know what is going on.

Charlie

---

### Post by bodhi.zazen on 2007-01-15
With Beryl you can feel the difference !

Open a terminal and type:

beryl-manager

You should see a change.

post any errors.

---

### Post by rabid9797 on 2007-01-15
what kind of video card are you using?

---

### Post by ComplexNumber on 2007-01-15
> **Charlie Wilkes said:**
> :confused: I followed the instructions to install. configure and activate beryl, and everything seemed to go just fine.  Now I have a little red gemstone in the bar at the top of my screen, and that is the only difference in the appearance of my desktop.

I tried the beryl theme manager, clicking on various themes, but nothing changed.  When I choose "Import" it throws up a box in which I have to identify the location of the themes... I guess maybe I don't know where they are.

Maybe I haven't installed beryl at all... I just don't know what is going on.

Charlie
as bodhi.zazen says, if beryl settings isn't in your menu, then fire up the terminal and type in 'beryl-manager'. this will make beryl active, but it won't necessarily fire up beryl. you should now see a ruby icon in yur notification area on your panel. click on it, select 'Select Window Manager', then select 'beryl'. beryl should then kick in.

---

### Post by Charlie Wilkes on 2007-01-15
> **rabid9797 said:**
> what kind of video card are you using?


I have a GeForce4 MX 440 AGP8X, 64mb of memory.  Someone wrote out meticulous instructions for installing the nvidia driver under edgy, and I followed them exactly.  I think the driver is working, because when I type "glxinfo | grep render" I get "direct rendering: yes" plus the hardware ID string.

I have added "beryl-manager" to my startup script, and I have the red gemstone at the top of my screen.  The system is working fine; I just can't see any differences because of beryl.

Charlie

---

### Post by Hendrixski on 2007-01-15
also, make sure it's running... if you type " beryl-manager " into your terminal then you will start it manually.  If there's a little crystal on your menu bar click on it, and under "select window manager" or something, you'll have the option "metacity", or "KDE" or whatever, make sure it's set to Beryl, not any of the others.  If you still don't see a difference then play with the manager, and the themes.

---

### Post by Charlie Wilkes on 2007-01-15
> **ComplexNumber said:**
> as bodhi.zazen says, if beryl settings isn't in your menu, then fire up the terminal and type in 'beryl-manager'. this will make beryl active, but it won't necessarily fire up beryl. you should now see a ruby icon in yur notification area on your panel. click on it, select 'Select Window Manager', then select 'beryl'. beryl should then kick in.

Ahhh...

When I bring up that menu,  the Metacity box is checked.  When I check Beryl, the screen flickers a couple of times, and when I look again at the "select window manager" menu, Metacity is still checked.

So, apparently something is wrong... but I'm not getting any error codes, or if I am I don't know where the log is.

Charlie

---

### Post by ComplexNumber on 2007-01-15
> **Charlie Wilkes said:**
> Ahhh...

When I bring up that menu,  the Metacity box is checked.  When I check Beryl, the screen flickers a couple of times, and when I look again at the "select window manager" menu, Metacity is still checked.

So, apparently something is wrong... but I'm not getting any error codes, or if I am I don't know where the log is.

Charlie
fire up the synaptic package manager, then search for "beryl". then attach the screenshot of which beryl components you have installed.
the "flickering" is what you should see when berly kicks in. it also brings up a beryl splash screen for a few  seconds.
if you type in 'beryl-manager' in the terminal, it should give you a printout of any errors. if possible, can you cut and paste them in your next post.

---

### Post by Charlie Wilkes on 2007-01-15
> **ComplexNumber said:**
> fire up the synaptic package manager, then search for "beryl". then attach the screenshot of which beryl components you have installed.
the "flickering" is what you should see when berly kicks in. it also brings up a beryl splash screen for a few  seconds.
if you type in 'beryl-manager' in the terminal, it should give you a printout of any errors. if possible, can you cut and paste them in your next post.

:-k I wasn't sure how to do the screenshot, but I copied the components listed and checked in synaptic package mgr.  They are as follows:

package                
beryl                   
beryl core            
beryl-manager
beryl-plugins
beryl-plugins-data
beryl-settings
emerald
libberylsettings0
libemeraldengine0

Here is what I get when I type "beryl manager" in a terminal:

charlie@charlie-desktop:~$ beryl manager
XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present
beryl: No composite extension
charlie@charlie-desktop:~$ 

In the beryl configuration menu (the red gemstone) I unchecked "Launch fall-back window manager if beryl crashes" and so now beryl is checked under "select window manager," but again, I'm not seeing any changes in the appearance/capabilities of my desktop.

Charlie

---

### Post by ComplexNumber on 2007-01-15
>  I wasn't sure how to do the screenshotmain menu -> accessories. its in there.


for a start,  install  libberylsettings0-dev.

it may also be because:
a) you haven't got the composite libraries isntalled. in synaptic, do a search for "composite" on the name only. install them all except libxcomposite1-dbg(not necessary. it just aids in denugging). there's only 3 to install in total.
b) although i'm not entirely certain, but you may need the xcompmgr package installed, so install this too. 
c) you haven't configured your /etc/X11/xorg.conf file. don't touch that file yet! just let me know when you have the packages given in a) and b), and i'll show you what to change in the xorg.conf file.


also, i think you will need the nvidia-glx package installed too.

---

### Post by Charlie Wilkes on 2007-01-15
> **ComplexNumber said:**
> main menu -> accessories. its in there.


for a start,  install  libberylsettings0-dev.

it may also be because:
a) you haven't got the composite libraries isntalled. in synaptic, do a search for "composite" on the name only. install them all except libxcomposite1-dbg(not necessary. it just aids in denugging). there's only 3 to install in total.
b) although i'm not entirely certain, but you may need the xcompmgr package installed, so install this too. 
c) you haven't configured your /etc/X11/xorg.conf file. don't touch that file yet! just let me know when you have the packages given in a) and b), and i'll show you what to change in the xorg.conf file.


also, i think you will need the nvidia-glx package installed too.


:-? I have installed the libxcomposite files and the xcompmgr as well as libberylsettings0.dev

nvidia-glx is already installed.

I guess it is time to edit xorg.conf.

Charlie

---

### Post by ComplexNumber on 2007-01-16
> **Charlie Wilkes said:**
> :-? I have installed the libxcomposite files and the xcompmgr as well as libberylsettings0.dev

nvidia-glx is already installed.

I guess it is time to edit xorg.conf.

Charlie
ok, we'll take this in steps because entering the wrong thing can mess thing up. BEFORE WE DO ANYTHING, I WANT YOU TO MAKE A BACKUP COPY OF YOUR xorg.conf FILE (JUST IN CASE). i want you to make a copy of your present xorg.conf file and store in the same directory as the current one. call it something like xorg.conf.bk. do that now before you do anything else.
now open your xorg.conf file by using 'gksudo gedit /etc/X11/xorg.conf'
1) go to the "Device" section(it will say *Section "Device"*). it will look something like this (on **my** system. don't copy my setup word for word,** only** the parts that i ask you to add):
> Section "Device"
    Identifier    "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
**     Driver        "nv"**
    BusID        "PCI:1:0:0"
EndSectionchange the "nv" to "nvidia" so that it looks like this:
> Section "Device"
    Identifier    "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
**     Driver        "nvidia"**
    BusID        "PCI:1:0:0"
EndSection2) the last section should look **exactly** like this:
> Section "DRI"
 Mode    0666
EndSection

Section "Extensions"
 Option "Composite" "Enable"
EndSectionadd the parts that are missing (in my case, i alread had the Section "DRI" part, so i just needed to add the *Section "Extensions"* part)

3) add the following to the *Section "Device"* part:
> Option      "XAANoOffscreenPixmaps"it should now look like this:
> Section "Device"
    Identifier    "NVIDIA Corporation NV28 [GeForce4 Ti 4200 AGP 8x]"
    Driver        "nvidia"
    BusID        "PCI:1:0:0"
** Option      "XAANoOffscreenPixmaps"**
EndSection4) add the following line to Section "Module"
> Load    "dbe"it will now look like this:
> Section "Module"
    Load    "i2c"
    Load    "bitmap"
    Load    "ddc"
    Load    "dri"
    Load    "extmod"
    Load    "freetype"
    Load    "glx"
    Load    "int10"
    Load    "type1"
    Load    "vbe"
**    Load    "dbe"**
EndSection5) reboot

---

### Post by Charlie Wilkes on 2007-01-16
> **ComplexNumber said:**
> ok, we'll take this in steps because entering the wrong thing can mess thing up. 

:D :D Thank you so much for all this help.  Beryl is now working and I can modify themes etc.

I really appreciate your excellent guidance.  It is very educational for me to get this kind of walk-through. 

Charlie

---

### Post by ComplexNumber on 2007-01-16
> **Charlie Wilkes said:**
> :D :D Thank you so much for all this help.  Beryl is now working and I can modify themes etc.

I really appreciate your excellent guidance.  It is very educational for me to get this kind of walk-through. 

Charlie
glad it works :D. the above xorg.conf walkthrough i remembered from one of the guides on this forum (i think the author of the guide was ts elliot, but i can't confirm that). i very nearly messed up because i couldn't for the life of me remember what step 3 was, even though i remembered that "there was something else that i needed to change". i looked through the forum, but i couldn't find the original guide that i went by, so i had to used an application called meld([click]("http://meld.sourceforge.net/")) to show me the difference between my current xorg.conf and the previous one.

---

### Post by bodhi.zazen on 2007-01-16
Nice walk-through Complex Number. Thank you as you saved me some time as well (I was going to jump back in, but you did such nice work I did not have to).

I am familiar with the link you mention, but I can not find it now either :(

If I find it I will PM it to you and/or re-post here :)

---

### Post by ComplexNumber on 2007-01-16
> **bodhi.zazen said:**
> Nice walk-through Complex Number. Thank you as you saved me some time as well (I was going to jump back in, but you did such nice work I did not have to).

I am familiar with the link you mention, but I can not find it now either :(

If I find it I will PM it to you and/or re-post here :)
thanks :). but as i'm just going by memory for the xorg.conf part, i can't take any credit. the credit goes to the person who made the original walkthough(whoever that was. it may have been ts elliot).

---

