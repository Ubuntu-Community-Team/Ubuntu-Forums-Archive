---
title: "Frozen window. Does not respond. Help!!"
date: 2008-01-12
forum: Absolute Beginner Talk
---

### Post by jorgevan007 on 2008-01-12
While using Ubuntu Gutsy, some of my windows (specially the small ones that appear in the middle of the screen) just freeze. The "ghost windows" cannot be minimized, closed or anything else. Once they appear all other windows operate behind these frozen windows and block the content of those other programs. The frozen windows also do not have close buttons. It seems to be a bug in the graphical user interface because other programs respond normally. 
This problem got worse one time i tried to use WINE (the windows appeared more often). I have uninstalled WINE but now and then i still get those "ghost windows". They only go away once i log off. 
Please take a look at the image i have attached to see the problem "in action". 
Any help would be greatly appreciated. 
PS- I am quite new to Ubuntu so please consider this in your contribution to this thread. If you give a suggestion please include good instructions. Thanks a lot!

Jorgevan007

---

### Post by nikoPSK on 2008-01-12
Happens in wine sometimes, just force quit the app. Also happens with firefox frequently. 

Regards,
nikoPSK

---

### Post by Linuxratty on 2008-01-12
You can force a reboot with ctrl alt backspace.

---

### Post by Casual Fan on 2008-01-12
> **Linuxratty said:**
> You can force a reboot with ctrl alt backspace.

That's not a reboot. That just restarts X, the program that draws the windows (for lack of a better explanation).

Until you figure out why the windows are appearing, add the Force Quit applet to your panel (right click on the panel, the bar at the top of the screen--click on add to panel--click on Force Quit--click on Add--click on Close). When the ghost windows appear, click on the Force Quit icon and then on the window you want to kill.

---

### Post by nikoPSK on 2008-01-12
> **Casual Fan said:**
> That's not a reboot. That just restarts X, the program that draws the windows (for lack of a better explanation).

Until you figure out why the windows are appearing, add the Force Quit applet to your panel (right click on the panel, the bar at the top of the screen--click on add to panel--click on Force Quit--click on Add--click on Close). When the ghost windows appear, click on the Force Quit icon and then on the window you want to kill.

or just click close and a logging app and it will say this app is not responding, do you want to force quit. :)

---

### Post by Casual Fan on 2008-01-13
> **nikoPSK said:**
> or just click close and a logging app and it will say this app is not responding, do you want to force quit. :)

There are no close buttons on his ghost windows. :)

---

### Post by nikoPSK on 2008-01-13
> **Casual Fan said:**
> There are no close buttons on his ghost windows. :)

ah, sorry, did not notice. :KS

---

### Post by jorgevan007 on 2008-01-13
> **Casual Fan said:**
> That's not a reboot. That just restarts X, the program that draws the windows (for lack of a better explanation).

Until you figure out why the windows are appearing, add the Force Quit applet to your panel (right click on the panel, the bar at the top of the screen--click on add to panel--click on Force Quit--click on Add--click on Close). When the ghost windows appear, click on the Force Quit icon and then on the window you want to kill.

Thanks, but the Force Quit did not work. It does not know what window to close. This "ghost  window is practically a piece of the screen that just does not exist other than the fact that those pixels are being used by the window that appeared. In this last case the ghost window came from printing a document. It is the window that displays page 1/2 is printing etc. Other times the frozen window is the window that appears promting me for a password when opening synaptica package manager. It does not seem to have a source program per se. Those windows just freeze! from regular usage of the system. 
Like i said before, i uninstalled WINE (so its not in my system anymore at this point) because that made the problem worse. 
I attached more images of the problem. As the matter of fact, i have been replying to you with that damn window witting there the whole time. It will go away only when i CTRL+ALT+Backspace. Sucks!! Thanks for all the replies. Once i can get around this problem i will be hapy with Ubuntu. 

Jorgevan007

---

### Post by Casual Fan on 2008-01-13
What happens when you click on the show desktop button?

---

### Post by nikoPSK on 2008-01-13
> **Casual Fan said:**
> What happens when you click on the show desktop button?

you can't alt tab it either?

---

### Post by jorgevan007 on 2008-01-14
I found the problem!!
It was an emerald theme i had downloaded and installed from Beryl's website. (a Vista look alike theme)
Once i switched to one of the themes that ship with Ubuntu the windows disappeared. 
It must be some bug with the theme that caused redrawing issues with some screens of the UI. 
Well, i will never use it again. Thanks to everyone for all your help.

Jorgevan007

---

### Post by nikoPSK on 2008-01-14
> **jorgevan007 said:**
> I found the problem!!
It was an emerald theme i had downloaded and installed from Beryl's website. (a Vista look alike theme)
Once i switched to one of the themes that ship with Ubuntu the windows disappeared. 
It must be some bug with the theme that caused redrawing issues with some screens of the UI. 
Well, i will never use it again. Thanks to everyone for all your help.
 
Jorgevan007
 
No problem! :) Could you please mark this thread as "SOLVED"
 
Best,
nikoPSK

---

### Post by jorgevan007 on 2008-01-15
Hold that thought!
I am still getting the ghost window every time I print a Office XP document with Open Office word processor. Does anybody get a ghost "or frozen window" when printing with Open Office word processor

try: printing a document with Office XP format

See previous posted pictures for an example of this problem. To be fair, this is the only time i am getting the ghost window now. It goes away only when i log off. 
Any chance its a bug with the printing module in Ubuntu or Open Office word processor?

Thanks,

Jorgevan007

---

### Post by Sisyphus48 on 2008-04-26
Thanks for the post it was helpful.

---

