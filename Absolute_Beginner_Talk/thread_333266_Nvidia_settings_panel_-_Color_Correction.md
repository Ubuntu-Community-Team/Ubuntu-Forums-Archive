---
title: "Nvidia settings panel - Color Correction"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by Contrid on 2007-01-07
Hi there,

I was hoping that someone can assist me with showing the nvidia-settings panel on my Ubuntu Edgy Eft os. All I really need to do is to change my color settings. I want to reduce the gamma of blue shade.

All help will be greatly appreciated. ;)

Thanks.

---

### Post by mxrten on 2007-01-07
The simplest way is to execute **nvidia-settings** in a terminal

---

### Post by Contrid on 2007-01-07
> **mxrten said:**
> The simplest way is to execute **nvidia-settings** in a terminal

Hi there,

You are right, though I don't see the color settings as I used to before.
Please see the screenshot below. Maybe I have to enable to somewhere.

[IMG]http://www.contrid.com/_images/nvidia-settings.png[/IMG]

Thanks alot for the help.
I have a strange blue glow on my screen which really doesn't make working pleasant at all.

Best,
Contrid.

---

### Post by Patrick K on 2007-01-07
I don't think you have the Nvidia drivers installed and running. The reason, I got this same screen before getting the drivers properly setup. I suggest looking here:
[http://ubuntuforums.org/showthread.php?t=301499](http://ubuntuforums.org/showthread.php?t=301499) 
Then follow the links. I used the Envy script to install the drivers. The link is in tseliot's sig. 

If the drivers are fully installed open the xorg.conf file ```
sudo gedit /ect/X11/xorg.conf
```and replace "nv" with "nvidia". Besure to make a backup, since the GUI will not start if the files are not properly installed. Even if the files are installed using the script will not hurt anything.

---

### Post by aidanr on 2007-01-07
that happens with xgl, try right clicking on the bery systray icon -> advanced -> rendering platform -> force nvidia

you'll want to have the latest nvidia drivers for this to work if you don't already

---

### Post by Contrid on 2007-01-07
Thanks for the replies guys...though I'm still stuck.

@aidanr :
Yes, I have the latest nvidia drivers. I installed them before installing xgl and beryl, since it only works with the latest direct rendering.
Something must have gone missing, cause if you look at the screenshot above, I seem to be getting 3 errors when launching "nvidia-settings".

Is there any other way to change my color settings?
In the past, I installed nvidia drivers using automatix and it installed the color settings and other things as well. This time I didn't...i just followed a guide which installes using 1 or 2 commands "sudo apt-get install nvidia-glx" etc...

Wish I could get those color settings back...

---

### Post by aidanr on 2007-01-07
you don't need xgl if you have the latest nvidia drivers, beryl can use the nvidia drivers instead of xgl and you'll have direct rendering and the nvidia-settings will work properly

---

### Post by Contrid on 2007-01-07
> **aidanr said:**
> you don't need xgl if you have the latest nvidia drivers, beryl can use the nvidia drivers instead of xgl and you'll have direct rendering and the nvidia-settings will work properly

Interesting...
I see what you're saying, though I don't really have much experience with Linux and all complying elements. I just read guides and follow them to get things done.

What do you suggest I should do?

---

### Post by steve.horsley on 2007-01-07
Try this to see if your nvidia driver is running:
**glxinfo | grep vendor**

Also, look in the file /etc/X11/xorg.conf, find the section Device and see what the driver is. Here's mine:
> Section "Device"
    Identifier     "NVIDIA Corporation NV43 [GeForce 6600 GT]"
    Driver         "nvidia"
EndSection

If the driver is "nv", that is the open-source non-3D accelerated driver. "nvidia" is the 3D driver. If you are sure the drivers are installed, you can edit this part of the file to specify the nvidia driver instead (make a backup of the original file first). Then log out and in again to see the result. 

Worst case is a white-on-black text window telling you your x-server config is wrong, in which case you will be wanting to undo the changes, but will have to do it in text mode. For practice, press Ctrl-Alt-F2 and see if you can navigate round the file system and edit files with nano. Use Ctrl-Alt-F7 to return to the GUI.

---

### Post by aidanr on 2007-01-07
> **Contrid said:**
> Interesting...
I see what you're saying, though I don't really have much experience with Linux and all complying elements. I just read guides and follow them to get things done.

What do you suggest I should do?

if it were me, i'd remove xserver-xgl, look up the how-to you already used and undo any changes you made to xorg.conf and any gdm config files and then look up an nvidia+beryl how-to and make the changes it instructs to xorg.conf

---

### Post by Contrid on 2007-01-08
> **aidanr said:**
> if it were me, i'd remove xserver-xgl, look up the how-to you already used and undo any changes you made to xorg.conf and any gdm config files and then look up an nvidia+beryl how-to and make the changes it instructs to xorg.conf

Thanks for the response.
I didn't get a notification, though I came back today to see if you had any advice for me.

I was playing around...doing several things.
I ended up breaking my xserver. I couldn't get into Ubuntu at all. I then executed my "xorg.conf" file using nano in gdm terminal. I had to change "nv" to "nvidia" to get my xserver back up and running. I'm back to square one now.

Ok...I'd like to remove xserver-xgl and beryl for xgl and then use beryl only with the latest nvidia drivers. Does that sound right? :) Man...I'm really confused. I saw a how-to on the beryl wiki for installing beryl for nvidia (not xgl).

What steps will I follow in order to not mess my OS up? I have some really important work that I can't afford to loose. Even though I still have WinXP on another partition, I most probably won't be able to access my ext3 partitions from Windows.

I really appreciate your help. ;)

---

### Post by Contrid on 2007-01-08
I can follow the guid for installing Beryl with nVidia...but what about the xserver-xgl? How do I remove that...and what will the consequences be?

---

### Post by aidanr on 2007-01-09
ok, first of all back your stuff up anyway

then to remove xgl, type this into a terminal
```
sudo apt-get remove xserver-xgl
```

to remove xgl from your sessions
```
sudo gedit /etc/gdm/gdm.conf-custom
```
and remove everything below [servers] at the end of the file, save and exit

then
```
sudo gedit /etc/X11/xorg.conf
```
and add
```
Option "AddARGBGLXVisuals" "True"
```
to section "Screen"

restart x (ctrl + alt + backspace) and when you log back in run beryl-manager, and if all is working add it to your startup programs

by the way, no guarantees this won't cause breakage so back up anything important, but it should work

oh and by the way there is an ext3 driver for windows

---

### Post by Contrid on 2007-01-10
Thank you very much AIDANR...you're extremely helpful.
My ubuntu is now running better than ever. I love it.

So...I can now see all those nVidia configuration settings when I run "nvidia-settings" in the terminal. I have a problem though. Even though I change my color settings, they don't stay that way when I reboot or restart X. Do you possibly have a link to a resource that explains how to somehow save the session and keep the new color settings?

Thanks again for all your help. It is greatly appreciated.

---

### Post by aidanr on 2007-01-10
great stuff, add 

```
nvidia-settings -l
```

to your startup items, the -l switch means load config only

---

### Post by Contrid on 2007-01-11
@ Aidanr

Thanks for all your help. You seriously have the Ubuntu flowing in your veins. ;)

I added the following to my startup session :

```

nvidia-settings -l

```

...but unforunately my color settings don't stick.
They are reset everytime a reboot or restart X.

I must be doing something wrong...
If you have any suggestions or advice, I will appreciate it.

Best,
Antonie

---

### Post by aidanr on 2007-01-11
:-k  i'll take a look when i get home, at work on windows at the moment

---

### Post by Contrid on 2007-01-11
> **aidanr said:**
> :-k  i'll take a look when i get home, at work on windows at the moment

Awesome...you're the best! ;)

---

### Post by aidanr on 2007-01-11
try it with the longer switch
```
nvidia-settings --load-config-only
```
and make sure the config file is in your home directory and open it in gedit to make sure it contains the values for your colour settings
```
gedit ~/.nvidia-settings-rc
```

---

### Post by Contrid on 2007-01-11
Ok...this is what I see in that file :

> 
#
# /home/contrid/.nvidia-settings-rc
#
# Configuration file for nvidia-settings - the NVIDIA X Server Settings utility
# Generated on Sun Jan  7 18:01:38 2007
#

# ConfigProperties:

ToolTips = Yes
DisplayStatusBar = Yes
SliderTextEntries = Yes
IncludeDisplayNameInConfigFile = No
ShowQuitDialog = Yes

# Attributes:


---

### Post by Contrid on 2007-01-11
Aha...there should be something below "Attributes". I found the following on another forum, so I can insert that :

> 
0/FlatpanelScaling[DFP-0]=0
0/DigitalVibrance[DFP-0]=0
0/ImageSharpening[DFP-0]=0
0/SyncToVBlank=0
0/AllowFlipping=1
0/LogAniso=0
0/FSAA=0
0/TextureSharpen=0
0/ForceGenericCpu=0
0/CursorShadow=0
0/CursorShadowXOffset=4
0/CursorShadowYOffset=2
0/CursorShadowAlpha=64
0/CursorShadowRed=0
0/CursorShadowGreen=0
0/CursorShadowBlue=0
0/FSAAAppControlled=1
0/LogAnisoAppControlled=1
0/RedBrightness=0.000000
0/GreenBrightness=0.000000
0/BlueBrightness=0.000000
0/RedContrast=0.000000
0/GreenContrast=0.000000
0/BlueContrast=0.000000
0/RedGamma=1.000000
0/GreenGamma=1.000000
0/BlueGamma=1.000000
0/OpenGLImageSettings=1
0/XVideoTextureSyncToVBlank=1
0/XVideoBlitterSyncToVBlank=0
0/XVideoSyncToDisplay=65536



What do you think?
Will it work?

Basically...I'm just changing the gamma

---

### Post by aidanr on 2007-01-11
sure, or you could try deleting the file, run nvidia-settings, change the gamma, quit nvidia-settings and see if it updates the config file with the gamma settings

---

### Post by itsjustarumour on 2007-01-14
Hmm, I got the same problem after installing XGL and Compiz - I go to Applications/System Tools/NVidia Settings and all the settings options have disappeared.  I'm using the lastest NVidia driver etc.  Thanks for the above posts, I'll try editing the config file manually.  It seems a pain to have to resort to this though rather than have a nice easy GUI like before! Just the sort of thing that puts off newcomers to Ubuntu...

---

### Post by jasidog on 2007-01-18
> **aidanr said:**
> great stuff, add 

```
nvidia-settings -l
```

to your startup items, the -l switch means load config only

I've been looking for a way to load only the configuration, no settings window. For ages! ](*,) :oops: 

Just wanted to say thanks aidanr. :)

---

