---
title: "Visual Effects Just installed Ubuntu"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Swampdonky on 2007-12-07
Hello,

I hope one of you guys can help me.  I just installed ubuntu, and upgraded to ver 7.10.  Before that My resolution was messed up, but the update fixed that.  

Everything works great now except I cant turn on visual effect.
I get this error message:

"Desktop Effects could not be enabled"

Now when I first loaded into 7.10 it told me i could install a non recommended driver or whatever for my video card.  I did that, and it still wouldnt let me use visual effects, and it dropped my rez to 1024 x 768 max.

So now I am back to the default drivers which display very nicely, except I cant use visual effects. Cany anyone help a linux noob?

Hardware specs

Laptop

Amd athlon 64 3000+
1 gig ram
Ati mobility X700.

Thanks!

---

### Post by Chilli Bob on 2007-12-07
Have you run the restricted drivers manager?

---

### Post by Swampdonky on 2007-12-07
> **Chilli Bob said:**
> Have you run the restricted drivers manager?

Yes and that is the driver that installed that forced my rez to 1024x768 and wouldnt let me use visual effects.

---

### Post by Chilli Bob on 2007-12-07
OK, have you worked through this how-to?

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

---

### Post by Swampdonky on 2007-12-07
No I havent, but is it a driver issue or is it something im missing for the OS?

Thanks for your help BTW bro.

---

### Post by Swampdonky on 2007-12-07
Also when i click on the medium or high visual effects it tries to load some window then closes it very quickly.. Dont know if that helps at all.

---

### Post by sloggerkhan on 2007-12-07
I also have ant ATI x700.
The reason for desktop effects not being active is your graphics card driver combination.
You basically have 3 choices:
ati driver, which is the open source driver and default driver for ati cards. This will work fine with compiz-fusion (desktop effects) but not games. To work it this way, use radeon or ati as your driver and make your video card un-blacklisted.

fglrx driver, repo version + xgl : this may interfere with games, may not. You will need to install the xgl xserver. (flgrx is the AMD/Ati proprietary driver.)

latest fglrx driver : can be downloaded from ati's website. Supports aiglx, but you will have to de-blacklist the card and change a couple of settings in xorg.conf.

The reason things are this way is that ATI didn't support the features necessary for an accelerated desktop when gutsy came out.
There are tutorials for pretty much all these methods scattered around the forums.

---

### Post by Swampdonky on 2007-12-07
> **sloggerkhan said:**
> I also have ant ATI x700.
The reason for desktop effects not being active is your graphics card driver combination.
You basically have 3 choices:
ati driver, which is the open source driver and default driver for ati cards. This will work fine with compiz-fusion (desktop effects) but not games. To work it this way, use radeon or ati as your driver and make your video card un-blacklisted.

fglrx driver, repo version + xgl : this may interfere with games, may not. You will need to install the xgl xserver. (flgrx is the AMD/Ati proprietary driver.)

latest fglrx driver : can be downloaded from ati's website. Supports aiglx, but you will have to de-blacklist the card and change a couple of settings in xorg.conf.

The reason things are this way is that ATI didn't support the features necessary for an accelerated desktop when gutsy came out.
There are tutorials for pretty much all these methods scattered around the forums.

Haha your talking to a total newb here man.

I downloaded the latest drivers for ATI, but i dont know what to type in the terminal to install it.

Its a .run file.  I navigated to my desktop using cd, but i cant seem to run the file.

If you could maybe tell me what to type in terminal to do install the drivers like you did that would be awesome.. Sorry man i dont know much about linux at all =(.

thanks again!

---

### Post by maharbA on 2007-12-07
> **Swampdonky said:**
> Ati mobility X700.

There's yer problem!
ATI cards are not very well supported in Linux (yet -- they just released the specs and have better proprietary and OS drivers in the works)

In order to enable Desktop Effects you need either a driver with AIGLX support or the driver you have plus an XGL session.

Check the forums here for setting up Copmiz/Desktop Effects with ATI cards and XGL
OR
Try Envy, a program by Alberto Milone ( [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html) ) it can install the latest, greatest proprietary driver. It's very easy to use and it worked like a charm for me.
OR
Search around for a way to install the latest OS ATI driver (make sure it supports AIGLX for your card)

EDIT:
Sloggerkhan is correct, and probably clearer than me :)
Still if you wan the latest fglrx driver, try Envy

---

### Post by erfahren on 2007-12-07
installing the new driver from ATI gets a little involved. I can post a link to a couple HowTos. 

In the meantime, have you installed xserver-xgl? You said you upgraded to Gutsy, did you have it installed before?

---

### Post by erfahren on 2007-12-07
[http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Gutsy_Installation_Guide)
[http://ubuntuforums.org/showthread.php?t=591445](http://ubuntuforums.org/showthread.php?t=591445)

if you had xserver-xgl installed before (from going by a guide for Feisty) you probably need to undo any changes (startup scripts and the like) and reinstall xserver-xgl.

xserver-xgl for Gutsy is configured not to need a seperate startup session. (To disable it you just make an empty file called "disable" in ~/.config/xserver-xgl/  and restart X.

---

### Post by Swampdonky on 2007-12-07
No i havent done any of that.. .Ill look into it, but if you guys could tell me exactly what i neeed to type into the terminal that would probably help the most..

Sorry If i suck, i just dont know my way around ubuntu yet.....

---

### Post by Swampdonky on 2007-12-07
Okay now I installed the latest ATI driver and my screen is locked at 800x600... and I still cant use visual effects...I have no idea what to do now and I cant revert back to the default driver.....

Everytime  I chang ethe driver in monitor config it wont keep the changes...

---

### Post by erfahren on 2007-12-08
> **Swampdonky said:**
> No i havent done any of that.. .Ill look into it, but if you guys could tell me exactly what i neeed to type into the terminal that would probably help the most..
Actually, not having xserver-xgl installed was probably the problem to begin with. Gutsy usually prompts to install it when enabling the desktop effects with the ATI proprietary driver (fglrx), but I guess it didn't for you.

As I mentioned, installing and configuring the newest ATI driver gets involved. I've never had much luck with it. I was going to recommend you just going with the fglrx driver in the Restricted Drivers Manager and install xserver-xgl . Someone mentioned the new driver, I kind of wished they hadn't.

I got involved with something else before I got a chance to find out if you had XGL installed or not.

Anyway, I can tell you how to revert back, if you are unable to get it configured. 

All you really need to do to revert is undo *any* changes you made to files for it (blacklisted it in [COLOR="Sienna"]/etc/default/linux-restricted-modules-common[/COLOR] and the like)

Then change the driver back to "ati" in xorg.conf (that's so you can temporaily use Ubuntu's open-source driver). you might want to reboot at this point (or restart X with Ctrl+Alt+Backspace).

Go into Synaptic and completely remove the .debs you installed. Click the button on the lower left In Synaptic that says "Status" then in the list in the left pane click on "Installed (local and obsolete)". The debs will be listed in there, completely remove them.

Then while in Synaptic search for "fglrx". Reinstall "linux-restricted-modules" and "xorg-driver-fglrx". You should be able to re-enable them in the Restricted Drivers Manager again. (Reinstalling those takes care of undoing the compiling stuff done when installing the new version.)

after rebooting run the "fglrxinfo" in the terminal to make sure it's being used (and says ATI instead of Mesa).

Then to get desktop effects install xserver-xgl and restart X. You should be able to enable them then.

(the older driver included with Ubuntu needs XGL to run desktop effects, but the new one doesn't. The older one is more stable though.)

---

### Post by Swampdonky on 2007-12-08
> **erfahren said:**
> Actually, not having xserver-xgl installed was probably the problem to begin with. Gutsy usually prompts to install it when enabling the desktop effects with the ATI proprietary driver (fglrx), but I guess it didn't for you.

As I mentioned, installing and configuring the newest ATI driver gets involved. I've never had much luck with it. I was going to recommend you just going with the fglrx driver in the Restricted Drivers Manager and install xserver-xgl . Someone mentioned the new driver, I kind of wished they hadn't.

I got involved with something else before I got a chance to find out if you had XGL installed or not.

Anyway, I can tell you how to revert back, if you are unable to get it configured. 

All you really need to do to revert is undo *any* changes you made to files for it (blacklisted it in [COLOR="Sienna"]/etc/default/linux-restricted-modules-common[/COLOR] and the like)

Then change the driver back to "ati" in xorg.conf (that's so you can temporaily use Ubuntu's open-source driver). you might want to reboot at this point (or restart X with Ctrl+Alt+Backspace).

Go into Synaptic and completely remove the .debs you installed. Click the button on the lower left In Synaptic that says "Status" then in the list in the left pane click on "Installed (local and obsolete)". The debs will be listed in there, completely remove them.

Then while in Synaptic search for "fglrx". Reinstall "linux-restricted-modules" and "xorg-driver-fglrx". You should be able to re-enable them in the Restricted Drivers Manager again. (Reinstalling those takes care of undoing the compiling stuff done when installing the new version.)

after rebooting run the "fglrxinfo" in the terminal to make sure it's being used (and says ATI instead of Mesa).

Then to get desktop effects install xserver-xgl and restart X. You should be able to enable them then.

(the older driver included with Ubuntu needs XGL to run desktop effects, but the new one doesn't. The older one is more stable though.)

Okay I really dont know how to uninstall all that garbage, but if I reinstall I should be back to square one right?

How do I get to synaptic????

I really appreciate you taking the time to help me man, I really want to get these desktop effects on here, because honestly thats the only reason I installed Linux =).

---

### Post by antisocialist on 2007-12-08
> **Swampdonky said:**
> Okay I really dont know how to uninstall all that garbage, but if I reinstall I should be back to square one right?

How do I get to synaptic????

I really appreciate you taking the time to help me man, I really want to get these desktop effects on here, because honestly thats the only reason I installed Linux =).

well, at least you are honest.

to go to synaptics you go to top left corner of your screen, click system, then in the drop down click admininstration, then go towards the bottom of the new menu and click synaptics package manager.   then it will prompt for your password, enter it and do what the other person said from there, and to answer your question, a reinstall would get you back on square one. i dont have an ATI card so i cant help you much there, but if you need other stuff feel free to pm me, it will email it to me and ill get a bunch of popups on my screen telling me about it so you will get a fast response.

---

### Post by erfahren on 2007-12-08
> ... I really want to get these desktop effects on here, because honestly thats the only reason I installed Linux =).
:roll:

I apologize, but I'm not going to walk you through the steps to uninstall the new driver any more than I already did.

reinstall Ubuntu.

enable the driver in the Restricted Driver Manager

install xserver-xgl package

restart X

enable desktop effects

---

