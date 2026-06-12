---
title: "ATI 8.24.8 drivers"
date: 2006-04-15
forum: Absolute Beginner Talk
---

### Post by evergreen on 2006-04-15
Hi I have just done a fresh install of Dapper Drake I **was** running a AMD64 bit version on my AMD3400 with ATI x800 xt video card. But chose to do a 32bit install this time. There are a number of reasons for this but the main one is I plan on installing Compiz 3d desktop & there seems to be lots of cool new plugins coming out for the 32bit version that I would like to try.

So I just installed the new ATI fglrx driver following this post [>here<]("http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide"). It was very straight forward thanks to a well writen tread. In preperation for doing the Compiz install.

After rebooting a checked to see if the diver was running "fglrxinfo" & got 

display: :0.0  screen: 0
OpenGL vendor string: ATI Technologies Inc.
OpenGL renderer string: RADEON X800 XT Generic
OpenGL version string: 2.0.5755 (8.24.8 )

Nice, Now heres my question the performance is not so good. Draging windows around the desktop shows tearing of the edges & general bad perfomance. Has anybody else installed these drivers? Whats your experiences with them? Is there any tweaks I could try to get the 2D performance up? Will they be better when I use them under Compiz in a 3D environment?

Don't get me wrong they are userable but not perfect. Am I expecting to much? I here the ATI drivers are no match for Nvidia. Is this tearing part of the reason why? Any help or ideas welcome.

---

### Post by Ramses de Norre on 2006-04-15
Never mind ;)

---

### Post by xXx 0wn3d xXx on 2006-04-15
I installed the new drivers on Breezy and they work fine. I even submitted a tutorial on how to install them but after over a day it has not been approved. Could you try re-installing the drivers ? And did you use the 32 bit drivers or the 32 bit drivers ?

---

### Post by evergreen on 2006-04-15
[QUOTE=MasterChief1234]I installed the new drivers on Breezy and they work fine. I even submitted a tutorial on how to install them but after over a day it has not been approved. Could you try re-installing the drivers ? And did you use the 32 bit drivers or the 32 bit drivers ?[/QUOTE]

I installed the 32bit not 64bit if thats what you mean MasterChief1234 gonna do   install of compiz later on I will test them running under Compiz see how they do. Also I ran glxgears demo & was getting more than 9000 fps which seems great. But the tearing still happens when moving windows about on the desktop?

---

### Post by Anttu^^ on 2006-04-17
Can anyone tell me what could be wrong here. i have an x1800 card and a fresh install of Ubuntu 5.10, i have to use the vesa drivers normaly, the ati or fglrx drivers wich comes with the installation wont work, i have gotten the 8.24.8 drivers successfully installed via this guide [http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.24.8_drivers_in_Breezy_Badger](http://wiki.cchtml.com/index.php/Ubuntu_Breezy_Installation_Guide#Method_2:_Generating.2FInstalling_Ubuntu_packages_for_the_newer_8.24.8_drivers_in_Breezy_Badger). but after reboot my screen says just out of range :???:  ? does anybody know how i could get this drivers to work properly :(

i have tried about 5 different distributions and no luck yet ](*,)

---

