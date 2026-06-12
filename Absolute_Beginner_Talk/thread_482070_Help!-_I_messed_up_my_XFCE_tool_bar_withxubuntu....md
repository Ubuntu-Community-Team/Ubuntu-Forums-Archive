---
title: "Help!- I messed up my XFCE tool bar with/xubuntu..."
date: 2007-06-23
forum: Absolute Beginner Talk
---

### Post by zazen666 on 2007-06-23
Hi,
I was trying to install a temprture monitor and followed the below advice, which I found here:


LINK
[http://ubuntuforums.org/showthread.php?t=282415&highlight=tempreture](http://ubuntuforums.org/showthread.php?t=282415&highlight=tempreture)

ADVICE
"I use the cpufreq monitor gnome applet to monitor my system's tempreture.

If you wan to give it a try copy this to a terminal.
Code:

sudo aptitude install gnome-cpufreq-applet

After the installation right click on the top panel select add to panel, you will find cpufreq-monitor at the bottom.""

Well, I guess I want not supposed to do this with my latest version of xubuntu. There is no temprture montitor for one, and not, the tool bar has frozen, clicking on icons has no effect...

How can I undo what i did?
Thanks so much


__________________

---

### Post by zazen666 on 2007-06-23
using this command, i get the following out put:


marshal@marshal-laptop:~$ sudo aptitude purge gnome-cpufreq-applet
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
marshal@marshal-laptop:~$

---

### Post by zazen666 on 2007-06-23
Here is what I orginially did...

Can I just purge gnome applets?



marshal@marshal-laptop:~$ sudo aptitude install gnome-cpufreq-applet
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
Note: selecting "gnome-applets" instead of the
      virtual package "gnome-cpufreq-applet"
The following NEW packages will be automatically installed:
  alacarte capplets-data cli-common deskbar-applet desktop-base 
  evolution-data-server evolution-data-server-common gnome-about 
  gnome-applets-data gnome-control-center gnome-desktop-data 
  gnome-doc-utils gnome-media gnome-menus gnome-netstatus-applet 
  gnome-panel gnome-panel-data gnome-power-manager gnome-session 
  gnome-system-monitor gnome-user-guide gnome-utils imagemagick libbeagle0 
  libcamel1.2-10 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 
  libeel2-data libegroupwise1.2-13 libgconf2.0-cil libgdiplus 
  libglade2.0-cil libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil 
  libgnome-menu2 libgnome-window-settings1 libgnome2.0-cil 
  libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomevfs2-extra 
  libgtk2.0-cil libgtkhtml3.14-19 libgucharmap6 liblpint-bonobo0 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil 
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil 
  libmono-system-data2.0-cil libmono-system-web2.0-cil 
  libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil 
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libslab0 libsoup2.2-8 
  libungif4g libxml2-utils menu menu-xdg metacity mono-common mono-gac 
  mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data 
  python-beagle python-gmenu python-gnome2 python-gnomecanvas python-soappy 
  tomboy xsltproc yelp 
The following NEW packages will be installed:
  alacarte capplets-data cli-common deskbar-applet desktop-base 
  evolution-data-server evolution-data-server-common gnome-about 
  gnome-applets gnome-applets-data gnome-control-center gnome-desktop-data 
  gnome-doc-utils gnome-media gnome-menus gnome-netstatus-applet 
  gnome-panel gnome-panel-data gnome-power-manager gnome-session 
  gnome-system-monitor gnome-user-guide gnome-utils imagemagick libbeagle0 
  libcamel1.2-10 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 
  libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 
  libeel2-data libegroupwise1.2-13 libgconf2.0-cil libgdiplus 
  libglade2.0-cil libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil 
  libgnome-menu2 libgnome-window-settings1 libgnome2.0-cil 
  libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomevfs2-extra 
  libgtk2.0-cil libgtkhtml3.14-19 libgucharmap6 liblpint-bonobo0 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil 
  libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil 
  libmono-system-data2.0-cil libmono-system-web2.0-cil 
  libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil 
  libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libslab0 libsoup2.2-8 
  libungif4g libxml2-utils menu menu-xdg metacity mono-common mono-gac 
  mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data 
  python-beagle python-gmenu python-gnome2 python-gnomecanvas python-soappy 
  tomboy xsltproc yelp 
0 packages upgraded, 88 newly installed, 0 to remove and 0 not upgraded.
Need to get 56.2MB of archives. After unpacking 234MB will be used.
Do you want to continue? [Y/n/?] y

---

