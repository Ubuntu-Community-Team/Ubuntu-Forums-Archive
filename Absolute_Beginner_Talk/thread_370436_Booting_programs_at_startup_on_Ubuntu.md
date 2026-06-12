---
title: "Booting programs at startup on Ubuntu"
date: 2007-02-25
forum: Absolute Beginner Talk
---

### Post by TimJBart on 2007-02-25
Hi,

I want Beryl, Gaim, and Last.fm to run very time I start my computer.  What is the easiest way of doing this?

I am used to windows where there is a STARTUP folder in the start menu:) 

Thanks

---

### Post by RomeReactor on 2007-02-25
Hi. If you're using Edgy, go to "System-->Preferences-->Sessions" and click on the 3rd tab, "Startup Programs".

---

### Post by tgalati4 on 2007-02-25
There are several places to put startup items in Ubuntu.  They are not obvious.  

Some candidates:

.xinitrc  (things that should be started with the xserver)
.bash_profile (things that should be started with each new bash session)

There is some info found in:

more /etc/init.d/README

You can insert processes  at several places during bootup and run level (single verus multiuser)

Under Dapper there is System-->Preferences-->Sessions

There is a "Startup" tab to drag applications (from the application menu on th left side.)  This is probably what you are looking for.

Good luck

---

### Post by TimJBart on 2007-02-25
thanks guys, that is exactly what I was looking for.  I knew it would be easy, just didn't know where to find it.

Should I be able to drag things into that window because they don't seem to do anything.

I take it for gaim I just add

```
gaim
```

and beryl

```
beryl-manager
```

---

### Post by tgalati4 on 2007-02-25
I just assumed that drag and drop would work since it works in many other Gnome applications.  Oh well.  At least you found what you were looking for.

---

### Post by TimJBart on 2007-02-26
> **tgalati4 said:**
> I just assumed that drag and drop would work since it works in many other Gnome applications.  Oh well.  At least you found what you were looking for.

Yes thank you.  You sorted out my problem for me.  I love how fast it boots ubuntu even with a few extra programs booting on startup.  Very impressed.

---

### Post by TimJBart on 2007-02-26
I have another question now :)

How do I get programs to start just in the system tray, and not show their windows.   for example, I want Gaim to run and log in, but I don't need it to show my contacts list every time I boot.

Thanks!

---

### Post by tgalati4 on 2007-02-26
I'm sure there is a command line switch such as 
#gaim -loginbutdontshowmycontactseverytimeIboot

man gaim

This will give you a list of options.

When you find the switches that you need, edit the gaim line in Startup Tab in Session Manager and add the switches.  Stand back and be amazed.

Good luck.

---

### Post by TimJBart on 2007-02-27
so it'll be different for each program I load.  I need to find one for SKype and one for Gaim.  Thanks I'll take a look

---

### Post by kelbizzle on 2007-02-27
[http://ubuntuforums.org/showthread.php?t=314141](http://ubuntuforums.org/showthread.php?t=314141) there ya go

---

### Post by kelbizzle on 2007-02-27
Is your gaim in the system tray? Because mine starts right to the system tray. Make sure in the interface preferences the system tray icon is shown.

---

### Post by TimJBart on 2007-02-27
> **kelbizzle said:**
> Is your gaim in the system tray? Because mine starts right to the system tray. Make sure in the interface preferences the system tray icon is shown.

Yes it is in the system tray fine, it is just I don't want the buddylist opening every time I boot.  I'd rather it just stayed in the system tray and didnt bother me :)

Tonight, I'll try the extended plugins that was in the thread you linked to. Thanks

---

### Post by tgalati4 on 2007-02-27
There's the easy way. The right way.  And the Linux way.  Aren't the forums grand?

---

