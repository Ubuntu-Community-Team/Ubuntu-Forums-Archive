---
title: "First Boot"
date: 2008-03-02
forum: Absolute Beginner Talk
---

### Post by marshall700 on 2008-03-02
first boot kind of failed....

It doesnt boot to the desktop instead it asks me to enter commands...... so i really haven no idea what to do any help would be apreciated?

---

### Post by Joeb454 on 2008-03-02
Do you have any errors?

More details would help us to further understand your situation :)

---

### Post by marshall700 on 2008-03-02
Well it doesnt come up with any errors it goes though all the [ok] steps and all say ok............

---

### Post by marshall700 on 2008-03-02
besides system clock thats the only one which doesnt say ok

---

### Post by Yes on 2008-03-02
Try entering the command 'gdm', and try pressing Ctrl + Alt + F7.

---

### Post by marshall700 on 2008-03-02
ok i now get:

/etc/gdm/failsafeXserver:Line 47:[:too many arguments
Warning: could not retrieve EDID because get-edid is not installed(1)
Warning: could not retrieve PCI IDs because discover is not installed (1)

: error: this program does not know how to configure the "10
shared/default-x-server doesnt exist" X server
Warning: Could not generate /etc/X11/xorg.conf.failsafe for vesa 
driver

That is now what i get when i installed GDM Ctrl+Alt+f7 does  nothing

---

### Post by marshall700 on 2008-03-02
Ok i installed EDID and discover now i just get:
etc/gdm/failsafeXserver:Line 47:[:too many arguments
 error: this program does not know how to configure the "10
shared/default-x-server doesnt exist" X server
Warning: Could not generate /etc/X11/xorg.conf.failsafe for vesa 
driver

---

### Post by Yes on 2008-03-02
Did you install from the graphical install disk or the alternate CD?  It seems like it didn't install the X server, which handles all the graphical... stuff.  You could install everything from the command line, but you would need to install a lot, and I'm not exactly sure what you would need to install.  I think it might be easier to just reinstall.

---

### Post by marshall700 on 2008-03-02
well in order to get this far i had to [http://ubuntuforums.org/showthread.php?t=713175](http://ubuntuforums.org/showthread.php?t=713175)
and format the whole pc so in order to reinstall i got to reinstall windows....... can i have a list of what to install lol

---

### Post by Yes on 2008-03-02
Start with xserver-xorg... that should install alot of other stuff with it.  I take it you want to install Gnome (instead of somthing like KDE or Xfce)?

---

### Post by marshall700 on 2008-03-02
At this point in time i dont care i can always go back over and install what ever

---

### Post by marshall700 on 2008-03-02
Hmmmmmm xerver-xorg is that the full name cause it aint letting me install it

---

### Post by Yes on 2008-03-02
Try running "sudo apt-get update".  Are you installing it with the command "sudo apt-get install xserver-xorg"?

---

### Post by marshall700 on 2008-03-02
yup im using sudo "apt-get install xserver-xorg" it comes up with error 

"dpkg was interurupted, you must manualy run 'dpkg --configure -a' to correct the problem"

with the update it updates somewhat then says the above error

---

### Post by Yes on 2008-03-02
Did you run 'dpkg --configure -a'?

---

### Post by coggins on 2008-03-02
xserver-xorg  not xerver-xorg.
EDIT: realised you only made that mistake once, but prob. worth checking in the CLI.

---

### Post by marshall700 on 2008-03-02
yup and it says

"requested operation requires superuser privilage"

---

### Post by Yes on 2008-03-02
Put sudo in front of it... 'sudo dpkg --configure -a'.  It'll ask you for a password, which is the same one that you set up when you installed Ubuntu.

When you enter your password, it won't print anything (not even *s).  Don't worry, it'll still get it.

---

### Post by marshall700 on 2008-03-02
Ok its now installing xserver what should i do after?

---

### Post by marshall700 on 2008-03-02
all that installed it asked me about video modes and then just went back to asking me for commands

---

### Post by Yes on 2008-03-02
Try starting gdm and see what happens (just run 'gdm').  It might be that gnome is already installed.

If nothing happens or you get an error (or it looks horribly buggy and incomplete), try installing 'gnome-about'.  It's not all that important of a program, but it should install all the necessary gnome files and programs with it.

e:  You might be able to just install 'gnome'.  It'll install a bunch of extra programs that normally aren't installed by default, but it's probably easier than installing them, one by one.  After you get everything working you can just uninstall everything you don't need.

---

### Post by marshall700 on 2008-03-02
"WARNING: GDM file gdm-daemon-config.c: lini2121 {}: Cannot run seteuid to 0: operation not permitted
GDM file gdm-daemon-config.c: line2121 {}@ Cannot run seteuid to 0: Operation not permited"

I installed gnome-about i get this error!

---

### Post by Yes on 2008-03-02
Did you run it as root (with 'sudo' in front)?

---

### Post by marshall700 on 2008-03-02
so sudo gdm?

---

### Post by marshall700 on 2008-03-02
ok ive tried that and it says WARNING: GDM already running. ABorting!

---

### Post by Yes on 2008-03-02
Try Ctrl + Alt + F7 again.

If that doesn't work, I would just reboot and see if it starts on its own.

---

### Post by marshall700 on 2008-03-02
Ctrl + alt + F7 brings up a black screen where nothing happens and i can ype anything nothing happens and a reboot does nothing either it doesnt start on its own!!!! and thanks for all the help btw i know its not fixed yet but..... stupid laptop

---

### Post by Yes on 2008-03-02
After you reboot, can you try starting GDM again?  If it says it's already running, try 'sudo killall gdm' and then starting it.

If all that fails, just try 'sudo apt-get install gnome'.

---

### Post by marshall700 on 2008-03-02
IM installing 'gnome" now its gonna take 10min or so long live 20mb internet connection.
ill post when its all been done thanks!

---

### Post by marshall700 on 2008-03-02
Well ive installed Gnome and well nothing seems to have changed, just rebooting see if that does anything

---

### Post by marshall700 on 2008-03-02
i think im going to try and find my windows XP disk put windows onthere and try a dual again

---

### Post by Yes on 2008-03-02
It really would be better to try reinstalling.  You're probably still missing some programs that for whatever reason weren't installed.

---

### Post by marshall700 on 2008-03-02
since i cant actually find my xp disk am just trying:

"sudo apt-get install ubuntu-desktop" im not sure if this will work but if not ill try and get hold of XP!!!

---

### Post by marshall700 on 2008-03-02
Ok that got it working.....

Thanks for all your help everyone who posted you made my life a lot easier!!!!

---

