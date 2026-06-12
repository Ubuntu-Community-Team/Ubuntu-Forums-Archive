---
title: "Problems running Steam under Wine"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by bidget on 2008-04-14
I get the following error when attempting to run HL2. It is an error with Steam and (I'm pretty sure) not with the way I have wine configured or anything.


Your video drivers appear to be out of date and could cause problems if you choose to continue and run the game. We strongly recommend that you follow the link below and update your video drivers to the latest version available from your driver vendor.

Your driver details

Windows Version: Windows Vista
Description: Direct3D HAL
Version 7.15.10.16921

Go to driver update page... (this is just a link to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us))


If I click on "continue anyway" and ignore the errors I get an extremely low (basically unplayable) framerate, which is a little strange cause in windows I would get around 70-80fps with all fhe graphic options enabled and set at the highest level. Is there a way to get around this issue? I've heard that instead of using wine I could try "running a vm" (not quite sure what that means though) but that it could be quite a performance hit. I can't really see how the performance could suffer any more than it already has though hahaha.

In the terminal window I am also getting this error:

fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x293582d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler

It just repeats over and over, although the 0x number changes every time. System specs are:

Athlon64 X2 5000+ Black Edition
eVGA GeForce 8800GT
2GB OCZ XTC Platinum Rev. 2 PC2-6400
Gigabyte GA-M57SLI-S4 Rev. 2

As far as I know I have the latest drivers (Envy reports version 169.12) I'm running the latest version of Wine as well, and I'm on Ubuntu 7.10. All help is greatly appreciated! :)

---

### Post by kesman on 2008-04-14
Did you search for Steam in wineHQ application database? They have a large wiki page for every program that is tested with Wine, and Steam seems to have very good grades with wine.

---

### Post by bidget on 2008-04-14
Yes and on their appdb page it lists steam as having "platinum" compatibility. I don't see any pages that list errors or fixes though :(

---

### Post by stchman on 2008-04-14
> **bidget said:**
> I get the following error when attempting to run HL2. It is an error with Steam and (I'm pretty sure) not with the way I have wine configured or anything.


Your video drivers appear to be out of date and could cause problems if you choose to continue and run the game. We strongly recommend that you follow the link below and update your video drivers to the latest version available from your driver vendor.

Your driver details

Windows Version: Windows Vista
Description: Direct3D HAL
Version 7.15.10.16921

Go to driver update page... (this is just a link to [http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us))


If I click on "continue anyway" and ignore the errors I get an extremely low (basically unplayable) framerate, which is a little strange cause in windows I would get around 70-80fps with all fhe graphic options enabled and set at the highest level. Is there a way to get around this issue? I've heard that instead of using wine I could try "running a vm" (not quite sure what that means though) but that it could be quite a performance hit. I can't really see how the performance could suffer any more than it already has though hahaha.

In the terminal window I am also getting this error:

fixme:d3d:IWineD3DCubeTextureImpl_PreLoad Cubetexture (0x293582d0) has been reloaded at least 20 times due to WINED3DSAMP_SRGBTEXTURE changes on it's sampler

It just repeats over and over, although the 0x number changes every time. System specs are:

Athlon64 X2 5000+ Black Edition
eVGA GeForce 8800GT
2GB OCZ XTC Platinum Rev. 2 PC2-6400
Gigabyte GA-M57SLI-S4 Rev. 2

As far as I know I have the latest drivers (Envy reports version 169.12) I'm running the latest version of Wine as well, and I'm on Ubuntu 7.10. All help is greatly appreciated! :)

I have tried to run Windows games under WINE and have had VERY LITTLE success.  I find that I use XP for gaming and Ubuntu for everything else.  It is also unfair to judge Linux by the readiness in which it runs software not designed for it.

How many Linux apps does XP run?

---

### Post by Daveth on 2008-04-14
I have just loaded up my HL2 and had the same driver message, but pressed on and altered the options setting to a better resolution. It seems to put the settings on max, and whilst your machine should handle it, it might be worth playing with the settings. Mine was OK, though a little laggy but it was set well above the usual- and looked lovely- and dying repeatedly under such circumstances seemed so much more poignant!
I think you are right, and it is a Steam issue as they continously update it.

---

### Post by bidget on 2008-04-14
I have already set my settings and resolution in the game, but the framerate is still quite unplayable. It will run at around 20fps when stationary, but as soon as I try to turn or move the mouse or something it drops down to like 3-5fps. I can't even imagine what it would be like if there was an explosion or something a little more graphic-intensive.

---

### Post by bidget on 2008-04-16
Anybody? :(

---

### Post by klybear on 2008-04-16
> **stchman said:**
> I have tried to run Windows games under WINE and have had VERY LITTLE success.  I find that I use XP for gaming and Ubuntu for everything else.  It is also unfair to judge Linux by the readiness in which it runs software not designed for it.

The consensus appears to that Wine really doesn't do games very well. I read that most gamers use Crossover Games which seems to work very well. While no more than a specialist adaptation of Wine, it seems to get consistently good reviews.

Wine seems to ru mostn ordinary software very well. It certainly meets all my limited needs, even running Office 2000, except for Access.

---

