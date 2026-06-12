---
title: "ati graphics problem followed post above to the letter"
date: 2007-09-26
forum: Absolute Beginner Talk
---

### Post by johnnyk1978 on 2007-09-26
i have an ati x1300 pro followed the cli it went fine then went to enable graphics card it told me to reboot i did right after the ubuntu loading screen it went black and nothing, twice this happened and cant get back to desktop have to boot from live cd until i fix it or reinstall ubuntu

---

### Post by overdrank on 2007-09-26
> **johnnyk1978 said:**
> i have an ati x1300 pro followed the cli it went fine then went to enable graphics card it told me to reboot i did right after the ubuntu loading screen it went black and nothing, twice this happened and cant get back to desktop have to boot from live cd until i fix it or reinstall ubuntu

Hi you don't have to reinstall ubuntu, just reconfigure your xorg.

---

### Post by johnnyk1978 on 2007-09-26
how do i configure from on hard drive from live cd

---

### Post by overdrank on 2007-09-26
> **johnnyk1978 said:**
> how do i configure from on hard drive from live cd

When you boot to ubuntu and you get the xorg error ( if you don't get the error then use the ctrl, alt, F1 keys to enter the command prompt) just click ok and it will bring you to the command prompt and login. Then use the command ```
sudo dpkg-reconfigure xserver-xorg
```
Choose vesa as the driver and then answer the questions and if you don't know the answer then leave as default given.

---

### Post by dmacdonald111 on 2007-09-26
When you boot into linux using your hard drive, are you presented with the 'text' login? Or no login at all?

If you are taken to the text login, you can log in using that and then make a copy of your xorg.conf file (so you can go back and see any errors, if you wish;

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

and then reconfigure your xorg by using;

```
sudo dpkg-reconfigure xserver-xorg
```

If all goes well, you can either reboot or try and start X;

```
sudo /etc/init.d/gdm start (kdm if you use KDE
```

If you get in trouble or you have a different problem/something else, post back :)

---

### Post by johnnyk1978 on 2007-09-26
ok i reconfigured everything and am back in motion but ati is off in the resticted driver manager i am afraid to try and turn it on, also a side question about plugins and flash players is there any for web browser, when i see "need plugin to see whole page no plug in will download unsuported file"

---

### Post by overdrank on 2007-09-26
> **johnnyk1978 said:**
> ok i reconfigured everything and am back in motion but ati is off in the resticted driver manager i am afraid to try and turn it on, also a side question about plugins and flash players is there any for web browser, when i see "need plugin to see whole page no plug in will download unsuported file"

Hi for flash
[https://help.ubuntu.com/community/RestrictedFormats/Flash](https://help.ubuntu.com/community/RestrictedFormats/Flash)
And for codecs and video
[https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs](https://help.ubuntu.com/community/RestrictedFormats/WindowsCodecs)
[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)
Good luck!

---

### Post by dmacdonald111 on 2007-09-26
I am guessing that your system is up to date with regard to upgrades. I would give turning on your restricted driver another go. If something does go wrong with it, then it looks like you have a different problem.

Does the system mention the card correctly if you use;

```
lspci
```

Also, are you using feisty or gutsy?

---

### Post by johnnyk1978 on 2007-09-27
VGA compatible controller: ATI Technologies Inc Unknown device 7183
03:00.1 Display controller: ATI Technologies Inc Unknown device 71a3
this is lspci it is a pcie card it reads on board nvidia just fine maybe i should take out ati and use motherboard i am not sure which ubuntu i have downloaded from here 7.04 but did not say feisty or gutsy.

also i want to try and install some games starcraft  dioblo2 sacred, and neverwinter nights i heard that wine might let me do that but could not find it

---

### Post by dmacdonald111 on 2007-09-27
Check in System, Administration and click on 'restricted drivers'. Does this allow you to turn it on? If not then I would say something is amiss.

With regard to your games. Yes, wine would seem the appropriate program. I think there is a seperate 'wine' forum which may be more helpful for finding out which games do and do not run.

And 7.04 would be Feisty :)

---

### Post by johnnyk1978 on 2007-09-27
ok i tried to turn on restricted drivers graphics card it did let me and told me i had to reboot i did and still after ubuntu loading screen it went blank i did reconfig and that went fine but still blank on reboot, and most games ubuntu packs stick or freeze momentaraly,i will pull ati out and use nvidia and post back. any more ideas are much appreciated and thank you guys for all the help thus far

---

### Post by overdrank on 2007-09-27
> **johnnyk1978 said:**
> ok i tried to turn on restricted drivers graphics card it did let me and told me i had to reboot i did and still after ubuntu loading screen it went blank i did reconfig and that went fine but still blank on reboot, and most games ubuntu packs stick or freeze momentaraly,i will pull ati out and use nvidia and post back. any more ideas are much appreciated and thank you guys for all the help thus far

Hi sorry to hear you are still having trouble but have you tried a xgl session with that card. I just put together a system with a intergrated nvidia 6100 and it runs great what is the intergrated system on yours?

---

### Post by johnnyk1978 on 2007-09-27
nVidia Corporation C51 [GeForce 6150 LE]

---

### Post by overdrank on 2007-09-27
> **johnnyk1978 said:**
> nVidia Corporation C51 [GeForce 6150 LE]

I have heard that it give some user a pain but there are other occasion that has worked great for user. Good luck and hope it works great and you know you will have to reconfigure your xorg again! :(

---

### Post by SpiritIsReality on 2007-09-27
howdy
x1300 is mentioned on this page
[https://help.ubuntu.com/community/RadeonDriver?highlight=%28x1300%29](https://help.ubuntu.com/community/RadeonDriver?highlight=%28x1300%29)
?
[https://help.ubuntu.com/community/RestrictedDrivers/ATI](https://help.ubuntu.com/community/RestrictedDrivers/ATI)
[https://help.ubuntu.com/community/RadeonDriver?highlight=%28radeon%29](https://help.ubuntu.com/community/RadeonDriver?highlight=%28radeon%29)

Am I wrong, or is my guess that you have to choose vesa or ati during your
sudo dpkg-reconfigure xserver-xorg
worth testing out?

no sooner said than proved wrong? is your rig an x86 or x86_64...
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
[http://www.amd.com/us-en/](http://www.amd.com/us-en/)
so is there a x1300 not radeon and a x1300 radeon?

what post did you follow?


trails

---

### Post by voided3 on 2007-09-27
I have an x1300 pro and they are, as your links stated, unsupported in the open source driver. If you reconfigure xorg, use vesa or try to get fglrx to work again. I tried out the new 8.41.7 driver on mine and it didn't work (kind of expected it, but had heard/hoped otherwise), so I guess i'm stuck with vesa since when I enable the restricted driver again it uses the Mesa3D even though fglrx is specified in xorg.conf.... no games for a while (seriously, i've tried everything i can find on the ATI wiki and here and have tried using Envy but no luck, but thats the risk you take with trying out drivers; from looking through my log files, i think it's just a matter of figuring out what the 8.41.7 driver left behind and deleting it, but that seems a bit tricky unless someone knows what to do exactly). 

Depending on how fed up I get, I may look into a 7 series nvdia card, but i use my x1300 on windows too (unfortunately; only good thing about it is the gaming) and I play games like UT2k4 and Flatout on full settings at 1440x900 without any fuss (even runs Quake 4 at respectably high settings at the same res) so I know the card can do what I ask of it. That and I have an older system that performs very well for how little it cost me (Athlon XP 2500+, 1.5GB DDR333, 2x160GB HDDs) so i'm probably better off saving up for a whole new multi-core, PCIe system rather than spending what I paid for this computer on a new vid card. I guess when Gutsy comes out i'll try the promising new 8.42 driver that should be out around the same time, which I would recommend to anyone with a supported vid card.

---

### Post by SpiritIsReality on 2007-09-27
howdy

voided3 ...thanks for the info
I hope someone shows up with the answer to your 8.41.7

trails

---

### Post by johnnyk1978 on 2007-09-27
no sooner said than proved wrong? is your rig an x86 or x86_64...
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
[http://www.amd.com/us-en/](http://www.amd.com/us-en/)
so is there a x1300 not radeon and a x1300 radeon?

what post did you follow?


trails[/QUOTE]

Sticky:  Installing Ubuntu 7.04: ATI X**** Cards
Mike  is the post that i followed i am not sure if there is a x1300 not radeon
my rig is x86_64 
i have the same issues as voided3 works on windows but not on ubuntu.
i have taken out the x1300 and am on nvidiaGeForce 6150 LE and it is worse than the x1300 i went and reconfigured and reboot then get an error that wont load desktop tellsme to reconfigure and i do but when i reboot same message shows up, might have to put x1300 back in with invidia can't get screen res past 800x600 but can with x1300

---

### Post by overdrank on 2007-09-27
> **johnnyk1978 said:**
> no sooner said than proved wrong? is your rig an x86 or x86_64...
[http://ati.amd.com/support/driver.html](http://ati.amd.com/support/driver.html)
[http://www.amd.com/us-en/](http://www.amd.com/us-en/)
so is there a x1300 not radeon and a x1300 radeon?

what post did you follow?


trails

Sticky:  Installing Ubuntu 7.04: ATI X**** Cards
Mike  is the post that i followed i am not sure if there is a x1300 not radeon
my rig is x86_64 
i have the same issues as voided3 works on windows but not on ubuntu.
i have taken out the x1300 and am on nvidiaGeForce 6150 LE and it is worse than the x1300 i went and reconfigured and reboot then get an error that wont load desktop tellsme to reconfigure and i do but when i reboot same message shows up, might have to put x1300 back in with invidia can't get screen res past 800x600 but can with x1300[/QUOTE]

Were you able to install the nvidia driver for the 6150?

---

### Post by SpiritIsReality on 2007-09-27
johnnyk1978 ...thanks... for pointing out the above post.

maybe Mike could put a heads up message in his sticky
is there a better list than this
[https://help.ubuntu.com/community/RestrictedDrivers/ATI](https://help.ubuntu.com/community/RestrictedDrivers/ATI)
or is this list up to date?

---

### Post by voided3 on 2007-09-27
> i have the same issues as voided3 works on windows but not on ubuntu.

Bear in mind the reason why I have no 3D acceleration is because I was trying out a few drivers and now I cannot revert properly. When I did a fresh install, I just check the box for the restricted driver and it worked perfectly using the older driver (except we all know the shortcomings of the older driver so hence why I wanted to try the new one). Also bear in mind that the Windows driver received a little more attention from the devs and came out earlier and that 8.41.7 for Linux was more of a partial compatibility release for those who have the HD2*** series cards. The October release is intended to be a full-line driver, but I had heard word of this working working on some x1*** series cards so I gave it a shot. I have also used the 8.40.4 driver (the latest supported one for these) when I had my x1300 pro in a different computer and it had worked fine with some slightly noticeable improvements over the older one in the Ubuntu repos. So basically i'm just trying to say I was the one who screwed it up and don't blame ATI, though as a consequence I now am having problems restoring full 3D with the older driver since there are now conflicting fglrx modules I need to get rid of somehow.

---

