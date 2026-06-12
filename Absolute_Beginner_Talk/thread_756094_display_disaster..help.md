---
title: "display disaster..help?"
date: 2008-04-15
forum: Absolute Beginner Talk
---

### Post by renovate on 2008-04-15
Hi,
I was installing some new packages and came across what looked like a DVD player. Not sure which one, but wanted to try it. It said that it would be deleting a few files (including xorg and two other x's) and replacing them with the new files. 

Now I don't have display and I'm no good at coding since I'm a noob. so could somebody help me code my way back to installing xorg and its associated files? I could just do a blank reinstall but i have some files on the drive I don't want to lose.

Thanks.

I use ubuntu 5.10 on a notebook laptop.

---

### Post by seepage87 on 2008-04-15
What kind of graphics card is in your machine?  Which drivers were you using?

---

### Post by renovate on 2008-04-29
my computer is a lenovo T40 thinkpat, it apparently has an ATI Mobility RADEON ... but my specs sheet lists 4 of them, so I don't know what is relevant.

I'm not sure about the drivers, is there an easy way for me to find out?

---

### Post by hellonull on 2008-04-30
You could just try reinstalling xorg through Synaptic. Find the packages, right click them, mark for re-installation, and apply.

---

### Post by AndThenWhat on 2008-04-30
in command line try:
```
sudo apt-get install xserver-xorg
```

then to restart:
```
sudo shutdown -r now
```

let us know if you fix it

---

### Post by renovate on 2008-05-04
I tried 
sudo apt-get install xserver-xorg
and got this:
```

Reading package lists... Done
Building dependency tree... Done
xserver-xorg is already the newest version. 0 upgraded, 0 newky installed 0 to remove and 0 not upgraded.
W: Couldn't stat source package list http://us.archive.ubuntu.com dapper/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com dapper/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)- stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems

```

and the apt-get update got me:
```

Err http://us.archive.ubuntu.com dapper Release.gpg
  Temporary failure resolving 'us.archive.ubuntu.com'
Failed to fetch http://us.archive.ubuntu.com/ubuntu/dists/dapper/Release.gpg Temporary failure resolving 'us.archive.ubuntu.com'
Reading package lists... Done
W: Couldn't stat source package list http://us.archive.ubuntu.com dapper/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com dapper/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com dapper/universe Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_universe_binary-i386_Packages)- stat (2 No such file or directory)
W: Couldn't stat source package list http://us.archive.ubuntu.com dapper/multiverse Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_dapper_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead

```

Could it just be my internet connection? It looks like the release is there.

---

### Post by renovate on 2008-05-04
I don't know why I haven't posted this yet, i thought it would be easier to fix my problem... anyway, it might be helpful.

When I boot up, I get a prompt that says:
```

Failed to start the x server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X server output to diagnose the problem?

<Yes> <No>

```

I select Yes, it says: 

```

X Window System Version 7.0.0
Release Date: 21 December 2005
X Protocol Version 11, Revision 0, Release 7.0
Build Operating System:Linux 2.6.12 i686
Current Operating System: Linux user 2.6.12-9-386 #1 Mon Oct 10 13:14:36BST 2005 i686
Build Date: 16 March 2006
Before reporting problems, check http://wiki.x.org
to make sure that you have the latest version.
Module Loader present
Markers: (--)probed, (**) from config file, (==) default setting, (++) from command line, (!!) notice, (II) informational, (WW) warning, (EE) error, (NI) not implemented, (??) unknown. 
(==) Log file: "/var/log/Xorg.0.log", Time: Sun May 4 10:53:32 2008
(==) Using config file: "/etc/X11/xorg.conf"
<Ok>

```

I select Ok:

```

Would you like to view the detailed X server output as well?
<Yes> <No>

```

I select Yes, and it says the same as above with no extra detail. 

the next prompt says:
```

The X server is now disabled. Restart GDM when it is configured correctly.
<Ok>

```

And then Ok takes me back, not to the desktop but to the terminal I guess. It is text-only and prompts me to log in.

Thanks

---

### Post by renovate on 2008-05-04
> **hellonull said:**
> You could just try reinstalling xorg through Synaptic. Find the packages, right click them, mark for re-installation, and apply.

I was using Synaptic to install things before I got into this mess, :). 
I can't use Synamptic now because my desktop environment isn't up and running. I don't have a graphic user interface, so no click-and-go for me. Thanks anyway.

---

### Post by nanog on 2008-05-04
It seems that you are running 6.06 not 5.10 (which is no longer supported). It does look like your internet connection is not working. 

The ubuntu alternate install cd has a repair option that shoulf leave your home directory intact. Obviously you should be cautious doing this. I would recommend using the live cd to mount your filesystem to backup any important data before attempting this.

I typically fix broken systems by chrooting in using a live cd. This is not for the inexperienced user but works very well. 

[http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)

---

### Post by peakshysteria on 2008-05-04
Not qualified to say for sure. But how about trying:

sudo dpkg-reconfigure -phigh xserver-xorg

Can anybody tell us if this will work or not before he gives it a go? If so, after do:

sudo shutdown -r now

---

### Post by renovate on 2008-05-11
> **nanog said:**
> It seems that you are running 6.06 not 5.10 (which is no longer supported). It does look like your internet connection is not working. 

The ubuntu alternate install cd has a repair option that shoulf leave your home directory intact. Obviously you should be cautious doing this. I would recommend using the live cd to mount your filesystem to backup any important data before attempting this.

I typically fix broken systems by chrooting in using a live cd. This is not for the inexperienced user but works very well. 

[http://ubuntuforums.org/showthread.php?t=306424](http://ubuntuforums.org/showthread.php?t=306424)

Actually I've edited my sources.list because I know that 5.10 is unsupported. I commented (#) the breezy lines and wrote dapper lines at the bottom of the file, hoping I could install a newer version. will chroot with a live cd still work? I do have one, and it works great, but I assumed I couldn't access the real system through it because it doesn't read the hard disk.

---

### Post by renovate on 2008-05-13
> **peakshysteria said:**
> Not qualified to say for sure. But how about trying:

sudo dpkg-reconfigure -phigh xserver-xorg

Can anybody tell us if this will work or not before he gives it a go? If so, after do:

sudo shutdown -r now

I tried this, and it brought me to a screen with a box selecting the screen resolutions I would like to use. there were no other options. I chose the three most reasonable sounding ones, but they were already the only ones selected so I didn't make any changes. 

Then it said something like
```
Xserver-xorg postint warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20080513001456
```


Then I wanted to access the file it backed up. I opened it with
```
sudo nano /etc/X11/xorg.conf.20080513001456
```

which says
```
If you have edited this file but would like it to be automatically updated again, run the following command:
sudo dpkg-reconfigure -phigh xserver-xorg
```

But that's what you told me to do, and it didn't change anything.

I also got the ```
sudo apt-get update && sudo apt-get upgrade
``` command to work with old-releases.ubuntu.com in my sources.list, 
BUT I still get the original error message about x server and xorg settings. (see 3 posts ago)

This is so frustrating.
Is there anything I can do to the xorg.conf file to make my problem go away? can somebody show me what theirs or an ideal one looks like?

If it's helpful I can post exactly what my xorg.conf file says. Will anybody be willing to diagnose from there?

---

### Post by renovate on 2008-05-13
For now I think it will be helpful to post what the bottom of the log file says... this is where the errors show up. 

```

(II) LoadModule: "ati"
(WW) Warning, couldn't open module "ati"
(II) UnloadModule: "ati"
(EE) Failed to load module "ati" (module does not exist, 0)
(II) LoadModule: "kbd"
(WW) Warning, couldn't open module "kbd"
(II) UnloadModule: "kbd"
(EE) Failed to load module "kbd" (module does not exist, 0)
(II) LoadModule: "mouse"
(WW) Warning, couldn't open module "mouse"
(II) UnloadModule: "mouse"
(EE) Failed to load module "mouse" (module does not exist, 0)
(II) LoadModule: "wacom"
(WW) Warning, couldn't open module "wacom"
(II) UnloadModule: "wacom"
(EE) Failed to load module "wacom" (module does not exist, 0)
(II) LoadModule: "synaptics"
(WW) Warning, couldn't open module "synaptics"
(II) UnloadModule: "synaptics"
(EE) Failed to load module "synaptics" (module does not exist, 0)
(EE) No drivers available.
Fatal server error: no screens found.

```

---

### Post by renovate on 2008-05-13
If I try to: sudo apt-get install (the missing drivers),
1) for "ati" (Identifier "Default Screen" in xorg.conf)
```

Reading Package Lists... Done
Building dependency tree... Done
E: Couldn't find package ati 

```

2) for "kbd" (Generic Keyboard)
```

Reading Package Lists... Done
Building dependency tree... Done
The following packages will be REMOVED:
 console-tools ubuntu-minimal
The following NEW packages will be installed:
 kbd
0 upgraded, 1newly installed, 2 to remove and 3 not upgraded.
Need to get 340kB of archives.
After unpacking 373kB of additional disk space will be used. 
Do you want to continue (Y/n)? n
Abort.

```

3) for "mouse" (Configured Mouse)
```

Reading Package Lists... Done
Building dependency tree... Done
E: Couldn't find package mouse

```

4) for "wacom" (Stylus)
```

Reading Package Lists... Done
Building dependency tree... Done
E: Couldn't find package wacom

```

5) for "synaptics" (Synaptics Touchpad)
```

Reading Package Lists... Done
Building dependency tree... Done
Package synaptics is not available, but is referred to by another package. This may mean that the package is missing, has been obsoleted, or is only available from another source
However the following packages replace it:
 tpconfig
E: Package synaptics has no installation candidate

```


Should I make the changes for kbd and synaptics, or just leave it alone?

---

