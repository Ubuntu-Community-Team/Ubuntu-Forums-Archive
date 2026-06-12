---
title: "Help, i lost my shutdown button!!"
date: 2007-12-06
forum: Absolute Beginner Talk
---

### Post by chaddiesel on 2007-12-06
I recently tried to let the desktop effects work and changed it back to no effects in the appearance options. Now when i hit quit, the shutdown button is missing. There is restart, log off, hibernate and others. But no shut down.

What do I do?

---

### Post by Biggy on 2007-12-06
i have same problem 


help plzzzz !!!!!!!!

---

### Post by Martin Witte on 2007-12-06
right click on the upper gnome bar, select add to panel option, select here the quit icon

---

### Post by DragonKore on 2007-12-06
Try this post: [http://ubuntuforums.org/showthread.php?t=467841](http://ubuntuforums.org/showthread.php?t=467841)

---

### Post by Cyblade on 2007-12-06
Just run the command poweroff and you pc will shutdown,simple

---

### Post by Biggy on 2007-12-06
i see the red button in panel and click but the problem is.: i can't se the shut down and restart option ...

---

### Post by Biggy on 2007-12-06
help

---

### Post by DragonKore on 2007-12-06
Did you check the thread?

> Run gnome-settings-daemon after everything has started and if your theme comes back just add gnome-settings-daemon to your startup programs.

---

### Post by Biggy on 2007-12-06
i try gnome settings daemon but give error :

 gnome-settings-daemon

** ERROR **: You can only run one xsettings manager at a time; exiting

aborting...
Aborted (core dumped)

---

### Post by chaddiesel on 2007-12-07
I still have no idea how to fix this problem. I have the quit button on the gnome bar but no shutdown on the menu it pops up. 

Any Ideas?

---

### Post by Happy_Man on 2007-12-07
Hmmm... are you using the Ubuntu login screen, or one of the other ones? If you are using something other, try the command ```
sudo dpkg-reconfigure gdm
``` and select GDM from the list. Then restart X (ctrl-alt-backspace), that may put the shut down option back. If it doesn't, well, you can always open a terminal and enter: ```
sudo shutdown now
``` Or you could log off and shut down from the login screen (that should always work).

---

### Post by teryowen on 2007-12-07
find in sessions or system processes look into the stuff that is run at starts up and make sure the power managment stuff is checked as to run, and all the other stuff just in case. this way the process for shuting down will be running.

---

### Post by Bigbird999 on 2007-12-07
I had a similar issue that was only solved by uninstalling the gnome power manager and reinstalling it via synaptic,  I seem to remember that ```
gconf-editor
``` under apps>gnomepower-manager and mucking about in the sub folders enabling some check boxes helped.

YMMV

BB

---

### Post by iammeagain on 2007-12-08
I am having a similar problem and it seems related to that I have KDE controlling the login screen. So i guess most of my visual settings must be done in KDE now. Is there anyway to stop kde from controlling settings while logged into gname? and have gnome-settings-daemon running instead?

---

### Post by chaddiesel on 2007-12-08
well, i'm pretty sure it happened whenever i tried to add effects to the actions of the computer.  I'm still not having any luck.

---

### Post by iammeagain on 2007-12-08
Is there a simple way to change just that gdm or kdm is the defualt display manager? I have figured out that is likely my problem, maybe other's issues are related.

I think this may work then set back to gdm. I just tried it, so we'll see.

```

sudo dpkg-reconfigure gdm

```



nope no luck, I get
```

 Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This
could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may 
already be active and conflicting with the GNOME settings manager.
```

when i run ```
 sudo gnome-appearance-properties %F 
``` from the terminal

---

### Post by willie_wang on 2007-12-08
I had this exact problem... took me ages to figure out what was wrong.

but this fixed it.

System > Preferences > Login Window > Local (tab)

then make sure the Show Actions Menu box is ticked. Fixed my problem. Hope it fixes yours.

:popcorn:

---

### Post by willie_wang on 2007-12-08
> **willie_wang said:**
> I had this exact problem... took me ages to figure out what was wrong.

but this fixed it.

System > Preferences > Login Window > Local (tab)

then make sure the Show Actions Menu box is ticked. Fixed my problem. Hope it fixes yours.

:popcorn:

ooh, you may have to restart x after doing this - [ctrl + alt + backspace]

---

### Post by iammeagain on 2007-12-08
found a solution, from here [http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon)


> **Joshua Swink said:**
> This seems to be related to this gnome-session bug: 
[http://bugzilla.gnome.org/show_bug.cgi?id=395488](http://bugzilla.gnome.org/show_bug.cgi?id=395488)

Here is a workaround. Two files are modified.

Change /etc/X11/Xsession.d/55gnome-session_gnomerc, adding two lines (identified below by comments):

```
# ADD FOLLOWING LINE
rm -f /tmp/session-is-gnome
BASESTARTUP=`basename "$STARTUP" | cut -d\  -f1`
if [ "$BASESTARTUP" = gnome-session -o \
        \( "$BASESTARTUP" = x-session-manager -a \
        "`readlink /etc/alternatives/x-session-manager`" = \
                /usr/bin/gnome-session \) ]; then
  GNOMERC=$HOME/.gnomerc
  if [ -r "$GNOMERC" ]; then
    . "$GNOMERC"
  fi
  # ADD FOLLOWING LINE
  touch /tmp/session-is-gnome
fi
```

Then change /etc/X11/Xsession.d/99x11-common_start completely, to the following text:

```
if [ -f /tmp/session-is-gnome ]; then
  exec /usr/bin/dbus-launch $STARTUP
else
  exec $STARTUP
fi
```

The way above my post is another solution, it seems to vary which one works for you.

---

### Post by chaddiesel on 2007-12-11
I've tried everything except the last thing posted. I'm not quite understanding what to do there.

---

### Post by chaddiesel on 2007-12-11
I JUST FOUND IT!!!!! wow, I can't believe it.

System->_ Administration_-> Login window-> Local(tab)

Checked the show actions check box. And it works.....which is funny because I don't believe that it was checked before.

Anyways, It's fixed. Thank ya'll tremendously for the help. :)

---

### Post by iammeagain on 2007-12-20
> **chaddiesel said:**
> I've tried everything except the last thing posted. I'm not quite understanding what to do there.

It only sorta worked, a temporary fix in a way. I just reinstalled because I had an almost fresh install and didn't care to mess with it too much.
I think the login window fix seems to work much better.

---

