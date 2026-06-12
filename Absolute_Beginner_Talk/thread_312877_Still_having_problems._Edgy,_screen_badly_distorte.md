---
title: "Still having problems. Edgy, screen badly distorted"
date: 2006-12-05
forum: Absolute Beginner Talk
---

### Post by Taigrr on 2006-12-05
Well, I waited awhile, burned a fresh copy of Edgy a couple hours ago, and it still doesn't work. 

It installs okay, but when I boot into the system, the screen is HORRIBLY distorted. It really looks as if you took the picture, and twisted it, to ring it out like a shirt. 

sudo nano /etc/X11/xorg.conf shows what I was told to be proper, using Vesa drivers.

sudo dpkg-reconfigure xserver-xorg Was useless as always

And i'm still frustrated over this whole thing, like I was a month ago.

So, does anyone have any hints here? Nothing in the forums about it, other than my old post.

---

### Post by steve.horsley on 2006-12-05
That's not at all normal. What kind of video card is it?

---

### Post by a.v.l on 2006-12-05
> **Taigrr said:**
> Well, I waited awhile, burned a fresh copy of Edgy a couple hours ago, and it still doesn't work. 

It installs okay, but when I boot into the system, the screen is HORRIBLY distorted. It really looks as if you took the picture, and twisted it, to ring it out like a shirt. 

sudo nano /etc/X11/xorg.conf shows what I was told to be proper, using Vesa drivers.

sudo dpkg-reconfigure xserver-xorg Was useless as always

And i'm still frustrated over this whole thing, like I was a month ago.

So, does anyone have any hints here? Nothing in the forums about it, other than my old post.


Being new myself, I cannot speak with any authority but I had the same issue when installing Dapper.  Fitting a better graphics card and adding a little more memory resolved this issue for me.

---

### Post by Taigrr on 2006-12-05
Well, I switched back to Dapper, and it doesn't do that. Only thing i'm seeing now, screen wise, is it's at 1024x768 resolution. Which I think will change when I get ATI drivers up.

---

### Post by andrewisett on 2007-02-28
I had this same problem.  What the problem is:

The ATi driver which is selected for your card - since it is an ATi card, is setting up the correct resolution for your respective monitor and video card - but since it is not the latest drivers it does not send the information correctly to either your video card or monitor.  If you do an OEM install - do not select any custom screen resolutions - and only choose 1024 x 768.  This way, the video should display properly.

To fix it if you have already ran through your installation is quite simple.  Boot into recovery mode, and run:

> sudo nano /etc/X11/xorg.conf

Once the file opens, find the area that references the resolution settings of your monitor and make sure that the largest resolution does not go over the 1024x768 setting, and if it does, delete the entries so that the lines contain only the following:

> "1024x768" "800x600" "648x460"

Save the file, than type in command line:

> startx

Hope this works for everyone.

---

