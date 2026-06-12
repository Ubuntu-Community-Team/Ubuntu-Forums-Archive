---
title: "Broken resolution ;\"
date: 2008-02-16
forum: Absolute Beginner Talk
---

### Post by Magictv on 2008-02-16
Hi, currently I'm using my laptop which is made for a 1440 x 900 resolution, but the current resolution it's running at is 640 x 480 which looks rather ridiculous.  Adminstration > screens + graphics wont allow me to change it to 1440 x 900.

Thanks for reading.

---

### Post by Magictv on 2008-02-16
Anyone?

---

### Post by RomeReactor on 2008-02-16
Hi. What video card do you have? If it's ATI or nVidia, have you installed the restricted drivers for it? If it's Intel, maybe installing 915resolution can help; look for it in Synaptic, or to install from the terminal (Applications->Accessories->Terminal):
```
sudo aptitude install 915resolution
```

EDIT: It looks like the 915resolution package is obsolete in newer versdions of Xorg. Just make sure you're using the **intel** driver instead of **i810**.

---

### Post by Magictv on 2008-02-16
My graphics card is an intel 945 apparently.

The strange thing is it was working fine ealier but has now gone to this tiny resolution.

---

### Post by RomeReactor on 2008-02-16
Have you installed anything that might have caused this--meaning, did you install anything or modify xorg.conf or something else and *then* noticed this change?

---

### Post by Magictv on 2008-02-16
What happened was I tried to select my monitor type from this list in admin > graphics + screens.  Once i selected a 1440 x 900 one the reolution switched to this small one and now i can't get it back.  Before I selected a 1440x900 monitor it was showing i was using a "plug and play" one.

---

### Post by Magictv on 2008-02-16
I have to go out now, i will be back later to investigate a bit more.  Thanks for the help.

---

### Post by RomeReactor on 2008-02-16
The plug and play monitor was the laptop's screen, correct? not an external monitor? Which video driver are you using?

In any case, did you try in 'System->Preferences->Screen Resolution'? Have you tried changing the driver in 'System->Administration->Screens and Graphics? Otherwise, you might have to reconfigure the display.

---

### Post by Magictv on 2008-02-16
> **RomeReactor said:**
> The plug and play monitor was the laptop's screen, correct? not an external monitor? Which video driver are you using?

In any case, did you try in 'System->Preferences->Screen Resolution'? Have you tried changing the driver in 'System->Administration->Screens and Graphics? Otherwise, you might have to reconfigure the display.


I have tried changing the resolution in both of those places.  Niether of them let me change it to 1440x900 as far as I can find.

I have tried changing the driver but i'm not sure what I should change it to.  Although I think it's the correct driver as the screen was working fine before and the only thing i changed that broke it was a screen resolution.

---

### Post by LacosteGirl23 on 2008-02-16
I got a new laptop for Valentine's Day...and the screen looks slightly blurry to me. I can't manage to get it where it works best for my eyes. I don't really understand. It's a Sony Vaio AR Series. Resolution is set at 1440x900? Anyone know what's been going on?

---

### Post by RomeReactor on 2008-02-16
Magictv, maybe reconfiguring your display will help; press CTRL+ALT+F1 to go to a terminal, log in if asked to, then run:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```
to make a backup of your current configuration. Then:
```
sudo /etc/init.d/gdm stop
```
to stop the display, and:
```
sudo dpkg-reconfigure xserver-xorg
```
accept all the defaults it shows you (unless you know for a fact that you need to change it) anbd when asked to select a video driver choose **intel**; also, when asked which resolutions you'd like, make sure to include the 1440x900--pressing the spacebar checks or unchecks the boxes.

Afterwards, your display should start automatically. If it doesn't, run:
```
sudo /etc/init.d/gdm start
```
or reboot:
```
shutdown -r now
```

LacosteGirl23, do you know what video card do you have? If you're unsure, please open a terminal (Applications->Accessories->Terminal) and write or paste:
```
lspci | grep VGA
```
and post the output.

---

