---
title: "How to take a screenshot of the login screen?"
date: 2005-11-03
forum: Art &amp; Design
---

### Post by Greeface on 2005-11-03
I was wondering how I would go about taking a screenshot of my GDM Login screen.  The 'Print Screen' key didn't work, but I kinda expected that.
Thanks

---

### Post by aysiu on 2005-11-03
I think some kind of emulator helper program (like Qemu) might help. I'm thinking you'd boot a live CD through Qemu ```
qemu -cdrom /dev/cdrom
``` install the theme you want, log out, then take the screenshot...

---

### Post by carbon-12 on 2005-11-03
sudo apt-get install xnest
gdmflexiserver --xnest

Then System -> Take Screenshot

---

### Post by benplaut on 2005-11-03
[QUOTE=carbon-12]sudo apt-get install xnest
gdmflexiserver --xnest

Then System -> Take Screenshot[/QUOTE]

scratch that last step, just do prt-scrn and alt

and no, i don't think there's a way to get the xnest res higher :mad:

---

### Post by Greeface on 2005-11-04
Hey, 
When I do 'gdmflexiserver --xnest' it says "Cannot start new display.  You do not seem to have the authentication needed for this operation.  Perhaps your .Xauthority file is not set up correctly."
Any ideas?
Thanks

---

### Post by carbon-12 on 2005-11-04
[QUOTE=benplaut]scratch that last step, just do prt-scrn and alt

and no, i don't think there's a way to get the xnest res higher :mad:[/QUOTE]

In Xnest, I'm able to change the resolution using **-geometry HxW**. For example:

Xnest :1 -geometry 1024x768

would give me a window 1024x768. :) Can't figure out how to get it to work with gdmflexiserver though. :(

---

### Post by carbon-12 on 2005-11-04
[QUOTE=Greeface]Hey, 
When I do 'gdmflexiserver --xnest' it says "Cannot start new display.  You do not seem to have the authentication needed for this operation.  Perhaps your .Xauthority file is not set up correctly."
Any ideas?
Thanks[/QUOTE]

Hmmm thats strange, that only happens if I try to start gdmflexiserver with sudo. Your doing this as a user right? This all seems to work on my machine:

[http://img496.imageshack.us/img496/662/gdmxnest7zu.jpg](http://img496.imageshack.us/img496/662/gdmxnest7zu.jpg)

To be honest, I'm not really sure what else the problem could be (I'm not 1337 enough :( ). Someone whos a lot smarter than me will proably come along though :)

---

### Post by carbon-12 on 2005-11-04
OK I just tried something different and it seems to work with user and sudo, so maybe this might solve your problem.

**gdmthemetester console /usr/share/gdm/themes/THEME_NAME/**

For default Ubuntu,
THEME_NAME = Human

and just:
[B]
ls /usr/share/gdm/themes/[/B]

for the other ones. Hope that helps.

---

### Post by Greeface on 2005-11-07
Ah, okay.  I was doing that as root and that was my problem.  Thanks for all of the help!

---

### Post by matthewburke on 2006-09-07
> **Greeface said:**
> Hey, 
When I do 'gdmflexiserver --xnest' it says "Cannot start new display.  You do not seem to have the authentication needed for this operation.  Perhaps your .Xauthority file is not set up correctly."
Any ideas?
Thanks

I actually get the same error. Only I have tried it both as root and as myself. It works fine if I boot normally into gnome. I get the error when I am in a gnome XGl compiz session. Can anyone help me with this.

Here's the error:
[ATTACH]15441[/ATTACH]

---

### Post by tacubuntuforums on 2007-07-01
gdmthemetester's help says:

"..If you set the environment variable XNESTSIZE to <width>x<height> (e.g. 800x600)
you can test the greeter at that resolution..."


After a while of trying to use it, NOT IMMEDIATELY AFTER (maybe because later I used export for the variable)  it worked, at least for the login screen, because a persistent error doesn't let me login with any of the 

**gdmthemetester *<environment>* ...**

different options

I also tried to use **gdmXnest** with a comand line for xnest but another error doesn't let me continue. This time it seems that cannot use the keyboard. Maybe that's because my gnome configuration does not correspond to that of Xnest, I use non-american keyboard. But I don't know if this is the reason.

the messages in my terminal command line  say things like:

** (gdmXnest:5801): WARNING **: Can't exec, trying Xnest
Couldn't get keyboard.

or

"(gdmgreeter:5854): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed"

the moment I start typing the username in all different ways I tried to use the gdmXnest command options.

---

### Post by jjross on 2007-07-01
I followed this to get a screenshot of my GDM screen

> Capturing your GDM screen

Once you masterpiece is done, you will need a screenshot. This part is a bit tricky as you have already logged off and do not have access to The Gimp o any other graphical screen capture application.
The best way around is to create a small script that switches from the text console to the graphical scren and takes the picture automatically. This script can be created by issuing the following command in your console: echo "chvt 7 ; sleep 5 ; XAUTHORITY=/var/gdm/:0.Xauth DISPLAY=:0.0 import -window root /tmp/gdm-shot.png" > /tmp/capture[[TableOfContents]] Note: This assumes your login screen is in VT7, meaning that you press CTRL+ALT+F7 to switch to your graphical screen
Now log off to the GDM screen and hit CTRL+ALT+F1 to switch to your text console. Log in as root and type sh /tmp/capture. The screen will switch to GDM and after five seconds you will hear a BEEP. If everything worked as expected, your screenshot will be located at /tmp/gdm-shot.png
Note that import is part of the ImageMagick package .
This is located at this site [http://live.gnome.org/GnomeArt/Tutorials/GdmThemes#head-c88c5d81cb55ce0da1b121759067d547f1e7748c]("http://live.gnome.org/GnomeArt/Tutorials/GdmThemes#head-c88c5d81cb55ce0da1b121759067d547f1e7748c")

---

### Post by RawMustard on 2007-07-17
In case anyone was still wondering how to set the size when testing GDM login screen.
Just type

```
export XNESTSIZE=1024x768
```
and then
```
 gdmthemetester console /usr/share/gdm/themes/ThemeName/
```

cheers!

---

### Post by tacubuntuforums on 2007-07-17
As I said before, in my system:

```
export XNESTSIZE=<width>x<height>
gdmthemetester console /usr/share/gdm/themes/<MyThemeName>
```

does not work for loging in. It shows the login screen that size, but after introducing the user name, you can't continue.

Here's the message I receive when the login screen appears::

(gdmgreeter:4278): Gtk-CRITICAL **: gtk_widget_hide: assertion `GTK_IS_WIDGET (widget)' failed

---

### Post by RawMustard on 2007-07-18
Sorry, I don't understand what you're trying to do.  Why would you want to login this way?  I only posted what I did because I thought people were having trouble setting the size for screen shots and such.

---

### Post by nowshining on 2007-09-08
installed xnest went to terminal typed gdmflexiserver --xnest opened up a new display area - awesome by the way.. :) an it worked now I gotta crop the thing tho..

---

### Post by exploder on 2007-09-08
I almost have it. If I can just figure out a way of not having the panel show up in the screenshot.

---

### Post by exploder on 2007-09-08
I used The Gimp to take the screenshot and everything turned out good!

Thanks everyone, for all of the help!

---

### Post by merlin_ie on 2010-01-23
> **exploder said:**
> I almost have it. If I can just figure out a way of not having the panel show up in the screenshot.

dont know if this will be of any help as its an old topic, but i came across the same prob last nite and then i read about ALT+PRNT screen...no panel trouble :D

---

