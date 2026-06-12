---
title: "GUI for Server install? (was: total newbie question)"
date: 2006-10-11
forum: Absolute Beginner Talk
---

### Post by deshawn on 2006-10-11
hi all,
a very simple question from someone who knows nothing about the Ubuntu server,but trying to learn.
most linux distros ive tried had graphic interfaces,and windows easy for newbies to get used to.
my question is this,is there one in the Ubuntu server or am i basically stuck with the command line interface.or can i easily install a graphical interface.?
(the Ubuntu server did not install with a desktop)

thanks

---

### Post by Endwin on 2006-10-11
The idea behind the no graphical interface for the server is that this uses less resources, and is more secure (If you run less stuff the less there is to exploit). With this in mind, yes you can install a graphical user interface.

```
sudo aptitude -R install ubuntu-desktop
```

or if you have a slower machine..

```
sudo aptitude -R install xubuntu-desktop
```

If you plan to really use a server on-line it may be a good idea to learn the command line way to install, manage, and use the server.

---

### Post by bulldog on 2006-10-11
You're basicly stuck with the command line but you can easely install a GUI.:D

---

### Post by deshawn on 2006-10-11
hi thanks for the replies,
Endwin,
i can understand the securety etc,
for the more experienced users im sure its awesome,
personally i have a fair amount of resorces etc,but implementing them is a chore for me as im unfamiliar with just command line options.
but thanks for the "heads up" on that.ill keep it in mind,and ill go give it a shot and post back.

bulldog,you got a point there hehe.

thanks
:mrgreen:

---

### Post by Brunellus on 2006-10-11
thread title changed to better reflect nature of the help request.  In the future, use the thread title to reflect the TYPE of help you're looking for, so users who know HOW to help you can know that they CAN help you.  This is the newbie forum.  You are presumed to be new.  Begging for mercy by posting "total newbie question!" is unlikely to get you good technical help.

Servers in their purest sense are headless machines serving up content.  It is perfectly possible to administer and run a server remotely over ssh using the command line--and in most cases this is preferable.

If you wanted a graphical desktop, you can simply install the necessary packages.  

I would encourage you to learn the command line, however.  It is powerful and efficient.  I find it actually LESS irritating than having to go to GUIs all the time.

---

### Post by deshawn on 2006-10-12
ok, it was a little time consuming 
but Endwin, that worked out perfect besides a couple font cache rebuilding errors,
thanks again
and sorry the wording of the topic etc.wont happen again.

---

### Post by Endwin on 2006-10-12
The font cache errors are ok as I recall. I am not sure why this happens but linux and fonts never want to play nice together. As everyone else said try and learn the command line (its scarry and diffrent at first but you start to like it after using it for a while). A thing to try might be is find the config files for what you want to do, do it by the GUI and see how the files have changed. It can be educational, also there are many guides on-line for a lot of the common command line tasks/setup you would want to do with a server.

---

### Post by mips on 2006-10-12
A better option would be to use a remote gui app like webmin. This way you keep X off the server.

---

### Post by Abhi Kalyan on 2006-10-24
1. Need to shift 150 users to UBUNTU under 45 days](*,) 
2.Creating Domain in Server
3.Authenticating users on this server
4.File sharing- with group based security
5.Mounting remote folders/drives (etc) on logon
6.Sharing Internet

Hi! Abhi Kalyan And am a new bie too!- 
Thank you, because of this thread am currently installing GUI on the server
Tahnk you all once again:)

---

### Post by brentoboy on 2006-10-24
instead of apt-getting the entire ubuntu-desktop.  you might consider a "best of both worlds" approach to Servier-GUI-ness.

140 clients is a decent number.  If you had 5 or 10, I would say "who cares, add the GUI -- you'll never notice it"  But, 140 clients is probably worth taking the time to squeeze out the best you can get.

install an empty "server" install (not the lamp stack -- unless you want all that stuff) I mean the bare bones minimal install.

when it kicks you to a command prompt after the first boot to the new system:
```

cd /etc/apt

#always backup the original before ruining a file
sudo cp ./sources.list ./original.sources.list

#give yourself the Universe and Multiverse Repos
sudo nano ./sources.list
#Edit the file by removing the "#" that comment out the universe lines
#save the file

#make sure you have the latest pathes
sudo apt-get update
sudo apt-get upgrade

#now add a simple core
sudo apt-get install x-window-system-core xfonts-base xserver-xorg xterm firefox leafpad synaptic openbox gkrellm feh emelfm mc openbox-themes obconf

```

“x-window-system-core , xfonts-base, xserver-xorg” are your basic gui system – they are not optional.

“xterm” is a terminal emulator for use inside of the gui environement – not optional.  If you want to swap it out for aterm or some other terminal emulator – go ahead, just dont bother me about it if it doesnt work.

“firefox”  You need a functional browser, and firefox works great.  some people say “that is too bloated for my server” but honestly now, most of the time, you arent even running the GUI, so it isnt taking up memory.  And, when you need a browser on your server for whatever you want something that works. 

“leafpad”  leafpad is my text editor of choice.  it is a lot like mousepad (the xfce4 text editor) I chose it because it is desktop agnositc, and therefor has no extra dependancies that arent needed.  I also choose it because it is feature rich and easy to use, and it is designed to be easy on day one, very very easy learning curve. 

“synaptic”  Synaptic is the GUI equivalent of apt-get.  Strictly speaking, it is not necessary, but I recommend it because package management is a fundamental part of system administration.  If you arent interested in gui tools that make adminstration point and click, what are you doing here in the first place?

“openbox”  Openbox is a Window Manager. Openbox is my favorite light weight window manager.  It is very very minimalistic.  Right click the desktop -> you get the menu.  Excelent choice for servers.

“gkrellm” is a nice little application that charts CPU, disk and active net interfaces in a graphical feedback sort of way.  It is a wonderful way to see how much of your systems resources are in use.  And, when your server is running a gui, it is nice feedback to have.

“feh” feh serves two purposes: It lets you set background to something other than the default X black and white dithered eye-crushing background, and it is a small image viewer that will let you view jpgs and things down the road if you need to.  I highly recommend it, if you dont want it, dont install it.

“emelfm” is a file manager that implements the popular two-window design. It features a simple GTK+ interface, a flexible file typing scheme, and a built-in command line for executing scommands without opening an xterm.   

“mc”  Midnight Commander is a text-mode full-screen file manager, somewhat akin to the Xtree Pro Gold file manager for DOS that was popular in the pre-windows 3.1 days.  It also implements the popular two-window design like emelfm, but it has the advantage of being available even if you are not running the X gui system.  It also includes a subshell for command execution, as well as an internal editor with syntax highlighting and an internal viewer with support for binary files.

“openbox-themes” these are optional but quite small, so I install them.  You need this package in order to have choices about how window decorations look inside of openbox. Feel free not to add this one

“obconf” this also is for managing the minimal eye-candy available inside of openbox, if you dont care what fonts are used, and just want a functional system, you can conveniently not install this package without running into any whiplash.

---

now, before you start your gui, lets pretty it up a bit (believe me, this is necessary)

#go to the home directory of the primary administrator, not ROOT, a person with sudo ability.  You will *never* start X as root -- that is considered poor form, and for good reason.

```

cd ~
nano .xinitrc

```

put this inside there:
```

feh --bg-scale /etc/xdg/openbox/bg.png &
gkrellm &
x-terminal-emulator &
exec openbox

```

that will give you a pretty background, automatically open gkrellm, a terminal, and launch openbox for you when you "startx"

in order to have a nifty background you will have to get one and put it here: /etc/xdg/openbox/bg.png
(if you get a jpg, you should fix it in .xinitrc -- but I recommend a png because they generally require less resources)

to get a graphic, go to gnome-look.org and find a url to download, or just use this one:
[http://www.gnome-look.org/content/pre1/47154-1.png](http://www.gnome-look.org/content/pre1/47154-1.png)

```

cd /etc/xdg/openbox
wget http://www.gnome-look.org/content/files/47154-Ubuntu_CrystalSoul_1024x768.png  
cp ./47154-Ubuntu_CrystalSoul_1024x768.png  ./bg.png

```

that will download a decent background and name it correctly so that your xinitrc file will display it for you.

anyway, now would be a good time to launch a gui...
```

startx

```

when you are done with your gui (durring normal server operation, the gui isnt important...)  close it.  Right click the desktop, and exit openbox.  it will take you back to the prompt, and you can "exit" your way back to the login screen.

---

### Post by brentoboy on 2006-10-24
> **Abhi Kalyan said:**
> 
1. Need to shift 150 users to UBUNTU under 45 days](*,) 


Good luck, this might be difficult for someone new to Ubuntu

> 
2.Creating Domain in Server
3.Authenticating users on this server
4.File sharing- with group based security


get "The Official Samba-3 HOWTO and Reference Guide" and maybe "samba-3 by example" both part of the Bruce Perens' open source series.  Even though some people will tell you to use NFS for file sharing, experinece tells me that some "imortant" person somewhere is going to demand that his (or her) XP box be plugged in to the network, and he want to see the shares.  Ubuntu clients can use samba as clients without issues, they can even use smbfs to mount the smb shares to specific folders.  in terms of features, Samba is a superset of NFS -- even if NFS is "native" and therefore "cooler."

> 
5.Mounting remote folders/drives (etc) on logon
6.Sharing Internet


You will probably also find the "Linux Quick Fix Notebook" a valuable reference.  It will help you setup a mail server, disk quotas, dhcp services, an internal web server, a firewall, a server that acts as a router... 

there is just no substitute for a good book.

---

### Post by Abhi Kalyan on 2006-10-25
Thank you brentoboy,
Thats swell advice.
Will check them out.
as you said there is no substitute to a good book.
Thank you once again.
Note: i had suggested your name to another user who needed some help.

---

