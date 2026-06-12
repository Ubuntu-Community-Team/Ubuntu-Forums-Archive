---
title: "X gui gone bye-bye"
date: 2006-03-29
forum: Absolute Beginner Talk
---

### Post by Mark_in_Hollywood on 2006-03-29
I started with a Hoary CD. After installing it, and manually configuring the modem, I was able to start Synaptic to update the OS. I have a 56K modem and my ISP allows 60 minutes per session. Updates took a while.

After several days of downloading the updates, I started on the upgrade. After several more days, I booted into Breezy. Hooray. Even more download time and I had Automatix working. 

Next I started updating Breezy. All went well. Then I tried to update files necessary for allowing the wallpaper to change. 

[https://wiki.ubuntu.com/RotateWallpapers](https://wiki.ubuntu.com/RotateWallpapers)

That page says: "Install both of the following."

libgnomevfs2-dev 
build-essential 

which Synaptic did. 

But due to following the instructions on that page, the X server/services are GONE. When the computer boots, it displays an ascii character like screen that says the X server is not installed and/or "broken" and to see the log. The keyboard and  mouse lock. The computer must be warm-booted. I never "ran" the command line:

gcc -Wall -o change-bg `pkg-config --cflags --libs gnome-vfs-2.0 gconf-2.0` change-bg.c

that changes the wallpaper, so the problem lies with libgnomevfs2-dev and
build-essential. 

Can they be removed? What about the dependencies? When they were installed through Synpatic, they needed oodles of dependencies. 

Now, I can only run in rescue mode. I am at a public library terminal to post to this forum. The modem will dial-up (WvDial), but I have no terminal program, or if I do, I don't know the name of it. I tried "term" but that ain't a terminal program.

How do I get the gui back? I miss my X (no pun intended).

Does the rescue mode have a terminal program through which I might use dSelect to download X files and re-install and what would be the right way to go about that?

Please help, this is the fourth linux installation to blow-up since January 26th of this year. And I've been careful. After all, I've been a "friend of Bill G's" since 1986.

---

### Post by ispmarin on 2006-03-29
You can do a reinstallation from command line: log with you normal user, and tries 
sudo dpkg-reconfigure xserver-xorg 
or, if you want to try to remove the packages that you have installed, you can do a 
sudo apt-get remove <package>, something like that
sudo apt-get remove build-essencial 
and
sudo apt-get remove libgnomevfs2-dev
, but I think that build-essencial is not the problem with you X...
Can you post the error from the ascii screen? If is too hard to do that, just the lines with (EE), especific of the error.
hope it helps...

---

### Post by Mark_in_Hollywood on 2006-03-30
Per your request for info:

X Window System version 6.8.2 (Uuntu 6.8.2-77 xxxxxxxxx)
Release Date 9 Feb 2005
X Protocol Version 11, Rev. 9, Release 6.8.2

OK 

After several dpkg-reconfigure xserver-xorg, I was finally able to get the screen to release the following critical data:

(ww) No FontPath specified. Using compiled-in dafault.
(ww) Teh directory "usr/share/X11/fonts/misc" does not exist. Entry deleted from font path.

then, upon seeing and exiting that message the boot continued to: "no gdm". 

How to I get those fonts up and running, sir?

---

### Post by Mustard on 2006-03-30
I'm thinking that a (ww) notation is not a critical error. I would assume that (ww) means a 'warning'.  A message with the (EE) notation is an error.  What I am curious to know is what method did you use to restart the X server after doing the dpkg-reconfigure xserver-xorg.  Normally you would try one of these commands...

```
startx
```

or 

```
sudo /etc/init.d/gdm restart
```

When you reconfigure the xserver, what drivers are you using?  Have you tried the 'vesa' drivers?

---

### Post by Mark_in_Hollywood on 2006-03-31
[QUOTE=Mustard]I'm thinking that a (ww) notation is not a critical error. I would assume that (ww) means a 'warning'.  A message with the (EE) notation is an error.  What I am curious to know is what method did you use to restart the X server after doing the dpkg-reconfigure xserver-xorg.  Normally you would try one of these commands...

```
startx
```

or 

```
sudo /etc/init.d/gdm restart
```

When you reconfigure the xserver, what drivers are you using?  Have you tried the 'vesa' drivers?[/QUOTE]

The driver seems to be specifically from Xorg for a series of ATI video cards. That is what dselect indicates. Mine in particular is the Rage 128 Pro card.

As I said earlier, I am using a terminal at a public library. So while I have made copious notes, some of the following is from memory.

The messages in /var/log/Xorg.0.log, had only 2 lines with (ww-s) as shown above. I may be wrong, in memory I can't recall ANY (ee) lines about errors.

As your mention of startx and sudo /etc/init.d/gdm restart are the first I've seen of these, I haven't tried to restart graphically.

I'm not sure about the VESA drivers. If the sudo--reconfigure xserver-xorg asks for them as a default, I would have returned a "yes" to it. The way of re-configging the xserver-xorg was with "no" to scroll mouse, even though I have one and yes to the 104KB, which I have. Everything else was as standard as possible. This is a Dell Dimension 4100 computer with ATI's Rage 128 Pro AGP video card. I believe it's got 16Meg of GDRAM. The dpkg config was set at 16meg of ram.

Boot up time also shows a problem with ALSA's TiMidity.

Shut-down time shows 4 problems, one (2) to do with TiMidity, 2 to do timing or scheduling:

/usr/bin/timidity: error while loading shared libraries: libXaw7.so.7 cannot op

and

* [star in red] shared object file: No such file or directory [fail] [in red]

There is a message about POSTFIX. Can't recall it, as they scroll by SO fast. Does Ubuntu keep a log of boot time messages?

I will reconfig the xserver-xorg with VESA and try the startx and sudo ... gdm and let you know. Thanks for the help in the meantime.

P.S.- Neither  startx  nor  gdm  restart work.  
Booting to  xwindow,  screen message is as follows:

Fatal Server Error
No Valid FontPath Could Be Found.

---

### Post by Mark_in_Hollywood on 2006-04-02
In /var/log/X.0.log the files says that the base X system and core fonts are not installed, not configured correctly or not found in the path.

I was able to use dpkg to check on the installation of the packages mentioned, but they all read: install installed.

I couldn't find a way to read the Path. Is there one?

Is there a way to run WvDial and then get apt-get to work? That might solve the problem, pronto.

---

### Post by Mustard on 2006-04-03
[QUOTE=Mark_in_Hollywood]In /var/log/X.0.log the files says that the base X system and core fonts are not installed, not configured correctly or not found in the path.

I was able to use dpkg to check on the installation of the packages mentioned, but they all read: install installed.

I couldn't find a way to read the Path. Is there one?

Is there a way to run WvDial and then get apt-get to work? That might solve the problem, pronto.[/QUOTE]

You could try this command to see if it installs anything that might be missing....

```
sudo apt-get install ubuntu-desktop
```

Also with regard to moving around an interface that doesn't use the mouse, you might find the tab key handy for that, as well as the direction keys, ie when using the dpkg-reconfigure xserver-xorg command, as well as using the space bar to select things from a list

---

### Post by Mark_in_Hollywood on 2006-04-04
[QUOTE=Mustard]You could try this command to see if it installs anything that might be missing....

```
sudo apt-get install ubuntu-desktop
```

Also with regard to moving around an interface that doesn't use the mouse, you might find the tab key handy for that, as well as the direction keys, ie when using the dpkg-reconfigure xserver-xorg command, as well as using the space bar to select things from a list[/QUOTE]

apt-get returns gibberish about not "stat" -ing the files.

After much sadness and soul-searching, I have re-installed 5.04 Hoary Hedgehog and am updating, for the third time from the beginning.

If you are offended by this, I wouldn't blame you a bit, Mr. Mustard, but nothing seemed to work. Thank you.

---

### Post by Mustard on 2006-04-04
[QUOTE=Mark_in_Hollywood]apt-get returns gibberish about not "stat" -ing the files.

After much sadness and soul-searching, I have re-installed 5.04 Hoary Hedgehog and am updating, for the third time from the beginning.

If you are offended by this, I wouldn't blame you a bit, Mr. Mustard, but nothing seemed to work. Thank you.[/QUOTE]

I don't mind what you do. :)  It's your system to play with. ;)

I think what might have fixed the "stat" -ing problem would have been to update the package lists from the online repositories using..

```
sudo apt-get update
```

If you still had errors I would be thinking that perhaps you might have had a problem with your sources.list somewhere.

Anyway, good luck with starting from scratch. :)

---

