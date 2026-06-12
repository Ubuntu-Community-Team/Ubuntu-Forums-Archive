---
title: "Compiz problem"
date: 2007-02-28
forum: Art &amp; Design
---

### Post by afham07 on 2007-02-28
Hi guys,

I just install compiz and everything going right but facing problem at the last step ... here is the tutorial:

[http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide](http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide)

My problem is the last step (to run the compiz - type "compiz-tray-icon" in terminal). Once I press Enter, the error message comes out in terminal and the close, minimize and maximize buttons disappear.

The error msg that appeared from the terminal is:

"(compiz-tray-icon:5986): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:5986): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:5986): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:5986): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed"

What should I do to overcome this problem guys? Please help me . I really new in this Linux World! ..

---

### Post by unknown_zohaib on 2007-02-28
guy im having the same problem! and i dont get any toolbars displayed

---

### Post by afham07 on 2007-03-01
erm .. now problem become more comlicated .. :( .. compiz-tray-icon, this msg appeared in tterminat:

** (compiz-tray-icon:5092): WARNING **: Enabled to detect compiz binary !!

** (compiz-tray-icon:5092): CRITICAL **: gcm_tray_menu_new: assertion `gl_desktop != NULL' failed

** (compiz-tray-icon:5092): CRITICAL **: gcm_gl_desktop_enabled: assertion `self != NULL' failed

(compiz-tray-icon:5092): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:5092): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:5092): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:5092): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


please help me guys !!! .. please tell me how to uninstall/delete everything and start from 1st step .. FYI, I follow this tutorial, [http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide](http://www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide)

---

### Post by afham07 on 2007-03-01
i also got this error msg:

dpkg: serious warning: files list file for package `compiz-core' missing, assuming package has no files currently installed.

dpkg: serious warning: files list file for package `compiz-gnome' missing, assuming package has no files currently installed.

---

### Post by zyx321 on 2007-03-11
I'm having the same problem. I can still get the effects that I wanted (cube, transparency, wobbly), but it'd be nice if I could resolve the errors issue. Does anyone know?

---

### Post by LtPitt on 2007-03-21
Same here :(

---

### Post by FAT_C on 2007-03-26
i have the same problem too? 

can anyone help??? :confused: :confused:

---

### Post by wj32 on 2007-03-27
Guys, just use Beryl! It's much better... Search the forums for more info if you want.

---

### Post by finferflu on 2007-04-10
Same problem here. Compiz not working, but Beryl working...

```
~$ compiz-tray-icon 

(compiz-tray-icon:27353): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:27353): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(compiz-tray-icon:27353): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(compiz-tray-icon:27353): GLib-GObject-CRITICAL **: g_signal_connect_data: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

```

---

### Post by super.rad on 2007-04-11
well seems a lot of people are having the same problems, i've got compiz running fine on mine.
The errors you are getting at the terminal i got aswell but just ignored them.
To solve the missing toolbar (minimize, maximize and close) try typing this at the terminal (if you have a nvidia graphics card)
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig --add-argb-glx-visuals
sudo reboot
```

Hope this helps

---

### Post by finferflu on 2007-04-11
I would ignore them as well, if only compiz worked. And by the way, I'm using an ATI Radeon Mobility 7500, I forgot to mention that. The point is that I get the GL desktop with Beryl, but not with Compiz, so it's not a matter of drivers, I guess...

---

### Post by tjxray99 on 2007-05-16
> **super.rad said:**
> well seems a lot of people are having the same problems, i've got compiz running fine on mine.
The errors you are getting at the terminal i got aswell but just ignored them.
To solve the missing toolbar (minimize, maximize and close) try typing this at the terminal (if you have a nvidia graphics card)
```
sudo apt-get install nvidia-glx
sudo nvidia-xconfig --add-argb-glx-visuals
sudo reboot
```

Hope this helps



unfortunatley this doesnt correct the problem  I do have nvidia driver, and everything seems to work fine, but no toolbars are displayed when I enable gl desktop???

any help would be appreciated.

thanks

---

### Post by finferflu on 2007-05-16
> **tjxray99 said:**
> unfortunatley this doesnt correct the problem  I do have nvidia driver, and everything seems to work fine, but no toolbars are displayed when I enable gl desktop???

any help would be appreciated.

thanks
On Feisty Compiz works as a charm, are you on Edgy by any chance? If so I suggest you to upgrade to Feisty Fawn... 
Good luck ;)

---

### Post by tjxray99 on 2007-05-16
> **finferflu said:**
> On Feisty Compiz works as a charm, are you on Edgy by any chance? If so I suggest you to upgrade to Feisty Fawn... 
Good luck ;)

Sorry,   Yes i am running Fiesty as well.

Thanks
TJ

---

### Post by finferflu on 2007-05-17
Well, I am sorry I can't help you, I have an ATI graphics card... I thought we had the same problem, but apparently we haven't...
I wish you luck anyways...

---

### Post by Casla on 2007-05-17
I heard you can fix the no window boarder problem by adding this:

```
Option "AddARGBGLXVisuals" "True"
```

into the Screen section of the /etc/X11/xorg.conf file

Didn't work for me, and i got no idea this option do.:confused:

Hope that helps

---

