---
title: "How to boot to command line instead of GUI?"
date: 2007-01-12
forum: Absolute Beginner Talk
---

### Post by JohnnyAvocado on 2007-01-12
I would like to boot to the command line when starting dapper drake instead of booting to the GUI. Would I modify the runlevel? If so which file is it in and what would I modify? 

Thanks for your help.

---

### Post by pay on 2007-01-12
Editing /boot/grub/menu.list would help you. Use something like this```
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda1 ro single
```it shoudl already be there though with "Recovery Mode" kernel. Alternatively you could just change the default kernel that is booted to whatever your "Recovery Mode" kernel is.

---

### Post by Tomosaur on 2007-01-12
pay - that way logs you in as root, and you can't get back out of it without rebooting.

Easiest method is to cd to /etc/init.d/ and to remove the graphical apps. The init.d directory is basically a collection of scripts which are run when the computer boots up. If you remove the GUI startup scripts, you should be able to boot straight to a command line.

---

### Post by JohnnyAvocado on 2007-01-12
Gents, thanks so much for the help. 
-Tomosaur, would I still be able to type: startx when I want to boot into Gnome?

Thanks again.

Johnny

---

### Post by Moldz on 2007-01-12
There is no need to modify the grub menu and don't remove any of the graphical apps from /etc/init.d.  The correct place to modify the default runlevel is **/etc/inittab**.

---

### Post by Tomosaur on 2007-01-12
EDIT: Woops, repost in a bit.

---

### Post by Indras on 2007-01-12
> **Moldz said:**
> There is no need to modify the grub menu and don't remove any of the graphical apps from /etc/init.d.  The correct place to modify the default runlevel is **/etc/inittab**.

This is the way I've always done it in other distros, but the /etc/inittab file doesn't seem to exist on my installation of Ubuntu.  It has to be set in some other place, if at all.  The readme file at /etc/init.d/README has some information, but I'd need somone more experienced with Ubuntu to fill in the details.

---

### Post by wildkarde on 2007-01-12
ok, this is what you do

go into /etc/rc6.d and look for K01gdm.
Should be there.  Now rename it to S01gdm.

this can be accomplished by typing this:
```
sudo mv /etc/rc6.d/K01gdm /etc/rc6.d/S01gdm
```

Someone please correct me if i'm wrong.  I'm an ubuntu user but my experience is with UNIX.

EDIT::::

my mistake.  it's actually rc5.d not rc6.d

EDIT::::

ok, mistake 2..  it's the other way around.

```
sudo mv /etc/rc5.d/S01gdm /etc/rc5.d/K01gdm
```

<sigh> i need a nap

EDIT:::::

yep, that's my bad.. good night.

---

### Post by bodhi.zazen on 2007-01-12
At default, run levels 2,3,4, and 5 are the SAME in Dapper.

The default run level is 2

To change so that you boot to the CLI, see this post:

[http://ubuntuforums.org/showpost.php?&p=1483050&postcount=3](http://ubuntuforums.org/showpost.php?&p=1483050&postcount=3)

substitute kdm for gdm if you use kde ...

Now, from the CLI you can start GDM with:

```
sudo gdm
```

Or start x with```
startx
```

Or start gnome with:```
gnome-session
```

See **pay's** post to change your default run-level. Thus you can have one entry in grub to boot to CLI, and a second to boot to GDM

**NOTE:** Booting in Edgy and Feisty has changed !! This advice applies to Dapper and earlier...

HTH 8)

---

### Post by Indras on 2007-01-12
> **wildkarde said:**
> ok, this is what you do

go into /etc/rc6.d and look for K01gdm.
Should be there.  Now rename it to S01gdm.

this can be accomplished by typing this:
```
sudo mv /etc/rc6.d/K01gdm /etc/rc6.d/S01gdm
```

Someone please correct me if i'm wrong.  I'm an ubuntu user but my experience is with UNIX.

Sorry, runlevel 6 is specifically reserved for rebooting... try typing "sudo init 6" to switch to runlevel 6... just the same as typing "reboot."

Likewise, runlevel 0 is always the same as "halt" - which just shuts your computer down/off.  Runlevel 1 is usually single-user mode, just the same as the "recovery mode" option in grub.  But the other four runlevels (2, 3, 4, and 5) vary from distribution to distribution.  We need to know how init determines which runlevel it automatically boots to without an /etc/inittab, and which runlevel is non-GUI.  In my Redhat days, runlevel 3 was text-only and runlevel 5 was graphical login (xdm).  Is Ubuntu the same?  I'm going to find out real quick... brb.

Edit: nevermind, everyone else solved it first :)

---

### Post by bodhi.zazen on 2007-01-12
> **Indras said:**
> Sorry, runlevel 6 is specifically reserved for rebooting... try typing "sudo init 6" to switch to runlevel 6... just the same as typing "reboot."

Likewise, runlevel 0 is always the same as "halt" - which just shuts your computer down/off.  Runlevel 1 is usually single-user mode, just the same as the "recovery mode" option in grub.  But the other four runlevels (2, 3, 4, and 5) vary from distribution to distribution.  We need to know how init determines which runlevel it automatically boots to without an /etc/inittab, and which runlevel is non-GUI.  In my Redhat days, runlevel 3 was text-only and runlevel 5 was graphical login (xdm).  Is Ubuntu the same?  I'm going to find out real quick... brb.

Edit: nevermind, everyone else solved it first :)

Good information on run levels :)

I had the same problem migrating to Ubuntu from Centos :)

---

### Post by pcomelade on 2007-01-12
check this:

[http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html](http://www.debianadmin.com/debian-and-ubuntu-linux-run-levels.html)

Hope it helps!


M;

---

