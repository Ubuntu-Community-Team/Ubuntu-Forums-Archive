---
title: "ATI Drivers"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by Bout to Snap on 2007-08-22
I've absolutely done all that i can do about this prob have no idea where to start really I've downloaded xfree86.bin which is required to install my drivers however i still cant get nothing to work...so ima looking for some remote assistance if anyone out there's up for the challenge woudl be much appreciated considering i have no 3d acceleration there for cant play any games.


Graphics Card:
Radeon 9250
PCI-128mb

i just recently purchased a copy of Cedega and would like to be able to use it so if anyone wants to get up with me Message me on GAIM(aim)@DeathbySocom thanks in advance for anyone who attempts.

---

### Post by asmoore82 on 2007-08-22
> **Bout to Snap said:**
> I've absolutely done all that i can do about this prob have no idea where to start really I've downloaded xfree86.bin which is required to install my drivers however i still cant get nothing to work...so ima looking for some remote assistance if anyone out there's up for the challenge woudl be much appreciated considering i have no 3d acceleration there for cant play any games.


Graphics Card:
Radeon 9250
PCI-128mb

i just recently purchased a copy of Cedega and would like to be able to use it so if anyone wants to get up with me Message me on GAIM(aim)@DeathbySocom thanks in advance for anyone who attempts.

you are going to have to get a different video card.
When you have some nVidia GeForce2 or higher
or ATI Radeon 9500 or higher the "Restricted Drivers Manager"
will get them working for you fairly automagically ...

the Radeon 9250 is unsupported in Linux by ATI themselves.
the open source ATI drivers will get you some basic acceleration but not
enough for full 3D gaming.

---

### Post by Bout to Snap on 2007-08-22
> **asmoore82 said:**
> you are going to have to get a different video card.
When you have some nVidia GeForce2 or higher
or ATI Radeon 9500 or higher the "Restricted Drivers Manager"
will get them working for you fairly automagically ...

the Radeon 9250 is unsupported in Linux by ATI themselves.
the open source ATI drivers will get you some basic acceleration but not
enough for full 3D gaming.

I've got the stuff just dont know how to use it, and yes ATI offers support for that Video card i just downloaded there linux drivers for it, all i need to do now is install xfree86 4.3 or higher and then install the drivers which i've already downloaded. I've found a few sites that are hosting the xfree86 that i need but im not sure which files i need to download...even if i did woudlnt know how to install them.

---

### Post by Terl on 2007-08-22
Why are you installing xfree86?  According to the ati site it works with XORG which Ubuntu uses.  

Have you checked here:  [Ubuntu Docs-Installing ATI Driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28xorg%29%7C%28version%29")?  It outlines what to do with your model card as well.

I am also not certain how well this card will do for you with cedega.  What games are you trying to run?

---

### Post by Kilz on 2007-08-22
The Radeon 9250 isnt listed in the [supported cards for the ATI driver.]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8.html") But it may work because if you go to the ati site and use the driver selector you are shown the [page with the drivers here]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") If you ewant to try it though, you dont want the xfree86 package but the ATI Driver Installer.  I would also [recommend this page]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") on how to use it.

---

### Post by Bout to Snap on 2007-08-22
> **Kilz said:**
> The Radeon 9250 isnt listed in the [supported cards for the ATI driver.]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/linux_8.28.8.html") But it may work because if you go to the ati site and use the driver selector you are shown the [page with the drivers here]("http://ati.amd.com/support/drivers/linux/linux-radeon-prer200.html") If you ewant to try it though, you dont want the xfree86 package but the ATI Driver Installer.  I would also [recommend this page]("http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide") on how to use it.

thanks...that was a big help with the info hopefully can get it to work now..much appreciated.

---

### Post by Bout to Snap on 2007-08-23
> **Terl said:**
> Why are you installing xfree86?  According to the ati site it works with XORG which Ubuntu uses.  

Have you checked here:  [Ubuntu Docs-Installing ATI Driver]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI?highlight=%28xorg%29%7C%28version%29")?  It outlines what to do with your model card as well.

I am also not certain how well this card will do for you with cedega.  What games are you trying to run?

Note to self.....Don't try this method if your in my situation!!! my computer has been down for 2 days!!! something to do with xserver messing up because of the commands you use in the Guide follow the other post instead.after updating xorg it wont save the changes or something no idea really...just dont use!!

---

### Post by Bout to Snap on 2007-08-23
> **Bout to Snap said:**
> thanks...that was a big help with the info hopefully can get it to work now..much appreciated.

This way is actually working out better for me ...im only having one little prob though.This command wont convert the file into a .deb file.

FILE NAME:ati-driver-installer-8.40.4-x86.x86_64.run


Command im using:  sudo bash ati-driver-installer-8.40.4-x86.x86_64.run --builddpkg Ubuntu/feisty

Message i get:Unknown File or directory


any suggestions?

---

### Post by w4ett on 2007-08-24
This issue keeps coming up, but the fact of the matter is the 9250 is NOT supported by ATI  in Ubuntu, see:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)

> Prerequisites

Make sure the following things are true about your video card:

    *

      It is a 'Radeon' card
    *

      The model of the card is in the 9xxx series, 9500 or higher, or it is in the X series (e.g. X300), or it has TV-Out capability. The 'fglrx' driver does not support cards earlier than the 9500.


This is due to the fact that the legacy card  fglrx  driver is not supported in  xorg 7.2.  In Ubuntu this card is supported by the open source xorg-driver-ati.

---

### Post by Bout to Snap on 2007-08-24
> **w4ett said:**
> This issue keeps coming up, but the fact of the matter is the 9250 is NOT supported by ATI  in Ubuntu, see:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)



This is due to the fact that the legacy card  fglrx  driver is not supported in  xorg 7.2.  In Ubuntu this card is supported by the open source xorg-driver-ati.

If there not suppose to work,then why would ATI host them for that card? both on x86 @xorg.
the above driver discription which i used is used in the tutorial im using. it's an older version im guessing maybe i should have been clear about that.

This is what im getting from tests at the momment^^trying to shoot for a higher framerate.


chris@chris-desktop:~$ glxgears2553 frames in 5.0 seconds = 510.072 FPS
2520 frames in 5.0 seconds = 499.165 FPS
2520 frames in 5.0 seconds = 499.152 FPS
2520 frames in 5.0 seconds = 499.045 FPS
2520 frames in 5.0 seconds = 499.178 FPS
2520 frames in 5.1 seconds = 498.974 FPS
2520 frames in 5.0 seconds = 499.204 FPS
2520 frames in 5.1 seconds = 498.816 FPS
2520 frames in 5.0 seconds = 499.179 FPS
2520 frames in 5.0 seconds = 499.191 FPS
2520 frames in 5.0 seconds = 499.193 FPS
2520 frames in 5.0 seconds = 499.364 FPS
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 62742 requests (35 known processed) with 0 events remaining.
chris@chris-desktop:~$

with this i havent even been able to install the correct driver for it

---

### Post by w4ett on 2007-08-24
> **Bout to Snap said:**
> If there not suppose to work,then why would ATI host them for that card? both on x86 @xorg.
the above driver discription which i used is used in the tutorial im using. it's an older version im guessing maybe i should have been clear about that.

Because ATI have been habitually bad in supporting Linux, plus they have a vested interest in selling you a new, more modern card, not provide you a free driver, I'm sorry to say.  :(  Additionally, there are Linux distros out there which are not near as cutting edge as Ubuntu and still use XFree86.

I use a 9200 (the same GPU as yours, the RV280) on one of my machines, and it does work with compiz using the open source driver, so all is not lost. 

 Another thing to remember is that Ubuntu has a very short development cycle (6 months), so the developers and constantly using newer versions of packages and kernel (Gutsy has xorg 7.3)....It takes ATI a year and a half or so to update fglrx

---

### Post by Bout to Snap on 2007-08-24
> **w4ett said:**
> Because ATI have been habitually bad in supporting Linux, plus they have a vested interest in selling you a new, more modern card, not provide you a free driver, I'm sorry to say.  :(  Additionally, there are Linux distros out there which are not near as cutting edge as Ubuntu and still use XFree86.

I use a 9200 (the same GPU as yours, the RV280) on one of my machines, and it does work with compiz using the open source driver, so all is not lost. 

 Another thing to remember is that Ubuntu has a very short development cycle (6 months), so the developers and constantly using newer versions of packages and kernel (Gutsy has xorg 7.3)....It takes ATI a year and a half or so to update fglrx

I'm glad to know that i might be able to get another graphics card instead of keeping this headache.Which would you recommend? something that would be easy installing(driver wise)and would of course have to be PCI (have no agp slots)no idea where to start i've had this 9250 for awhile and up untile now served me well, and FTW why does the gears give me a 3d framerate but cedega says test failed?...I'm in the beginner section for a reason.

---

### Post by w4ett on 2007-08-24
Anything Nvidia will do you a good job.they regularly update their drivers and give good Linux support..there are some 5xxx series PCI cards around.....a good place to check is:

[www.pricewatch.com](www.pricewatch.com)

a quick check of the site shows this 5500/128 Mb  [http://www.imagestore.us/Items/v28](http://www.imagestore.us/Items/v28)

[IMG]http://images.channeladvisor.com/Sell/SSProfiles/42000036/images/1/V28.jpg[/IMG]

---

### Post by Bout to Snap on 2007-08-24
> **w4ett said:**
> Anything Nvidia will do you a good job.they regularly update their drivers and give good Linux support..there are some 5xxx series PCI cards around.....a good place to check is:

[www.pricewatch.com](www.pricewatch.com)

a quick check of the site shows this 5500/128 Mb  [http://www.imagestore.us/Items/v28](http://www.imagestore.us/Items/v28)

[IMG]http://images.channeladvisor.com/Sell/SSProfiles/42000036/images/1/V28.jpg[/IMG]

Nice so basically just stick the card in and im set to go? Not a bad price either better than what i paid for this.I know i have an old Nvidia Geforce2 100/200 tried that the other day and my pc gave me a graphics error of some sort.

---

### Post by w4ett on 2007-08-24
Insert your new card and boot into recovery mode.  From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. then go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

Code:

sudo envy -t

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

---

### Post by w4ett on 2007-08-24
Insert your new card and boot into recovery mode.  From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. the go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

Code:

sudo envy -t

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Edit:  You can also try this same procedure with your old Nvidia card.

---

### Post by Bout to Snap on 2007-08-24
> **w4ett said:**
> Insert your new card and boot into recovery mode.  From the command line type:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

This will give you the interface to modify the driver and resolutions. Controls are UP and DOWN cursor keys move the cursor and scrolls through available options, the space selects options, and <enter> confirms selections.

Select "nv" as the driver and press <enter>, then at the next screen you can enable any addttional resolutions that you want to use.....then use the cursor keys to highlight {OK} and <spacebar> to select the resolutions and press <enter> to save the selections as prompted, then type:

```
startx
```

This will get you to a GUI desktop. the go to:

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Install envy and then from the terminal type:

Code:

sudo envy -t

This will run the installation script from the terminal....follow the instructions to remove the old attempted driver installation and then install the correct Nvidia proprietary driver.

Edit:  You can also try this same procedure with your old Nvidia card.

thanks man i needed that,much appreciated ima gonna order that card today hopefully i'll get it by tuesday it being the weekend and all,anyhow i think this one has been solved,better off to get another video card then waste time with something that dont wont to work or has major glitches when you do enable it.

---

