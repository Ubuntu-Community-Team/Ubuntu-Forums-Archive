---
title: "[SOLVED] Help!! I need my mouse back &amp;amp; to re-edit /etc/X11/xorg.conf"
date: 2008-05-19
forum: Apple Hardware Users
---

### Post by Brightbelt on 2008-05-19
Hi,
I've done a doozy. I was trying a fix for my mighty mouse (which does not scroll at all) and I replaced the "Input Device" section for the mouse with a new one instead of adding my fix. 

Well it didn't work and I made a backup of my xorg.conf but it can't help me sitting on my desktop because NO MOUSE WILL WORK NOW.

I'm not even sure I did the backup file right. Anyways, how can I edit my /etc/X11/xorg.conf file ????

I've tried the keyboard shortcut to get to the terminal (Contr-Alt F1) and it takes me to the black screen command line. I tried doing 'sudo gedit /etc/X11/xorg.conf' there but it says it "cannot display file" for some reason. 

How can I get any mouse back? I DO KNOW HOW to edit the /etc/X11/xorg.conf' file to get it back to normal once I get to the file. That's no problem. I just can't get to the file.

I appreciate any help,...Many Thanks, Frank B.

PS I'm dual booting and have rEFit, so I can get to a shell command line. I'm new to that and have no idea what to do there.

---

### Post by cyberdork33 on 2008-05-20
> **Brightbelt said:**
> Hi,
I've done a doozy. I was trying a fix for my mighty mouse (which does not scroll at all) and I replaced the "Input Device" section for the mouse with a new one instead of adding my fix. 

Well it didn't work and I made a backup of my xorg.conf but it can't help me sitting on my desktop because NO MOUSE WILL WORK NOW.

I'm not even sure I did the backup file right. Anyways, how can I edit my /etc/X11/xorg.conf file ????

I've tried the keyboard shortcut to get to the terminal (Contr-Alt F1) and it takes me to the black screen command line. I tried doing 'sudo gedit /etc/X11/xorg.conf' there but it says it "cannot display file" for some reason. 

How can I get any mouse back? I DO KNOW HOW to edit the /etc/X11/xorg.conf' file to get it back to normal once I get to the file. That's no problem. I just can't get to the file.

I appreciate any help,...Many Thanks, Frank B.

PS I'm dual booting and have rEFit, so I can get to a shell command line. I'm new to that and have no idea what to do there.
gedit requires xorg, so you can't run it from a console. try nano.

Or you can just start things from the keyboard if you know the shortcuts ;)
ALT+F2 opens the "Run Application" dialog.  you can start whatever you want from there (gnome-terminal, or even just gedit)

The easiest way to backup your file is to make a copy before making changes:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
```

Then if you need to copy it back,
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
```

---

### Post by Brightbelt on 2008-05-20
Thanks Cyber....There's one "tiny" little detail I need help with.

How do I click 'Save' or do a 'Save' without a mouse??

Pressing enter justs creates a space like I'm in a word processing document...
Many Thanks, Frank B.

---

### Post by cyberdork33 on 2008-05-20
> **Brightbelt said:**
> Thanks Cyber....There's one "tiny" little detail I need help with.

How do I click 'Save' or do a 'Save' without a mouse??

Pressing enter justs creates a space like I'm in a word processing document...
Many Thanks, Frank B.
Ctrl+S is save in gedit
Alt+f4 closes it.

---

### Post by Brightbelt on 2008-05-20
Many Thanks, Cyber. Well, I'm back in business, but with a regular mouse for now. ;)

---

