---
title: "Trouble with Amarok"
date: 2005-12-29
forum: Absolute Beginner Talk
---

### Post by paulgroovy on 2005-12-29
I have Amarok installed on Breezy but can't get it to start up.  When I try to launch I get the following message.

Amarok could not find any sound-engine plugins.  amaroK is now updating KDE configuration database.  Please wait a couple of minutes, then restart amaroK.

If this does not help, it is likely that amaroK is installed under the wrong prefix, please fix your installation using:

$ cd /path/to/amarok/source-code/
$ su -c "make uninstall"
$ ./configure --prefix='kde-config --prefix'  && su -c "make install"
$ kbuildsycoca
$ amarok

More information can be found in the README file.  For further assistance join us at #amarok on irc.freenode.net.

Has anybody else run into this problem?  If so, what was the fix?

Thanks

---

### Post by claydoh on 2005-12-29
Do you have amarok-gstreamer, amarok-xine, or (if you run Kubuntu) amarok-arts installed? those are the engines amarok  is looking for

---

### Post by paulgroovy on 2005-12-29
I do have those installed.  I have even uninstalled and reinstalled everything and it is still doing the same thing.  Probably something very simple, but what?

---

### Post by claydoh on 2005-12-29
is it crashing? If the app is running but not working, you can try and go to Settings > configure Amarok > Engine and select a different engine

One other thing to try is to delete/rename your   /home<your-username>/.kde/share/config/amarokrc and maybe /home<your-username>/.kde/share/apps/amarok and re-running amarok

---

### Post by paulgroovy on 2005-12-30
it doesn't crash and it doesn't start up.  I just get the beginnig splash screen with the dude that looks like he's listening to an ipod, and then behind that screen will pop up that error message.  So I can't even get into the program.

---

### Post by dueY on 2005-12-30
Try uninstalling them all and only having one on at a time.  The same thing used to happen to me.

---

### Post by nolan- on 2006-01-05
Hi,
I am having exactly the same problem. I just updated Amarok to version 2:1.3.7 yesterday through Synaptic and now it won't start. I have tried to uninstall/re-install numerous times and still get the same error. I had amarok-gstreamer and amarok-xine installed previously and it worked fine and now it will now work with any.

It doesn't even startup, just fails with the same error as mentioned above...there are 2 or 3 threads running about this problem and none have been resolved!

HELP!  I NEED MUSIC !!!!!!!!

---

### Post by nolan- on 2006-01-11
Amarok seems to have repaired itself.
Synaptic ran an update and now Amarok works.

```
Upgraded the following packages:
libkpathsea3 (2.0.2-30ubuntu3.3) to 2.0.2-30ubuntu3.4
libpoppler0c2 (0.4.2-0ubuntu6.4) to 0.4.2-0ubuntu6.5
libpoppler0c2-glib (0.4.2-0ubuntu6.4) to 0.4.2-0ubuntu6.5
sudo (1.6.8p9-2ubuntu2.1) to 1.6.8p9-2ubuntu2.2

```

Don't know if it's anything to do with Amarok fixing itself but that is what was updated, certainly wasn't anything I done :???: 

Anyhow it works again :D

---

