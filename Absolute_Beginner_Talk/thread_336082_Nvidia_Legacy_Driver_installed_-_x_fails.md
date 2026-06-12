---
title: "Nvidia Legacy Driver installed - x fails"
date: 2007-01-11
forum: Absolute Beginner Talk
---

### Post by chinocracy on 2007-01-11
Hi, just wondering why.... I installed the nvidia legacy driver 7174 in my system via Synaptic. I even used the nvidia-config file offered to change the config file. But when I restart and boot in, after the progress bar loading components, the Nvidia logo flashes several times to interrupt fully black screens. And then I get the message that X fails to start. So it won't boot. I restore the original configuration afterwards. 
I try installing again but it still fails in the X part. What's wrong?

Some notes:
I use the 2.6.15-27-686 kernel on Dapper.
Card is a Geforce 2 MX400 w/ tv-out.
I believe Load "glcore" is absent from even the unaltered config file.
System is a Celeron 1.2 S370. 

Should I use the non-legacy driver? 

Thanks.

---

### Post by moma on 2007-01-11
Try this:

$ [COLOR="SeaGreen"]mkdir $HOME/tmp[/COLOR]
$ [COLOR="SeaGreen"]cd $HOME/tmp[/COLOR]

Download Nvidia's driver package v9746. 
$ [COLOR="SeaGreen"]wget [http://i1.no/0411/](http://i1.no/0411/)[/COLOR]

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/NVIDIA-Linux-x86-1.0-9755-pkg1.run)

The driver comes from [http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html]("http://www.nvidia.com/object/linux_display_ia32_1.0-9746.html") 

Install necessities
$ [COLOR="SeaGreen"]sudo apt-get install build-essential[/COLOR]

Save your data and Stop X (stop the graphical GUI).
$ [COLOR="SeaGreen"]sudo /etc/init.d/?dm stop [/COLOR]

Login on the text-console (you may need to press CNTR + ALT +F1 først) and 
$ [COLOR="SeaGreen"]cd $HOME/tmp[/COLOR]

Unload (remove from memory) the old NVIDIA module
$ [COLOR="SeaGreen"]sudo modprobe -r nvidia [/COLOR]

Install the driver
$ [COLOR="SeaGreen"]sudo sh NVIDIA-Linux-x86-1.0-9746-pkg1.run[/COLOR]

Restart X 
$ [COLOR="SeaGreen"]sudo /etc/init.d/?dm restart [/COLOR]

or dive down to runlevel 1 and back to runlevel 2.
$ [COLOR="SeaGreen"]sudo init 1[/COLOR]
#[COLOR="SeaGreen"]init 2[/COLOR]
-------------------------

Check any error messages in  /var/log/Xorg.0.log
$ cat /var/log/Xorg.0.log

Take backup copy of your good "/etc/X11/xorg.conf".

---

### Post by chinocracy on 2007-01-11
Thanks.
Forgot to mention I have the 7184 and 9746 run files. Could I work with the 9746? Anyway, I'll get the version you suggested.

---

### Post by Ben Sprinkle on 2007-01-11
Uh-oh, if you don't get everything worked out, heres how to go back to default driver so x will work:
```

sudo dpkg-reconfigure xserver-xorg

```
Fill out everything, when you come to the driver screen select VESA.

---

### Post by chinocracy on 2007-01-11
Heeeeeeey, it works! So it seems  I'm running on the regular driver, not the legacy one... Graphics seem to have more depth now, and run faster... Thanks!

---

### Post by Ben Sprinkle on 2007-01-11
> **chinocracy said:**
> Heeeeeeey, it works! So it seems  I'm running on the regular driver, not the legacy one... Graphics seem to have more depth now, and run faster... Thanks!

No problamo.

---

### Post by chinocracy on 2007-01-12
Hmmm... seems I've run into another problem. The driver worked when I installed via the gdm stop method. When I started it, it worked. But when I rebooted and loaded Ubuntu again, the X server failed to start again. I think I saw another thread on this. I'll look it up.

---

### Post by moma on 2007-01-12
Check if your system has loaded the nvidia driver.
$ [COLOR="SeaGreen"]sudo modprobe nvidia [/COLOR]

$ [COLOR="SeaGreen"]lsmod | grep nvidia [/COLOR]

and 
$ [COLOR="SeaGreen"]sudo /etc/init.d/gd? restart [/COLOR]

You can put "nvidia" into /etc/modules file if it's not loaded automatically.

If you upgrade to a new kernel, you must reinstall the driver.

---

### Post by Ben Sprinkle on 2007-01-12
I reccomend using the default VESA driver. ;)

---

### Post by clantoncs on 2007-01-12
Wow, this should really be a sticky or someone should repost all this.  Thanks a lot for the great info.  The bane of my existence has been getting nvidia installed correctly.  After a couple download problems installing the regular nvidia drivers I was finally able to get it installed.  Then I tried installing beryl which for some reason made X restart everytime I used opengl (including screensavers).  

I tried installing the beta nvidia drivers using the ubuntu guide, but that just made everything crash without even being able to load X at all.  I think the 

```
sudo dpkg-reconfigure x-server-xorg
``` will work like a charm. 

thanks!

---

### Post by Ben Sprinkle on 2007-01-12
> **clantoncs said:**
> Wow, this should really be a sticky or someone should repost all this.  Thanks a lot for the great info.  The bane of my existence has been getting nvidia installed correctly.  After a couple download problems installing the regular nvidia drivers I was finally able to get it installed.  Then I tried installing beryl which for some reason made X restart everytime I used opengl (including screensavers).  

I tried installing the beta nvidia drivers using the ubuntu guide, but that just made everything crash without even being able to load X at all.  I think the 

```
sudo dpkg-reconfigure x-server-xorg
``` will work like a charm. 

thanks!

Nice to see you're happy. :)

---

### Post by chinocracy on 2007-01-13
Thanks for the help. What Moma shared is what I saw in the other forum post. I'd better write it down.

@Goat Spirit: How do I use the VESA driver? When running the dpkg-reconfigure thing, I only get the option to do the resolution. Or is that already loaded in the normal mode?

---

### Post by Ben Sprinkle on 2007-01-13
> **chinocracy said:**
> Thanks for the help. What Moma shared is what I saw in the other forum. I'd better write it down.

@Goat Spirit: How do I use the VESA driver? When running the dpkg-reconfigure thing, I only get the option to do the resolution. Or is that already loaded in the normal mode?

You keep going through the steps of reconfiguring it untill you see it, use your arrows for moving. ;)

---

### Post by chinocracy on 2007-01-15
Goat Spirit, 
I've gone through the dpkg-reconfig several times already, though I still could only see a selection for resolutions. I always select only the last 3. I still haven't found the vesa option. Maybe I should look again. 

I've done the modprobe thing, but it only shows the nvidia driver working after install. When I restart, again it's lost. I installed X server development modules, since those were being asked for during installation, as nvidia kernel modules were said to be missing, and a new module was built. But after that, still the same result. Will try installing again to see what else went wrong.

---

### Post by Ben Sprinkle on 2007-01-15
Here, I will screen mine and attach it.
*Attaches*
Look, I have found VESA. ;)

---

### Post by chinocracy on 2007-01-17
Hmm, I wonder why that doesn't turn up when I run the dpkg-reconfigure.... maybe I only press up and down and not left and right when that menu comes up... ](*,) Anyway, I'll keep on experimenting further till I get it. Maybe I lack source modules that the driver needs in compiling a kernel interface without building, or when it builds, it can immediately recognize on the next boot. Thanks.

---

### Post by Ben Sprinkle on 2007-01-17
You don't lack anything. Push the left and right to change between options, then up or down to choose an option. That dialog is one of the first to come up, like maby in the first 5 slides.

---

### Post by chinocracy on 2007-01-17
Hmm, the menu doesn't change anymore than the resolutions choices. Anyway, I just press enter, and the xorg configuration is reset and all is normal - w/out the Nvidia driver. Perhaps my hardware setup prevents me from having vesa. 
Another thing I found is in the xorg log. If I use a 96xx driver, it reports that despite the driver's successful installation, it says that it has a 7174 module and it fails to initialize the Nvidia kernel module. If I use the 7174 driver, glx and nvidia don't load (nvidia doesn't exist). So it's the same: though I install successfully with each gdm restart, restarting the computer continues to bring up an x failure. 
Goat Spirit, you're going out a great deal to help me on this, and I thank you. Maybe later on I'll see the light at the end of the tunnel.

---

### Post by Ben Sprinkle on 2007-01-17
You can manually edit the file anyway lol:
```

sudo gedit /etc/X11/xorg.conf

```
Look for the driver part and change to "vesa".

---

### Post by mistypotato on 2007-01-17
> **Goat Spirit said:**
> I reccomend using the default VESA driver. ;)

Wow....why???

I have an nVidia card and I was using the Vesa option until someone told me to install the nvidia driver using **Automatix**.

SMooooooooooth sailing ever since.

Fast graphics, no problems at all.   The screen saver was "choppy" with Vesa but is fluid with the proper nVidia driver installed.

---

### Post by Ben Sprinkle on 2007-01-18
Okay, I use i810 for my driver.

---

### Post by chinocracy on 2007-01-20
Hi GS,
I once tried the manually set 'vesa' option, but it just got stuck at the gnome login screen. When I enter my password and username, it just goes blank, then goes back to the login screen. 

And I'm afraid I couldn't do anymore experimentation with my video card -- and ubuntuing. Seems my Inno3d MX 400 card just went kaput. All of a sudden it went one long beep and two short beeps (Award bios) when I switch on the box. I use my backup S3 Trio PCI 4MB card now. If I put back my Nvidia card, it gets the beep error again. Looks like I'll have to get a new card. And I can't boot Ubuntu. It always goes blank after loading devices. ](*,) 

Thanks.

---

### Post by Ben Sprinkle on 2007-01-21
Eh, oh well, we tried.

---

### Post by chinocracy on 2007-01-21
I finally got a new nvidia card... quick, eh? Same MX 400 kind but second hand. I'll try again when I have free time... I think I should post this problem in that sticky thread tseliot posted about video driver install. Thanks.

---

### Post by Ben Sprinkle on 2007-01-22
> **chinocracy said:**
> I finally got a new nvidia card... quick, eh? Same MX 400 kind but second hand. I'll try again when I have free time... I think I should post this problem in that sticky thread tseliot posted about video driver install. Thanks.

No problem mate. :D

---

### Post by chinocracy on 2007-01-23
OK, I think I got it.

What I did is to manually copy /lib/modules/2.6.15-27-686/volatile/nvidia.ko
to:
/lib/modules/2.6.15-27-686/kernel/drivers/video/nvidia.ko

via 'gksudo nautilus' on Alt-F2.

When I restart X AND the computer, the Nvidia logo flashes and it successfully enters Ubuntu. 

Success?

---

### Post by Ben Sprinkle on 2007-01-23
> **chinocracy said:**
> OK, I think I got it.

What I did is to manually copy /lib/modules/2.6.15-27-686/volatile/nvidia.ko
to:
/lib/modules/2.6.15-27-686/kernel/drivers/video/nvidia.ko

via 'gksudo nautilus' on Alt-F2.

When I restart X AND the computer, the Nvidia logo flashes and it successfully enters Ubuntu. 

Success?

I call that success. :)

---

### Post by chinocracy on 2007-01-24
> **Ben Sprinkle said:**
> I call that success. :)

\\:D/ :guitar:

---

