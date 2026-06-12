---
title: "Getting Xubuntu to work"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by intense.ego on 2008-02-09
I just installed Xubuntu and there seem to be some problems and some questions i have:

1) is there a simple and easy step-by-step guide on how to install compiz fusion on xubuntu (it is already working on gutsy so compatibility is not a problem)?

2)Conky seems to just suddenly move to the middle of the desktop instead of the right where it is supposed to be.

That's it for the moment.

EDIT: Also, how do I increase the volume. The keys on my keyboard don't seem to work with that.

---

### Post by Therion on 2008-02-09
[How to Set Up Compiz]("http://forlong.blogage.de/article/2007/8/29/How-to-set-up-Compiz-Fusion").

Can't help you with Conky.

As for volume control, the only thing I can suggest since your keyboard is not responding (and assuming using the volume knob for the speakers themselves is not an option) is to use the Volume Control icon in the panel.  If you don't see an Volume Control icon in your panel, right-click on either panel and then select "Add to Panel".  Scroll down to the System & Hardware section and drag the Volume Control icon where you want it on one of the panels.

---

### Post by intense.ego on 2008-02-09
It's a laptop, so there is no volume knob. Thanks for your suggestions. I will try them out.

---

### Post by intense.ego on 2008-02-09
I enabled compiz, but the window manager has disappeared. There is no X button or minimise/maximise. I remember with Feisty, reloading the window manager would fix this. how do i do it from the terminal?

---

### Post by gn2 on 2008-02-09
To adjust the volume create a panel launcher for volume.
Right click on the panel and use the options to add it.

---

### Post by Kilz on 2008-02-09
open a terminal and type ```
mousepad ~/.conkyrc 
```to edit the hidden conky settings file. In that file you will find these settings. These are from my conkyrc. 


alignment top_right
gap_x 55
gap_y 100

Yours probably say alignment middle or center. the gap_x is pixels from right the gap _y is pixels from top. Edit them to place conky where you want it. You will have to restart conky for the settings to change.

---

### Post by intense.ego on 2008-02-09
> **gn2 said:**
> To adjust the volume create a panel launcher for volume.
Right click on the panel and use the options to add it.

Thank you, but when the volume buttons still don't work by default.

---

### Post by sub2007 on 2008-02-09
> **intense.ego said:**
> I enabled compiz, but the window manager has disappeared. There is no X button or minimise/maximise. I remember with Feisty, reloading the window manager would fix this. how do i do it from the terminal?

Assuming that you're using the Emerald Window Decorator:

```
emerald --replace
```

---

### Post by gn2 on 2008-02-09
> **intense.ego said:**
> Thank you, but when the volume buttons still don't work by default.

Do you mean the keyboard Fn shortcuts?
No idea how to make those work, my laptop has a slidery twiddly dial thingumajig.

---

### Post by intense.ego on 2008-02-09
I'm not using the emerald window decorator. Do I have to install it or can I use the default one?

---

### Post by intense.ego on 2008-02-09
> **gn2 said:**
> Do you mean the keyboard Fn shortcuts?
No idea how to make those work, my laptop has a slidery twiddly dial thingumajig.

No, there is a button specifically for volume increase/decrease. My laptop is a thinkpad t60 BTW.

---

### Post by sub2007 on 2008-02-09
> **intense.ego said:**
> I'm not using the emerald window decorator. Do I have to install it or can I use the default one?

No need to install emerald unless you want to. The default is GTK Window Decorator, you can restart it using this command:

```
gtk-window-decorator --replace
```

---

### Post by intense.ego on 2008-02-10
> **sub2007 said:**
> No need to install emerald unless you want to. The default is GTK Window Decorator, you can restart it using this command:

```
gtk-window-decorator --replace
```

Your solutions work, but then if I close the terminal window, it goes back to the way it was. I can't type "exit" either because the "xxxxx@xxxxxxx-computer" doesn't come up.

---

### Post by sub2007 on 2008-02-10
Press ALT + F2 and enter that command into the box and press enter. Then save the session (System > Preferences > Sessions and then Save Session) and it should work automatically the next time you log in.

---

