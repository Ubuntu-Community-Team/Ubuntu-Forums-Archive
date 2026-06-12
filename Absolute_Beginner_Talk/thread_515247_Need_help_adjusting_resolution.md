---
title: "Need help adjusting resolution"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by jpat on 2007-08-01
Within the last few days i switched to ubuntu (v. 7.04) on one of my machines.  While i was running windows i also had an extended desktop going on another monitor.  i tried to get this monitor to work and instead it corrupted the xserver somehow and i was not able to log back into linux using a graphical interface.  and since i am so new to linux i didn't know any of the command prompts so i reinstalled the os using the live cd.  however when i booted the OS again it ran fine but my resolution is now stuck on two settings of very low resolution.  i can't get it past 800X600.  i think that i may have installed a driver that is incompatible with my graphics card (ati radeon x1400) or something.  the OS tells me i am running a driver that is incompatible with linux is someway but i can't figure out how to a) figure what driver that is and b) find the right driver to fix that problem.  i am at a complete loss for how to fix this and increase the screen resolution. everything else works fine, but my laptop screen can run at a much higher res.

---

### Post by Rocket2DMn on 2007-08-01
If you installed the restricted driver, you can follow the first page of this Beryl installation guide, it will help you get rid of the restricted driver and install the open source one.  You do not need to continue with installing Beryl, of course. [http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon](http://www.howtoforge.com/ubuntu_feisty_beryl_ati_radeon)
AND since I seem to be the designated Xserver guy around here today, once you have that setup, you need to reconfigure the Xserver
```
sudo dpkg-reconfigure xserver-xorg
```
Use TAB to move around and SPACEBAR to select/enable when necessary.  When you get to the resolution page, enable your monitor's highest resolution and everything less.  Then you can restart the Xserver with CTRL+ALT+BACKSPACE.  You will lose any unsaved data.  Then go to System->Preferences->Screen Resolution and your normal res should be available.

---

### Post by jpat on 2007-08-02
thanks for the advice however,

okay so a couple things about that set-up

a) i do not believe my card is supported by the beryl drivers
--> my card is an X1400 and even though it does not specifically say that it is unsupported, i believe it would fall into this category
Unsupported

    * X1300 / R515 based cards.
    * X1600 / R530 based cards.
    * X1800 / R520 based cards.
    * X1900 / R580 based cards.

b) i tried the commands for some things and they did not function properly

jeff@jeff-laptop:~$ glxinfo | grep vendor
X Error of failed request:  GLXBadContext
  Major opcode of failed request:  142 (GLX)
  Minor opcode of failed request:  5 (X_GLXMakeCurrent)
  Serial number of failed request:  17
  Current serial number in output stream:  17

some later commands did not work as well when trying to access some files, so i don't think these things are still available, however i might be wrong because i don't properly understand how to interpret this response.  does the glxbadcontext mean i entered the command wrong, i dont believe so because i also tried copy/paste and still got the same response

c) i tried doing the last part recommended:

Code:

sudo dpkg-reconfigure xserver-xorg

Use TAB to move around and SPACEBAR to select/enable when necessary. When you get to the resolution page, enable your monitor's highest resolution and everything less. Then you can restart the Xserver with CTRL+ALT+BACKSPACE. You will lose any unsaved data. Then go to System->Preferences->Screen Resolution and your normal res should be available.

--> all this resulted in was causing the xserver to become incapable of booting in graphic mode when i restarted, so i had to reinstall the os so i could get things to work again


is there another path i might be able to install these drivers? or something i can go about doing? any help would be greatly appreciated

---

### Post by nitro_n2o on 2007-08-02
this might help [http://www2.ati.com/drivers/linux/linux_8.24.8.html](http://www2.ati.com/drivers/linux/linux_8.24.8.html) have a look at it 
you should always back up your xorg.conf before doing anything as a best practice.. actually you have to back up anything before playing with it. It just makes your life easier...

---

### Post by jpat on 2007-08-02
okay so i think it may work, i believe i found a newer version of the software though

see [http://ati.amd.com/support/drivers/linux/linux-radeon.html](http://ati.amd.com/support/drivers/linux/linux-radeon.html)

however i downloaded the file and tried to open it without avail.  what is the code that the instruction manual refers to when it says 'navigate to the ATI Proprietary Linux driver download'  i am not sure how to do that through the terminal application
To install the ATI Proprietary Linux driver using the Automatic option, follow these steps:

   1. Launch the Terminal Application/Window and navigate to the ATI Proprietary Linux driver download.
   2. Enter the command sh ./ati-driver-installer-8.39.4.run to launch the ATI Proprietary Linux driver installer. The ATI Proprietary Linux Driver Setup dialog box is displayed.

also when i tried the sh ./..... command it said that it couldnt open it

---

### Post by Tux Aubrey on 2007-08-02
Are you using the "official" version of the ATI driver installed through System>Administration>Restricted Drivers ?

---

### Post by jpat on 2007-08-02
> **Tux Aubrey said:**
> Are you using the "official" version of the ATI driver installed through System>Administration>Restricted Drivers ?

under restricted drivers there is listed the ati accelerated grapics driver and i do have in enabled, however i am still limited to the 800X600 res
[ATTACH]39586[/ATTACH]

---

### Post by OZTack on 2007-08-02
Have a look at this thread - works well :)
[http://ubuntuforums.org/showthread.php?t=514296]("http://ubuntuforums.org/showthread.php?t=514296")

---

### Post by nitro_n2o on 2007-08-02
> **jpat said:**
> 
also when i tried the sh ./..... command it said that it couldnt open it
if you are still interested use sh <file_name> without the ./

---

