---
title: "Unable to start the settings manager 'gnome-settings-daemon'"
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by Fixel on 2007-10-18
Hi, when i go to System -> Preferences -> Appearance

it gives me the following error:

> 
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.


I'd like to change theme but when I click the themes nothing changes. (except slight color nuances)

Then I tried to start the 'gnome-settings-daemon' through the terminal by typing:
```

sudo gnome-settings-daemon

```

And it gave me the following error:
[QUOTE]
Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.
[/CODE]

and oh, I'm running the gutsy RC.

---

### Post by Fixel on 2007-10-18
bump?

---

### Post by Officer Dibble on 2007-10-18
I'm not saying this is the answer to your problem, but certainly worth considering.

I once had a problem similar to this and it was due to a bad install, which was in itself due to a badly written CD. If it is something you would like to try, download Gutsy again and write it at a slower speed - maybe about 18x or 24x and try installing again.

I found this solved the problem for me, but others may have a better suggestion. :)

---

### Post by Fixel on 2007-10-18
Gonna try the official releaes of gutsy now... buuhuu...

---

### Post by darkazurka on 2007-10-31
Fixel: Try that : "change theme but when I click the themes nothing changes. (except slight color nuances)". Then reboot. This solved this issue for me. There's no more any warning messages.

Officer Dibble: I tried the "check for CD defects" and it said "no errors found" .... phew :)
-----------
Original message:
Really? This is the first time I run into a problem.

I'll give more detail into my problem. This message box that our friend Fixel mentioned , didn't pop up the first time I started "System -> Preferences -> Appearance". I've used it numerous times without any problems before.

After I installed VLC media player and the numerous(!) dependencies, and after I've just now booted into ubuntu Gutsy (7.10) it shows our friend's error message, and I can't choose themes as well.
------
Officer Dibble: Is it possible to understand if the CD was burnt the wrong way by checking the 'built-in' function that the cd has to "check this CD for errors"? I mean, if it says "no errors", does that mean that it was burnt the right way, in your opinion? Your help is always welcome.

---

### Post by Palmyra on 2007-12-04
I have the same problem.

---

### Post by dast on 2007-12-06
I just upgraded from 7.04 to 7.10 and I can confirm this bug happened to me

$uname -a
Linux wolf 2.6.22-14-generic #1 SMP Sun Oct 14 23:05:12 GMT 2007 i686 GNU/Linux

See the following bugs.

[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/146946)
[https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277](https://bugs.launchpad.net/ubuntu/+source/gnome-control-center/+bug/138277)

Unlike some people, I found that i could start the daemon from the command line. So... I "fixed" the problem by going under System > Preferences > Sessions (in the main Gnome menu) and adding a startup program entry for the daemon. That does not work for everyone, apparently. Others have hacked up init.d scripts (i believe) to start this daemon, which I opted not to try.

See also
[http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon)

---

### Post by iammeagain on 2007-12-08
> **dast said:**
> 

See also
[http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon](http://ubuntuforums.org/showthread.php?t=587410&highlight=gnome+settings+daemon)

found a solution, from above


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

---

### Post by quantboy on 2007-12-14
Joshua, 

Those two lines completely fixed the problem for me.  But why did not problem start in the first place?  My Gutsy was running fine for weeks when this problem came from out of the blue.

Patrick
:confused:

---

### Post by Nzer24 on 2007-12-15
Yeah this happened to me suddenly too, and I've had it fine for months. I'll try your fix.

---

### Post by Nzer24 on 2007-12-15
Totally works! How did you figure out what to put in those files?

---

### Post by popch on 2007-12-15
I have had the same error message as well when booting Ubuntu 7.10, but only from time to time (two or three times, I believe).

The problem went away each time when I rebooted the computer.

---

### Post by iammeagain on 2007-12-20
This seems to be another way to fix this problem or maybe a related problem. > **willie_wang said:**
> I had this exact problem... took me ages to figure out what was wrong.

but this fixed it.

System > Preferences > Login Window > Local (tab)

then make sure the Show Actions Menu box is ticked. Fixed my problem. Hope it fixes yours.

:popcorn:

This is the link to the full thread. [http://ubuntuforums.org/showthread.php?p=3989462#post3989462](http://ubuntuforums.org/showthread.php?p=3989462#post3989462)

---

### Post by cunfuzd4 on 2008-01-15
> **Nzer24 said:**
> Yeah this happened to me suddenly too, and I've had it fine for months. I'll try your fix.



I started to get the same "Unable to start the settings manager..." message on every startup and reboot.  Since it did happen after an update I figured possible damage to dbus. I went to the synaptic package manager and searched for dbus then marked it for reinstallation (it asked for the installation disk when I clicked on apply).  After reinstallation and reboot the problem has not returned

---

### Post by Sinkingships7 on 2008-01-15
i just had this problem a few minutes ago.

at the log in screen, go to option -> select session.

select gnome (2.) and make it your default.

then log in.

---

### Post by MountainX on 2008-02-18
> **cunfuzd4 said:**
> I started to get the same "Unable to start the settings manager..." message on every startup and reboot.  Since it did happen after an update I figured possible damage to dbus. I went to the synaptic package manager and searched for dbus then marked it for reinstallation (it asked for the installation disk when I clicked on apply).  After reinstallation and reboot the problem has not returned

I just had this problem too. Happened on every reboot or cold boot since last night (3 in total). I tried your solution and on the next reboot, no problem. Thanks.

---

### Post by vixmusic01 on 2008-03-03
I have the smae problem - gutsy has been working fine after a clean install. I then installed Scribus. No problem. Then I installed some codecs to run on my player.

Thats when I saw the error message. 

Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.

Could the codecs be conflicting? Seems odd.

I will try your fix above, but I know for sure it was not a faulty CD as I installed perfectly and the session manager worked fine until I started installing software.

Is there a restore point feature in Ubuntu so I can go back in time to last known good?

I would be happy to set a restore point before installing software so I will not run into further problems.

I love Ubuntu and want to use it, so I don't want to have to wipe the drive and start again (my last fix)

Thanks all,

vixmusic01

---

### Post by speirint on 2008-03-09
I too have a similar problem that just happened overnight. I believe it was after I had installed some packages for shared drives through shared folders, but now I don't know how to disable or undo it, and I'm not sure what will happen to some of my data if I reboot to an older session (I'm unable to back up with my external drive, but that's a different problem).

  I reinstaled the dbus, and now I can access the appearence tab, but I still receive the same message (Unable to start the settings manager 'gnome-settings-daemon'.
Without the GNOME settings manager running, some preferences may not take effect. This could indicate a problem with Bonobo, or a non-GNOME (e.g. KDE) settings manager may already be active and conflicting with the GNOME settings manager.) every time I open it or try changing the desktop background.  

As an absolute beginner, I am willing to try the things iammeagain posted, but I don't know how to get to the necessary place to edit the stuff.  Do I just paste it into terminal?

---

### Post by bertram_wooster on 2008-03-13
speirint: If you haven't dealt with this problem yet. Can I suggest you try the reinstallation of dbus first. I suggest this because it doesn't involve tampering with system config files, which in my experience is always preferable.

***

I had this same problem.

At login I got a message, which I don't have the details of sorry. I had to OK it to proceed.

Then at one point my Firefox became transparent to the underlying windows.

When I went to investigate in: System -> Preferences -> Appearance
I got the error message mentioned by Fixel in his original post.

I opened a terminal and tried to start the gnome-settings-daemon and got an error (included at the bottom of the post).

I followed cunfuzd4's advice to reinstall dbus which I have expanded below:

 - Go to: System -> Administration -> Synaptic Package Manager (this requires your password).
 - Either search for dbus or scroll down to it and click on the left hand square. 
 - A menu appears, 
 - Select the Reinstallation option.
 - Click the Apply button at the top of the screen.
 - Restart your machine.

If this doesn't work for you, then it may be time to edit config files.

I hope this helps.

Bertie


P.S. Here is the error from the gnome-settings-daemon command.

```

$ sudo gnome-settings-daemon
** (gnome-settings-daemon:7571): WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-N54BNcwI00: Connection refused

(gnome-settings-daemon:7571): GnomeKbdIndicator-WARNING **: Unable to connect to dbus: Failed to connect to socket /tmp/dbus-N54BNcwI00: Connection refused

(gnome-settings-daemon:7571): GnomeKbdIndicator-WARNING **: Not connected to dbus, will not register the object
xrdb:  "*Label.background" on line 220 overrides entry on line 150
xrdb:  "*Text.background" on line 226 overrides entry on line 191
xrdb:  "*Label.foreground" on line 232 overrides entry on line 151
xrdb:  "*Text.foreground" on line 238 overrides entry on line 192

** (gnome-screensaver:7578): WARNING **: failed to register with the message bus

```

---

### Post by Rising_deecaY on 2008-03-18
Hi,
Thanks for mentioning that solution. It worked.

---

### Post by Dr_VidoKifla on 2008-03-23
Could not save the file /etc/X11/Xsession.d/55gnome-session_gnomerc.

You do not have the permissions necessary to save the file. Please check that you typed the location correctly and try again.


So what do I do now, I am a beginner so please help?

---

### Post by dark_phantom on 2008-03-26
I tried all of those suggestions, but I'm still having problems.  Any other fixes out there?

---

### Post by bertram_wooster on 2008-03-30
Dr_VidoKifla:

What follows is a (possibly over-long) explanation, but it might help.

I am guessing that you have opened the file as a normal user and not admin/su. The file will have permission levels for the owner, the group and everyone else. So if I open a terminal, go to the appropriate folder with the 'cd' command and list the contents with the 'ls -l' (long list) command I will see.

```

$ cd /etc/X11/Xsession.d/
/etc/X11/Xsession.d$ ls -l
total 28
-rw-r--r-- 1 root root 1878 2007-07-04 15:55 20x11-common_process-args
-rw-r--r-- 1 root root  899 2007-07-04 15:55 30x11-common_xresources
-rw-r--r-- 1 root root 1561 2007-07-04 15:55 50x11-common_determine-startup
-rw-r--r-- 1 root root  361 2007-10-05 09:31 55gnome-session_gnomerc
-rw-r--r-- 1 root root   80 2007-10-10 20:35 60xdg-user-dirs-update
-rw-r--r-- 1 root root  612 2007-07-04 15:55 90x11-common_ssh-agent
-rw-r--r-- 1 root root  166 2007-07-04 15:55 99x11-common_start

```

To interpret this first locate the line corresponding to our file and you will see 'root root' in the 2nd and 3rd column. This means the file is owned by user root group root. The first column shows me the associated permissions 'rw-r--r--', this is split into three sets of three permissions: user (read:write:execute), group (read:write:execute) and all(read:write:execute). Our file '55gnome-session_gnomerc' has permissions read and write for the user (root) and read permissions for the group (root) and all.

So from my user account I can read the file, but I must be root to edit it.

The quickest way I know to do this is to fire up a text editor via the sudo command in the terminal (the & means that this doesn't hog the command line while it is running)

```

/etc/X11/Xsession.d$ sudo gedit 55gnome-session_gnomerc &
[sudo] password for bertie:

```

It asks for a password here, unless you have played with super-user before this will be your user password.

I hope this helps and there are no more problems.

Bertie

---

### Post by gfixler on 2008-04-08
@cunfuzd4: I found so many answers in this, and other threads on the same issue here, that I decided to rank them from least, to most difficult/potentially dangerous. Your "reinstall dbus" was thus the first, easiest, and safest method, and in fact, worked beautifully! I can now actually see the proper Ubuntu Studio theme colors, enter the Appearance settings, and use Compiz with no errors, and no longer get an error at startup! Things had been working after the install, and broke after the massive set of updates, so something in there must be responsible for hosing dbus, or something related to dbus that the installation thereof fixes.

Thanks!

Edit: I spoke too soon! It worked yesterday, but right after this reply, I booted it up, and the boot error was back! I simply added a launcher to my panel for now with the command:

```
gnome-settings-daemon
```

gnome-settings is another command, so as I typed that in, it changed the icon to a little mixer panel, which I've decided to keep. I'll try other things in here, later, and likely report back, but for now, I'm just glad to (as usual) have a decent workaround.

---

### Post by farpost on 2008-04-18
Thanks to all.  Used post #19 instructions and worked to fix problem after reboot.  Using Ubuntu 7.10 server w/GUI installed and occured, I think, sometime after using SSH terminal access to server.

---

### Post by crisdeli on 2008-04-19
Thanks everyone, I had the same problem after installing some new packages and now I 've solved it by re-installing dbus.

---

### Post by crisdeli on 2008-04-19
Thanks everyone, I had the same problem after installing some new packages and now I 've solved it by re-installing dbus.:)

---

### Post by reuben_guillen on 2008-06-30
> **iammeagain said:**
> found a solution, from above
I tried this fix but I dont have this path available, /etc/X11/Xsession ....
I have /etc/X11 but after that I dont have the directory Xsession.d or anything like it.
Thanks for helping
Reuben

---

