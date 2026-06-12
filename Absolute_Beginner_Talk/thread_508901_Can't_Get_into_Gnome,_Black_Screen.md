---
title: "Can't Get into Gnome, Black Screen"
date: 2007-07-24
forum: Absolute Beginner Talk
---

### Post by dylan623 on 2007-07-24
Hello, beginning yesterday I haven't been able to go into Gnome. Soon after I get to the splash screen, the screen goes black and I can't do anything. I waited for a few minutes and nothing happened, and I was not able to turn it off except by taking out the battery. I am able to use KDE as if nothing was wrong, but Failsafe Gnome and E-Gnome also do not work. In E-Gnome I get a message saying something about the Session Manager not being able to be found. I don't remember making any system-wide changes the day before, but I did uninstall glade-common and installed glade-gnome. I did the reverse yesterday, but it didn't change anything. I also changed the theme to a Mac OSX-style one, but I doubt that could cause this. Does anyone know what could be going on?

---

### Post by bigfox on 2007-07-24
using the Synaptic Package Manager

Find the ubuntu-desktop package and mark it for reinstallation.

Then apply the settings.

Hopefully that will fix the problem with gnome.

It may take a while do re install all the packages.   It may also ask for the Ubuntu disk you used to install originally.

Hope that works for you.

---

### Post by Gen2ly on 2007-07-24
Isn't this a "Desktop Effects" problem? Start a fail safe session and and try to disable it.

---

### Post by dylan623 on 2007-07-25
> **bigfox said:**
> using the Synaptic Package Manager

Find the ubuntu-desktop package and mark it for reinstallation.

Then apply the settings.

Hopefully that will fix the problem with gnome.

It may take a while do re install all the packages.   It may also ask for the Ubuntu disk you used to install originally.

Hope that works for you.

Ok, I will try that when I go upstairs.

" 	Isn't this a "Desktop Effects" problem? Start a fail safe session and and try to disable it. "

It doesn't work on fail safe either. As far as I know, I don't have Desktop Effects enabled.

---

### Post by dylan623 on 2007-07-25
I tried what you said, and I still can't get in. This also happens when I log out, but it's been like that ever since I installed Ubuntu.

---

### Post by dylan623 on 2007-07-25
I followed most of the advice here [http://ubuntuforums.org/showthread.php?t=490144](http://ubuntuforums.org/showthread.php?t=490144), but I still can't get it to work. I really need help here.

---

### Post by anewguy on 2007-07-25
Can you log into a terminal by ctrl-alt-F2 even with the black screen?  If so, do the following:

(1)  cd /etc/X11

(2)  ls -al xorg.*

(3) in the list from (2), search for xorg.conf and xorg.conf~ (or maybe "backup").  If you find one of those, check the date and time and see if it is before you started having problems.  If so:

     -   sudo  cp   xxxxxxxxxxx   xorg.conf    <- where xxxxxxxxxxx is the xorg.conf~ or backup file

(4) sudo gdm restart

(5) if nothing happens after (4), type:
    
      -    sudo gdm start

(6) do ctrl-alt-F7 and see if you have a regular logon screen now.

Please post back what happens.:)

---

### Post by dylan623 on 2007-07-26
> **anewguy said:**
> Can you log into a terminal by ctrl-alt-F2 even with the black screen?  If so, do the following:

(1)  cd /etc/X11

(2)  ls -al xorg.*

(3) in the list from (2), search for xorg.conf and xorg.conf~ (or maybe "backup").  If you find one of those, check the date and time and see if it is before you started having problems.  If so:

     -   sudo  cp   xxxxxxxxxxx   xorg.conf    <- where xxxxxxxxxxx is the xorg.conf~ or backup file

(4) sudo gdm restart

(5) if nothing happens after (4), type:
    
      -    sudo gdm start

(6) do ctrl-alt-F7 and see if you have a regular logon screen now.

Please post back what happens.:)
Nope, I can't do ANYTHING while it's like that. I tried what you said, but it still goes black.

---

### Post by dylan623 on 2007-07-26
Come on, I really need your help.

---

### Post by dylan623 on 2007-07-26
*bump*
Does anyone have an answer?

---

### Post by dylan623 on 2007-07-27
This is getting ridiculous, I COMPLETELY removed practically all my Gnome packages, but it STILL keeps doing this. I have no idea what to do now.

---

### Post by zoroko on 2007-08-12
Im havint the same problem.. but my screen gloes all white.

I can however get into a terminal by alt+ctrl+f2, and Ive tried replacing my xorg.conf with older versions, but that doesnt fix it. gnome failsafe doesnt work.  

I have tried sudo dkpg-reconfigure xserver-xorg and that doesnt work either..

Does anyone have an answer?

EDIT:

It has to have something to do with my beryl  installation, or something that im running as Im starting gnome. Heres is why I think that.

When i change the config files around sometimes I get the blue screen saying that x is broken... i say ok and it takes me to console without gdm running, so then i run sudo dkpg-reconfigure -phigh xserver-org and then do sudo startx and then im logged in as root and everything works fine, How can i change my users start up session from root or from a terminal? I have beryl and AWN, so Im thinking that something has gone awry.

EDIT 2:

SO far Ive found a fix that works for me.. Some how by the grace of the Gnome gods, gnome failsafe allowed me in once, from there i disabled beryl from start up sessions. restarted and from then on it has let me in, i found that after doing dkpg-reconfigure xserver-xorg my restricted drivers were not being used.I tried running beryl when i logged in and the same thing happened as before, so then i restarted and I noticed that they werent being used so i opened up the restricted drivers dialogue, i clicked and enabled them, it downloaded and installed them. Now I  am running beryl just fine and it is working properly, I havnt restarted the comptuer yet, but i will shortly and see how it goes. If all is well I'll reenable it in start up sessions and see how it goes.

i guess i got lucky

I hope this helps someone

---

### Post by anewguy on 2007-08-13
IF you can ctrl-alt-F2 and get to a terminal Window, try:

- via sudo apt-get remove  xxxxxxx   , try removing beryl, compiz, and desktop effects

- type  vi /etc/X11/xorg.conf

Scroll thru this until you see your default video card/controller.  Move the cursor over to the beginning of the driver name, then press the "insert" key on your keyboard.  Type in vesa, press the esc key, then use the delete key to remove the old driver name.  Next press the ":" key on your keyboard then type write and press enter.  Press the ":" key again and type quit and press enter.  Now type in:

shutdown -r now       and press enter.  This will restart your PC.  When it is up, report back as to whether or not your problem is gone.:)

---

### Post by anewguy on 2007-08-13
One other thing, if you get to a log on screen, look in the bottom left for the word "Options".  Click it and scroll up to "Sessions", then click the "Gnome" button.  It may be that it was perhaps stuck in a xgl or other session - that would explain why it would say session manager couldn't find xxxxx and I think you probably would have been in a different session type if trying out desktop-effects or beryl/compiz.:)

---

### Post by erginemr on 2007-10-16
Apparently long time has passed since your problem. Have you managed to solve it already, because I also had a similar experience. 

That was because I had enabled "accessibility" option in the Login Manager dialog out of curiosity, and could not see the login window any more. Besides, this may be a mis-cinfiguration of your graphic card. For instance, for NVidia cards, using the default generic NVidia driver in xorg.conf can bring back your desktop. 

You should change the "nvidia" to "nv" for this effect in the section:

Section "Device"
   ...
   Driver "nvidia"
   ...
EndSection

---

