---
title: "problem with screenlets.."
date: 2007-11-30
forum: Absolute Beginner Talk
---

### Post by sourcemorph on 2007-11-30
i've got this problem with the application "Screenlets" .. the ones given with the application work fine but the ones i downloaded from [http://www.gnome-look.org](http://www.gnome-look.org) don't install by themselves

then when i copy them to the /usr/local/share/screenlets folder n run them by ./xyz.py thing they give the following error msg..

"OSError: [Errno 13] Permission denied: '/home/surge/.config/Screenlets/WallpaperClock/default/"

i noticed that the read-write access to this folder is for root only.. so i changed it using chmod.. but even then the thing gives the same error.

---

### Post by quandary on 2007-11-30
read and write permission is not sufficient. You need executing permission:
chmod +x xyz.py

If that doesn't work, try sudo

---

### Post by sourcemorph on 2007-11-30
oh i tried sudo as well, dint work gave some other error.. do i need to add executing permission to the folder too..

i changed the chmod of "/home/surge/.config/Screenlets/WallpaperClock/def ault/"

---

### Post by quandary on 2007-11-30
> **sourcemorph said:**
> oh i tried sudo as well, dint work gave some other error.. do i need to add executing permission to the folder too..

i changed the chmod of "/home/surge/.config/Screenlets/WallpaperClock/def ault/"

Hm, i don't think you need executing permission on folders. But you can try ;-)
Maybe login as root is helpful...

---

### Post by sourcemorph on 2007-12-01
dunno nothing seems to work for those screenlets... but i downloaded other screenlets frm gnome-look n they work.... the WallpaperClock thing isn't working tho.... i really wanted to see it...

---

### Post by Paul820 on 2007-12-01
Extract the archive to your desktop, you will get a folder from it. Now go to your home folder and press Ctrl+h, look for a folder called **.screenlets**, if you can't find it, make it. Don't forget the period/full stop in front of the name. Now put that folder that you extracted into the **.screenlets** folder and start the program. Your new screenlet will be in there with the others.

---

### Post by sourcemorph on 2007-12-01
im still getting the same error...


[email]surge@glory:~/.scre[/email]enlets/WallpaperClock$ ./WallpaperClockScreenlet.py Traceback (most recent call last):
  File "./WallpaperClockScreenlet.py", line 511, in <module>
    screenlets.session.create_session(WallpaperClockScreenlet)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 391, in create_session
    session = ScreenletSession(classobj)
  File "/usr/lib/python2.5/site-packages/screenlets/session.py", line 72, in __init__
    self.path = BaseDirectory.save_config_path('Screenlets/' + p)
  File "/var/lib/python-support/python2.5/xdg/BaseDirectory.py", line 59, in save_config_path
    os.makedirs(path, 0700)
  File "/usr/lib/python2.5/os.py", line 172, in makedirs
    mkdir(name, mode)
OSError: [Errno 13] Permission denied: '/home/surge/.config/Screenlets/WallpaperClock/default/'


what shud i do?

---

