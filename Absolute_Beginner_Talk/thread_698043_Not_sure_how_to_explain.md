---
title: "Not sure how to explain"
date: 2008-02-15
forum: Absolute Beginner Talk
---

### Post by m3_del on 2008-02-15
I want to start this by saying I have had a hard time searching for similar issues. Just not sure what word combo would work

That said, I have an issue with my fairly new Ubuntu Gutsy box. I was working on manually installing some dependencies  required to install Mpeg4IP and after I was unable to successfully build the Mpeg4IP package (another issue I am having) I rebooted. 

Now when my system comes up I log in and my background and mouse come up, but no user interface. All my normal services start up (sshd, net, fuppes, etc) but I am unable to do anything on the GUI session. I have checked my syslog and dmesg, nothing seems abnormal there. Please help! I am sorta familiar with Linux, but still consider myself a noob. Thanks in advance for any help :)

---

### Post by dstew on 2008-02-15
There is probably a problem with your xserver configuration, so you are not getting a graphical interface. Linux is still there, only the GUI is messed up.

There is a fairly easy way to re-configure the xserver. Get a command line interface by pressing ctrl-alt-F1 when you get to the messed up GUI interface. That key combination opens a terminal. Since the xserver comes as a debian package (all Ubuntu programs come as debian packages) you can use the command```
sudo dpkg-reconfigure xserver-xorg
```. After you reconfigure your xserver, enter the command ```
startx
```

---

### Post by spiderbatdad on 2008-02-15
As dstew said: although it is easier to add the -phigh option because not all users know how to navigate through the manual configuration...```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Regarding problems with compiling or installing dependencies, the build-essential package is often vital. ```
sudo apt-get install build-essential
```

---

### Post by m3_del on 2008-02-15
Ok I have run the reconfig. It did not fix the issue. Nothing has changed in my xorg.conf file from what I can tell. I think a package got messed up somewhere along the line. At first the top and bottom bars appear (just 2 solid gray bars) and the loading window appears (again solid gray) but then disapears as the wallpaper is being displayed. What is also interesting is that I can switch between virtual desktops using my scroll wheel of my mouse. Also the GUI displays for the volume buttons on my multimedia keyboard.

---

### Post by m3_del on 2008-02-16
Anyone have any suggestions? I suppose I don't mind being shell only but the gui would be nice. What are things/logs I should be checking that might lead me in the right direction? What are some good search terms. Anything at this point would be sweet. Thanks again!

---

### Post by Sidewinder1 on 2008-02-16
I'm a noob and this probably is not your problem but any issues I've had (not many) with the GUI have been solved by removing and reinstalling the nvidia restricted video driver. Have no idea how you'd do that from the command line. Not alot of help, sorry.

---

### Post by Darkade on 2008-02-16
Try to log into a "Safe GNOME" session (In your log in manager press F10 and select Safe GNOME session. If you have your session configured to start at boot then press CTRL+ALT+BACKSPACE to get to your log in mannager). Chances are that you'll be prompted with an error message suggesting what is wrong with your system. If it doesn't or cant solve it please copy the error message (if any) and we'll try to help :D:D

And sorry for the bad English.

---

### Post by kaginken on 2008-02-16
try disabling the compiz 'special effects' eye candy. (System -> Preferences -> Appearance -> Visual Effects). This locks up most of my laptops as none have very high end graphics cards.:guitar:

---

### Post by m3_del on 2008-02-16
> **kaginken said:**
> try disabling the compiz 'special effects' eye candy. (System -> Preferences -> Appearance -> Visual Effects). This locks up most of my laptops as none have very high end graphics cards.:guitar:

This is not the problem as I have been running this fine for some time now. Even if it were, I am unable to do anything in the GUI as mentioned at the beginning of the thread, making menu navigation just a bit tricky as it is not displaying. This issue occurred after trying to manually install some dependencies. The last one I can think of trying was wxWidgets. Things did not seem to go right during the install. Is this in any way a key component of gnome or X?

---

### Post by m3_del on 2008-02-16
OK after pressing ctrl+alt+backspace It takes me to the GDM login screen. Problem is that the screen is flashing, not typical flashing though. It is almost as if gdm is constantly loading and failing and loading and failing and so on and so on. I never get a chance to type. Typically my machine auto logs on so I never see the GDM screen anymore, but after initial install, obviously this was working just fine.

---

### Post by RomeReactor on 2008-02-16
Hi. What video card do you have, and which video driver did you choose when reconfiguring X? You may have a broken package, so try:
```
sudo aptitude update
```
If you get errors, try:
```
sudo aptitude install -f
```

---

### Post by m3_del on 2008-02-16
> **RomeReactor said:**
> Hi. What video card do you have, and which video driver did you choose when reconfiguring X? You may have a broken package, so try:
```
sudo aptitude update
```
If you get errors, try:
```
sudo aptitude install -f
```

I have a 6600 I chose the Nvidia driver over the nv as it has been working like that for over a month, until I started futzing around.

Also I assume those are equivalent to apt-get -f install and apt-get update    I have also run upgrade all with no luck.

The futzing done was manual not using the repos as most of the packages were not in the repos.

---

### Post by RomeReactor on 2008-02-16
Try the dpkg-reconfigure again, but this time select **nv** as the driver. I imagine the important thing for you is to get back to the GUI, so if you can get your desktop again using the nv driver, you can try to sort out the problem with the nvidia driver later (which I suspect has more to do with Compiz). Did you have Compiz enabled before? Did you get any warning about packages being removed when you tried to install Mpeg4IP?

---

### Post by m3_del on 2008-02-16
Ok I have switched to the nv driver. rebooted and the results remain the same. The UI flashes several times and then disappears. Is there any logs that would show what is crashing? Is there a way to rebuild all gnome/Xorg required packages?

---

### Post by Darkade on 2008-02-16
I had a similar problem with a computer just a week or so ago. The thing was that I accidentally removed some package that GNOME needs to run. In my case the computer logged in but never really loaded anything. So, have you recently removed anything and so by accident could you have removed some vital package? Because if that's it then you probably can solve it from a tty terminal

---

### Post by Darkade on 2008-02-16
> **m3_del said:**
> Ok I have switched to the nv driver. rebooted and the results remain the same. The UI flashes several times and then disappears. Is there any logs that would show what is crashing? Is there a way to rebuild all gnome/Xorg required packages?

Yes there is. ~/.xsession-errors log would help now. I dunno why I didn't though of it :P. Open it in a tty and post the last lines please. let's see if that may help

however I'm not sure if there is one for GNOME too :-k

---

### Post by m3_del on 2008-02-16
Here is the xsessions, definitely some issues here......

---

### Post by m3_del on 2008-02-16
Ok I ran sudo apt-get install libcairo2

This looked like it reinstalled the package (seems to be causeing all the problems) rebooted, no change.

I just went to sudo apt-get remove libcairo2 so I could then re-add it, but it looks like that would uninstall half of my system.

---

### Post by magicman5421 on 2008-02-16
Do you have anything vital that you can't back up? Because otherwise, reinstallation is a quick and easy fix for just about anything.

---

### Post by Darkade on 2008-02-16
try

sudo dpkg-reconfigure gnome-mount

that's the package I removed accidentally that time hehe. Just couldn't remember the name
ohh and if you get an error message that it is not installed then reinstall it by:

sudo apt-get install gonome-mount

---

### Post by m3_del on 2008-02-16
The backup would not be quick. It would take days to do over the wire. That is why I really would like to just fix this issue as is.

---

### Post by m3_del on 2008-02-16
No dice on the gnome-mount reconfig. I am trying that with libcairo2 and gnome-panel though. Will let you all know the results

Same as before. It seems the crux of the problems really lie somewhere with that libcairo.so.2 lib. Everything has symbol lookup failures with that file. And at the very top we have GTK warnings that don't look great, especially when it says refusing to initialize GTK+

---

### Post by m3_del on 2008-02-16
Here is the latest .xsessions

---

### Post by Darkade on 2008-02-16
I think this is the real ugly part. Sorry I can't helpt you (or try to help you) anymore for today, gotta go. I'll keep track anyway, since it sounds quite like a problem I had with another pc. Hope It all goes fine

** (x-session-manager:5710): WARNING **: Host name lookup failure on localhost.
Checking for Xgl: not present. 
Detected PCI ID for VGA: 03:00.0 0300: 10de:0141 (rev a2) (prog-if 00 [VGA])
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (1600x1200) to maximum 3D texture size (4096): Passed.
Checking for nVidia: present. 
Checking for FBConfig: present. 
Checking for Xgl: not present. 
Starting gtk-window-decorator
Initializing gnome-mount extension
gnome-panel: symbol lookup error: /usr/lib/libcairo.so.2: undefined symbol: FT_Library_SetLcdFilter
** Message: Starting remote desktop server

---

### Post by RomeReactor on 2008-02-16
Try booting into a previous kernel by pressing ESC before GRUB loads.

---

### Post by m3_del on 2008-02-16
When I go to the Grub menu I only see 3 options the same kernel version twice (one is recovery mode) and the memtest+

...

---

### Post by m3_del on 2008-02-17
Can someone help me turn off auto login from the command line?

Never mind, got that. Did not realize that they custom files is where that was located

---

### Post by m3_del on 2008-02-18
Anyone else willing to throw their hat in the ring? Any help to fix my blunder would be much appriciated

---

### Post by dstew on 2008-02-18
Do I dare? Anyway, the first error in your xsessions-errors shows that you are attempting to run GTK as suid root. This may have been the "root" of your problems. See [this]("http://www.gtk.org/setuid.html"). When you run a program suid root, then all the processes that are spawned by that program get root privleges. If any of those programs change something in your system, it can become unstable. Since GTK is so huge, that can lead to unpredictable changes in your system.

I am not sure if fixing it would help. You might check the permissions on the file /etc/x11/gdm and see if the suid bit is set (shows up as an 's' in the permissions). If so, you can try to change it with chmod uog-s

However, I am just guessing, throwing out a possibility.

---

### Post by m3_del on 2008-02-18
I went to go check and the file /etc/X11/gdm does not exist.....is it perhaps somewhere else?

---

### Post by dstew on 2008-02-19
Try```
locate gdm
```If your gdm system is broken, you have big problems. If that is the case, you can do```
sudo apt-get install ubuntu-desktop
```That will re-install gdm, and a lot of other stuff, without removing your /home folder. But, it takes about 1 and 1/2 hours over a DSL connection.

I don't know if you can just install gdm or not, without installing the whole Ubuntu desktop.

---

### Post by m3_del on 2008-02-19
When I run sudo apt-get install ubuntu-desktop it says it is all up to date. When I run with the --reinstall tag it takes about 2 minutes and reinstalls just the one package.

---

### Post by dstew on 2008-02-19
I guess it is only installing the packages it thinks it needs, so it is essentially doing an update. To really re-install it, you will have to remove it first:```
sudo apt-get remove ubuntu-desktop
```then re-install it. But, that is pretty radical surgery. I don't think this will delete your /home directory, or other installed programs, but I really don't  know. It might be wise to back things up. You are getting close to a total re-installation with this.

EDIT: I think to really remove the ubuntu-desktop you might need to use apt-get remove --purge ubuntu-desktop
EDIT again: You can also try to reinstall, or re-configure the gdm package. It is the main display engine, and it seems to be the thing giving problems. Maybe try sudo dpkg-reconfigure gdm.

---

### Post by m3_del on 2008-02-20
Thank you I will try this when I get back home and post the results!!!


Edit: How do I go about having it uninstall and reisntall the desktop and all of the dependancies? Everything I do just unloads and reloads the ubuntu-desktop package and nothing else....

Ok I did a sudo apt-get remove --purge gdm

gonna reboot and reinstall and see if that changes anything

---

### Post by m3_del on 2008-02-23
Ok, I have decided to do a 

```

sudo apt-get remove libx11-6

```

This removed just about everything but the base system. The problem I have now is that it also removed my networking. I have downloaded the alternate cd and ran

```

sudo apt-cdrom add

```

It says it added it to my sources.list. I then run an update and then try installing ubuntu-desktop but there is no love. How can I at least get my networking working again so I can pull sources off of the internet again.

---

### Post by dstew on 2008-02-23
What error message do you get when you try to install ubuntu-desktop?

---

### Post by m3_del on 2008-02-23
Got thruogh that fiascal. I am right back to where I was in the begining. If I turn off auto logon, the GDM screen just loads and reload, etc and etc. If I set it to auto logon, GNome loads but the gnome menu bars flash of and on about 5-6 times and then just go away, the mouse works but not hotkeys or anything.

This has me thinking that it is something ina a config file somewhere. I wonder if I should have done a --purge when removing the libx11-6 and maybe I should have removed a key gtk library that most gnome compnents rely on. Anymore help as I move forward. 

I am ordering a external HD for backing up my data, but I would still like to try and resolve my issue.

---

