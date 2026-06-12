---
title: "Changing resolution"
date: 2007-07-27
forum: Absolute Beginner Talk
---

### Post by Skorzen on 2007-07-27
Hello everyone,

I installed recently Ubuntu on my desktop and now I'm limited to 1024x768 @ 60 Hz. I wanna change this to 1280x1024 @ 75 Hz as I had on Windows.

How do I do it?

Thanks!

---

### Post by jingo811 on 2007-07-27
I have tried this on my Nvidia and ATI machines just so you know, in case you have some other graphics card.  Here's the commands for terminal. [COLOR="Red"]You better write them down on paper you won\t be having Desktop when you do them!!!![/COLOR]
_Step 1_
[B]
1.)[/B]
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

**2.)**
```
sudo /etc/init.d/gdm stop
```

**3.)**
Ctrl+ Alt+ F1

**4.)**
User login first!

**5.)**
```
sudo dpkg-reconfigure -phigh xserver-xorg
```

**6.)**
```
sudo /etc/init.d/gdm start
```

IF 
Your keyboard gets all weird and shuffled, then do this to fix it back.
System > Preferences> Keyboard> _Layouts_
ELSE
I'll give you instructions for _Step 2_ and _3_ to further heal your PC.  Just say when!

---

### Post by wolfen69 on 2007-07-27
no need for all that. this alone will do:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Ek0nomik on 2007-07-27
> **wolfen69 said:**
> no need for all that. this alone will do:
```
sudo dpkg-reconfigure xserver-xorg
```

Backing up your xorg.conf file is worth while.

Running dpkg-reconfigure-server-xorg has you change a lot of different settings, not just your resolution and refresh rate.  Thus, running the comman dpkg-reconfigure -phigh will cut down on a lot of options in which the user can make a mistake.  ;)

---

### Post by kyphi on 2007-07-27
At the top left of your screen, where it says 'Applications Places System', click on Applications and then select Accessories from the drop-down menu and then click on Terminal.

On the Terminal screen type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
use your up/down keys on your keyboard to scroll to the resolution that you want: 1280x1024 and press the spacebar then press Enter and then exit the screen.

Then reboot.

What these commands mean is something you will learn another day.

---

### Post by Depressed Man on 2007-07-27
Will this erase any addition things in xorg? I have mine setup for Compiz Fusion (such as adding things in modules). Or will it only reconfigure my resolution?

---

### Post by kyphi on 2007-07-28
> will it only reconfigure my resolution?

As far as I am aware, yes.  If you are not sure create a back up file first.

---

### Post by Skorzen on 2007-08-18
> **kyphi said:**
> At the top left of your screen, where it says 'Applications Places System', click on Applications and then select Accessories from the drop-down menu and then click on Terminal.

On the Terminal screen type
```
sudo dpkg-reconfigure -phigh xserver-xorg
```
use your up/down keys on your keyboard to scroll to the resolution that you want: 1280x1024 and press the spacebar then press Enter and then exit the screen.

Then reboot.

What these commands mean is something you will learn another day.

Thanks a lot, mate. I did that and it worked. Now, how do I change my refresh rate? The only option that appears in the menu is 60 Hz. I want 75 Hz.

Best regards.

---

### Post by overdrank on 2007-08-18
> **Skorzen said:**
> Thanks a lot, mate. I did that and it worked. Now, how do I change my refresh rate? The only option that appears in the menu is 60 Hz. I want 75 Hz.

Best regards.

Hi maybe this thread will help
[http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=resolution)

---

### Post by jingo811 on 2007-08-18
That's really a big and nice guide, however I see some bits and pieces that caused much confusion  and headaches for me when I was trying to fix my resolutions.
Here's my notes of how I fixed my refresh rates.  The really crude and BASIC way, if it's not enough then you should study that big and complete guide.  


Hope my notes won't break your monitor  :) because my experience with XORG.conf and monitors is limitied.
[http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6](http://virtualseafarer.com/renaissance/allsparks/chapter6.html#ch6)

---

### Post by UbuntuniX on 2007-08-18
```
sudo gedit /etc/X11/xorg.conf
```

Find and edit the sections with resolutions. They are noticable.

Example:
```
"1024x768" "800x600"
```

Becomes:
```
"1280x1024" "1024x768" "800x600"
```

Best to insert that in every resolution field. I'm not certain on refresh rates, though.

Once you've saved that, press Ctrl+Alt+Backspace.

---

### Post by jingo811 on 2007-08-18
> sudo gedit /etc/X11/xorg.conf

**OFFTOPIC:**
It's really a non issue in these circumstances but what's right should be right.
When running **textual** executions/programs like NANO or just processes in terminal use = **sudo**.
When opening up **graphical** programs like gedit use = **gksudo**.
In this case use this instead of the above! 

> **gk**sudo gedit /etc/X11/xorg.conf

Once again it's a non issue but since the GREAT aysiu advocated this once.  I just follow like a zombie, I can't find the link to his explanation though I lost it somewhere...

---

### Post by overdrank on 2007-08-18
> **jingo811 said:**
> **OFFTOPIC:**
It's really a non issue in these circumstances but what's right should be right.
When running **textual** executions/programs like NANO or just processes in terminal use = **sudo**.
When opening up **graphical** programs like gedit use = **gksudo**.
In this case use this instead of the above! 



Once again it's a non issue but since the GREAT aysiu advocated this once.  I just follow like a zombie, I can't find the link to his explanation though I lost it somewhere...

I agree
[http://www.psychocats.net/ubuntu/graphicalsudo](http://www.psychocats.net/ubuntu/graphicalsudo)
:)

---

### Post by alienexplorers on 2007-08-19
Try inserting this into your monitor section of xorg.conf:
> Section "Monitor"
    Identifier     "Monitor0"
    HorizSync       28.0 - 70.0     (Insert your Horiz refresh here)
    VertRefresh     43.0 - 120.0    (Insert your Vert refresh here)
    # 1280x1024 @ 75.00 Hz (GTF) hsync: 80.17 kHz; pclk: 138.54 MHz
    Modeline "1280x1024_75.00"  138.54  1280 1368 1504 1728  1024 1025 1028 1069  -HSync +Vsync
    Option         "DPMS"
EndSection


---

### Post by Skorzen on 2007-08-22
> **alienexplorers said:**
> Try inserting this into your monitor section of xorg.conf:

I did that and worked, thanks!

I saw my monitor specs here:
[http://www.tutienda.net/elemento_detalle.php?pk_cd_elemento=3419](http://www.tutienda.net/elemento_detalle.php?pk_cd_elemento=3419)

---

