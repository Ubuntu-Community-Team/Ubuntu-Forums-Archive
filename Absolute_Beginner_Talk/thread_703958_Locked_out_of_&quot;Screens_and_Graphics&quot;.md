---
title: "Locked out of &quot;Screens and Graphics&quot;"
date: 2008-02-21
forum: Absolute Beginner Talk
---

### Post by Sugi on 2008-02-21
I can not open "Screens and Graphics" under System > Administration.  I can't only open it with multiple monitors or even just one monitor.  When I click on it, the password window comes up and I type in the password and hit enter.  It says it starting up "Starting Screens and Graphics", but then nothing happens.


Please, if anyone knows what to do, let me know.  I use Sytem > Preferences > Screen Resolutions to set resolutions.


Sugi

---

### Post by dcstar on 2008-02-21
> **Sugi said:**
> I can not open "Screens and Graphics" under System > Administration.  I can't only open it with multiple monitors or even just one monitor.  When I click on it, the password window comes up and I type in the password and hit enter.  It says it starting up "Starting Screens and Graphics", but then nothing happens.
........i

Open a terminal, and see what happens who you enter this:
```
gksu displayconfig-gtk
```

---

### Post by taurus on 2008-02-21
Are you able to run sudo/gksudo?  Can you post the output of this command from a terminal?

```
sudo apt-get update
```

p.s.  I didn't have any problem running System -> Administration -> Screens and Graphics at all.

---

### Post by Sugi on 2008-02-21
dcstar:
> midori@midoriGUTSY:~$ gksu displayconfig-gtk
[]
  File "/usr/bin/displayconfig-gtk", line 75, in <module>
    app = DisplayConfig(options)
  File "/usr/lib/python2.5/site-packages/displayconfiggtk/DisplayConfig.py", line 190, in __init__
    debug_scan_pci_filename=self.options.pcitable)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 392, in __init__
    self._finalizeInit()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 411, in _finalizeInit
    self.setLayout(gfxcard._getDetectedLayout())
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 965, in setLayout
    gfxcard.setLayout(XSetup.LAYOUT_CLONE)
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1177, in setLayout
    screen._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1854, in _resyncResolution
    self.gfx_card.setup.getPrimaryScreen()._resyncResolution()
  File "/var/lib/python-support/python2.5/displayconfigabstraction.py", line 1810, in _resyncResolution
    (preferred_width,preferred_height) = self.getAvailableResolutions()[-1]
IndexError: list index out of range

taurus, I use to be able to run "Screens and Graphics/gksu displayconfig-gtk", but not anymore.

Whats wrong with it?


Sugi

---

### Post by Sugi on 2008-02-21
Bump

---

### Post by Sugi on 2008-02-21
Bump

---

### Post by Sugi on 2008-02-22
Bump

---

### Post by Sugi on 2008-02-22
Bump

---

### Post by Sugi on 2008-02-22
Bump

---

### Post by philinux on 2008-02-22
It's probably borking at your xorg.conf.

Try doing the reconfigure and see if that sorts it.

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by Sugi on 2008-02-22
If I do,
> sudo dpkg-reconfigure -phigh xserver-xorg should I make a back up of my currently xorg.conf?  could it lock me out of GUI?  I want to be every careful.  I have, many times locked myself out of the GUI before.  It's hard to get back in, at least for me.

Sugi

---

### Post by ahsile on 2008-02-22
Always make a backup :)

---

### Post by philinux on 2008-02-22
You might have a backup allready have a look with nautilus at the time stamps of any file like
xorg.conf~ 
xorg.conf1

etc.

You may remember when it was working and you could use any of the backups created by the system.

---

### Post by ahsile on 2008-02-22
I like to create my own backups before I fiddle with things, just so I can give them meaningful names:

xorg.conf.before-changing-xxxxx

Mostly because I can never remember when things were working/not-working.

---

### Post by Sugi on 2008-02-22
I think I have something like 23 of them or somewhere near that.  What should I do to use one of my back ups?  Should I just rename my current one to something like "xorg.conf-not-working" and change for example "xorg.conf21" to "xorg.conf"?   Would that work?

Sugi

---

### Post by philinux on 2008-02-22
Yep that would do. You'd need 

gksudo nautilus 

to do it. Then ctrl alt backspace to restart the session. Look a the time and date of your backups to get the most recent that you think might work.

---

### Post by Sugi on 2008-02-22
so......
 - change "xorg.conf" to "xorg.conf-not-working"
 - then change "xorg.conf23" to "xorg.conf"
 - gksudo nautilus
 - restart

Is that the corrent order?

I have not had the Screens and Graphics working for a long time.  I would just have to test it trail by error.

Sugi

---

### Post by Sugi on 2008-02-22
Bump

---

### Post by philinux on 2008-02-22
> **Sugi said:**
> so......
 - change "xorg.conf" to "xorg.conf-not-working"
 - then change "xorg.conf23" to "xorg.conf"
 - gksudo nautilus
 - restart

Is that the corrent order?

I have not had the Screens and Graphics working for a long time.  I would just have to test it trail by error.

Sugi

Run gksudo nautilus first, navigate to /etc/X11

then do your stuff

---

### Post by Sugi on 2008-02-22
Cool, thanks.  I'll give it a try after school and let you know the update.

Sugi

---

### Post by Sugi on 2008-02-26
Sorry for the late reply.  Papers have been keeping me busy.  >.<  Anyways, I ran the 
> sudo dpkg-reconfigure -phigh xserver-xorg
and now Screens and Graphics can be displays now.  So, I am going to hook up my s-video and see what happens.  Test didn't go so well, so now I am going to do a restart with the new config.

Sugi

---

### Post by Sugi on 2008-02-26
After a few restarts, I can now display video on my s-video again.  :)  So, I am pretty happy.  I am going to try multiple monitors now.  I am shooting for three different outputs.  I will let everyone know how that works, but I am starting to believe that Screens and Graphics won't cut it.  I might have to go into the xorg.conf for this.  If anyone knows some tips on this, please share with me.


Sugi

---

