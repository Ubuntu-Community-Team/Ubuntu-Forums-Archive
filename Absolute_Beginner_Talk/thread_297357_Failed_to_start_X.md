---
title: "Failed to start X"
date: 2006-11-11
forum: Absolute Beginner Talk
---

### Post by wildsrv on 2006-11-11
The NOOB did it now.. I was making some changes and updating some stuff and now I get an error and can't start X. I found out how to view the error log and it says.

WW Warning, Couldn't open module nvidia
EE Failed to load module "nvidia" (module dows not exist , 0)
and the last line says
EE No drivers available.

Ofcourse i didn't put all of this but i'm hopeing that will help you to help me :D I tried to switch the drivers but i guess it didn't work.

---

### Post by meng on 2006-11-11
Please explain how did you get into this mess in the first place. Then perhaps I can tell you how to back out.

---

### Post by wildsrv on 2006-11-11
Honestly... I don't know. The most i can come up with is i was selecting under the menu item under admin that lets you select and install LOTS of programs. I changed the video driver to a different one and thats where i'm at. Hope this helps.

---

### Post by tommcd on 2006-11-11
Have you tried: 'sudo dpkg-reconfigure xserver-xorg' in terminal? This should get you back to the GUI. Then you can backup that /etc/X11/xorg.conf file and reinstall the nvidia driver.

---

### Post by wildsrv on 2006-11-11
that seems to work some now i need to figure why its booting but all i get is a black screen. I hear the music of it loading fine but can't see any thing. Guess i'll check the config file again.

---

### Post by wildsrv on 2006-11-12
I'm still having issues i'm wandering if it has to do with the refresh rate and what not. I've tryed to do easy/simple not the middle or advanced for the video but it just gives me the black screen as it loads and doesn't show any thing...

---

### Post by djsroknrol on 2006-11-12
You're not running the right video driver for your card...that's why the black screen...what card is it? Not much of an Nvidia kind of guy...hopefully someone has the same video card and can lead you to the correct driver for it..

---

### Post by teaker1s on 2006-11-12
your problem is that you have installed the wrong nvidia driver for your card 
I too did this when automatrix installed wrong driver.
reboot and run the recovery kernel option. you will now be presented with an unfriendly text login or prompt AFTER LOGIN you will need to type 
sudo dpkg-reconfigure xserver-xorg

there will be choice of either "nv "or "nvidia""
select "nv" as your driver 
for all other options don't let it auto detect and leave the same "tab" selects okay and use "return"

your problem is the nvidia open gl driver is incorrectly chosen by automatrix2-when you feel like a challenge and breaking it again you can find out if you need current or legacy nvidia driver to get open GL

---

### Post by wildsrv on 2006-11-12
My video card is a Nvidia GeForce 7800. I have two running in SLI. I have been selecting the Nv Because that is the only one close to what i have i don't see the other you mintioned.

Also in the error file it says

WW) NV: No matching Device section for instance (BusID PCI:5:0:0)

---

### Post by wildsrv on 2006-11-12
I also just found out that when i check the info off my monitor it says the current configureation its trying to display is 640x400 at 69Hz. Not any where near where i was wanting. I get a black screen with a white cursor in the top left. When i login as myself (not root/recovery) i can hear the (two drums) sound. I can type in my name and password and i hear it log in. Hope this helps

---

### Post by tommcd on 2006-11-13
It appears that SLI is problematic in linux at best. Perhaps you could try to remove one vid card, install ubuntu, then reinstall the other card. Or try hooking the monitor up to the other card. Do a search for 'SLI' as title of thread in ubuntu forums:
[http://ubuntuforums.org/showthread.php?t=258117&highlight=sli](http://ubuntuforums.org/showthread.php?t=258117&highlight=sli)
[http://ubuntuforums.org/showthread.php?t=258117&highlight=sli](http://ubuntuforums.org/showthread.php?t=258117&highlight=sli)
See in particular the replies from tseliot:
[http://www.ubuntuforums.org/showthread.php?t=272295&highlight=SLI](http://www.ubuntuforums.org/showthread.php?t=272295&highlight=SLI)
It seems it is possible to get SLI to work, but the results may not produce the same expected perfomance results as you may see in windows.

---

### Post by teaker1s on 2006-11-13
my advice is get one card working then think about what drivers and  manual xorg config you need

---

### Post by timothy_duncan on 2006-11-13
> **tommcd said:**
> Have you tried: 'sudo dpkg-reconfigure xserver-xorg' in terminal? This should get you back to the GUI. Then you can backup that /etc/X11/xorg.conf file and reinstall the nvidia driver.
hi,

i've got the same problem but when i tried the above command, the GUI is still not showing up..  please see below thread

[can' t try kubuntu 6.10, text screen login showing up]("http://ubuntuforums.org/showthread.php?t=297858")

sorry for stealing this thread..

---

### Post by AndyCooll on 2006-11-13
timothy_duncan: When you go through the config process:
```
sudo dpkg-reconfigure xserver-xorg
```

At the the graphics card stage choose "vesa". This is will at least get you up and running with a gui. 

It's a bog standard driver and works with practically all graphics cards. Of course once you are up and running you may well wish to play around setting up the nvidia/ati drivers for optimum performance.

:cool:

---

### Post by tommcd on 2006-11-14
timothy_duncan,
If you are running from the live CD, and kubuntu is not installed on the hard drive, then when you reboot you are back to where you started since nothing is stored on the hard drive. After you do 'sudo dpkg-reconfigure xserver-xorg' just type 'startx'. this should get you the GUI. If that doesn't work try: 'dpkg-reconfigure kdm' (or gdm for ubuntu). Then type 'startx'.

---

### Post by wildsrv on 2006-11-16
thanks every one I didn't have any SLI settings before and i will try that other driver and see if it works.

---

### Post by wildsrv on 2006-11-16
Well i've tried most settings and still haven't been able to get it to work. I'm also wandering if the PCI bus stuff has some thing to do with it. Of course I could be wrong but I don't know. Attached is the info I got from winblows if it helps.

---

### Post by jsteve54302 on 2006-11-16
wildsrv, if you're running Edgy, I would first boot in Recovery Mode (choose at grub) and try adding

```
Section "Extensions"
    Option "Composite" "0"
EndSection
```to the end of /etc/X11/xorg.conf (back it up first by
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf
).  This is needed for hardware opengl on ATI/fglrx to work, maybe it'll help with Nvidia too...

If this doesn't work, get back to a (very) basic gui (most likely 1024x768 or 1280x1024 resolution) by booting Recovery Mode, logging in, and then typing:

dpkg-reconfigure xserver-xorg

and, when you get to the video part, chose vesa (**not** nv or nvidia).  You won't have opengl, but at least you can use the gui from it.  It is possible, but **very** unlikely, that the PCI bus is not being correctly detected, and if this is the case, you'll still get a blank screen.  If this happens, repeat the above procedure, this time looking for a screen that has PCI:5:0:0 in the input line, and asks for you PCI Device Bus or some such, and try PCI:2:0:0  if you have the monitor on your secondary screen (not primary) DVI/VGA (not familiar with this card's outputs).  Once you get video, write down and keep the working PCI bus settings - the Nvidia drivers may want to change them, and if the new ones don't work you'll have to reconfigure from a recovery console again - with these PCIx.x.xsettings, but keep the Nvidia driver if you get it to work otherwise.

Once you've got a vesa XOrg working, go on to install the **correct** Nvidia driver (after all, you almost certainly got the wrong drivers):

1.  Open a web browser
2.  Go to [http://www.nvidia.com/](http://www.nvidia.com/)
3.  Hover over the Download Drivers (first link on the silver bar - ignore the missing flash plugin - thats for another post and i haven't fixed it yet) and select Download Drivers
4.  In the next window, select Graphics Drivers in the first box, GeForce and TNT2 in the second, and either Linux IA32 or Linux AMD64/EM64, depending on whether you're using the 32-bit or 64-bit ubuntu, and click "Go".
5.  Follow the instructions on the following page.  I would detail them here but a) they're already there and b) if I try to follow them my self I'll break my system - I have ATI Crossfire...

Hope this gets OpenGL running, if not send me a message from a working system...

---

### Post by wildsrv on 2006-11-19
JSteve54302>

You rock i was playing with my settings and it had my PCI set up as PCI:2:0:0 I changed it to PCI:5:0:0 and now it works GREAT!!!!!!! Well I dont' know if I have spoken to soon because I am now going to attempt to update my settings as per the second part of your post. THANKS AGAIN

---

### Post by wildsrv on 2006-11-19
OK I got to run X and now I'm trying to install the NVIDIA drivers. I'm getting after i run the installer it says "Skipping the runlevel check (the utility 'runlevel' failed to run)". And I'm also getting this error "Unable to find the system utility 'ld' ; please make sure you have package 'binutils' installed. If you do have binutils installed then please check that 'ld' is in your PATH." I need help once again](*,) ](*,)

---

### Post by jsteve54302 on 2006-11-20
> **wildsrv said:**
> OK I got to run X and now I'm trying to install the NVIDIA drivers. I'm getting after i run the installer it says "Skipping the runlevel check (the utility 'runlevel' failed to run)". And I'm also getting this error "Unable to find the system utility 'ld' ; please make sure you have package 'binutils' installed. If you do have binutils installed then please check that 'ld' is in your PATH." I need help once again](*,) ](*,)

Oh dear...  it looks like the driver is trying to build itself from the source code...  I didn't catch which distribution of Ubuntu your using... it probably shouldn't matter though...  (probably :))  You don't really need these if you get the pre-compiled drivers...

You may do well to disregard my previous advice and use System->Administration->Synaptic to install the nvidia-glx and nvidia-settings (and probably nvidia-xconfig) packages.  The description for nvidia-glx says you may need to use nvidia-glx-legacy if you have an "older" GeForce card, but it doesn't define "older", so if you can't get nvidia-glx to work, you may try the legacy package.

These drivers may be a bit older but they should be stable.  If you still want to keep trying with the driver from Nvidia:

The installer is telling you that it needs some programs that aren't installed on you're system, specifically binutils and upstart-compat-sysv (this seems to be where runlevel lives) (:confused:they really should have been installed by default - they were on my Edgy box:confused:)...  It's likely that you'll also need other developement packages as well, but until it tells you which ones there's no way to know...  To get the missing packages, either open System->Administration->Synaptic, enter your root password, and search for the two package names and install them from there, or open a terminal (Applications->Accessories->Terminal and enter the command:

```
 sudo apt-get install binutils upstart-compat-sysv
```However, you'll probably end up in a long cycle of satisfying one dependency only to find 3 more in its place if you go this route...


I apologize for the misdirection before...

---

### Post by wildsrv on 2006-11-20
LOL you are great man. I was able find the things you listed but the only question i have is that it wouldn't let me select and install both the nvidia-glx and nvidia-settings it was one or the other and if i rember right the nvidia-settings once i selected that i had to install the nvidia-xconfig. which just saved me time having to find that LOL. How do I check and see what version of my video card drivers i'm using? As of now i don't plan on doing to much but as i'm getting more and more use to and adjusted to *nix i'm able to do more. (trying to still stay on subject and not ask other quesitons that belong in different area) LOL

and also FYI:

nathan@nathan-desktop:~$ sudo apt-get install binutils upstart-compat-sys5
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package upstart-compat-sys5
nathan@nathan-desktop:~$

---

### Post by jsteve54302 on 2006-11-20
Oops again - "upstart-compat-sys5" should read "upstart-compat-sysv"...  I've got this problem with autotranslation of Roman numerals...  fixing it now...

As for selecting both nvidia-glx and nvidia-settings, I was able to select both, but installing either could kill my Gnome :) so I don't know how it would react...  Trying to select nvidia-glx and nvidia-glx-legacy would definitely be a bad idea, however, as they are for different GPU chipsets which cannot coexist...

To get version info, use glxinfo:

```
john@john-desktop:~$ glxinfo
name of display: :0.0
display: :0  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.2
```

Your vendor and version strings (and possibly the screen name/info, esp on multi-head systems) will be different, of course.  This is only a partial output - you'll get a bunch more with vendor id's and renderer capabilities.  Also, note the "name of display" and "direct rendering" lines.  If you get a "cannot find screen on 0" or "direct rendering: No" it means that the driver isn't working properly.  If you get a screen name and "direct rendering: Yes", open a terminal and try:

```
glxgears
```

to display a nice set of spinning gears, and 

```
fgl_glxgears
```

to get a wildly spinning cube, and framerate info in the terminal window.  Also, your GL screensavers will fly :)...



If this doesn't get GL running, post your complete /etc/X11/xorg.conf  file and the output from glxinfo, and I'll see what I can find.

---

### Post by wildsrv on 2006-11-25
Sorry for the long reply but it seems to work now. Except for the other issue i'm having (file system got messed up and i think i'm gonna have to format after trying to resize my partitions) but that IS a different thread. Again thanks for all your help and you were able to show/teach me so much.

/me hands jsteve54302 a cold one!

---

