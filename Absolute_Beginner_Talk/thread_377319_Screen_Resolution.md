---
title: "Screen Resolution"
date: 2007-03-05
forum: Absolute Beginner Talk
---

### Post by Sandfly on 2007-03-05
Having just achieved something I haven't managed before on any computer I have owned, this being a working Dual Boot, I must say that my very very first impression of Ubuntu is really good. (I've had it running all of 90 minutes). This is my very first foray into Linux of any description and I am here simply because I am becoming less and less happy with Bill and his over-priced, over-sized bits of software 

One thing that is proving a bit difficult is setting the screen resolution to be the same as my Windows Xp boot. That is set to 1280 x 1024, but when I set Ubuntu to the same res it seems to duplicate the left-hand side of the screen on the right, i.e. I have two hda1 icons at the same level on the screen but one on the left hand side and one on the right, I also get two mouse pointers which gets REAL confusing. Is this a known problem? and is there anything I can do about it? 'cause it is a bit dissapointing to have icons etc which look a bit clunky on Ubuntu when I know that XP can display a finer resolution image.

I loved the fact that Ubuntu recognised my wireless card as soon as I plugged it in...unlike XP which I had to play with for an hour before I could make it work.

I would appreciate any help I can get from the resident gray-beards!

Thanks in advance.

The Sandfly

---

### Post by Dr. Nick on 2007-03-06
Check the refresh rate and see if it makes a differnece.

The file that controls resolutions is /etc/X1/xorg.conf

You can open it using [B]gksudo gedit /etc/X11/xorg.conf
[/B] 
Their you can add/remove any resolutions desired.


I've never seen that problem before

---

### Post by Sandfly on 2007-03-06
The Refresh rate is fixed on 60Hz with no other choices, however I will give your other info a whirl tonight when I get home (I'm at work right now).

many thanks for your help

The Sandlfy

---

### Post by alienexplorers on 2007-03-06
You could try the modeline editor and take those results and enter them in your monitor section of xorg.conf...  The gtf mode line program is at:
[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)

---

