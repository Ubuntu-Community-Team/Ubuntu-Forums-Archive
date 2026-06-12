---
title: "Openbox help..."
date: 2005-09-10
forum: Absolute Beginner Talk
---

### Post by xequence on 2005-09-10
Yes, I know this question doesent matter to absolute beginners, but I asked a question in the community chat and it was moved. 

I installed openbox and I like it alot... I just wish it had a little dock on the bottom like fluxbox. I dont use fluxbox because wikipedia says it is slow on ubuntu and red hat, which it is... It takes awhile to load while openbox logs in and loads instantly.

It is annoying not knowing what time it is... And id like to swtich windows easier.

> patrick@ubuntu:~$ sudo apt-get install fbpanel
Reading package lists... Done
Building dependency tree... Done
The following NEW packages will be installed:
  fbpanel
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 88.6kB of archives.
After unpacking 373kB of additional disk space will be used.
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe fbpanel 4.0-1 [88.6kB]
Fetched 88.6kB in 2s (36.0kB/s)

Preconfiguring packages ...
Selecting previously deselected package fbpanel.
(Reading database ... 90715 files and directories currently installed.)
Unpacking fbpanel (from .../fbpanel_4.0-1_i386.deb) ...
Setting up fbpanel (4.0-1) ...

patrick@ubuntu:~$ fbpanel
Can't include /etc/fbpanel/menu
menu: plugin init failde
fbpanel: can't start plugin menu
fbpanel: can't start panel
patrick@ubuntu:~$
 

I used apt-get to get a panel but it wont work for some reason... WOnt load at all.

It is getting a little annoying how somethings just dont work and dont tell you why they arnt working :( And all this XML editing stuff, I dont understand it one bit :P

> Fluxbox can be very slow on some Linux distributions such as RH 9 and Ubuntu. One possible reason is that the Xfree server cannot handle UTF-8 font request very well. One workaround is to add export LC_ALL=C before Exec ..../fluxbox in the local ".fluxbox/startup" script. 

THats how wikipedia says to fix fluxbox... BUt there is no .fluxbox/startup folder.

Why is the dot in front of it anyway?

THanks :)

---

### Post by Muhammad on 2005-09-10
I use Fluxbox on Ubuntu, and it ain't slow at all... 0_o

I'm not really sure, but I advise you to look for it(fbpanel) in the session menu in the Login screen. ;)

---

### Post by xequence on 2005-09-10
I have it too, it just takes long to load the accual DE... Longer then gnome. Openbox is instant loading.

And the session button is for DEs... I am trying to get a dock for the DE ;)

Thanks anyway :P

EDIT: It says:

checking for X... no
configure: error: Hackedbox requires the X Window System libraries and headers.


When I try to compile hackedbox. I am downloading 50 MB of "X" development libraries...

---

### Post by Pete051 on 2005-09-12
I don't find fluxbox slow at all, in fact the only annoying thing I've found is that when I try to sudo it tells me it's the wrong root password and it's not very odd  :???:  but I'll find a solution sooner or later  O:) 
Pete

---

### Post by xequence on 2005-09-12
[QUOTE=Pete051]I don't find fluxbox slow at all, in fact the only annoying thing I've found is that when I try to sudo it tells me it's the wrong root password and it's not very odd  :???:  but I'll find a solution sooner or later  O:) 
Pete[/QUOTE]

For me it takes longer then gnome to load from gdm. Openbox loads in 2 seconds :)

---

### Post by thewayofzen on 2007-03-15
You could probably try something like pypanel.
When i use openbox i use it..  it will let you do pretty much anything u can with the fluxbox toolbar but has a few more options.  Some of the features include

-workspace name/changer
-transparency (simulated)
-task list
-launchers
-systemtray
-clock

Its in the repos.. though i suggest grabbing it here > [http://pypanel.sourceforge.net/](http://pypanel.sourceforge.net/)

Ive found some of the repos builds unfunctional.


Hope taht helps some..

Delaney!

---

### Post by kerry_s on 2007-03-15
Oop's, brain fart, i was thinking blackbox, skip the bb apps and go straight for wm dock apps.

There are a few ways you can go, instead of using a panel, you can use slit app. Just open synpatic, and have a look, there are several "bb" app's in including 1 for time, pager, run...You can also use wm dock app's, there are alot in the repos, you can check them out here and install them from synaptic if it's there-> [http://dockapps.org/](http://dockapps.org/)
The wmdrawer is a good launcher dock app.

Also what file manager are you using? Alot have a panel as a dependency and you can use them. Example thunar has xfce4-panel, nautilus has gnome-panel, rox has a panel to.

---

### Post by moore.bryan on 2007-03-16
> **thewayofzen said:**
> You could probably try something like pypanel.
When i use openbox i use it..  it will let you do pretty much anything u can with the fluxbox toolbar but has a few more options.  Some of the features include

-workspace name/changer
-transparency (simulated)
-task list
-launchers
-systemtray
-clock

Its in the repos.. though i suggest grabbing it here > [http://pypanel.sourceforge.net/](http://pypanel.sourceforge.net/)

Ive found some of the repos builds unfunctional.


Hope taht helps some..

Delaney!
*i second pypanel and make sure to grab the most current version (not the one in the repos).  you need to write a script to tell openbox to launch pypanel during load-up or include a line in your .xinitrc file.*

---

### Post by heathen on 2007-03-16
you could also try conky... i dont use the panel in fb, only reason i use fb over ob is i like the transparency.. so having conky to display time/date/other system data is nice...

---

