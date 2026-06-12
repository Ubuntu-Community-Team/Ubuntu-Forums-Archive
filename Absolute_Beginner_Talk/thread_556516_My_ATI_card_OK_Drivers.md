---
title: "My ATI card OK? Drivers?"
date: 2007-09-21
forum: Absolute Beginner Talk
---

### Post by ROUBOS on 2007-09-21
Hi people,
I have the Restricted Driver Enabled.

When I use the command: fgl_glxgears it shows t he 3D animation and it is moving fast.

the command fglrxinfo gives me:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6334 (8.34.8 )

Now my card is the ATI Radeon X1950pro 512MB. Does this info mean that it all works fine?
I just installed Neverwinter Nights and I cannot activate shiny-water on the video options. I do have everything else on full and it looks great. 
I was just wondering cause there is the issue of having to change to glx or something in order to enable Beryl etc. And cause Beryl and Desktop Effects don't work with the current setup.

Could someone please explain if it's all OK as it is? I don't want to have Beryl or Compiz running by the way. As long as I know that my Video card is running as it should be.

Thanks

---

### Post by Daveth on 2007-09-21
check out Envy:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by mysticmatrix on 2007-09-21
> **ROUBOS said:**
> Hi people,
I have the Restricted Driver Enabled.

When I use the command: fgl_glxgears it shows t he 3D animation and it is moving fast.

the command fglrxinfo gives me:

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: Radeon X1950 Series
OpenGL version string: 2.0.6334 (8.34.8 )

Now my card is the ATI Radeon X1950pro 512MB. Does this info mean that it all works fine?
I just installed Neverwinter Nights and I cannot activate shiny-water on the video options. I do have everything else on full and it looks great. 
I was just wondering cause there is the issue of having to change to glx or something in order to enable Beryl etc. And cause Beryl and Desktop Effects don't work with the current setup.

Could someone please explain if it's all OK as it is? I don't want to have Beryl or Compiz running by the way. As long as I know that my Video card is running as it should be.

Thanks

Congrats, you have got correct drivers installed. Don't mess with them now.
Now about NeverNight Winters: Are you sure your ATI drivers support that feature? ATI drivers are poor in suporting many basic features, so that might just be the case

Coming to Beryl/Compiz. ATI believes end user doesn't needs Desktop Effects. So they have not implemented a trivial OpenGL extension in their drivers. Workaround: Use XGL. [https://help.ubuntu.com/community/CompositeManager/Xgl](https://help.ubuntu.com/community/CompositeManager/Xgl)
Note that you will not be able to play games when inside XGL session, so you'll have to use default desktops when you play game, and use EyeCandy for day to day.
Check out this thread also. [http://ubuntuforums.org/showthread.php?t=497332](http://ubuntuforums.org/showthread.php?t=497332)
See the section under launcher script. That would enable a game running on seperate X server, and you would be then able to squeeze some extra performance.

---

### Post by Nulifier on 2007-09-21
That most likely has to do with shaders which if I remember correctly dont work quite right in the latest ATI driver.

from what I can tell your system runs fine
One final test you might need is:

glxinfo | grep direct

if this returns yes then everything works, if not then you dont have direct rendering

But in the linux drivers there are some that haven't been worked on yet I think they are at x1000 for support and are moving up.

ATI recently released the specs to their graphics drivers so better support should be coming soon

---

### Post by ROUBOS on 2007-09-21
> **Nulifier said:**
> That most likely has to do with shaders which if I remember correctly dont work quite right in the latest ATI driver.

from what I can tell your system runs fine
One final test you might need is:

glxinfo | grep direct

if this returns yes then everything works, if not then you dont have direct rendering

But in the linux drivers there are some that haven't been worked on yet I think they are at x1000 for support and are moving up.

ATI recently released the specs to their graphics drivers so better support should be coming soon

It does return YES. So I guess everything is fine.

Thanks to all for the info. I do like the eye-candy stuff but it's eye-candy and I just want a nice box that works.
This is why I moved to Ubuntu. And now with VirtualBox running winXP for my Adobe apps I don't need anything else. A game line NWN can entertain and I have another box for real gaming.

I believe the future is all LINUX. Companies will have to start taking it into serious consideration because the market is growing fast. Dell is already selling PCs with Ubuntu pre-installed.

I just love my ubuntu and soon we'll be able to play native games. Cannot wait.

Thanks again to all for the responses. :)

---

### Post by Nulifier on 2007-09-21
You can have your cake and eat it too...

All you need is a file in ~/.config/xserver-xgl/

called disable, if xserver sees this when booting up (or just log out and back in) then it will disable xgl and compiz should fall back to metacity (if it doesn't just run the command metacity.

This will disable xgl until you remove that file
you could even get fancy and create a script that toggles it for you.

With xgl diabled you will not have compiz but you can play games with full 3d

If you dont mind logging out and back in (takes like 10s for my laptop) then this should be no problem.

One of the features that are supposed to be implemented for ATI cards very soon is AIGLX which allows you to have 3d accel with compositng

---

