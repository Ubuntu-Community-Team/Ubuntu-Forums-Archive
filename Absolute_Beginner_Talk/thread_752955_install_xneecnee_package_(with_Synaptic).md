---
title: "install xnee/cnee package (with Synaptic?)"
date: 2008-04-12
forum: Absolute Beginner Talk
---

### Post by mrodent on 2008-04-12
hi

want to move over to Linux but 2 or 3 apps in the Windows environment are vital... one is autohotkey... want to find whether xnee/cnee is an adequate substitute.

so I went to Synaptic, found xnee in the list... installed this package... looking at the "getting started" section in the manual found here: [http://www.sandklef.com/xnee/?q=node/13](http://www.sandklef.com/xnee/?q=node/13)

but bash tells me "cnee" is not a command
did whois cnee and locate cnee... no joy
cnee is not listed in the Synaptic package list

I'm struggling... help!  Does this mean I have to download & install a package or sthg?  

Thanks

---

### Post by Capricori on 2008-04-12
I couldn't find a package called 'cnee', and it seems that xnee doesn't do the same thing as autohotkey. Have a look at a program called keylaunch, is that a suitable replacement?

Capricori

---

### Post by Mark20 on 2008-04-12
@ Capricori
Keylaunch is a program for binding commands to a hot key.  I think mrodent is looking for an automation program which allows users to automate a bunch of steps.  Like a macro, except for the O/S.  In which case xnee seems like it's the right program to use.

@ mrodent.
I tried downloading the xnee package, but it seems that it didn't include the package cnee.  
I then tried downloading the source code and compiling it.  I unzipped the xnee file, then opened up a terminal, and tried the following:

```

./configure
make
make install

```

I think this work should for you.  Unfortunately, I don't have the gtk+-2,0 package, so it refuses to install.  As long as you have the right packages, the manual install (aka the code above) should work.

Mark

---

### Post by Capricori on 2008-04-12
> **Mark20 said:**
> @ Capricori
Keylaunch is a program for binding commands to a hot key.  I think mrodent is looking for an automation program which allows users to automate a bunch of steps.  Like a macro, except for the O/S.  In which case xnee seems like it's the right program to use.

My mistake. I used 'apt-cache search' to find xnee, and from it's description, I assumed it was a screen recorder. Thanks for the heads up.

Capricori

---

### Post by Mark20 on 2008-04-13
Hey mrodent,

Just to let you know, when I installed the package, xnee worked perfectly (aka, the steps I gave you work).

It's actually a really cool program.  If you still have problems just let me know.

Mark

---

### Post by aouie on 2008-07-23
The gtk library to select in synaptic is "libgtk2.0-dev".
---
Installing latest xnee.
Download the latest xnee from [the Xnee site http://savannah.gnu.org/projects/xnee/]("http://savannah.gnu.org/projects/xnee/").
Extract the archive to some folder.
Go over to the folder and then type:
```
./configure --enable-gnome-applet --prefix=/usr

```
Unless you had all the necessary files in place you will not succeed in the previous step.
Try installing from synaptic: libpanel-applet2-dev, build-essential, libxtst-dev, and libgtk2.0-dev (this will also install several dependencies).
Now try the configure step again and it should succeed.
Then type:
```
make
sudo make install
sudo gedit /etc/X11/xorg.conf

```
Add the following line in the module section
```
Load "record"

```
Restart X. (If you don't know how, then simply restart the computer (or logout (and just to be sure CTRL+ALT+BACKSPACE) and log back in)).
You could learn to use GNEE, but I stuck to CNEE.

I created two bash scripts (which you can put in /usr/local/bin if you don't know how else to set it up) (Make them executables. (In Nautilus file manager right click on file then set to executable on the permissions tab.)
Script 1 is MacRec
```
sleep 0.3s
cnee --record -o /tmp/cnee_$1.xns --events-to-record 10000 --keyboard  --stop-key Shift_R

```

Script 2 is MacPlay
```
sleep 0.3s
cnee --replay --keyboard --file /tmp/cnee_$1.xns --stop-key Shift_R -sp 10

```

On any terminal (command prompt) type MacRec 1 (or any other value "Val" to create a tmp macro file /tmp/cnee_Val.xns).
Hit the right shift key to stop recording the events.

MacPlay 1 (or whatever "Val" you used) should play back the file.

You should just have to add --mouse to the cnee arguments to record and play back mouse events, but I didn't test that.

Now setup your keyboard shortcuts for your desktop (On XFCE it is under Settings->Settings Manager->Keyboard, for gnome it is probably under System->Preferences->Keyboard), I setup shortcuts for the commands "MacRec 1", "MacPlay 1", "MacRec 2" and "MacPlay 2".

Either look up the documentation on the site or "man cnee" to check what other options you may find useful in cnee.

Sincerely,
Aouie

---

