---
title: "First-time installer issue-- graphical interface"
date: 2006-05-09
forum: Absolute Beginner Talk
---

### Post by deactivated-30Jul2012 on 2006-05-09
This is my first time installing Ubuntu on a machine.  After finishing the installation and prepping to login I get an interesting screen that says:

> Failed to start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diangnose the problem?

I hit yes and get a version information screen with a lot of info that doesn't seem to relate to the problem.  After getting out of that screen I get:

> The X server is now disabled.  Restart GDM when it is configured correctly.

So, how do I configure it correctly? :confused: It then takes me to shell access.

Thanks for any help, and sorry if this is posted in the wrong place.

---

### Post by browndog on 2006-05-09
[QUOTE=Matt Housch]This is my first time installing Ubuntu on a machine.  After finishing the installation and prepping to login I get an interesting screen that says:



I hit yes and get a version information screen with a lot of info that doesn't seem to relate to the problem.  After getting out of that screen I get:



So, how do I configure it correctly? :confused: It then takes me to shell access.

Thanks for any help, and sorry if this is posted in the wrong place.[/QUOTE]

Try typing the following:

```
dpkg-reconfigure xserver-xorg 
```

When you do this it will give you the chance to reconfigure xserver.  Read each screen carefully, and make sure you select your monitor settings appropriately.  Most of the default settings should be fine, but when it asks you if you want to autodetect your graphics settings say no and do it manually...autodetecting is what got you into the problem in the first place.  Good luck.

BD

---

### Post by mostwanted on 2006-05-09
Type in

```
sudo dpkg-reconfigure xserver-xorg
```

That should start a configuration process for your X server (what makes graphics on UNIX systems). The sudo part is very important! (in case you see the similarities between my post and the post above mine)

The password it'll ask you for is just your user password.

---

### Post by deactivated-30Jul2012 on 2006-05-09
[QUOTE=browndog]Try typing the following:

```
dpkg-reconfigure xserver-xorg 
```

When you do this it will give you the chance to reconfigure xserver.  Read each screen carefully, and make sure you select your monitor settings appropriately.  Most of the default settings should be fine, but when it asks you if you want to autodetect your graphics settings say no and do it manually...autodetecting is what got you into the problem in the first place.  Good luck.

BD[/QUOTE]

The first question is to auto-detect video hardware...I select no and it gives me the list of drivers.  The card is Nvidia-- is nv the appropriate server driver, and is this likely what was causing the problem?

---

### Post by mostwanted on 2006-05-09
[QUOTE=Matt Housch]The first question is to auto-detect video hardware...I select no and it gives me the list of drivers.  The card is Nvidia-- is nv the appropriate server driver, and is this likely what was causing the problem?[/QUOTE]

nv is probably the best choice (the open source, no-3D Nvidia driver), but if that causes you problems, go for the mesa one.

---

### Post by deactivated-30Jul2012 on 2006-05-09
Thanks for the help folks.  I ended up hard-installing the actual Nvidia drivers.  This seems like wonderful community and I appreciate the first-time support.

---

### Post by gRiMgRaVy014 on 2006-05-09
Mesa drivers work with linux cards?

---

