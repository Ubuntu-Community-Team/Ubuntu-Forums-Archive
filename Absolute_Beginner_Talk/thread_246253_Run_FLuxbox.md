---
title: "Run FLuxbox?"
date: 2006-08-29
forum: Absolute Beginner Talk
---

### Post by jamesr316 on 2006-08-29
I have a fresh install of 64 bit server. I ran the following code given to me in another post:

```

sudo aptitude update
sudo aptitude install x-window-system-core icewm
startx

```

when i do startx it says 
"Xsession: unable to start x session --no /home/james/.xsession file, no /home/james/Xsession file, no window managers, and no terminal emulators found; aborting."

I do not want to use a complete desktop environment like KDE or GNOME unless I have to. I would like to be able to use this fluxbox that i was reading about. Also, would it be possible to completely lose the monitor and remote into it from my laptop and still get a graphical environment? eventually i hope to be able to do everything from command line and i can ssh in.

---

### Post by etc on 2006-08-29
I am using [this]("http://www.cs.bu.edu/help/unix/the_.xsession_file.html") webpage as a reference.

First, install nano if it already isn't installed 
```
sudo aptitude install nano
```

then, edit and create the .xsession file
```
nano ~/.xsession
```

enter
```
icewm &
```

and hit CTRL + X, and y to confirm that you want to save the file

then try startx again to start icewm

--

to install fluxbox 

```
sudo aptitude install fluxbox
```

and replace 'icewm &' with

```
fluxbox &
```

in /home/james/.xsession

--

EDIT: you could probably use vnc to do what you want to do with your monitor, but I'll let someone who is more experienced help you out with that

---

### Post by croak77 on 2006-08-29
Create a file call .xinitrc in your user's home folder;

```
nano -w /home/username/.xinitrc
```

Add this line;

```
exec icewm
```

Hit Ctrl-X to save. It should then start icewm when you startx. If you want fluxbox then change exec icewm to exec fluxbox.

---

### Post by bodhi.zazen on 2006-08-29
You can run without editing .xsession or .xinitrc.

for IceWM:
```
startx /usr/bin/icewm-session
```
For Fluxbox:
```
startx /usr/bin/startfluxbox
```

---

### Post by jamesr316 on 2006-08-29
did both of those, it isnt working. the error doesnt come up anymore like it did before, it just lists a bunch of stuff and goes back to prompt.

---

### Post by jamesr316 on 2006-08-29
bodhi, tried that, same thing...list of things.

i can see this though:

xinit: no such file or directory (errno 2): no program named "/usr/bin/startfluxbox" in PATH

---

### Post by bodhi.zazen on 2006-08-29
> **jamesr316 said:**
> bodhi, tried that, same thing...list of things.

i can see this though:

xinit: no such file or directory (errno 2): no program named "/usr/bin/startfluxbox" in PATH

> **jamesr316 said:**
> bodhi, tried that, same thing...list of things.

i can see this though:

xinit: no such file or directory (errno 2): no program named "/usr/bin/startfluxbox" in PATH

First: I assume you installed Fluxbox? And /usr/bin/icewm-session also does not work?

I think you need a little more X. Try:
```
sudo aptitude install x-server-xorg x-window-system-core numlockx
```

---

### Post by jamesr316 on 2006-08-29
flux or ice is probably not installed. I did the line you just said, said couldnt find any packages "x-server-xorg" "numlockx"

did the same when i tried to run the code above to install flux / ice

---

### Post by bodhi.zazen on 2006-08-29
Sorry, I booted to Ubuntu.

Try:
```
sudo aptitude install xserver-xorg xserver-xorg-core xterm numlockx fluxbox eterm eterm-themes icewm icwwm-common icewm-themes
```

---

### Post by jamesr316 on 2006-08-29
a lot of those could not be found...

eterm-themes, icewm, icwwm-common, icewm-themes...there might be more but i cant see that far up on the screen

---

### Post by bodhi.zazen on 2006-08-29
Sounds like you need to enable a few repositories. (should be a matter of removing a few hash marks (#)).

Edit /etc/apt/sources.list to look like this:
> # 
# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted


# deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse


deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

Then
```
 aptitude update
```
and re-try

---

### Post by jamesr316 on 2006-08-29
sorry for all the probs. it wont let me save, permission denied. i am using the regular account i made when i installed ubunut, "james"

---

### Post by jamesr316 on 2006-08-29
nvm, i got into root. trying now

---

### Post by jamesr316 on 2006-08-29
Wow, thanks. Ok, so startx now starts fluxbox. and if i wanted it to start icewm, i would just change the file .xinitrc file?

Is there a way to access this from a remote computer? I would like to isolate this computer and play with it from another computer on the network, freeing up my monitor/inet connection for my regular desktop.

---

### Post by bodhi.zazen on 2006-08-29
First, try icewm:

close (exit) fluxbox.

```
startx /usr/bin/icewm-session
```

---

### Post by jamesr316 on 2006-08-29
that works as well.

---

### Post by bodhi.zazen on 2006-08-29
Second, yes. From what OS? I presume Windows XP.

Are you familiar with ssh, Cygwin, putty ??

What I used to do:

From windows XP:
Start X Cygwin (option rootless)
Launch Putty
Log into Ubuntu box -> This will be a CLI.
Log onto Ubutnu
type startx or startx icewm-session

Need to configure Ubuntu. Mainly add yourself to the ssh group.
? enable X Forwarding

configure Cygwin -> read the startx file in Cygwin for options (Fullscreen vs. Rootless).

Configure putty -> enable X forwarding is an option you choose from a check box BEFORE you ssh into Ubuntu.

You can ssh via Cygwin without Putty, but Putty has more options.

It is late for me, I may need to help with this another night if you are unfamiliar with this process.

---

### Post by jamesr316 on 2006-08-29
am familiar with ssh and i do have putty already. i will try to get this right, you get some rest, thanks for helping. will let you know if i have any more problems with this.

---

### Post by bodhi.zazen on 2006-08-29
Now, you can edit your .xinit or .xsessions if you want....

Easier to edit .bashrc. This you can do as a regular user.

Add these lines:

```

#Alias for window managers
alias flux='startx &'
alias ice='startx /usr/bin/icewm-session &'
```

Now log out and log back in. You can now start with:

flux -> should start fluxbox

ice -> should start icewm

for info on icewm:
[http://forums.debian.net/viewtopic.php?t=5450](http://forums.debian.net/viewtopic.php?t=5450)

for Fluxbox:
[http://forums.debian.net/viewtopic.php?t=5382&highlight=fluxbox&sid=b03a6cbd75085bc7828862f1cdcea42d](http://forums.debian.net/viewtopic.php?t=5382&highlight=fluxbox&sid=b03a6cbd75085bc7828862f1cdcea42d)

Say "hi" to Lou for me !!

As far as Fluxbox goes, it is easy to configure but takes time to learn.

I usually edit menu and configuration by hand. These files are in ~/.fluxbox. Backup before you edit !

---

### Post by bodhi.zazen on 2006-08-29
One other cool trick:

You can run both icewm and fluxbox at ath same time. Not too taxing on your box as both are light:

```
startx &   #This will start fluxbox.

Ctrl-Alt-F1 #This retunr you to the CLI

startx /usr/bin/icewm-session -- :1

Or, if you get errors

startx /usr/bin/icewm-session -- :2 # this will start icewm
```

to change to fluxbox -> Ctrl-alt-F7

to change to icewm -> ctrl-alt-F8

I almost never boot to GDM any longer, the CLI is faster, more secure, and just as easy.

When you start X you may want to run xscreensaver (screensaver) and numblockx (enables number lock when starting X).

You can put these in a start script:

[quote]#!/bin/bash
xscreensaver &
numblockx &
startx[quote]

Save this as say Autostartfluxbox in ~

chmod u+x Autostartfluxbox

Now to start fluxbox type ~/Autostartfluxbox

and fluxbox should start with xscreensaver and nmuber lock activated.

Be sure to change your alias in .bashrc if you like thi script.


also be sure to colorize your prompt and ls output (I use a green prompt for a normal user, and a red for root).

---

### Post by croak77 on 2006-08-29
I think it must easier to just create an .xinitrc and put everything you want to start when X starts in there.

```
numlockx &
feh --bg-scale ~/wallpaper.jpg
exec icewm
```

---

### Post by justin whitaker on 2006-08-29
Is there any reason to install both icewm and fluxbox?

---

### Post by bodhi.zazen on 2006-08-29
> **justin whitaker said:**
> Is there any reason to install both icewm and fluxbox?

I advise you look at both if you are unfamiliar with them as they are somewhat different as far as features. Once you know what you want either will suffice. I personally prefer flux, but ice is a nice change from the norm.

---

### Post by bodhi.zazen on 2006-08-29
> **croak77 said:**
> I think it must easier to just create an .xinitrc and put everything you want to start when X starts in there.

```
numlockx &
feh --bg-scale ~/wallpaper.jpg
exec icewm
```

Yes, true if you always want the same things without variation. Adding numlockx and xscreensaver to .xinitrc makes sense.

Now what if you want different backgrounds/applications depending on WM? I run primarily flux, but openbox is also nice. Occasional icewm.

I have configured my system boot to the CLI and can start fluxbox with different options/backgrounds then I use with Openbox again separate from icewm.

I find it takes a little time to set up start scripts, but then it is easier to fine tune. Once you have a "base" start script, a new start script is as easy as cp ~/.fluxbox/startscript ~.openbox/startscript and away you go. Now I do not always have to modify .xinitrc if I want to change how I start openbox.

I guess I like to tweak my WM and start scripts are easier than constant edits to .xinitrc.

Is my method "easier", no. But it is as I like and this is the freedom Linux offers.

---

### Post by croak77 on 2006-08-29
That's great that you have separate startx scripts for every window manager you use. But you never know how much GNU/Linux experience a poster has especially on this forum.

---

