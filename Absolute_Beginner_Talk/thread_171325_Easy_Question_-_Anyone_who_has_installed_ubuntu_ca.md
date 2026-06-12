---
title: "Easy Question - Anyone who has installed ubuntu can help.  Installing Apps"
date: 2006-05-06
forum: Absolute Beginner Talk
---

### Post by amsgwp on 2006-05-06
Make biggest concern with linux is how the distros come with about a 1000 apps that I dont know what the hell are.  My Fedora install is ridiculous I dont know what any of the apps are or what they do.  So my goal with ubuntu is to have an install with just the base o/s and config apps and then add all the apps I want on my own.  Since the sticky has that awsome conversion chart this should be very easy.  So is it possible to make ubuntu install without any extras?  Are there somethings that I need to make sure to include?  I've never even ran the installer so I don't know what to expect.

thanks,
Austin

---

### Post by Peter76 on 2006-05-06
Just do the normal install thing. Ubuntu is quite clean by default. You can always easily uninstall what you don't want.

---

### Post by ds[de] on 2006-05-06
As far as I know, the smallest install you can get (i.e. the least packages installed) is with the 'server' or 'base' install.
When booting from the Ubuntu install CD, you'll be asked whether to install the 'normal' ubuntu (with X.org and KDE or Gnome included) or just the server-install, with only neccessary packages (and some "extras" like ssh I think). Just type 'server' in that prompt, you won't have any desktop environment, only console. But this is probably the best way to only install the packages you want or to know exactly what is being installed, since KDE/X.org/Gnome/Xfce and so on install a lot of package since they depend on a lot of libraries.

Regards,
ds[de]

---

### Post by monomaniacpat on 2006-05-06
That doesn't work as the hosts list works on the assumption of static IP's. However, a quick google was sufficient to turn up the answer. I simply had to go to system properties on Windows and look under the 'Computer Name' tab. Entering the 'Full Name' into /etc/cups/printers.conf. allowed me to connect successfully.

Thanks though.

---

### Post by gr0kzer0 on 2006-05-06
> Make biggest concern with linux is how the distros come with about a 1000 apps that I dont know what the hell are. My Fedora install is ridiculous I dont know what any of the apps are or what they do. So my goal with ubuntu is to have an install with just the base o/s and config apps and then add all the apps I want on my own.

Ubuntu isn't like Fedora. You do the default install, you get one web browser, one email agent, etc, one of everything. Then you can change them or add others after.

---

### Post by gr0kzer0 on 2006-05-06
Whoops! Accidently posted rwice...

---

### Post by AnRuaRi on 2006-05-06
The basic install contains links to repositories. these contain 1000's of applications available to install, but not yet installed. dont worry about them. just do a basic desktop install, then add any packages you want.
 The easiest thing is to install Automatix, (search for it on this forum) and pick the tick boxes for the apps you think you will need.

---

### Post by amsgwp on 2006-05-08
thanks for the response.  That really helps me out and makes my day.

---

### Post by user1397 on 2006-05-08
If you uninstall the apps that are there right after a fresh install, then the ubuntu-desktop package will be removed automatically, because it depends on those.  If you do remove some apps,  then ubuntu -desktop will be uninstalled, and next time you log out/restart/shut down, you will have no more desktop, just a black and white terminal.  If it comes to that, don't freak out though.  You can always do 
```
sudo apt-get update 
```
and then 
```
sudo apt-get install ubuntu-desktop
```
(this takes a long time, by the way)
and then you will be back to your good-ol' GNOME desktop environment.

---

### Post by jasay on 2006-05-08
[QUOTE=erik1397]If you uninstall the apps that are there right after a fresh install, then the ubuntu-desktop package will be removed automatically, because it depends on those.  If you do remove some apps,  then ubuntu -desktop will be uninstalled, and next time you log out/restart/shut down, you will have no more desktop, just a black and white terminal.  If it comes to that, don't freak out though.  You can always do 
```
sudo apt-get update 
```
and then 
```
sudo apt-get install ubuntu-desktop
```
(this takes a long time, by the way)
and then you will be back to your good-ol' GNOME desktop environment.[/QUOTE]You can remove the ubuntu-desktop package and still have a graphical interface.  In fact, removing the ubuntu-desktop package doesn't remove any software from your computer at all.  It's simply a meta-package that depends on all of the other software in a normal default install.

---

### Post by user1397 on 2006-05-08
[quote=jasay]You can remove the ubuntu-desktop package and still have a graphical interface.  In fact, removing the ubuntu-desktop package doesn't remove any software from your computer at all.  It's simply a meta-package that depends on all of the other software in a normal default install.[/quote] Reaally? That's weird because when I removed it, the exact scenario that I described happened to me!

EDIT: I remember now what I actually did! I tried removing all of the kde-dependent programs and libs(after installing kde-desktop and not liking it) with some crazy thread, that actually removed my ubuntu-desktop and all of the core programs.  Still, I did those commands I mentioned before, and so I fixed my problem (none of my settings or /home folder files were gone!)
So follow  jasay's advice.

---

### Post by catlett on 2006-05-08
Do the server install like the above post said but you'll have to do a bit of research to install what you want. the ubuntu-desktop has alot by default. without it you'll have to install the x window system and a window manager etc all by command line.you'll have the system you want but you need to make sure you know what you want and how to install it without a metapackage.
I ran into this when I installed debian. I ended up with the debian server base and I had to install everyhting on top to have a gnome desktop.

---

