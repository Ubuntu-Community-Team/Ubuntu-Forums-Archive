---
title: "Unable to copy and paste to terminal"
date: 2007-11-29
forum: Absolute Beginner Talk
---

### Post by cub682 on 2007-11-29
I'm unable to copy and paste to UXterm or any run command.
I am running gOS which is based on Ubuntu/7.10 and it's my first time using Linux.
Thanks for any help.

---

### Post by executor on 2007-11-29
what i now is you have to use copy/paste from rigth clik whit the mouse, you cant use ctrl v/c

---

### Post by olejorgen on 2007-11-29
I don't know about UXterm, but in gnome-terminal the shortcuts are ctrl+shift+c/v.

Have you tried right-clicking on the selected text?

---

### Post by cub682 on 2007-11-29
Yes, I right click and highlight text and hit copy but cannot right click in terminal.

---

### Post by quandary on 2007-11-29
> **cub682 said:**
> I'm unable to copy and paste to UXterm or any run command.
I am running gOS which is based on Ubuntu/7.10 and it's my first time using Linux.
Thanks for any help.

I don't know UXterm, but maybe your xterm doesn't support copy/paste (rather unlikely).
go to a console and type:
apt-get install gnome-terminal

then you can start gnome terminal from UXterm by typing:
gnome-terminal

Gnome terminal surely supports copy/paste.
To copy press: CTRL + SHIFT + c
To paste press: CTRL + SHIFT + v

You can then create a shortcut to gnome-terminal, so you don't have to start it every time from UXterm.

---

### Post by rune0077 on 2007-11-29
You can also try highlighting what you want to copy, then go to where you want to paste it and press the middle button (the mousewheel) if you have one: this will copy whatever is currently highlighted and paste it into current location.

---

### Post by cub682 on 2007-11-29
> **rune0077 said:**
> You can also try highlighting what you want to copy, then go to where you want to paste it and press the middle button (the mousewheel) if you have one: this will copy whatever is currently highlighted and paste it into current location.

Well that works, Thanks!  I will also try the Gnome terminal.

---

### Post by cub682 on 2007-11-29
Copy and paste does work in Gnome terminal. How do I add it to my system tools?

---

### Post by cub682 on 2007-11-29
How do I add Gnome terminal to my system tools.

---

### Post by quandary on 2007-11-29
> **cub682 said:**
> How do I add Gnome terminal to my system tools.

Right click on desktop, select "create launcher"
In the dialog field appearing, type:
for name: gnome-terminal
for command: gnome-terminal
for comment: anything you want
Click OK

Then move the shortcut via drag and drop to where you want it to be.

---

### Post by cub682 on 2007-11-29
I guess this gOS configuration is different. A right click on the desktop brings up Favorite Applications. :(

---

### Post by koleoptero on 2007-11-29
The proper way to paste into the terminal is to use shift+insert. At least that's what I do.

---

### Post by quandary on 2007-11-29
> **cub682 said:**
> I guess this gOS configuration is different. A right click on the desktop brings up Favorite Applications. :(

Ah yes. gOS uses Enlightenment 17 Window manager, while standard Ubuntu uses Gnome.
I don't know about Enlightenment, but here some instructions copied from elsewhere:

----------------------------------
This is a quick guide to menu/launcher editing - but I haven`t done extensive testing. If all is well, I`ll add this to the howto. It deals mainly with creating entries, but will show the path to removing entries as well, using the .order files.

First off, launch the application you want to create an 'icon' for.

Click the top left corner (but not the border!) with the left mouse button and select "Create Icon". Note that you need e_utils (which needs e17/libs/engrave) installed in order for this to work. (You should have this package installed already if you followed the howto.)

An .eapp file will be created and moved to ~/.e/e/applications/all.

Next, you need to add this .eapp file to the relevant .order file. These order files are what e17 parses when starting the apps, and are stored in the following directories:

iBar: ~/.e/e/applications/bar
E17 menu: ~/.e/e/applications/favourite
Engage: ~/.e/e/applications/engage


Here's and example iBar .order file:

firefox.eapp
xmms.eapp
engage.eapp
entice.eapp
evidence.eapp

Note that you can also create subdirectories for the menu. Simply make directories within ~/.e/e/applications/favourite and create .order files in each one of them.

Here's an example:
assuming that you have the following directories

~/.e/e/applications/favourite/music
~/.e/e/applications/favourite/web

you can make a ~/.e/e/applications/.order which contains the following text:

terminal.eapp
music
web

This would create a menu that first shows the terminal icon and then has 2 directories - music and web. Following this system you'll also need to create .order files in those directories to select what .eapp files to have and in what order you want them to be in.


If you don`t want to create your own icons - the author of engage has a ton of them rolled already for your pleasure here ([http://aje.codewordt.co.uk/Files_files/applicatio](http://aje.codewordt.co.uk/Files_files/applicatio) ns.tar.gz) .

Note, that this has been heavily lifted from the site I linked to in the howto - but I`ve parsed it and packaged nicely for my fellow Ubuntians. :)
----------------------------

Good luck, and let us know if it works. :)

---

### Post by edm1 on 2007-11-29
> **rune0077 said:**
> You can also try highlighting what you want to copy, then go to where you want to paste it and press the middle button (the mousewheel) if you have one: this will copy whatever is currently highlighted and paste it into current location.

WOW!...and i've been using computers how long?

---

### Post by rune0077 on 2007-11-29
> **edm1 said:**
> WOW!...and i've been using computers how long?

Yeah, it's not so long ago I figured this out either. However, its only a Linux thing, 'cause once I did figure it out, I immediately booted up in Windows to see if I had wasted untold hours of my life doing Ctrl+C/Ctrl+V routines. But I hadn't. It doesn't work in Windows.

---

### Post by cub682 on 2007-11-29
I really appreciate all the help. This forum has helped me learn more then any other.
The gOS Official Forum - [http://cafelinux.org/gosforum/](http://cafelinux.org/gosforum/) -  A total joke.
The Everex Forum - [http://www.everexforum.com/forum/index.php?a=forum&f=40](http://www.everexforum.com/forum/index.php?a=forum&f=40) - An even bigger joke.

I have a lot more questions and hope I am welcome to post them here.

---

### Post by quandary on 2007-11-29
> **cub682 said:**
> I really appreciate all the help. This forum has helped me learn more then any other.
The gOS Official Forum - [http://cafelinux.org/gosforum/](http://cafelinux.org/gosforum/) -  A total joke.
The Everex Forum - [http://www.everexforum.com/forum/index.php?a=forum&f=40](http://www.everexforum.com/forum/index.php?a=forum&f=40) - An even bigger joke.

I have a lot more questions and hope I am welcome to post them here.

Sure, you're welcome to do so.
gOS is Ubuntu-based.
If you have a broadband internet connection, you might try:
apt-get install ubuntu-desktop
or
apt-get install gnome-desktop

Then you can have the real Ubuntu, instead of gOS ;-)

---

### Post by cub682 on 2007-11-29
> **quandary said:**
> Sure, you're welcome to do so.
gOS is Ubuntu-based.
If you have a broadband internet connection, you might try:
apt-get install ubuntu-desktop
or
apt-get install gnome-desktop

Then you can have the real Ubuntu, instead of gOS ;-)

I just tried and got this error.
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by quandary on 2007-11-29
you can either try 
sudo apt-get install gnome-desktop 
etc.
or use
su
(su = switch user) to become root.
then try apt-get again
The error messages should then disappear.

if the root account is enabled, you can also try to login as root.
The error messages should then disappear, too.


However, if the root account is disabled, you can't login as root. You then have to search the config file in which you can enable root login.

---

### Post by cub682 on 2007-11-29
I got a little farther but this error came up.

E: Couldn't find package gnome-desktop

---

### Post by quandary on 2007-11-29
> **cub682 said:**
> I got a little farther but this error came up.

E: Couldn't find package gnome-desktop

sorry, my fault. i meant ubuntu-desktop

---

### Post by bred on 2008-02-25
Thx man!
U saved me :))

> **olejorgen said:**
> I don't know about UXterm, but in gnome-terminal the shortcuts are ctrl+shift+c/v.

Have you tried right-clicking on the selected text?

---

