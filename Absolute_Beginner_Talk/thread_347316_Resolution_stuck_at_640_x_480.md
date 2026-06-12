---
title: "Resolution stuck at 640 x 480"
date: 2007-01-27
forum: Absolute Beginner Talk
---

### Post by paydaydaddy on 2007-01-27
I search the forums and came up with some possible solutions. I keep getting message "sudo: dpgk-reconfigure-phigh: command not found" I am working with dapper drake.Anybody have a command that might work for me?

---

### Post by Iarwain ben-adar on 2007-01-27
Try
```
sudo dpkg-reconfigure xserver-xorg -phigh
``` (it could be that -phigh doesn't need the - in front of it, don't know for sure)


Iarwain

---

### Post by jordanmthomas on 2007-01-27
```
sudo dpkg-reconfigure xserver-xorg -phigh
```
maybe?

The command you need is listed in /etc/X11/xorg.conf
I don't use a debian-based distro so I can't just look in mine for you.

---

### Post by paydaydaddy on 2007-01-27
> **Iarwain ben-adar said:**
> Try
```
sudo dpkg-reconfigure xserver-xorg -phigh
``` (it could be that -phigh doesn't need the - in front of it, don't know for sure)


Iarwain

That code returns this message:
Package `xserver-xorg-phigh' is not installed and no info is available.
Use dpkg --info (= dpkg-deb --info) to examine archive files,
and dpkg --contents (= dpkg-deb --contents) to list their contents.
/usr/sbin/dpkg-reconfigure: xserver-xorg-phigh is not installed
paydaydaddy@pacman:~$

---

### Post by Iarwain ben-adar on 2007-01-27
Note the space between xserver-xorg and -phigh :wink:

Just copy the command from the forum


Iarwain

---

### Post by paydaydaddy on 2007-01-27
> **Iarwain ben-adar said:**
> Note the space between xserver-xorg and -phigh :wink:

Just copy the command from the forum


Iarwain

redid it and got this:

xserver-xorg postinst warning: overwriting possibly-customised configuration   file; backup in /etc/X11/xorg.conf.20070127012222

I'm not sure how this helps me.

---

### Post by jordanmthomas on 2007-01-27
That just means that it made a backup of the old file in case this one is even more messed up so you can at least go back to the way it was before you tried to fix it.

Now that you have reconfigured X, try starting GDM up.
```
sudo /etc/init.d/gdm restart
```
and see what happens

---

### Post by Iarwain ben-adar on 2007-01-27
It should have overwritten it, and having backed-up your previous xorg.conf.

Now you should restart X (log out, and search for something called Restart X) nicely,
Or by just pushing Ctrl-Alt-Bcksp :wink:


Iarwain

---

### Post by paydaydaddy on 2007-01-27
> **jordanmthomas said:**
> That just means that it made a backup of the old file in case this one is even more messed up so you can at least go back to the way it was before you tried to fix it.

Now that you have reconfigured X, try starting GDM up.
```
sudo /etc/init.d/gdm restart
```
and see what happens


that took me to a DOS type window that wanted my login and password. I entered and now it seems to be waiting for a command.

---

### Post by paydaydaddy on 2007-01-27
Got the OS to restart. Still stuck in Fat resolution. The has to be a way to get back to the default resolution.

---

### Post by xmastree on 2007-01-27
The usual fix for this is setting your monitor refresh rates in the config file.

Run this command:
**gedit /etc/X11/xorg.conf**
A text editor should open, showing you the contents of the configuration file. Look through it for a section like this:```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	[COLOR="Red"]HorizSync	28-51
	VertRefresh	43-60[/COLOR]
EndSection
```

Yours may not have those two lines I've marked in red. If that's the case, it can stick you at 640x480. You can enter them manually, but **make sure you get the correct values or you can damage your monitor.**


If you do want to edit that file, run the gedit command again, but put **sudo** before it. This will allow you to edit it, since you will have higher privileges.

---

### Post by lnxnewbie on 2007-01-27
paydaydaddy,
Have you checked /etc/X11/xorg.conf? Section "Screen", Subsection "Display"...
make sure Modes has the desired resolution. 
Must be "root" to edit this file (su root).
Alt+Ctl+BSpace to relaunch X.

---

### Post by paydaydaddy on 2007-01-27
[QUOTE=xmastree;2069668]The usual fix for this is setting your monitor refresh rates in the config file.

Run this command:
**gedit /etc/X11/xorg.conf**
A text editor should open, showing you the contents of the configuration file. Look through it for a section like this:```

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	[COLOR="Red"]HorizSync	28-51
	VertRefresh	43-60[/COLOR]
EndSection
```

Yours may not have those two lines I've marked in red. If that's the case, it can stick you at 640x480. You can enter them manually, but **make sure you get the correct values or you can damage your monitor.**


How do I know the correct values to enter? Would I go to the monitor manufacturers website to find that info? I just want it back to the default resolution it was at when I did the install.

---

### Post by xmastree on 2007-01-27
I would search the forums for your monitor. Chances are, someone may have already been through this. Failing that, the manufacturer's website, or the manual itself (if you have one).

---

### Post by paydaydaddy on 2007-01-27
> **lnxnewbie said:**
> paydaydaddy,
Have you checked /etc/X11/xorg.conf? Section "Screen", Subsection "Display"...
make sure Modes has the desired resolution. 
Must be "root" to edit this file (su root).
Alt+Ctl+BSpace to relaunch X.

It has been suggested and I have tried to find /etc/X11/xorg.conf with no luck. Do I type in su root then /etc/X11/xorg.conf?

---

### Post by paydaydaddy on 2007-01-27
I tried using the command su root /etc/X11/xorg.conf and was prompted for a password. I entered my password and got "authentication failure sorry". Is there a super secret way of getting into root. I haven't set up any extra passwords and I am the only user of this computer.

---

### Post by xmastree on 2007-01-27
> **paydaydaddy said:**
> It has been suggested and I have tried to find /etc/X11/xorg.conf with no luck. 

Open a terminal, and run this command: ** cat /etc/X11/xorg.conf **

That ought to display the contents of the file.

To edit it, you need root privileges, so you need to put **sudo** before the command to edit. For editing, I suggest you use gedit (the default text editor in gnome). The command you need is this: **sudo gedit /etc/X11/xorg.conf**

---

### Post by paydaydaddy on 2007-01-27
> **xmastree said:**
> Open a terminal, and run this command: ** cat /etc/X11/xorg.conf **

That ought to display the contents of the file.

To edit it, you need root privileges, so you need to put **sudo** before the command to edit. For editing, I suggest you use gedit (the default text editor in gnome). The command you need is this: **sudo gedit /etc/X11/xorg.conf**

I am at the edit stage if the game, I just am not sure what to enter. I share this monitor with another computer so I don't want to mess it up, although if I understand things correctly andy screw up will only affect the monitor while switched to this machine. I have a CRT monitor. The specs are:
Horizontal 30kHz to 72kHz automatically
Vertical 50Hz to 160Hz automatically
Max Resolution 1280 x 1024

Do you have any suggestions for my settings?

---

### Post by paydaydaddy on 2007-01-27
I got it fixed. Thanks for your help.

---

### Post by xmastree on 2007-01-27
Glad to be of service.

---

### Post by bluejuice on 2007-02-01
[SIZE="1"]A lot of people have been having trouble with X/GDM and resolutions. Seriously, why hasn't this been fixed in X yet?[/SIZE]

---

### Post by Jasper84 on 2007-02-01
BTW xrandr can set resolutions xrandr -q shows what is possible, xrandr -s sets them. (ofcourse xrandr --help and info xrandr for more info)

---

