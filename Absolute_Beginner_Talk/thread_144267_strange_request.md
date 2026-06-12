---
title: "strange request"
date: 2006-03-13
forum: Absolute Beginner Talk
---

### Post by brooklynlou on 2006-03-13
Hi,

I've managed to get Ubuntu installed and working on oneof my old laptops and have so far been very impressed with its speed and responsiveness compared to WXP.

Unfurtunately I may have gone too far by installing Ubunto on a reaaallly old laptop (233Mhz, 64 Meg, 4 Gig). Though Ubuntu works, its slow as hell.

What I would like to do is format the HD and start from scratch by installing a distro meant more for lower end machines. What is the command / process I need to use to clear out the HD and make room for a clean install of another distro?

L

---

### Post by xmastree on 2006-03-13
I would just start to install the new distro. There will probably be an option to erase the disk at some point.

---

### Post by xtacocorex on 2006-03-13
If you have the other distro's cd, all you should have to do is put it in, boot off of it and let the partitioner on the cd do the work for you.

---

### Post by aysiu on 2006-03-13
Just install the new distro (Damn Small Linux or whatever)--it'll overwrite Ubuntu.

There's no need to uninstall.

---

### Post by Zelut on 2006-03-13
Well an installation of another distro will wipe the drive at time of installation.  What I would suggest however is try the Xfce desktop (instead of gnome) and you should see a significant increase in speed & responsiveness.  This is what I've done on a lot of older machines.  Steps below:

I suggest re-installing Ubuntu, but this time use the 'server' installation.  (At the first prompt after booting from disk type **server** and let it go as usual.  This will install just the basics--no GUI.

After this is finished you'll be just left with a prompt (dont worry, you'll be out in no time).  Continue with **sudo apt-get install xubuntu-desktop**.  This is a super light-weight GUI that should work much better on that machine.

For more info do some searches for Xfce.

---

### Post by aysiu on 2006-03-14
Even XFCE might be a little too intensive for 64 MB of RAM. IceWM or Fluxbox may be better choices.

---

### Post by Sutekh on 2006-03-14
[Ubuntu Wiki - Low Memory Systems](https://wiki.ubuntu.com/Installation/LowMemorySystems)

Has some good options for a lower end machine including fluxbox (v.light)

---

### Post by brooklynlou on 2006-03-14
Ok, I tried the following command from the wiki

> sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic

The CLI tells me that it cant find package fluxbox. How do I know that it is connected to the net?

---

### Post by Sutekh on 2006-03-14
Okay fluxbox is in the universe repository, which you will need to enable.

This is a very simple process.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
Will backup and edit your sources.list using nano (a simple editor)

You need to identify lines such as these```
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe
``` and remove the '#'.  

You can then save the file (Ctrl+O) and exit nano (Ctrl+X), then refresh the repositories and try again
```
sudo apt-get update
sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic
```

---

### Post by IYY on 2006-03-14
Use Fluxbox as your window manager, ROX as your file manager, Dillo as your browser whenever possible. I have a laptop with similar specs and it works quite well. 

Of course, DSL is also a pretty decent choice.

---

### Post by chimera on 2006-03-14
Acctually, IceWM is a much lighter windows manager, and I'd use mc as a file manager.

---

### Post by Sutekh on 2006-03-14
Openbox?

[Ubuntu Wiki - Openbox]("https://wiki.ubuntu.com/Openbox")

[Ubuntu Forums - Howto use Openbox in GNOME and by itself]("http://www.ubuntuforums.org/showthread.php?t=75471")

---

### Post by bobpur on 2006-03-14
I'm not trying to run you off Ubuntu by any means, but I found these distros I want to check out some time for a couple of old computers I have sitting in the closet. 
   1). Puppy Linux  2). Damn Small Linux  3). Feather Linux 
I came across these three distros while looking for a "How to" for Linux commands. I hope they'll work on two old computers I have with 2.0 GB harddrives from the mid 1990's.

---

### Post by brooklynlou on 2006-03-14
[QUOTE=Sutekh]Okay fluxbox is in the universe repository, which you will need to enable.

This is a very simple process.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list_backup
sudo nano /etc/apt/sources.list
```
Will backup and edit your sources.list using nano (a simple editor)

You need to identify lines such as these```
# deb http://archive.ubuntu.com/ubuntu breezy universe
# deb-src http://archive.ubuntu.com/ubuntu breezy universe
``` and remove the '#'.  

You can then save the file (Ctrl+O) and exit nano (Ctrl+X), then refresh the repositories and try again
```
sudo apt-get update
sudo apt-get install fluxbox x-window-system-core xdm dillo synaptic
```[/QUOTE]


Ok folks, did the above. PC went through a very impressive process of downloading a bunch of stuff. One more dumb question.

How do you start the GUI from the CLI?

---

### Post by xmastree on 2006-03-14
startx

---

### Post by brooklynlou on 2006-03-14
Ah, the joys of the fresh install.

After doing startx at the prompt,

I have the following error message appear in a very crude windowed box:

> Xsession: unable to start X session --- no "/home/louis/.xsession" file, no "/home/louis/.Xsession", no session manager, no window manager, and no terminal emulators found; aborting.

I then press the [okay] button and it brings me back to the CLI

So where did I go wrong in the above steps?

---

### Post by Sutekh on 2006-03-14
Firstly you'll see ~/ a lot. Its a shortcut for your home folder /home/louis.  The use of '.' (period/full-stop) means that the file/folder is hidden.


So basically to start fluxbox using **startx**, you need to set fluxbox in your X startup script **~/.xinitrc**.  

Edit it using nano
```
nano ~/.xinitrc
```
and add this line to the end of the file.  
```
exec /usr/local/bin/fluxbox
```
/usr/local/bin/fluxbox should be the executable for fluxbox.

Save the file (Ctrl+X) and exit nano (Ctrl+O).

Set the permissions for ~/.xinitrc and create a ~/.fluxbox folder (for storing your settings)
```
chmod 700 ~/.xinitrc
mkdir ~/.fluxbox
```

Then use```
startx
``` to run start X, thus fluxbox.


To get rid of that error, when using the X Display Manager (XDM, which uses **~/.xsession** to start up instead of ~/.xinitrc) try creating a symbolic link to ~/.xinitrc
```
ln -s ~/.xinitrc ~/.xsession
```
So when the XDM tries to start, it looks for ~/.xsession and it linked to ~/.xinitrc and starts fluxbox.

---

### Post by brooklynlou on 2006-03-14
[QUOTE=Sutekh]
So basically to start fluxbox using **startx**, you need to set fluxbox in your X startup script **~/.xinitrc**.  

Edit it using nano
```
nano ~/.xinitrc
```
and add this line to the end of the file.  
```
exec /usr/local/bin/fluxbox
```
/usr/local/bin/fluxbox should be the executable for fluxbox.

Save the file (Ctrl+X) and exit nano (Ctrl+O).[/quote]

No file existed called .xinitrc. Basically added the above text to an empty file and then saved it.

> Set the permissions for ~/.xinitrc and create a ~/.fluxbox folder (for storing your settings)
```
chmod 700 ~/.xinitrc
mkdir ~/.fluxbox
```

Then use```
startx
``` to run start X, thus fluxbox.


To get rid of that error, when using the X Display Manager (XDM, which uses **~/.xsession** to start up instead of ~/.xinitrc) try creating a symbolic link to ~/.xinitrc
```
ln -s ~/.xinitrc ~/.xsession
```
So when the XDM tries to start, it looks for ~/.xsession and it linked to ~/.xinitrc and starts fluxbox.

I get less than before. Once I so startx it flashes twice and goes back to the command prompt

it also says that /usr/local/bin/fluxbox  does not exist.

---

### Post by Sutekh on 2006-03-14
[QUOTE=brooklynlou]No file existed called .xinitrc. Basically added the above text to an empty file and then saved it.
[/quote]Thats okay.

[QUOTE=brooklnlou]
I get less than before. Once I so startx it flashes twice and goes back to the command prompt

it also says that /usr/local/bin/fluxbox  does not exist.[/QUOTE]
Okay so we need to find out where it is and modify that line
```
whereis fluxbox
```
Should tell you where the fluxbox executable is, then just change the line in ~/.xinitrc.  Should be something similar to /usr/bin/local/fluxbox or /usr/bin/fluxbox.

**Edit:** I just checked the contents of the [Fluxbox package]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=fluxbox&version=breezy&arch=i386") at [packages.ubuntu.com](packages.ubuntu.com).  I'm pretty sure that the fluxbox executable is **/usr/bin/fluxbox**

---

### Post by brooklynlou on 2006-03-14
[QUOTE=Sutekh]Thats okay.


Okay so we need to find out where it is and modify that line
```
whereis fluxbox
```
Should tell you where the fluxbox executable is, then just change the line in ~/.xinitrc.  Should be something similar to /usr/bin/local/fluxbox or /usr/bin/fluxbox.

**Edit:** I just checked the contents of the [Fluxbox package]("http://packages.ubuntu.com/cgi-bin/search_contents.pl?searchmode=filelist&word=fluxbox&version=breezy&arch=i386") at [packages.ubuntu.com](packages.ubuntu.com).  I'm pretty sure that the fluxbox executable is **/usr/bin/fluxbox**[/QUOTE]


I get the following from the whereis:

/usr/bin/fluxbox
/usr/bin/X11/fluxbox
/usr/share/fluxbox
/usr/share/man/man1/fluxbox.1.gz

---

### Post by Sutekh on 2006-03-14
Try **/usr/bin/fluxbox**

---

### Post by brooklynlou on 2006-03-14
Thank you sir. That did the trick. Now I have the joy and pleasure in figuring out how fluxbox works :-)
\
L

---

### Post by Sutekh on 2006-03-14
Cool!  Well I hope you enjoy it, some of the minimal window managers have some very cool features

---

### Post by Edward The Bonobo on 2006-03-15
I was running xfce on a PII 333MHz 64MB machine.  Yes, it was faster than Gnome...but barely tolerable.  Last night I put in an extra 256MB and I'm a lot happier.  I haven't had time to try Gnome yet.

---

