---
title: "Signal Out of Range in Counter Strike Source"
date: 2007-12-13
forum: Absolute Beginner Talk
---

### Post by mikethepirate on 2007-12-13
Hey guys, the title says it all.  When I run CS:S, my monitor goes black and displays a messages that says "Input Signal Out Of Range".  I'm pretty sure this means the resolution is too high for my monitor to understand, but I have no idea how to fix it and I haven't had any luck searching.

Thanks in advance :)

---

### Post by mikethepirate on 2007-12-14
Also, when the screen is black and the warning is being show, i can hear my mouse go over the options in Counter Strike.  So, I know that the game is running but my monitor won't recognize it.  Any help would be appreciated :)

---

### Post by mikethepirate on 2007-12-14
Also, I am running the restricted ATI accellerated graphics driver.  Is there another driver I should be using.  I downloaded a driver from the ati site, but it was a .run file and I could not find a way to make it run.

---

### Post by mikethepirate on 2007-12-14
Also, for some reason, ubuntu won't recognize my microphone and when I go to the audio tab under wine, it freezes and I have to force quit?  I think it's a driver problem.  Could someone please point me in the right direction for drivers for ubuntu?  Thank you in advance :)

---

### Post by mikethepirate on 2007-12-14
Guys, I am having no luck searching.  I keep getting outdate information that won't work on 7.10.  Please, if any of you know how to, please help.  I don't want to be annoying, but my games are the only thing keeping me on windows :(

---

### Post by Het Irv on 2007-12-14
> **mikethepirate said:**
> Hey guys, the title says it all.  When I run CS:S, my monitor goes black and displays a messages that says "Input Signal Out Of Range".  I'm pretty sure this means the resolution is too high for my monitor to understand, but I have no idea how to fix it and I haven't had any luck searching.

Thanks in advance :)
Have you tried changing the Hertz of the moniter.  I am not sure how to do that in Ubuntu, but I know that could fix the problem in Windows.  60 Hz is usually the best bet.

Also the ATI Restricted drivers do not support 3D rendering.  Google for "how to Install in Ubuntu" and look for the monkeyblog article (Edit: unfortuneatly .run is not on there, sorry)

Edit:Edit: Right click on the .run file and go to the third tab and change the pirmissions so that it can run as exicuteable.  Then double click the file.

For Audio what sound card do you have (If onboard, what motherboard)?

---

### Post by mikethepirate on 2007-12-14
Ok, so I downloaded the latest driver from ati but everytime i try to run it, it tells me to log in as super-user. "root@michael-desktop:/home/michael#" is what i see when I open terminal and I got there using the sudo su command, so why is it still telling me to log in under super user when I am?

[http://www.mcsquared.org/analog/sales/181~itemdesc.html](http://www.mcsquared.org/analog/sales/181~itemdesc.html)  <-I'm sure this is the board to my computer.  The computer I have is a Dell Dimension E510 with a P4 @ 3.0Ghz if that helps any.

Thanks a bunch for the suggestions het, I had no idea I could make it run like that under the properties :)  Hopefully, we can get to the bottom of this soon :)

---

### Post by mikethepirate on 2007-12-14
Well now I'm on windows again trying to work this problem out.  After I installed the ATI drivers through the terminal (because it would let me bring up the installer for the reason stated above), I disabled the ATI Accelerated Graphics Drivers in my Restricted Drivers Manager and restarted my computer.  Now when I try to login, It just crashes and kicks me right back the the log in screen.  This is turning into a huge headace just for Counter-Strike. :confused:

---

### Post by mikethepirate on 2007-12-14
Guys, any help would be greatly appreciated. I can't even get into ubuntu now and I'm completely lost :(

---

### Post by mikethepirate on 2007-12-15
I tried dpkg-reconfigure xserver-xorg last night and it just made things worse :(  Now the log in screen doesn't even show up and I just get a black screen and my monitor turns off.  I guess I'm going to have to reinstall as I have found no information, after two days of looking, on why my CounterStrike messes up.  I installed it the way all the tutorials tell me too and I get this. :(  This is such a bummer because I really really really want to use this OS.

---

### Post by mikethepirate on 2007-12-16
No guesses?

---

### Post by mikethepirate on 2007-12-16
*Bump

Do you guys think it may have anything to do with the PCI-E bus number I used.  I just used the default value when I was in dpkg-reconfigure xserver-xorg

---

### Post by discoade on 2007-12-16
I have a similar problem m8! every time i try to run a game that launches full screen my monitor goes out of range if it launches in a window it runs fine. the only advice i got was to get a newer monitor! (not from this forum i might add) real useful eh!?

my monitor is about a month old 19" lcd and runs anything i throw at it in xp! it has to be a driver issue! :(  oh and Gharrr! by the way!

---

### Post by mikethepirate on 2007-12-16
Really!  Great advice lol.  I think I might just reinstall ubuntu cause I can't get into it now.  My monitor is fairly new too.

---

