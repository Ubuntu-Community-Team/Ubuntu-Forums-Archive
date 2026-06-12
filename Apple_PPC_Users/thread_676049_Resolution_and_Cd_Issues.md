---
title: "Resolution and Cd Issues"
date: 2008-01-23
forum: Apple PPC Users
---

### Post by keiranevans on 2008-01-23
Afternoon all,

I acquired an Ibook G3 500 yesterday which had Mac OS9 installed. It had to go straight away.

I downloaded Ubuntu live Installer which wouldn't do anything.

So i downloaded the Alternative install of Kubuntu. Which i did manage to install, But it was un-usable due to massive display issues.

So i downloaded xubuntu, which installed fine, but wouldn't boot, however after some quick searching im now posting on the machine,

I have a few issues though...

1) I can only have a max screen resolution of 800x600

and

2) How am i meant to eject the CD Drive?!

Look forward to any response in regards to solving these problems.

Thanks

---

### Post by stream303 on 2008-01-23
> **keiranevans said:**
> 1) I can only have a max screen resolution of 800x600

Great - you're almost home!  Looks like you need to edit your /etc/X11/xorg.conf file.  This thread may help.  Lots of G3 resolution problems like this fixed in the forums.  This may not be exactly what you need, but should help:

[http://ubuntuforums.org/showthread.php?t=663583](http://ubuntuforums.org/showthread.php?t=663583)

If editing at 800x600 is just too weird/fuzzy, you can always CTRL-ALT-F1 to a virtual terminal to do editing with say the nano editor.  When you are done with your editing, you can CTRL-ALT-F7 to get back to the gui and log yourself out to see if your changes took effect.  Or you can reboot from the terminal with
```
sudo shutdown -r now
```

Usually F12 should eject the cd.  Or if you are in a terminal, just type "eject"

---

### Post by keiranevans on 2008-01-24
All sorted now. Thanks alot!

---

