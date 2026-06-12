---
title: "Screen Resolution"
date: 2006-06-02
forum: Absolute Beginner Talk
---

### Post by sophtpaw on 2006-06-02
Fresh Install of Dapper. 1600x1200 makes my dapper look waaay too small. 
I go to Screen Resolution in System/Preferences and try the alternatives but they don't save and i keep ending up back at 1600x1200. I've had to increase all the fonts and toolbars but it doesn't feel right. Scrolling down Firefox it is a bit rough somehow.

Anyone, else find resolution doesn't hold?

---

### Post by nalmeth on 2006-06-02
When you switch, don't you get a dialogue come up saying "Keep this resolution" with a 15 second timer?

---

### Post by sophtpaw on 2006-06-02
[QUOTE=nalmeth]When you switch, don't you get a dialogue come up saying "Keep this resolution" with a 15 second timer?[/QUOTE]
nope :???:

---

### Post by BobSongs on 2006-06-02
When you bring it down from 1600x1200, what do you bring it down to? Try bringing it to the next larger size. See if the confirmation box appears. If so, click Keep This Resolution. If it just doesn't appear... I dunno what to tell ya.

---

### Post by sophtpaw on 2006-06-03
[QUOTE=BobSongs]When you bring it down from 1600x1200, what do you bring it down to? Try bringing it to the next larger size. See if the confirmation box appears. If so, click Keep This Resolution. If it just doesn't appear... I dunno what to tell ya.[/QUOTE]
bob, can you imagine that is exactly what i tried. I tried the next size down which over here is 1280x1024, although the next size down further still is probably what i really need.
Anyhow, what happens is after selecting size it takes me back to login screen; retype login name and password and next thing i'm back where i started.

Anyone else have any ideas? :confused:

---

### Post by Dr. Nick on 2006-06-03
You can edit your /etc/X11/xorg.conf and remove 1600x1200 so it cant be used. Try this out

sudo gedit /etc/X11/xorg.conf

Look under the screen section and delete the resoulition, then save the file and logout. It should pick the next highest one. You might backup the file first just to be safe until you get used to editing it. Though it isnt to hard a job

---

### Post by BobSongs on 2006-06-03
Dr. Nick's advice = good. ;)

---

### Post by auhsor on 2006-06-03
I am a new user to Ubuntu and I also have this problem. When I change the resolution and click apply, it brings me back to the login screen. When I log in it's as if I didn't do anything. I'll try what Dr Nick said. I havn't updated any drivers for my video card (I'm not sure if I need to), and it might be possible that having multi monitors could affect it?

---

### Post by confused57 on 2006-06-03
[QUOTE=Dr. Nick]You can edit your /etc/X11/xorg.conf and remove 1600x1200 so it cant be used. Try this out

sudo gedit /etc/X11/xorg.conf

Look under the screen section and delete the resoulition, then save the file and logout. It should pick the next highest one. You might backup the file first just to be safe until you get used to editing it. Though it isnt to hard a job[/QUOTE]

If that doesn't work, you might try:

```
sudo dpkg-reconfigure xserver-xorg
```

then you can select which resolutions you want your monitor to be able to display.

---

### Post by sophtpaw on 2006-06-03
[QUOTE=confused57]If that doesn't work, you might try:

```
sudo dpkg-reconfigure xserver-xorg
```

then you can select which resolutions you want your monitor to be able to display.[/QUOTE]

Yes, but to go the reconfiguring route you need to first travel through many valleys and have knowledge of each terrain. video card, then one thing after the other before getting to actual screen resolution!

The gedit method i have not tried. Simply remove 1200xetc from all columns?

WHY is this so difficult in Dapper?! 
9 months of toil and i can't simply change screen resolution from the gui that is dedicated to do this.   hmpf[-(

---

### Post by Dr. Nick on 2006-06-03
[quote=sophtpaw]Yes, but to go the reconfiguring route you need to first travel through many valleys and have knowledge of each terrain. video card, then one thing after the other before getting to actual screen resolution!

The gedit method i have not tried. Simply remove 1200xetc from all columns?

WHY is this so difficult in Dapper?! 
9 months of toil and i can't simply change screen resolution from the gui that is dedicated to do this.   hmpf[-([/quote]

Yes remove the 1600x1200 or whatever from each depth line. Most likely you monitor got detected differently on this install then previous ones. If you did the dpkg-reconfigure but and chose a different monitor it would limit what res. are available, but simply hand editing it is easier

---

### Post by MojoWorkin on 2006-06-05
Could I jump in here, and ask a related question, instead of creating a new topic?
I'm running an nVidia 7900GT, and a Samsung 930B LCD (native res. 1280x1024) and I don't have an option for this desired res. 
Highest it shows is 1024x768.
Can I simply edit in the desired res. into the results of the terminal command:
( sudo dpkg-reconfigure xserver-xorg ) and have my problem solved?
Or am I missing an easier way to add a bigger res.?
And, what is the name of the linux equivalant for Windowblinds in Ubuntu?
(to change themes, wallpapers, etc.) 
Which dependancy does Dapper/Drake rely on?
(KDE, Gnome, GDM, etc. / before I dnld any)

This is only my second day in Ubuntu 6.06, after a shaky start during install, sorry if this is considered a hijacked post.

---

### Post by nalmeth on 2006-06-05
sudo dpkg-reconfigure xserver-xorg

Will bring you through a wizard type configuration. You'll come to the screen resolution's step eventually. Pick defaults for everything unless you know better. 

It aint pretty but it works.

Yeah, it is sort of hijacking, and tends to be frowned on, but being your second day it's not a big deal.

Don't hesitate to start your own thread for any problems in the future.  :)

---

### Post by MojoWorkin on 2006-06-05
I just left the Wizard, but couldn't add the 1280x1024 value to the entry.
I pressed all keys, and couldn't place an asterisk (*) in square to select.
What did I miss?
It wrote a new cfg file, but res. wasn't selected.
Thanks for answering my questions.

---

### Post by Dr. Nick on 2006-06-05
[quote=MojoWorkin]I just left the Wizard, but couldn't add the 1280x1024 value to the entry.
I pressed all keys, and couldn't place an asterisk (*) in square to select.
What did I miss?
It wrote a new cfg file, but res. wasn't selected.
Thanks for answering my questions.[/quote]

When running the dpkg to pick res. maks sure you also get the monitor selecion part, pick a monitor that has the highest res you want. Dont just let it autodetect it.

---

### Post by MojoWorkin on 2006-06-05
Ah! Now that makes sense.... the whole idea of Linux, is Control!
Thanks man, will try that.

---

