---
title: "Removing Google earth"
date: 2007-04-03
forum: Absolute Beginner Talk
---

### Post by a.v.l on 2007-04-03
What is the command to remove Google Earth please.

---

### Post by taurus on 2007-04-03
How did you install it and where did you install it?  You can remove the whole Google Earth's directory with the "rm" command from a terminal or with nautilus.

---

### Post by Martje_001 on 2007-04-03
Did you install it via apt-get or aptitude? Simple: sudo apt-get remove google-earth

---

### Post by a.v.l on 2007-04-03
> **taurus said:**
> How did you install it and where did you install it?  You can remove the whole Google Earth's directory with the "rm" command from a terminal or with nautilus.

Thanks for the comment, it  reminded me that it came from Automatix and I was able to uninstalled it from there.  

For some reason when I installed Google Earth I was unable to see the globe.  Google Earth opens and I can see the tool bars  and the black background, but no sign of the earth.  Any suggestions why this might be?

---

### Post by taurus on 2007-04-03
Did you by any change install a 3D driver for your graphic card first?

---

### Post by a.v.l on 2007-04-03
> **taurus said:**
> Did you by any change install a 3D driver for your graphic card first?

To be honest No I didn't,  I am trying to get Google Earth to work on three Linux computers and having very mixed results with them all.  

One works as I've just discribed. Another requires a graphics card update (ATI card) because it is running very slowly with a jurky action. When I do a graphics card driver update from the manufacturer's website it makes no difference to the slow jurky operation. The last PC works reasonably well with its Nvidia G/Card but large area of the word are blurred out .  Any help would be appreciated.

---

### Post by taurus on 2007-04-03
Google Earth is a 3D app so you need to install a driver for your graphic card before you run it.  Either you have ATI or nVidia, you can try to use envy to install a driver for it.  Then, see if Google Earth improves/works now.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

---

### Post by a.v.l on 2007-04-03
> **taurus said:**
> Google Earth is a 3D app so you need to install a driver for your graphic card before you run it.  Either you have ATI or nVidia, you can try to use envy to install a driver for it.  Then, see if Google Earth improves/works now.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Thanks for your help, I'll try your suggestions this evening.

---

### Post by a.v.l on 2007-04-03
> **taurus said:**
> Google Earth is a 3D app so you need to install a driver for your graphic card before you run it.  Either you have ATI or nVidia, you can try to use envy to install a driver for it.  Then, see if Google Earth improves/works now.

[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

I've used the above link to install the latest driver for my ATI graphics card which seem to go fine but when instructed to reboot I find that I cannot.  Before I get to the desktop I get this message.

Quote:
Failed to start X server (your graphical interface)
It is likely that it is not set up correctly.  Would you like to view the X server output to giagnos the problem.  (then with a yes or no option) If I choose "no" I get this message:

Quote:
The X server is now disabled. Restart GDM when it is configured correctly.

No panic, but can anyone help me to restart my PC please

---

### Post by taurus on 2007-04-03
Boot into recovery mode from GRUB menu and reconfgure your X again with

```
dpkg-reconfigure xserver-xorg.conf
```
And if you want to restart Ubuntu after that, run

```
shutdown -r now
```

---

### Post by a.v.l on 2007-04-03
> **taurus said:**
> Boot into recovery mode from GRUB menu and reconfgure your X again with

```
dpkg-reconfigure xserver-xorg.conf
```
And if you want to restart Ubuntu after that, run

```
shutdown -r now
```

Thanks again, when type in I dpkg-reconfigure xserver-xorg.conf in the terminal I get the following message:

dpkg-reconfigure xserver.conf package xserver -org.conf is not installed and no info is available. Use dpkg --info (=dpkg-deb --info) to examine archive files and dpkg --contents (=dpkg-deb --contents) To list their contents
/usr/sbin/dpkg-reconfigure: xserver-xorg.conf is not installed.

Now I'm stuck.

One thing I can do is boot into recovery mode and when I type in envy I'm taken to the envy driver installation page. In there I can install or remove drivers as well as activate xserver.  I've tried selecting activate xserver there but it doesn't work either. Would uninstalling the ATI drivers resolve this problem?

---

### Post by taurus on 2007-04-03
My bad.  :oops: 

```
dpkg-reconfigure xserver-xorg
```

---

### Post by a.v.l on 2007-04-03
> **taurus said:**
> My bad.  :oops: 

```
dpkg-reconfigure xserver-xorg
```

OK we are getting somewhere now. Your instruction above allowed me to reset my xserver,  something which involved  making choices I was unsure about, but fortunatly they have allowed me to get back into Ubuntu and as far as I can see everything is still working, except Google Earth that is, which I need to reinstall.  

I now have an ATI control entry under applications/accessories but when I open it it tells me:

Driver does not provide FireGL X11 extentions, panel componets will only operate partially. I'm unsure what this means at present and perhaps I'll wait to see how Google Earth performs before looking any further into it.  

Where can I get Google Earth from as it's disapeared from Automatix.

Thanks again for you help it has been invaluable, I would have been lost without it.:confused:

---

### Post by Maestro23 on 2007-04-03
Try the repositories:

Synaptic: search Google Earth.  Install

or from their website: [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

To run the bin file from their site:
> 
chmod a+x GoogleEarth.bin

sudo ./GoogleEarth.bin

---

### Post by a.v.l on 2007-04-04
> **Maestro23 said:**
> Try the repositories:

Synaptic: search Google Earth.  Install

or from their website: [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

To run the bin file from their site:

Much appreciated.

---

### Post by a.v.l on 2007-04-04
> **Maestro23 said:**
> Try the repositories:

Synaptic: search Google Earth.  Install

or from their website: [http://earth.google.com/download-earth.html](http://earth.google.com/download-earth.html)

To run the bin file from their site:

chmod a+x GoogleEarth.bin

sudo ./GoogleEarth.bin



I've downloaded Google Earth from their website but the command above returns a result  "file not found" in the terminal.

---

### Post by ynottony on 2007-06-12
Also trying to remove Google Earth.  

Installed it with Automatix.  When I open the uninstall window there I don't see it there as an option to be removed.  Searched each of the categories in the uninstall window and it is not there.

It shows to still be an option for installation in the install window.  

When I click on it on my desktop to open it, it brings up my log-in window.

Tried the Terminal remove option suggested and it can't find the package to unstall.  Please advise.  Thanks.

- Tony Brigmon

---

### Post by w4ett on 2007-06-12
> **ynottony said:**
> Also trying to remove Google Earth.  

Installed it with Automatix.  When I open the uninstall window there I don't see it there as an option to be removed.  Searched each of the categories in the uninstall window and it is not there.

It shows to still be an option for installation in the install window.  

When I click on it on my desktop to open it, it brings up my log-in window.

Tried the Terminal remove option suggested and it can't find the package to unstall.  Please advise.  Thanks.

- Tony Brigmon

Try using the install option in Automatix to repopulate  Google Earth in the Uninstall tab...this won't reinstall it, but should allow you to uninstall it via Automatix.

---

### Post by ynottony on 2007-06-12
Thank you.  Got it removed.  

As a "newbie" I am amazed at the help available here.  Hopefully I can return the favor to someone when I get "up-to-speed".  Again, thank you.

- Tony Brigmon

---

