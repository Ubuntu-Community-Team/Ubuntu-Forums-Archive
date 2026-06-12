---
title: "how to remove &quot;quiet&quot; and &quot;splash&quot; from grub"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by mineirosotan on 2008-03-02
Hello, I should preface this by saying that I am a complete newbie.  

I recently installed Ubuntu 7.10 on a Compaq Evo n400c laptop. Install seemed to complete without a hitch.   However, after reboot, I'm presented with a black screen that fades to blotchy white.

I searched the forum and found another user with the same laptop and a similar problem.  His description of his problem and solution:

...I did have to change the settings in Grub to eliminate "splash" and "quiet" from the kernel parameters, otherwise I just got a white screen when X started from the installed version. But after that (edit /boot/grub/menu.lst), everything works fine. Didn't have the problem when booted from the CD.

I'd like to try this, but I'm not sure how to eliminate "splash" and "quiet."  I looked for an explanation on the forum but didn't find anything that was simple enough for my newbie brain.  

I was able to enter "safe mode" by hitting ESC at the start of the boot up process, but... that was about as far as I got.

Many thanks in advance for some simplified advice.

---

### Post by jan quark on 2008-03-02
first make a backup copy of the menu.lst

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_backup
```

then you can change the menu.lst with this command
```

gksudo gedit /boot/grub/menu.lst
```

---

### Post by mineirosotan on 2008-03-02
Thanks for the info; however, I think I'm still missing the boat.  

Here's what I did and what happened.

I booted up in safe mode.  At the end of the boot process, I had the following prompt:
root@jeffrey-laptop:~# 

Here I entered the  "sudo cp /boot/grub/menu.1st /boot/grub/menu.1st_backup"  (enter)

And I received the message "cp: cannot stat '/boot/grub/menu.1st': No such file or directory

What did I miss?   

Thanks in advance for any help.

---

### Post by Scooby Doo on 2008-03-02
.lst

instead of

.1st

---

### Post by Oldsoldier2003 on 2008-03-02
> **mineirosotan said:**
> Thanks for the info; however, I think I'm still missing the boat.  

Here's what I did and what happened.

I booted up in safe mode.  At the end of the boot process, I had the following prompt:
root@jeffrey-laptop:~# 

Here I entered the  "sudo cp /boot/grub/menu.1st /boot/grub/menu.1st_backup"  (enter)

And I received the message "cp: cannot stat '/boot/grub/menu.1st': No such file or directory

What did I miss?   

Thanks in advance for any help.

if you entered in recovery mode you are root and don't need sudo 

.cp /boot/grub/menu.1st /boot/grub/menu.1st_backup is incorrect those are L's not 1's plus you missed a space...

try this: ```
cp /boot/grub/menu.lst  /boot/grub/menu.lst_backup
```

---

### Post by mineirosotan on 2008-03-02
(I thought that "1" didn't looke quite right... but thanks a lot  for the help.  I was able to execute the backup command.  

Now, when I try to enter the command to edit the "grub" settings (whatever those are), I enter and get the following response.

root@jeffrey-laptop:~#gksudo gedit /boot/grub/menu.lst
(gksudo:4234): Gtk-WARNING **:cannot open display

then I tried just 
gedit /boot/grub/menu.lst
and received
cannot open display
Run 'gedit --help'...

---

### Post by Tatty on 2008-03-02
If you are in a recovery console then [X]("http://en.wikipedia.org/wiki/X_Window_System") will not be loaded.  So gedit wont work as it is a grapical text editor... try using nano:

```
nano /boot/grub/menu.lst
```

---

### Post by JoshuaRL on 2008-03-02
> **Tatty said:**
> If you are in a recovery console then [X]("http://en.wikipedia.org/wiki/X_Window_System") will not be loaded.  So gedit wont work as it is a grapical text editor... try using nano:

```
nano /boot/grub/menu.lst
```

Well, you'll need root priviledges to edit that file.  So try:
```

gksu nano /boot/grub/menu.lst

```

---

### Post by Tatty on 2008-03-02
> **JoshuaRL said:**
> Well, you'll need root priviledges to edit that file.  So try:
```

gksu nano /boot/grub/menu.lst

```

He will already have root privilages if he is already logged on as root.

Also gksudo is for graphical applications, so if a root password is required for nano you would need to use sudo.

---

### Post by Oldsoldier2003 on 2008-03-02
> **Tatty said:**
> If you are in a recovery console then [X]("http://en.wikipedia.org/wiki/X_Window_System") will not be loaded.  So gedit wont work as it is a grapical text editor... try using nano:

```
nano /boot/grub/menu.lst
```

Yep I'd say nano is a good choice, its quick and easy, unlike vi or emacs which take a lot of effort to learn. Learning vi or emacs is something not everyone is going to do, but the complete insistence upon coddling new linux people by using gui text editors really doesn't help them. A little guided command line action is a great experience for the newbies, it shows them the power of the terminal, and also teaches them not to be afraid of it.   Now if they had only left good enough alone and kept it named PICO, thank god for aliases....

---

### Post by JoshuaRL on 2008-03-02
> **Tatty said:**
> He will already have root privilages if he is already logged on as root.

Also gksudo is for graphical applications, so if a root password is required for nano you would need to use sudo.

Dude, you are so right.  I'm sorry I got two different threads mixed in my head.

---

### Post by Tatty on 2008-03-02
> **JoshuaRL said:**
> Dude, you are so right.  I'm sorry I got two different threads mixed in my head.

easily done, lol :popcorn:

---

### Post by Sirchristopher on 2008-03-02
I am having the same problem.   When I get to the place where I normaly have my GUI login screen I just have

kinit: No resume image, doing normal boot...

chris-laptop login:

I tried gksu /boot/grub/menu.lst

But I got

"Gtk-WARNING **: Cannot open display:

---

### Post by Tatty on 2008-03-02
> **Sirchristopher said:**
> I am having the same problem.   When I get to the place where I normaly have my GUI login screen I just have

kinit: No resume image, doing normal boot...

chris-laptop login:

I tried gksu /boot/grub/menu.lst

But I got

"Gtk-WARNING **: Cannot open display:


gksu only works for graphical applications.  As you are in a console you need to use "sudo".  so if you want to edit that file using nano you need to type:

```
sudo nano /boot/grub/menu.lst
```

---

### Post by Sirchristopher on 2008-03-02
Thanks, that got me in there but I don't thing that was the fix I needed. 

I took a break from Ubuntu for a while and just got back into it so I am again a complete noob.  I don't know what is causing the problem. 

 It started after I couldn't get Compiz to work.  I restarted and got the text based login screen.  I have tried everything from trying to reconfigure xserver toinstall ubuntu desktop with no luck .  :-(

---

### Post by Tatty on 2008-03-02
> **Sirchristopher said:**
> Thanks, that got me in there but I don't thing that was the fix I needed. 

I took a break from Ubuntu for a while and just got back into it so I am again a complete noob.  I don't know what is causing the problem. 

 It started after I couldn't get Compiz to work.  I restarted and got the text based login screen.  I have tried everything from trying to reconfigure xserver toinstall ubuntu desktop with no luck .  :-(

What exactly happened before it broke?

---

### Post by seventhc on 2008-03-02
Did you change anything with your vid card, or any xorg config?
you might need to run this
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by Sirchristopher on 2008-03-02
I found the answer in another thread...
[http://ubuntuforums.org/showthread.php?t=698043&highlight=login+problem&page=4]("http://ubuntuforums.org/showthread.php?t=698043&highlight=login+problem&page=4")

Now I have the GUI login, I am logged in, and need to fix the problem.

When I go to System, preferences, CompizConfig Setings Manager  and click on it nothing opens up.  I am just going to remove Compiz.  And see if that fixes it.

---

### Post by JoshuaRL on 2008-03-02
Before you try that, see what the error is.  Try the following in the terminal:
```

ccsm

```

---

### Post by Tatty on 2008-03-02
> **Sirchristopher said:**
> I found the answer in another thread...
[http://ubuntuforums.org/showthread.php?t=698043&highlight=login+problem&page=4]("http://ubuntuforums.org/showthread.php?t=698043&highlight=login+problem&page=4")

Now I have the GUI login, I am logged in, and need to fix the problem.

When I go to System, preferences, CompizConfig Setings Manager  and click on it nothing opens up.  I am just going to remove Compiz.  And see if that fixes it.

try:

```
sudo apt-get install compizconfig-settings-manager
```

if it says it is already installed, then try re-installing it

---

### Post by Sirchristopher on 2008-03-02
Sorry, already did it, but I reinstalled it and ran sssm and got...

AttributeError: 'compizconfig.Plugin' object has no attribute "Initialized'

---

### Post by Sirchristopher on 2008-03-02
When I click on the 'CompizConfig Settings Manager'  it still wont bring up the application.

---

### Post by JoshuaRL on 2008-03-02
So that error is when you try:
```

ccsm

```
right?

---

### Post by Sirchristopher on 2008-03-02
Right

---

### Post by JoshuaRL on 2008-03-02
Okay, lets go basic.

What card and what does your xorg.conf look like?

---

### Post by Sirchristopher on 2008-03-02
I know it's an Intel video card, how do I find out about the xorg.config?

---

### Post by Tatty on 2008-03-02
> **Sirchristopher said:**
> I know it's an Intel video card, how do I find out about the xorg.config?

```
cat /etc/X11/xorg.conf
```

---

### Post by Sirchristopher on 2008-03-02
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
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Driver          "intel"
        BusID           "PCI:0:2:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation Mobile 915GM/GMS/910GML Express Graphics Controller"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1280x800"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

---

### Post by mineirosotan on 2008-03-03
OK, my Evo n400c is up and running.  Removing "quiet" and "splash" from the grub parameters seems to have done the trick.

Thank you very much to all who posted suggestions.  I have to say, as a linux/ubuntu newbie, I'm pretty impressed with the speed of the response and viability of the solution.

And as a further comment/comparison between MS OS's and Linux...  I live in Brazil.  Most people here, as in most developing countries, don't have the money to buy new computers, especially with a configuration adequate to power something like Vista.  So, it seems that MS has more or less abandoned the developing world.  

So, from a socially responsible, technologically inclusive viewpoint... hats off and many thanks to Ubuntu and the greater Linux community.

In addition, I think using Linux and specifically distros built for older slower computers has environmental implications.  Fewer people needing to buy new computers, more people continuing to use older equipment and revitalizing older machines and using more energy efficient solutions (e.g. Via C3 processors)  rather than jumping on the consumerism, more and bigger is better bandwagon.

So again, I'm grateful for Linux and all the effort that people have put in to make it work.

---

