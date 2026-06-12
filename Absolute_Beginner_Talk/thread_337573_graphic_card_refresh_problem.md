---
title: "graphic card refresh problem"
date: 2007-01-13
forum: Absolute Beginner Talk
---

### Post by imbill3 on 2007-01-13
I have just installed a 'triple boot' system on my computer with 6.06 and 6.10 and XP .. no small task !

I was soooooo proud ! ....  but for some reason I cant get above 60 cycles on the refresh rate with this video (s-3 built into a via board) and since I am (God this hurts! after 20 years in the computer service business!) CLUELESS when it comes to linux .. I was hoping someone could point me in the right direction ..

it seems ununtu doesn't regognize the card or needs the drivers maybe ?? ... all I know is that this flickering is about to give me a stroke !!

Thanks all 

Bill

---

### Post by hal10000 on 2007-01-13
Did you try [COLOR="Red"]sudo dpkg-reconfigure xserver-xorg[/COLOR] ?

If you know the exact specifications of your monitor (horiz./vert. refresh rates), you may choose the "advanced" setup for your monitor specs., otherwise "medium".

---

### Post by imbill3 on 2007-01-13
Thank You so very much !!!!!

Now... could you possibly try that in english for those clueless idiots like me in the cheap seats ?? !!!!

I've tried French, German, and Spanish  and so far I still dont know what your talking about !!

(I thought this was the 'beginners' corner)  

Thanx

Bill

---

### Post by hal10000 on 2007-01-14
Oh, I didn't realize thid is the beginners forum.
So now in English (hope it's good enough)

Open a terminal window (Apps--->Terminal). 
Prior to the following steps, I recommend to backup your existing graphic card's configuration file: Type in [COLOR="Red"]sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bkup[/COLOR] (you will be asked for your password).
This creates a file named xorg.conf.bkup in the directory /etc/X11. If anything went wrong you can restore it with [COLOR="Red"]sudo cp /etc/X11/xorg.conf.bkup /etc/X11/xorg.conf[/COLOR]

Now type in the command from the upper posting (red colored), you can mark it with your mouse an then just right click to your termianl window.

Short explanation:
[COLOR="Red"]sudo [/COLOR]is the command to gain root access (type your user's password). We need root (Administator) access for the things to do.
[COLOR="Red"]dpkg-reconfigure[/COLOR] is the command to reconfigure packages installed in your system
[COLOR="Red"]xserver-xorg [/COLOR]is the name of the package to be reconfigured. (xserver-xorg is the package which manages your graphic card behaviour)

In the appearing dialog you will be asked for settings which are concerned to your graphic settings (mainly mouse, keyboard monitor and graphic card settings). It' a good idea to read the comments.
Some settings can be autoprobed or autodetected, but take care if they are correct. Some settings are autoselected, change them only if you sure you know it better.

For usb and PS/2 mouse select IMPS/2 as mouse protocol and "Emulate 3 button mouse"

In the monitor settings section you may select "Attempt monitor autodetection".
Select the "Video modes to be used by the X server" (with <SPACE> key) or leave it at the preselected settings.

The most relevant part for your attempt i suppose is "Method for selecting the monitor characteristics".
If you have a manual of your monitor you may look into it to get the exact value for horizontal and vertical sync ranges and select [COLOR="Red"]"Advanced"[/COLOR] to type in these values. But be careful if you have an older monitor, because wrong values may harm your monitor's hardware.

If you don't know the exact settings, then select [COLOR="Red"]"Medium"[/COLOR] and choose an entry which is suitable to your monitor.

Let the program "write monitor sync ranges to the configuration file".

I guess these are the main points to take in mind. 
Hope it helps.

---

### Post by imbill3 on 2007-01-15
Thank You Hal1000 !!  It worked like a champ !!  (hal1000 .... 2001 a space odyssey ?? !!)

Anyway, I really do appreciate it !!

---

### Post by hal10000 on 2007-01-15
hal10000 is the latest update of hal9000
How to get it? Just install ubuntu.

---

