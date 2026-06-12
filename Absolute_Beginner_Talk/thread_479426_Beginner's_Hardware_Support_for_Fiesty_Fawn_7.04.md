---
title: "Beginner's Hardware Support for Fiesty Fawn 7.04"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by z708090 on 2007-06-20
I'm an absolute newbe at Linux. This is the first time i've installed something other than windows in my life. So far i've got everything to work just ok on 7.04 install, except few things. When i look at my hardware profile, there are list of hardwares with tiny x, which i'm assuming aren't supported. (Btw, I have Dell Latitude D600 with base configuration). My biggest problem is identifying drivers for those hardwares ( some of them i can't even identify!).
My second problem is the video card (Mobility ATI Radeon 9000). So far it seems to be working fine (though somehow i get cripser image at 1400x1200, then it's native resolution of 1280x1024). 
Last night I was trying to get fglrx installed using [ATI 9000 + Beryl + Edgy FGLRX ]("http://ubuntuforums.org/showthread.php?t=291464"), it failed to reboot in x. luckily i found a way to reconfigure the xorg and was able to get the screen back. My prob is, i can't get Wolfenstein: ET to give me decent FPS (right now it's 6-12fps). I tried killing all rendering in the ET config but still no help. I'm guessing its 3D rendering issue since when I move over undetailed portion of the game i get decent 80fps but not when there's some kind of 3D rendering in the game. How do i know what video driver i have installed and what's the alternate one i can try to have better 3D rendering? I have been researching the forums but no help, can someone point me to the right direction? 

If i can get this game to work decent and all my hardware supported i'm ready to port over from XP for good :) Please help me switch.

---

### Post by Damanther on 2007-06-20
This guys ENVY script works pretty well resolving driver issues/conflicts for ATI and nvidia.

[ENVY]("http://www.albertomilone.com/nvidia_scripts1.html")

I know it pulled me out of  a ditch I had gotten myself into a while back.

---

### Post by z708090 on 2007-06-22
Envy is not helping. I tried installing it automatically and manually but no luck. It says my graphics card is supported only by the legacy driver and then it says the legacy driver does not support my OS! I asked it to install manulally and it still throws out same error. 

I tried installing the ATI 8.28.8 drivers manually by 
$ chmod +x <driver.run> 
$ ./<driver.run>

and after deflating it says ./install-script.sh (or some similar sound file) is not the correct substitution (arg, i hate my short term memory loss!!! i'll get the correct error tonight when i get home). but in short, i have not been able to get my graphics card to give decent FPS in ET. when i try the screensavers, my CPU usage bumps to 95%. and under settings->hardware profile, my video card still has tiny x, indicating no driver?compatibility?

I also tried this tutorial [http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") but when i restart it ends up failing to restart xserver and i end up reconfiguring the xorg by $ dpkg-configuration xserver-xorg . This is getting annoying, can someone please help me!!

---

### Post by z708090 on 2007-06-22
Just found out that 'fglrx' does not support Radeon Mobility cards older than 9500... which sucks..
so when i tried installing 8.28.8 ATI's  proprietary driver, it gave me following error:

$ ./<driver.run>
   :
   "Out put stuff"
   :
$ [COLOR="Red"]./ati-installer.sh: 165: Syntax error: Bad substitution[/COLOR]

:'( Please HELP ME!

---

