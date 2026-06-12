---
title: "Battery Efficiency"
date: 2007-07-04
forum: Apple PPC Users
---

### Post by czechman86 on 2007-07-04
I have noticed that the battery on my Powerbook runs less efficient, when I am in Linux, than when I am in OSX. For example, when I am on battery power in OSX, I normally get a good 3.5 hours of time, before I must plug in again, however in Linux, I only get around 2 hours of time. Are there anyways to increase battery performance in Linux?

Also, I am not doing anything more or less graphically intense in Linux than OSX.

Thanks for your help!

---

### Post by ubuntu.daemon on 2007-07-04
um yeah i believe, yep, when you plug it in you should get a little icon saying that your plugged in linux right? or even a battery signal w/e, in that you should be able to change how you want your battery to perform under linux i believe....

---

### Post by tcrroadie on 2007-07-04
Beyond adjusting your screen brightness, what video card chipset is in your PowerBook?  If your PowerBook has an ATI Radeon chipset, there is a display driver option that can be set that will allow cpu throttling for graphics processing.  I have an iBook G4 with an ATI Radeon 9550, and I usually get about 3 hours with Beryl on.

Run this in a terminal and post your results. 

```
lspci | grep VGA
```

---

### Post by tablebreaker on 2007-07-05
> **tcrroadie said:**
> Beyond adjusting your screen brightness, what video card chipset is in your PowerBook?  If your PowerBook has an ATI Radeon chipset, there is a display driver option that can be set that will allow cpu throttling for graphics processing.  I have an iBook G4 with an ATI Radeon 9550, and I usually get about 3 hours with Beryl on.

Run this in a terminal and post your results. 

```
lspci | grep VGA
```

this sounds like it could help me!
here's my output
```
0000:00:10.0 VGA compatible controller: ATI Technologies Inc M9+ 5C63 [Radeon Mobility 9200 (AGP)] (rev 01)
```

my battery is about an hour in ubuntu and i can get around 3 in os x. battery power and the inability to scroll (adb trackpad instead of synaptics) and the only things keeping me from a permanent switch.

edit: oh, are you talking about the Dynamic Clocks option? i already have that set....

---

### Post by tcrroadie on 2007-07-05
Tablebreaker, your in luck, your mac has an ATI Radeon 9200 display card.  Lets enable a driver option called Dynamic Clock Scaling for your card.  Follow these steps. 

1.  First check your /etc/X11/xorg.conf file and make sure the driver "radeon" is set in the "Device" section. 
```

Section  "Device"
          Driver   "radeon"
```

2.  Now add this option to the same section of your xorg.conf file.
     
     ```
Option  "DynamicClocks" "true"
```

3.  Save the file and restart your xserver. 

```
sudo /etc/init.d/gdm restart
```

You can find more information on  ATI Radeon graphics chipset tweaks in the [PowerPCFAQ Wiki]("https://wiki.ubuntu.com/PowerPCFAQ#head-d6be5f475782e6b1d7c441ad9571a2d83d8cbffa").  Page down to the section labeled **3D performance tweak for ATI Radeon cards:**.

You can also adjust your default panel brightness settings by right clicking the battery icon in the top panel, (accomplished by pressing the F12/Eject key if you are not using a mouse), or in the Power Managment section of the Gnome Settings menu.  

Sorry I''m not able to help you on your trackpad issue since I always use a 5 button mouse on my iBook.

---

### Post by stmiller on 2007-07-05
You can tweak hard disk operation for performance and battery life by changing settings in

/etc/hdparm.conf

The execute

sudo /etc/init.d/hdparm restart

to restart the service.

EDIT: Attached is the hdparm.conf from my 15" TiBook G4 867Mhz. Use my suggestions at your own risk! Mainly, be sure to turn dma on and tweak the spin down and apm settings.

---

