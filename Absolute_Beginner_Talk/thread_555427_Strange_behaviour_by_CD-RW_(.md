---
title: "Strange behaviour by CD-RW ("
date: 2007-09-20
forum: Absolute Beginner Talk
---

### Post by getmeoutofhere on 2007-09-20
This isn't really a problem, more of an observation - I don't really use CD-RWs.

Anyway, I formatted a CD-RW on XP, then put it in Ubuntu.

Ubuntu didn't recognise it.

I blanked the disk with Gnomebaker.  The blanking only seemed to get as far as 99%, so I stopped it.

Yet the disk seemed OK.  Was able, on Ubuntu, to transfer some files to it.

Then I couldn't open the CD drive - not with an 'eject' command or with the physical button.  I tried various 'sudo...' commands recommended on these forums, to cause an eject, but they didn't work.

Anyway, I fired up Virtualbox, with the CD still stuck in the drive.

Virtualbox fired up, I then, in Virtualbox, tried to mount the CD.  At least I pressed the button to do this - ie, on Virtualbox, Devices -> Mount CD/DVD-ROM.   There were no options given, of either a host drive or an image.  In fact... the entire system froze, at all levels.  Everything on the screen froze, in and out of Virtualbox.  Had to press the off button on the computer.

I did this again, just in case it was a fluke.  It happened again, the moment I chose the Virtual box mount CD option.  So, under the right circumstances, a CD-RW would appear to be able to crash Ubuntu.

Any suggestions as to what happened?  Thanks.

---

### Post by getmeoutofhere on 2007-09-20
No-one got any ideas?  

And by the way, would there have been anyway to have got out of this frozen situation without turning off the whole computer?  No Ubuntu equivalent of of CTRL-ALT-DELETE to get into something like a task manager and hopefully close down the offending process?

---

### Post by tenjin1 on 2007-09-20
May want to check your /etc/fstab entry to see if your cd drive is getting mounted on boot-up.
in terminal:

```
sudo gedit /etc/fstab
```

or 

```
hdparm
```

** How to enable Ctrl+Alt+Del to open System Monitor in GNOME**
```
gconftool-2 -t str --set /apps/metacity/global_keybindings/run_command_9 "<Control><Alt>Delete"
gconftool-2 -t str --set /apps/metacity/keybinding_commands/command_9 "gnome-system-monitor"

```

---

### Post by LowSky on 2007-09-20
if you reboot the system can you open the Drive?

If not, your drive is dead.. you'll need to buy a new one.

---

### Post by getmeoutofhere on 2007-09-20
LowSky,

The drive is fine.

---

### Post by getmeoutofhere on 2007-09-20
tenjin1,

Thanks for the tips.  As I said, it's not a problem,  more of an observation.  I'm still very new to Ubuntu, and I'm hesitant about using the terminal too much, until I've got a better grip with the system.  I think I need to read a few books before I go ploughing in.

Anyone with Virtualbox want to do what I did, and see if it crashes their system? :)

---

### Post by tenjin1 on 2007-09-20
> **getmeoutofhere said:**
> tenjin1,

Thanks for the tips.  As I said, it's not a problem,  more of an observation.  I'm still very new to Ubuntu, and I'm hesitant about using the terminal too much, until I've got a better grip with the system.  I think I need to read a few books before I go ploughing in.

Anyone with Virtualbox want to do what I did, and see if it crashes their system? :)

No problem friend :)

If hesitant about working in terminal...I guess I should have told you to make a backup copy of the file before you go changing it ..that way it is safe and you can revert back to it if something goes wrong.

```
sudo cp /etc/fstab /etc/fstab_backup
```
then..
```
sudo gedit /etc/fstab
```

and hdpam will just list your cd drives you have with info regarding them

---

