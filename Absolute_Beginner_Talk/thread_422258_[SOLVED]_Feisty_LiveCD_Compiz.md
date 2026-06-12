---
title: "[SOLVED] Feisty LiveCD Compiz"
date: 2007-04-25
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-04-25
I heard that Feisty came bundled with Compiz. Can I check out Compiz from the LiveCD just to see what it can do?
 
if so, how can I switch it on ?

---

### Post by johnc4510 on 2007-04-25
This is a good question. I'm not really sure, but if you have the live cd, pop it in a see. To access Compiz do this. Go to the drop down menus and choose:

System>Preferences>Desktop Effects

This will start Compiz

Note: If you don't have a video card such as nvidia or ati, it probably won't work because 

composite rendering needs graphic acceleration.

Hope this helps

---

### Post by Inxsible on 2007-04-25
I have NVidia GeForce 7600 installed.
 
I could not get Compiz to start, because altho, I installed the restricted proprietary drivers for Nvidia, i still havent restarted my machine because since I am using LiveCD, a restart wont do any good. will it ?

---

### Post by johnc4510 on 2007-04-25
No the settings are not retained when using the live cd. Your best bet to see what it can do is possibly to go to youtube or google video and search for compiz.

---

### Post by Inxsible on 2007-04-25
Alrite, Thanks.
 
I am pretty much ready to install now. So it won't be long before I get to the good stuff !!
 
Thanks for your replies guys !

---

### Post by kvonb on 2007-04-25
Yes you can,  if you click on menu->system->administration->restricted drivers manager, and select "enabled" which will download and install the video driver.

When finished it will ask you to reboot, **don't do that**, instead switch to the virtual terminal with <ctrl><alt><f1> and type this:

```
sudo /etc/init.d/gdm restart
```Then switch back to the desktop with <ctrl><alt><f7>, log out then restart X by pressing <ctrl><alt><backspace>.

It should automatically log back in again.

Now make sure you have the video driver installed by opening a terminal and typing:

```
glxinfo | grep direct
```If the answer is "Yes", all is good, continue.

Select menu->system->preferences->gl desktop, and click on "enable GL desktop".

The window borders will vanish, then re-appear shortly.

If they don't come back, it doesn't work and there's not much I can suggest at that point!

You could install "Beryl" from Synaptic and give that a go, but chances are that either the driver does not support your card, or it didn't initialise properly, try logging pressing <ctrl><alt><backspace> again and see if it makes a difference.

---

### Post by Inxsible on 2007-04-25
> **kvonb said:**
> Yes you can, if you click on menu->system->administration->restricted drivers manager, and select "enabled" which will download and install the video driver.
 
When finished it will ask you to reboot, **don't do that**, instead switch to the virtual terminal with <ctrl><alt><f1> and type this:
 
```
sudo /etc/init.d/gdm restart
```Then switch back to the desktop with <ctrl><alt><f7>, log out then restart X by pressing <ctrl><alt><backspace>.
 
It should automatically log back in again.
 
Now make sure you have the video driver installed by opening a terminal and typing:
 
```
glxinfo | grep direct
```If the answer is "Yes", all is good, continue.
 
Select menu->system->preferences->gl desktop, and click on "enable GL desktop".
 
The window borders will vanish, then re-appear shortly.
 
If they don't come back, it doesn't work and there's not much I can suggest at that point!
 
You could install "Beryl" from Synaptic and give that a go, but chances are that either the driver does not support your card, or it didn't initialise properly, try logging pressing <ctrl><alt><backspace> again and see if it makes a difference.
 
Oops !!!   It Works !!!  :) 
 
Will check out Compiz and see what it can do. 
 
Thanks kvonb !!

---

### Post by Inxsible on 2007-04-25
Checked out the Windows wobble and even the desktops on the cube. Sweet !!

What are the features that Beryl gives over Compiz ?

Man, I cant wait for the installation to finish and make Ubuntu my primary OS!!

Compared to what I just saw, Vista doesn't even come close !

Honestly, I liked a little bit of eye candy that Vista gave over XP namely, Aero 
But Compiz makes Aero eat its dust !

Hail Open Source !!

---

### Post by kvonb on 2007-04-25
You're most welcome, glad it worked out for you :).

It will of course all vanish once you reboot though :(.

Beryl is like Compiz on acid, it had tons more features, much better control over just about everything, and in my experience it is actually more stable than Compiz, although you will now see thousands of people flame me for those observations :).

The simplest and best thing that Beryl has over Compiz, is the ability (by default) to spin the cube using your middle mouse button, ie press the wheel and move the mouse.

Plus when you move the mouse to the top right of the screen, it pops up a window selection "menu", if you have more than one application open you will see the beauty of it.

Regards, Kev :)

---

