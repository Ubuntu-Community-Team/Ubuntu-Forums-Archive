---
title: "view doesn't fit screen"
date: 2006-10-24
forum: Absolute Beginner Talk
---

### Post by Jonas_Henricsson on 2006-10-24
I have a problem with my screen. The screen is not filled by the view. I would like to extend the view to the left. I've understood that xorg.conf is the file I'm supposed to change somehow, but what should I change? 

Thanks for any help!

/Jonas

---

### Post by taurus on 2006-10-24
You are not using the right resolution for your monitor!  I guess that is your question, right?  You can reconfigure your X again with (from a terminal, Applications -> Accessories -> Terminal)

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by Jonas_Henricsson on 2006-10-24
But I can change the resolution in System settings. I tried that. But then the size of everything on the screen changes. I want to just extend the view to the left. When I change the resolution, I still have a gap of varying size on the left side of the screen. 

Is it not possible to just extend the view to the left without changing the resolution and thereby the size of everything?

Thank you for your reply!

/Jonas

---

### Post by taurus on 2006-10-24
Are you using a regular monitor (not the widescreen one) and did you install a driver for your graphic card?

---

### Post by Jonas_Henricsson on 2006-10-25
I have a regular monitor. In Synaptic I can see that this has been downloaded NVIDIA binary XFree86 4.x/X.Org driver. I guess that means I got a driver. However in the info about the driver there is the following sentence:

"To enable the driver, run "sudo nvidia-glx-config enable"."

When I tried this, I got an error message:

"Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia."

/Jonas

---

### Post by BlocknBleed on 2006-10-25
You might be thinking too high tech. My screen doesn't fit perfectly either compared to windows. I just adjusted the monitor with the menu buttons on it. That should stretch the screen if its just out a hair otherwise it would probably distort the image.

---

### Post by Jonas_Henricsson on 2006-10-25
If only things were so easy, BlocknBlead :)

The thing is my monitor doesn't have any menu button or adjustment buttons. All I can change is sound, brightness and colour. 

I hope this isn't too hard to believe. My monitor is kind of old, I guess..

But it must be possible to adjust this somehow anyway, right? 

/Jonas

---

### Post by taurus on 2006-10-25
What does your /etc/X11/xorg.conf look like anyway?

```
more /etc/X11/xorg.conf
```

---

### Post by CatKiller on 2006-10-25
That does seem to happen quite frequently. You can do as it says and edit xorg.conf: ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo nano /etc/X11/xorg.conf
```Use the Page Down button to scroll down to the Device section, and change the Driver line to "nvidia".

---

### Post by Jonas_Henricsson on 2006-10-25
Hmm, the thing is I had some problems with my graphics card before I switched to Ubuntu. The computer would restart before I got into Windows. If I used safe mode and uninstalled the Nvidia driver, it would work. After a while, however, I got problems again.

I'm not sure if I dare mess with my graphics card or it's drivers too much...

Anyway, I guess I know what I could do. Thanks for the help!

/Jonas

---

