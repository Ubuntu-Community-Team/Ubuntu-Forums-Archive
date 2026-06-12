---
title: "OpenOffice Logs Me Off!"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by Sinkingships7 on 2008-04-12
Whenever I try to click any of the menu bar items in any openoffice app, i'm kicked back the login screen.

Has anyone ever had a similar issue and does anyone know how I might be able to fix this?

I need to have a presentation done in 2 days!

Thank you so much to any responders.

---

### Post by Diabolis on 2008-04-12
Seems like open office is restarting your X session. Check your video card drivers and your X11 configuration. Also a lack of RAM could lead to this kind of error.

---

### Post by Sinkingships7 on 2008-04-12
> **Diabolis said:**
> Seems like open office is restarting your X session. Check your video card drivers and your X11 configuration. Also a lack of RAM could lead to this kind of error.

i'm going to take a guess here and say that my 2 GB's of dual channel RAM isn't he issue :p

i've never had any issues with my graphics drivers... compiz works wonders. how do i check my X11 config? i don't even know what that is or what to look for lol

i'm still somewhat new to ubuntu... maybe 4-5 months in.

go easy on me :)

---

### Post by Diabolis on 2008-04-12
Maybe the error is somewhere else, Run oppen office through the terminal, and see if you get any error messages.

xserver is the app that handles all the graphical stuff such as windows, mouse input etc.

You can see/edit its configuration file with this command:
```
sudo gedi /etc/X11/xorg.conf
```

or

This one will guide you through the reconfiguration of xserver
```
sudo dpkg-reconfigure xserver-xorg
```

You can test how well your graphics are being drawn with this command:
```
glxgears
```

---

### Post by bt224 on 2008-04-12
Could be that there is something wrong with the package. Open Synaptic, click on Edit>Fix Broken Packages. Hopefully it's that simple.

---

### Post by Sinkingships7 on 2008-04-12
> **bt224 said:**
> Could be that there is something wrong with the package. Open Synaptic, click on Edit>Fix Broken Packages. Hopefully it's that simple.

nope. that didn't do it.

@Diabolis:

the glxgears thing works perfectly.

will reconfiguring my xserver cause any problems? is it possible that i would encounter any issues by doing that?

---

### Post by Diabolis on 2008-04-12
Have you tried to run open office from the terminal to see if you get any error messages?

Also updating your system could help.
```
sudo apt-get update
sudo apt-get upgrade
```

Another option is to get the latest open office from [here]("http://www.openoffice.org/"), if you don't have it already. You would have to uninstall the old one.

---

### Post by Sinkingships7 on 2008-04-12
> **Diabolis said:**
> Have you tried to run open office from the terminal to see if you get any error messages?

Also updating your system could help.
```
sudo apt-get update
sudo apt-get upgrade
```

Another option is to get the latest open office from [here]("http://www.openoffice.org/"), if you don't have it already. You would have to uninstall the old one.

running it from the terminal presented no errors, but the problem still persists.

i ran those two commands, and to no avail.

reinstalling was my first idea, but i wanted to see if someone knew how to fix my current installation. do i have to download it or can i just go to the repos and reinstall? if so, what packages to i have to check?

---

### Post by Diabolis on 2008-04-12
If you install from the repository, chances are that you'll end up with the same problem. 

If you have the time give it a try and post back ;-D.

---

### Post by Diabolis on 2008-04-12
Just as a last hope, mark open office for re-installation in synaptic.

---

### Post by GOROSSI on 2008-04-12
make sure you mark for complete remove first to remove all configuration files

---

### Post by Sinkingships7 on 2008-04-13
i completely removed openoffice from my computer and downloaded 2.4 from their website. installation went fine (new icons ^_^), but the same thing still happens!

any other ideas?

---

### Post by Diabolis on 2008-04-13
Open office used to have similar problems because it wouldn't find fonts, It could also be related to your java installation or graphics card drivers. But I'm not really sure, since you have a good nvidia card.

It would be great if you had a error message from the terminal or maybe the contents of a log file kept by open office. I tried to search in my pc the log file, but no luck. maybe open office doesn't use one, not sure.

---

### Post by Sinkingships7 on 2008-04-14
Well, I just ended up deciding to reinstall Ubuntu -_-

It works now, of course. It's too bad we couldn't solve this issue for future users, though.



In better news, my new installation of Ubuntu seems to be extra stable. I think more than just one thing went wrong with my other installation.

---

