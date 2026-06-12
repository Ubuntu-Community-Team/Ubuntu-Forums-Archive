---
title: "Xubuntu and Xfwm4's composite manager"
date: 2006-03-01
forum: Absolute Beginner Talk
---

### Post by Sutekh on 2006-03-01
Long winded title, but simple enough question (if you know XFCE  ;))

I installed Xubuntu through apt-get.  What I'd like to know is if Xfwm4's composite manager was enabled in the Xfwm4 binary, or will I have to build it myself with the *--enable-compositor* option?

---

### Post by Gurgeh on 2006-06-02
A very good question - editing the xorg.conf file doesn't appear to change anything....

---

### Post by doublejoon on 2006-06-02
hm I installed xubuntu yesterday....the composite stuff works ok for me

Check in Settings->Window Manager Tweaks for transparency settings
The panels have there own individual transparency settings as well

bottom of my xorg.conf

```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```

---

### Post by Sutekh on 2006-06-02
[quote=doublejoon]hm I installed xubuntu yesterday....the composite stuff works ok for me

Check in Settings->Window Manager Tweaks for transparency settings
The panels have there own individual transparency settings as well

bottom of my xorg.conf

```
Section "Extensions"
    Option "Composite" "Enable"
EndSection
```[/quote] Guess I should have replied to my own thread, when I solved this.  

Yes that's all you need to do to enable the xfwm compositor.

Then you install an application such as [transset]("http://packages.ubuntu.com/dapper/x11/transset") from the universe repository to change the transparency of individual windows```
sudo apt-get install transset
```You can either use transset from the Terminal```
transset 0.5
``` and click on a window to change its opacity to 0.5, or assign a shortcut to do the same.

Love the xfwm compositor...

---

