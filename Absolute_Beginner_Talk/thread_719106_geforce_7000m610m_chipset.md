---
title: "geforce 7000m/610m chipset?"
date: 2008-03-08
forum: Absolute Beginner Talk
---

### Post by nocturnalsixer on 2008-03-08
Im running dual boot,  ubuntu gutsy 7.10 x64 and windows xp professional x86

My laptop is acer aspire 5520 5912  
turiton tl-58 1.9 ghz dual core 64 bit
160 gig hdd
2gb ram ddr2
geforce 7000m/610m
aheros 5007eg b/g wireless card

i guessed with tabbing in the dark to get ubuntu installed after going into safe graphics mode to install it.  i booted it with all_generic_ide after the splash in boot info.  it boot up perfectly every time.

i tried to do "sudo install nvidia-linux-x86_64-169.12-pkg2.tar" in the terminal and it said destation invalid or something it just plainly wont install i tried doing ndiswrapper too.

  im an complete noobie at loonix.  i never used loonix execpt for mandrake back in 99 or so and i didnt even get around to customizing mandrake.  can someone please please tell me what im supposed to do.  

im pretty good with xp and around computers i can understand what to do as long as i know what im doing then its all smooth sailing from there.  

thanks a lot for your time and help/ear

---

### Post by overdrank on 2008-03-08
> **nocturnalsixer said:**
> Im running dual boot,  ubuntu gutsy 7.10 x64 and windows xp professional x86

My laptop is acer aspire 5520 5912  
turiton tl-58 1.9 ghz dual core 64 bit
160 gig hdd
2gb ram ddr2
geforce 7000m/610m
aheros 5007eg b/g wireless card

i guessed with tabbing in the dark to get ubuntu installed after going into safe graphics mode to install it.  i booted it with all_generic_ide after the splash in boot info.  it boot up perfectly every time.

i tried to do "sudo install nvidia-linux-x86_64-169.12-pkg2.tar" in the terminal and it said destation invalid or something it just plainly wont install i tried doing ndiswrapper too.

  im an complete noobie at loonix.  i never used loonix execpt for mandrake back in 99 or so and i didnt even get around to customizing mandrake.  can someone please please tell me what im supposed to do.  

im pretty good with xp and around computers i can understand what to do as long as i know what im doing then its all smooth sailing from there.  

thanks a lot for your time and help/ear

HI and welcome, have you tried the restricted drivers located under system, administration or you may look at Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by nocturnalsixer on 2008-03-09
um i got the video card installed under restriction driver devices, but i still cant install the drivers that i downloaded and i cant even install envy it need debhelper, i downloaded the debhelper files alreeady and all those are doing nothing.  its pretty frustrating.  i cant install ndiswrapper or envy or anything  none of the sudo commands seem to work when i want to install  for example i have the geforce 7000m driver its labelled  nvidia-linux-x86_64-169.12-pkg2.run   

i type in  sudo install nvidia-linux-x86_64-169.12-pkg2.run 

or

sh nvidia-linux-x86_64-169.12-pkg2.run 


i keep getting "Install:missing destination file operand after nvidia-linux-x86_64-169.12-pkg2.run "

when i tried to install envy it said " error: dependency is not satisfiable: debhelper"

---

### Post by overdrank on 2008-03-09
> **nocturnalsixer said:**
> um i got the video card installed under restriction driver devices, but i still cant install the drivers that i downloaded and i cant even install envy it need debhelper, i downloaded the debhelper files alreeady and all those are doing nothing.  its pretty frustrating.  i cant install ndiswrapper or envy or anything  none of the sudo commands seem to work when i want to install  for example i have the geforce 7000m driver its labelled  nvidia-linux-x86_64-169.12-pkg2.run   

i type in  sudo install nvidia-linux-x86_64-169.12-pkg2.run 

or

sh nvidia-linux-x86_64-169.12-pkg2.run 


i keep getting "Install:missing destination file operand after nvidia-linux-x86_64-169.12-pkg2.run "

when i tried to install envy it said " error: dependency is not satisfiable: debhelper"

HI and you will have to enable your repositories for Envy, This link will help with the repositories
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

