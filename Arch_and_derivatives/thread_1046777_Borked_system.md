---
title: "Borked system"
date: 2009-01-21
forum: Arch and derivatives
---

### Post by ghindo on 2009-01-21
I have a GNOME/Openbox setup, and it's set to auto login with GDM.  Thing is, as of today my computer just automatically logs in to GNOME and everything freezes.  The panels and background load, but I can't move the mouse, and Ctrl + Alt + Backspace doesn't do anything.  I tried the fallback kernel, but that didn't help either.

I updated my system (pacman -Syu) this morning, but I'm kinda doubting that that has anything to do with it, as I think only bash and curl were updated.

I'm guessing I have to fix it via a LiveCD.  I was wondering if anybody had any suggestions on how I could fix this?  Thanks. :popcorn:

---

### Post by handy on 2009-01-21
What happens if you take GDM out of the equation? Do you have a happy Arch before you startx?

---

### Post by ghindo on 2009-01-21
> **handy said:**
> What happens if you take GDM out of the equation? Do you have a happy Arch before you startx?I don't know.  My Arch installation starts X automatically, so I don't have an opportunity to take GDM out of the equation.

---

### Post by namegame on 2009-01-21
I would also think the recent update to Xorg (hotplugging and such) is also a suspect in this matter.

I had the same issue a few weeks ago. I added this to my Xorg.conf to fix the problem.

```

Section "ServerFlags"
     Option "AutoAddDevices" "False"
EndSection

```

---

### Post by handy on 2009-01-21
> **namegame said:**
> I would also think the recent update to Xorg (hotplugging and such) is also a suspect in this matter.

I had the same issue a few weeks ago. I added this to my Xorg.conf to fix the problem.

```

Section "ServerFlags"
     Option "AutoAddDevices" "False"
EndSection

```

Good thinking. :-)

I had to do the same thing to get my keyboard & mouse to work properly.

Still, I've only had two problems from using -Syu in 9 months - the Linux kernel bug & the Xorg update, both problems from upstream of Arch, which isn't bad all things considered.
[I]
@**ghindo**:[/I] How long has it been since your last -Syu ?

If it has been some weeks I think the Xorg update is your problem & you will need to edit your xorg.conf as *namegame* suggested in the previous post.

---

### Post by ghindo on 2009-01-22
> **handy said:**
> [I]
@**ghindo**:[/I] How long has it been since your last -Syu ?

If it has been some weeks I think the Xorg update is your problem & you will need to edit your xorg.conf as *namegame* suggested in the previous post.I ran -Syu this morning, but I think it only updated bash and curl.  I run -Syu fairly regularly, so I don't think Xorg is the problem.  I think it may be a configuration I messed with :(

Thanks for the help so far, guys!

---

### Post by fwojciec on 2009-01-22
I don't know what the solution to your problem is ultimately, but what you should do to begin with is boot with some live cd, mount arch partition and remove gdm from daemons line in rc.conf so that it is not started automatically.  That way, at least, you will be able to begin sorting it out.

---

### Post by kellemes on 2009-01-22
> **ghindo said:**
> I have a GNOME/Openbox setup, and it's set to auto login with GDM.  Thing is, as of today my computer just automatically logs in to GNOME and everything freezes.  The panels and background load, but I can't move the mouse, and Ctrl + Alt + Backspace doesn't do anything.  I tried the fallback kernel, but that didn't help either.

I updated my system (pacman -Syu) this morning, but I'm kinda doubting that that has anything to do with it, as I think only bash and curl were updated.

I'm guessing I have to fix it via a LiveCD.  I was wondering if anybody had any suggestions on how I could fix this?  Thanks. :popcorn:

From Grub bootmenu..
Press 'e' to get to editmode.
Scroll down to the kernelline you want to edit.
Press 'e' again to edit this line.
Add "ro 3"  to boot into runlevel 3. No X that is.
(This edit isn't permanent)

Now fix GDM or remove it all together and get [SLIM]("http://slim.berlios.de/") ;-)

And to make sure you can always boot into console just add another kernelline to /boot/grub/menu.lst that brings you to runlevel 3.

---

### Post by ghindo on 2009-01-22
> **kellemes said:**
> From Grub bootmenu..
Press 'e' to get to editmode.
Scroll down to the kernelline you want to edit.
Press 'e' again to edit this line.
Add "ro 3"  to boot into runlevel 3. No X that is.
(This edit isn't permanent)

Now fix GDM or remove it all together and get [SLIM]("http://slim.berlios.de/") ;-)

And to make sure you can always boot into console just add another kernelline to /boot/grub/menu.lst that brings you to runlevel 3.GDM still launches, even at runlevel 3 :(  Would that be because I have the GDM daemon set to load in the background?

I think I'm going to try fwojciec's solution.  SliTaz CD, here I come!

---

### Post by fwojciec on 2009-01-22
> **ghindo said:**
> Would that be because I have the GDM daemon set to load in the background?

The solution kellemes described works if you use the "inittab" method to start a graphical login manager.  If GDM is started as a daemon it won't work.

---

### Post by mips on 2009-01-23
Try hitting the "CTRL+ALT+Backspace" sequence several times, in KDM that will throw me back to the console login prompt.

---

### Post by kellemes on 2009-01-23
> **fwojciec said:**
> The solution kellemes described works if you use the "inittab" method to start a graphical login manager.  If GDM is started as a daemon it won't work.

That's the method I use indeed, well.. with SLIM instead of GDM ofcourse ;-)
Sorry for the confusion..

---

### Post by crimesaucer on 2009-01-23
> **kellemes said:**
> That's the method I use indeed, well.. with SLIM instead of GDM ofcourse ;-)
Sorry for the confusion..

Same for me.

Don't put "gdm/slim" in your /etc/rc.conf daemons..... use /etc/inittab instead to start your login manager.


Edit the first section from id:3 to id:5, then choose your login manager (id:3 and xdm are default and will open to console):

```

## Only one of the following two lines can be uncommented!
# Boot to console
#id:3:initdefault:
# Boot to X11
id:5:initdefault:

```


```

# Example lines for starting a login manager
#x:5:respawn:/usr/bin/xdm -nodaemon
#x:5:respawn:/usr/sbin/gdm -nodaemon
#x:5:respawn:/opt/kde/bin/kdm -nodaemon
x:5:respawn:/usr/bin/slim >& /dev/null

```

---

### Post by ghindo on 2009-01-23
Thanks for all the responses, everybody :)

Unfortunately, even after removing GDM from rc.conf daemons, when I log into GNOME with xinit, the cursor doesn't respond, and Ctrl + Alt + Backspace still does nothing.  Maybe it *is* an Xorg problem.

---

### Post by fwojciec on 2009-01-23
> **ghindo said:**
> Thanks for all the responses, everybody :)

Unfortunately, even after removing GDM from rc.conf daemons, when I log into GNOME with xinit, the cursor doesn't respond, and Ctrl + Alt + Backspace still does nothing.  Maybe it *is* an Xorg problem.

Try the suggestion from Handy's post earlier about disabling "AutoAddDevices" option in xorg.conf.  My guess is that your problem has something to do with xorg hotplugging, and this setting disables it, making xorg.conf work like it used to in older versions of X.

---

### Post by kellemes on 2009-01-23
> **ghindo said:**
> Thanks for all the responses, everybody :)

Unfortunately, even after removing GDM from rc.conf daemons, when I log into GNOME with xinit, the cursor doesn't respond, and Ctrl + Alt + Backspace still does nothing.  Maybe it *is* an Xorg problem.

You can always check /var/log/Xorg.0.log for hints.

---

### Post by ghindo on 2009-01-23
> **fwojciec said:**
> Try the suggestion from Handy's post earlier about disabling "AutoAddDevices" option in xorg.conf.  My guess is that your problem has something to do with xorg hotplugging, and this setting disables it, making xorg.conf work like it used to in older versions of X.I edited my ~/xorg.conf with namegame's suggestion and things still aren't working.  GNOME loads with the background and panels, but the mouse and keyboard don't respond.  :(

I thought it might have something to do with .xinitrc, but that looks okay.  The only uncommented line is gnome-session.

---

### Post by smartboyathome on 2009-01-23
> **ghindo said:**
> I edited my ~/xorg.conf with namegame's suggestion and things still aren't working.  GNOME loads with the background and panels, but the mouse and keyboard don't respond.  :(

I thought it might have something to do with .xinitrc, but that looks okay.  The only uncommented line is gnome-session.

Edit your /etc/X11/xorg.conf, not your ~/xorg.conf.

---

### Post by ghindo on 2009-01-23
> **smartboyathome said:**
> Edit your /etc/X11/xorg.conf, not your ~/xorg.conf.Oh, okay.  For some reason, I hadn't made an /etc/X11/xorg.conf. :(

Created an /etc/X11/xorg.conf, added the options that were mentioned in this thread.  Looks like X works now :)  Thanks everybody.

---

