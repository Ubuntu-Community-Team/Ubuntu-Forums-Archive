---
title: "Lower Memory usage."
date: 2005-05-27
forum: Absolute Beginner Talk
---

### Post by served on 2005-05-27
I have 196 mb ram. I dunno why but ubuntu uses all most 90% of it and all the time.
So when i start to listen music then its not clean. How can i make it work with less resursses? Its really beag problem.
NB: i installed LILO boot loader and i have ubuntu 4.10.

---

### Post by dataw0lf on 2005-05-27
Try installing xfce4.  It's a less resource heavy window manager.

sudo apt-get install xfce4

At the gdm login greeting, change your session to 'xfce4'

---

### Post by served on 2005-05-27
Console says :Couldn't find package xfce4

---

### Post by Moobert on 2005-05-27
you can try lighter window managers like fluxbox...

[http://fluxbox.sourceforge.net/themes.php](http://fluxbox.sourceforge.net/themes.php)

theres a fairly new verson on the apt

apt-get install fluxbox

 (then just look for in on the login screen). My system on first load uses about 45mb...

Then it realy a case of using lighter memory apps like;

xterminal or xterm over gnome-terminal
abiword over openoffice writer

most kde apps are lighter than gnome app and do more :)

so konquerer over nautilus
kwrite over gedit (or nano over the both of them)

opera 8 seems to be far lighter over firefox too...

Also if fluxbox is abit to 'cut down' for you, (but you can get all your normal themes by using gtk-theme-switcher2 and kcontrol)... you can try xfce.

Using hoary might be an idea to, as it uses a never verson of X which is less memory heavy.

---

### Post by nocturn on 2005-05-27
[QUOTE=served]I have 196 mb ram. I dunno why but ubuntu uses all most 90% of it and all the time.
So when i start to listen music then its not clean. How can i make it work with less resursses? Its really beag problem.
NB: i installed LILO boot loader and i have ubuntu 4.10.[/QUOTE]

The amount of RAM used inlcudes buffers and caches.
Unix manages memory different from Windows, unused memory is taken to speed things up, the downside is that free memory is always shown to be low.

Try the free command, it will show what amount is allocated to buffers and cache.

---

### Post by served on 2005-05-27
But how can i install that? Im too nub and i dunno how to creat commands.
I downloaded that file manually

EDIT: ok i installed xmms package and its working now.

could some one write down here that comand line what insalles that fluxpox?
 But still want that some one teaches me how to install xfce4

---

### Post by Moobert on 2005-05-27
try running:

free -m

in a terminal then look at the...

-/+ buffers/cache: 

line... the first value is used ram, the next free ram.

As for installing flux/xfce, either load synaptic and search for and install 'fluxbox'or 'xfce4'

or type this into a terminal...

sudo apt-get install fluxbox

sudo apt-get install xfce4

You might need extra apt lists.. get them by following:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

there are varous other googies like fluxkeys and xfce apps you may want to install to...

With either flux or xfce installed logout of gnome and wait for the login menu then.. click the session button and pick fluxbox or xfce.. then login as normal.

---

### Post by served on 2005-05-28
well my problem is that i dont have these packages and it seems that i cant download them.
Where can i download them manually and how can i add them into the package manager?

NEw guestion: How can i change folder icons and stuff to make ubuntu look more simple? Like removing graphics and stuff. How can i create my own theme?

ADD: I tested that free -m command and it told me that 107 mb ram is used, its good but always can be better  ;-)

---

### Post by phen on 2005-05-29
[QUOTE=served]well my problem is that i dont have these packages and it seems that i cant download them.
Where can i download them manually and how can i add them into the package manager?

NEw guestion: How can i change folder icons and stuff to make ubuntu look more simple? Like removing graphics and stuff. How can i create my own theme?

ADD: I tested that free -m command and it told me that 107 mb ram is used, its good but always can be better  ;-)[/QUOTE]
 you don't have to download them manually! just look here:

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

there is a very good step-by-step procedure to add several repositories (= servers with thousands of packages on it). Then open a terminal and type:

sudo apt-get install fluxbox

apt-get will automatically download the package fluxbox and eventually other needed packages and install it.

you can install nearly everything with apt-get!

cheers,
kai

---

