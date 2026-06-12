---
title: "Graphic Card problem in feisty....ATI 9200SE"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by SurR3AL on 2007-04-24
i just ran a clean install of feisty....& everything's great.... :) xcept my graphic card :(

in edgy, i ran envy and it just did its stuff and everything was super!

but in feisty, envy downloads the ati driver and then shows me a blue screen and says 'build of fglrx-kernel-src failed'. and after that i chose to continue to install the remaining stuff and when i rebooted X failed to load so i had to replace by xorg.conf (luckily i had backed it up). so now i'm running the default ubuntu drivers. can anyone help me install the ati driver through envy or anything else?? i have an ati 9200SE.

Thanks!

---

### Post by lamalex on 2007-04-24
have you tried using the restricted drivers manager? system > administration > restricted drivers manager. give that a try.

---

### Post by SurR3AL on 2007-04-24
i tried that......it jus says "your hardware does not need any restricted drivers."
At this point i have the default ubuntu drivers itself installed....

---

### Post by compmodder26 on 2007-04-24
IIRC, the latest ATI drivers do not support cards below 9500.  I think the last drivers to support anything below the 9500 were the 8.28 set.  Perhaps Envy is grabbing the latest version instead of 8.28?  I don't know how Envy works as I've never used it.  I've always just used the "radeon" xorg driver.

---

### Post by compmodder26 on 2007-04-24
Just had a look at the ATI driver page for the 8.28 driver and it doesn't say anything about support for xorg 7.2.  The highest it goes is 7.1.  So even if Envy is grabbing the 8.28 driver, it may not work for xorg 7.2, which is in feisty.

---

### Post by SurR3AL on 2007-04-24
envy is installing 8.28.8.....any solution?? do i have to install anything?? i think the problem here is that the fglrx kernel is not being compiled properly

---

### Post by trippinnik on 2007-04-24
why don't you use the open source driver? It's quite good with better support for Beryl and all that stuff.

---

### Post by compmodder26 on 2007-04-24
> **trippinnik said:**
> why don't you use the open source driver? It's quite good with better support for Beryl and all that stuff.

Agreed.  I had a 9200SE running in Edgy with the open source "radeon" driver and it worked fine.  Was even able to use it with AIGLX and Beryl.

---

### Post by SurR3AL on 2007-04-24
open source driver.....i didnt even know there was something like that....could u pl point me to any relevant tutorials??

---

### Post by Waappu on 2007-04-24
> **SurR3AL said:**
> open source driver.....i didnt even know there was something like that....could u pl point me to any relevant tutorials??


Hi

I don't have Feisty but I think this guide works also for Feisty
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

---

### Post by compmodder26 on 2007-04-24
I don't remember the location of the threads I used to make mine work, but off the top of my head, here is what I did.

Do these steps from a terminal: Applications->Accessories->Terminal.

1.  Make a backup of your X server configuration file:
```
cp /etc/X11/xorg.conf /etc/X11/xorg.conf_bak
```

2.  Open the X server configuration file (we'll use gedit):
```
gksudo gedit /etc/X11/xorg.conf
```

3. Scroll down to 'Section "Device" ' and change the line 'Driver   "vesa" ' to 'Driver "radeon" '. (if it doesn't say vesa, it will most likely be "ati", in either case, just change the part in parenthesis to "radeon".

4.  Right below th line for "Driver", add these lines:
```
Option          "AGPMode"       "8"
Option          "AccelMethod"   "EXA"
Option          "ColorTiling"   "on"
```

5.  Save the file: File->Save. Then close gedit.

6.  Restart your X server: Ctrl+Alt+Backspace.

You should be in business.  In the event it doesn't work, you should get an error message and then be brought to a command prompt. 

1.  Make a note of the error you receive.  
2.  Log in via the command prompt.  
3. Type:
```
sudo cp /etc/X11/xorg.conf_bak /etc/X11/xorg.conf
```

4. Then type:
```
startx
```

5.  Get back on the forums and let us know what the error message said.

---

### Post by MWHICKS on 2007-04-24
THIS LINK WILL WORK YOU THROUGH IT STEP BY STEP (IT ALSO ALLOWS ALL THE EYE CANDY IN BERYL)
I ALSO HAD THE 9200 CARD.  IT WORKED PERFECTLY

[http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)

---

### Post by SurR3AL on 2007-04-25
thanks for all your replies, but i got the open source driver with AIGLX and compiz working from waappu's post (#10)....thanks anyway.....but right now my problem is when i play ut2004 it majorly lags....as far as i understand, only fglrx can make it work perfectly.....but it doesnt support my card and/or feisty......is that right?

---

### Post by wyth on 2007-04-25
That may be right.  I wrangled with an ATI 9000 card for about a month, since Feisty Beta, and finally went back to Edgy where fglrx worked flawlessly (but with no desktop eye candy, although I consider a clean screen that's fast and doesn't shred candy enough).  

The open source drivers work, but I think they work better on newer cards.  If your hardware is old enough, you may need to consider a previous distro designed for that vintage.  I'm not sure if/when Feisty -- or any new Linux distro -- will fully support the geezer gear.

---

