---
title: "Color Depth?"
date: 2006-11-15
forum: Absolute Beginner Talk
---

### Post by PartisanEntity on 2006-11-15
According to my xorg.conf file the color depth of laptop screen should be 24. But when I look at images with a gradient, such as certain desktop backgrounds, I can see pixelated transitions from one color to the next.

What else do I need to check or configure?

The graphics card is an Nvidia GeForce Go 6200.

---

### Post by DoorGunner on 2006-11-15
just curious....what is your screen resolution set to??

---

### Post by PartisanEntity on 2006-11-15
1280x800 currently

---

### Post by PartisanEntity on 2006-11-16
Just a friendly bump :)

I have been searching the forum but have not found anything helpful yet.

I see artifacts everywhere. For example here on the ubuntu forums website, if I look at the above ubuntu logo, I see the actual color lines instead of a nice gradient.

If I look at high resolution images, I see artifacts, instead of gradients.

---

### Post by PartisanEntity on 2006-11-16
Here is a screenshot of what I see. I made this image of the log in screen on my laptops lcd:

(Instead of a nice gradient, you should see ugly artifacts where on colour stops and another starts)

[IMG]http://i15.tinypic.com/44bq1iq.jpg[/IMG]

---

### Post by LLRNR on 2006-11-16
Ok, this is just a stupid thought I have. Sometimes I've been able to correct certain resolution issues with the "Resolution Switcher" applet. I see you use Gnome, if it's already installed you should find it if I remember well under Applications -> Accessories -> Resolution Switcher. If it's not there, type```
sudo apt-get install resapplet
```Check and see, if it doesn't appear then type ```
killall gnome-panel
```You should find it now in the menu. (Well if it still doesn't appear type "resapplet &")

You'll get a small grey box/button right near your clock/date. Click on it and play around, see if you can solve something.

Still, I'm sorry, I couldn't find anything better... Hope that helps!

---

### Post by PartisanEntity on 2006-11-16
I was able to change the resolution using the method you mentioned, but this did not get rid of the artifacts  unfortunately. I already have the correct resolution, its just the color depth that seems to be too low.

---

### Post by PartisanEntity on 2006-11-18
Just a kind *bump* :)

---

### Post by LLRNR on 2006-11-18
Sorry that didn't work out :( Nothing else I could think of, I didn't hear of such problems... but still there's something else to do; I don't know if it's gonna help at all, but at least you could try and who knows... maybe you'll be lucky.

You'd need to reconfigure your xserver, so first be SURE you do a copy of it (just in case something... fails). So fire up a terminal and type:

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup

```

Next

```
sudo dkpg-reconfigure xserver-xorg
```
You'll be asked some questions... for your sake, _try_ to get them right. After you're done, press Ctrl+Alt+Backspace to restart X.

In case anything goes wrong (even if you can't login via X), login in "text" mode, that is tty1, you know, white text on black background and then, since you DID backup the xorg.conf file, you can type:

```
mv /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

And then Ctrl+Alt+Backspace again.

I'm sorry I can't come up with a brighter solution, but maybe someone else has a better idea.

Whoops, almost forgot: you _did_ install the nVidida drivers, right ?

---

### Post by PartisanEntity on 2006-11-18
I tried installing the nvidia drivers from the nvidia website once and the desktop environment would no longer load. So no at the moment I am using whatever drivers came with Dapper.

Should I try to install the nvidia drivers from the repository first?

---

### Post by LLRNR on 2006-11-18
Well... don't hassle, try it with 
```
sudo apt-get install nvidia-glx nvidia-kernel-common
sudo nvidia-glx-config enable
```
I think it's a lot more faster anyway than searching through Synaptic (take me for instance... I wouldn't even find them through Synaptic or Adept :lol:)

LLRNR

---

### Post by PartisanEntity on 2006-11-18
DUH it was the nvidia drivers.

I actually used Automatix2 to install the drivers, but thanks for mentioning it and thanks for your help. The artifacts are gone :)

---

