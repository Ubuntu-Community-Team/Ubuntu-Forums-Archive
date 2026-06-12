---
title: "Irexec startup"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by culliard on 2007-03-22
Hi all, 

First of all I'm a complete novice at linux, but with a lot of help from colleagues I have managed to get this far.

I have installed ubuntu Edgy 2.6.20.1 with the aim of running MythTV with a dual tuner (Hauppage nova T 500) and remote.

I built a serial port receiver, compiled and installed Lirc, which is working fine with my remote through the .lircrc file in /root/.lircrc. I can control mythtv and xine.

I got a bit advanced and tried to use irexec to detect remote buttons after I logged in so that I could launch the above applications after logging in.

I did manage to get irexec to start automatically in 2 different ways

1. edited /etc/rc.local and added 
```
 irexec -d /root/.lircrc
```

2. created a script in /etc/init.d/irexecloader  with the following

```
#/bin/sh

irexec -d /root/.lircrc
exit 0
```

When logged  in as a normal user, goto Preferences | Sessions, then select Startup Programs. Add the script here.

In case 1, irexec starts as root. If I login as my username, irexec doesn't respond to any commands, and if open the programs manually, they don't respond either.

If change user to root in a terminal window and start irexec again, everything works fine. Also if I login as root everything works perfectly.


In case 2, irexec starts as 'user', and when I login as 'user', I can use the remote to launch the programs, but when they are loaded they don't respond. This is something to do with the fact that the apps are also started as 'user'.

I believe that irexec should be started as root, but I don't know how to get it working under ' user'. I suspect this is something to with /etc/sudoers but I don't know what to change.

All fun and games! But some help would be much appreciated

---

### Post by culliard on 2007-03-28
I have been fighting with permissions and sudoers since my last post and it seems this is 

After the update to lirc came through (0.8.1+cvs20070310) I could run the session startup program to start irexec as my normal user. 

Xine now responds as expected but mythfrontend still won't respond to the remote unless the script in ran while logged in as root.

I'll keep on trying...

---

### Post by culliard on 2007-05-31
Thought I'd come back to this one, now that I have a little more experience...

It turned out to be really simple too

I had created the lirc file /root/.lircrc and made a symbolic link to /root/.mythtv

In root directory
```
ln -s ~/.lircrc ~/.mythtv/lircrc
```

So obviously when I logged in as 'nc' I could start mythfrontend as user 'nc' but it couldn't find the .lircrc file.

The fix:
I copied the .lircrc file from /root/ to /home/nc/

then created a symbolic link 
```
ln -s /home/nc/.lircrc  /home/nc/.mythtv/lircrc
```

It seems to work great now!

---

### Post by Kipee on 2008-02-05
This is how I managed to get rid of the problem. Sleep is just there to make sure lirc has already started.
**Note:** This solution runs as root! (I want to have shutdown in one of my buttons)

Edit crontab:
```
sudo crontab -e
```

Add next line to crontab, replacing USER with your own username.
```
@reboot sleep 120 && export DISPLAY=:0 &&/usr/bin/irexec -d /home/USER/.lircrc
```

---

