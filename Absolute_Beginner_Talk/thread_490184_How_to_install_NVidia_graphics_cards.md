---
title: "How to install NVidia graphics cards"
date: 2007-07-02
forum: Absolute Beginner Talk
---

### Post by microsoft92sucks on 2007-07-02
I have a NVidia GeForce4 MX 440 (model p162) And How do I install it on Linux. Can someone give me a link or tell me them selfs. I found the drivers for it but I'm not sure if I need the 86x or 64x driver. Here's were the drivers are [http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)
Thanks in advance for any help.

---

### Post by serfcx on 2007-07-02
I used Envy with the same card and all OK.

Link here [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Good luck, dont forget to copy your xorg.conf before making changes

---

### Post by microsoft92sucks on 2007-07-02
> **serfcx said:**
> I used Envy with the same card and all OK.

Link here [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Good luck, dont forget to copy your xorg.conf before making changes

I don't want to do that becouse you have to re do it every time you up date. And I'm using Kubuntu and I don't know if I supports it. So can someone help me install the drivers. Or just even tell me if I ne 86 or 64.
Thanks

---

### Post by microsoft92sucks on 2007-07-02
Any help with this.

---

### Post by microsoft92sucks on 2007-07-02
Do I need 64 or 86 just tell me that or tell me how I can tell.PLEASE

---

### Post by Seisen on 2007-07-02
Maybe this will help

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia]("https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia")

---

### Post by moredhel on 2007-07-02
64 is only if you have a 64bit edition of (in your case) kubuntu.

Surely using the restricted drivers management should install it for you?

And when you say

' don't want to do that becouse you have to re do it every time you up date'

You have to do the same if you get the ones of the website, and that way takes even more effort.

Try the restricted driver management, it's in the adminstration menu i think (can't check at the moment, at work on a mac :( )

---

### Post by bioShark on 2007-07-02
Hi

I have the same video card, and I also have problems. People around have suggested to install the nvidia-glx (go to add/remove programs or to synaptic manager). If this driver won't help try to search for nvidia-glx-legacy. This is for older cards. I will try this out tonight to...so good luck!

---

### Post by microsoft92sucks on 2007-07-03
So just install this
(What it say's about it in add or remove)
```
NVidia binary X.Org driver
Package: nvidia-glx
NVIDIA binary XFree86 4.x/X.Org driver
These XFree86 4.x/X.Org binary drivers provide optimized hardware acceleration of OpenGL applications via a direct-rendering X Server and support the newer GeForce, nForce and Quadro families of NVIDIA chipsets. AGP, TV-out and flat panel displays are also supported.
If you have a TNT, TNT2, or older GeForce, you may need the nvidia-glx-legacy package instead of this one.
To enable the driver, run "sudo nvidia-glx-config enable".
```
And Then turn off my Computer put the Card in restart and It will work? (If I put it in without the driver it complan's about Graphic's And I have to shut down and take out the card)

And I think I need the one for newer card's becouse mines the 4 series and the one for the old card only go's up to the 2 series. And thanks a lot for all the help.

---

### Post by microsoft92sucks on 2007-07-03
Any Help on that

---

### Post by forestpixie on 2007-07-03
I installed via System>Admin>Restricted Drivers and it installed the nvidia-glx driver.

I have an nVidia GeForce MX440 AGP8X video card - I didn't install driver from anywhere but Sysnaptic - and it works ok

Does that help?

---

### Post by microsoft92sucks on 2007-07-03
I think. I still need to now though if I install that glx thing then shutdown. Put the GC in and reboot will it then install the drivers that I need for my GC.

---

### Post by cogadh on 2007-07-03
Wait a minute, the card you are trying to install drivers for is not physically installed in the PC yet? What kind of card is it currently using?

EDIT - Actually, that doesn't matter. Install the card and then boot up the PC. It will probably complain that it can't start the GUI, that's OK. If the GUI does start, do a CTRL-ALT-F1 to close it. Login to the console and run this:
```
sudo dpkg-reconfigure xserver-xorg
```
Then run "startx" to re-launch the GUI. Next follow [these instructions]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") to properly install the Nvidia drivers (yes the nvidia-glx package). You will probably need the legacy package, since the 440 is pretty old.

---

### Post by microsoft92sucks on 2007-07-03
No if I install it physically then my kubuntu geos into some weird thing and complans about graphics. Right now I have an integrated one.

---

### Post by cogadh on 2007-07-03
As I said, it will complain and that is OK. You will need to login to the console (i.e. text-mode interface, command line, etc.), which is what should come up after it is done complaining. 

One thing that may help is if you disable the onboard graphics after you install the new graphics card, but before you try to boot Kubuntu.

---

### Post by microsoft92sucks on 2007-07-03
Thank's cogadh I think I can get it now. But one more question once I have the GC in without the driver will I be able to still run firefox to look at that how to. Thanks

---

### Post by cogadh on 2007-07-03
No.
Just to try and clarify, physically install the card, then boot the PC (let it complain, etc.) and  run this command in text mode:
```
sudo dpkg-reconfigure xserver-xorg
```
That will reconfigure your xorg.conf file to a generic working state which will allow the GUI to start using generic video drivers. Type "startx" to restart the GUI. After that, you will need to follow [these instructions]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") to install the Nvidia driver. Part of those instruction may require you to use text mode, but you start them in GUI mode.

---

### Post by microsoft92sucks on 2007-07-03
Ok thanks. I got some stuff converting but once it's done I'll try it out.

---

### Post by microsoft92sucks on 2007-07-03
OK I'm using the driver's right now but I got a problem with the install on step 6 the file it tells me to open and write some stuff on doesn't exits. What should I do I need help on this quick please any1.
[http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty)
here's the how to

---

### Post by sab0403 on 2007-07-03
What method are you using? Method 1, Method 1 offline, or Method 2?

---

### Post by microsoft92sucks on 2007-07-03
1 online

---

### Post by sab0403 on 2007-07-03
Alright.

Just to be sure, after you did step 5, did you do step 7 of the "Problems" section? It's required considering your particular card model.

*after* you do step 7 of the "Problems" section (which you'll find at nearly the end of the guide) go back and do step 6 of method 1. Simply copy and paste the code indicated on the terminal; what you're doing is creating a launcher (or shortcut) to the nvidia settings, which will reside in the "System" section of your "Applications" menu (on the top left corner of your screen). Since you're creating it, the file you're trying to edit doesn't exist, but the code you're putting on the terminal will create the file for you. Then continue following the instructions.

---

### Post by microsoft92sucks on 2007-07-03
Thanks for the help but what am I suposed to do about this.(it's the second part of step 7 in problems)
```
  GNU nano 2.0.2         File: /etc/modprobe.d/options                Modified  

# Enable double-buffering so gstreamer et. al. work
options quickcam compatible=2

# Default hostap to managed mode
options hostap_pci iw_mode=2
options hostap_cs iw_mode=2
options nvidia NVreg_SoftEDIDs=0 NVreg_Mobile=1












File Name to Write: /etc/modprobe.d/options                                     
^G Get Help         ^T To Files         M-M Mac Format      M-P Prepend
^C Cancel           M-D DOS Format      M-A Append          M-B Backup File
```
What format deos it need to be in thanks.

---

### Post by sab0403 on 2007-07-03
Ok, the screen you're showing me is the terminal editor nano, editing modprobe.d/options.

So after you add the line you're indicated to (which it appears you already have), you press <Ctrl>+O to save, <Enter> to save in the location indicated (near the bottom), then <Ctrl>+X to exit.

then continue with the guide.

You do not need any "format"; even if it doesn't have any extension (like .txt or .pl or whatever), the file is supposed to be named like that. So don't modify it; just press <Enter>.

---

### Post by sab0403 on 2007-07-03
Just to follow up, in Linux is pretty common to have common text files without any extension.

---

### Post by microsoft92sucks on 2007-07-03
I finished the install. So I rebooted and It won't let me load a GUI. It say's something about poker-network and that's what's making it not work. So how would I uninstall it through texed mode. I've tried ```

sudo apt-get remove poker-network
```
but it say's there is'ent such thing so How could I find out what it's called. And remove it I know this is the problem becouse it try's to load it first and it crashes or something and make the rest not load. So I really nead to get rid of this.

---

### Post by sab0403 on 2007-07-03
Ok.

Please try to boot to the GUI again, but write down the error exactly so we can analyze it.

You can reconfigure X by typing

```
sudo dpkg-reconfigure xserver-xorg
```

but I would like to see the error first, maybe we can correct it.

---

### Post by microsoft92sucks on 2007-07-04
ok sorry it took so long for reply but back to the Problem. It say's in some problem report thing 
```

Eorror: API mismacth: The nvidia kernal module has the version
1.0-7184, but
this X module has the version 1.0-9631.
```
And a lot of other stuff. But I was running of those drivers for a while then I rebooted and this.
And thank you a hole lot for all the help.

---

### Post by metallicamaster3 on 2007-07-04
try:

in terminal:

sudo apt-get install nvidia-glx

that worked for me on the MX 400, maybe it will for you.

---

### Post by microsoft92sucks on 2007-07-05
> **sab0403 said:**
> Ok.

Please try to boot to the GUI again, but write down the error exactly so we can analyze it.

You can reconfigure X by typing

```
sudo dpkg-reconfigure xserver-xorg
```

but I would like to see the error first, maybe we can correct it.
That worked and I think I'm running off the driver's now but is there something I should do to get more power out of them or anything. And should I be able to run compiz of this other specs are
1ghz
256mb ram
Not very good I know but will Compiz work with that and this gpu. Thanks

And metallicamaster3 you didn't read all the post did you. Not to be rude.

---

### Post by microsoft92sucks on 2007-07-05
ok that last post was only true untill I rebooted. Now it's broke again and I've tried ```
sudo dpkg-reconfigure xserver-xorg
```
and
```
sudo apt-get install nvidia-glx

```
But there both not working. The error that's making it not work is
Error```
Falied to load NVIDIA kernal module
```
How do I fix this please help me get this gpu working so I can run compiz and a few other games.
Thanks

---

### Post by cogadh on 2007-07-05
First, to get the GUI back up do this:
```
sudo nano /etc/X11/xorg.conf
```
Scroll down to the "Device" section and change the driver entry from "nvidia" to "nv". Then restart and log in. Once you are back in the GUI follow [these instructions]("http://doc.gwos.org/index.php/Latest_nvidia_feisty") **to the letter** and you will have the Nvidia driver installed and functioning.

---

### Post by microsoft92sucks on 2007-07-06
Ok I got It working again with ```
sudo dpkg-reconfigure xserver-xorg
```
But i'm sure if I reboot it will brake again and I'll try that how to again cogahd but it mest me up last time. And What am I running off right now the nv driver right so y do I have to do all that other stuff. And will I be able to get compiz to work with all this.

---

### Post by microsoft92sucks on 2007-07-06
I think this might be what went wrong last time I did that how to.
```
spaje@EggHead:~$ uname -r
2.6.20-16-generic
spaje@EggHead:~$ sudo apt-get install 2.6.20-16-generic
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package 2.6.20-16-generic

```
Why is it saying that. And how do I fix it.

---

### Post by microsoft92sucks on 2007-07-06
Is this normal what should I do next. I want to get this driver working right.
So please any help.

---

### Post by cogadh on 2007-07-06
Which method are you trying to follow in that how-to, Method 1, Method 1 offline or Method 2? 

If you are following Method 1, then the line you want to enter is *not* this:
```
sudo apt-get install 2.6.20-16-generic
```
It should simply be this:
```
sudo apt-get install linux-generic
```
It will probably come back and tell you that you already have the latest installed.

---

### Post by microsoft92sucks on 2007-07-06
I got it so when I reboot it still works. I think I did'ent save a file last time. But look what happen's when I try to run compiz.
```
Enable the driver?

NVIDIA accelerated graphics driver

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D acceleration of newer cards.

If you wish to enable desktop effects, this driver is required.

If this driver is not enabled, you will not be able to enable desktop effects and will not be able to run software that requires 3D acceleration, such as some games.
```
What driver am I running off of? Am I running off my NVIDIA card or not I don't get that. Should I try to enable it. That's what mest me up last was enableing it. How can I get this driver working so I can try out compiz. I don't want fancy plugins I just want a few that I think would be usefull and cool. And maybe a good game or two.
Please explan why it's saying this.

---

### Post by sab0403 on 2007-07-06
Whew! I'm back.

So... wait. You have to finish method 1 of the guide BEFORE trying to run Compiz. It's normal that Compiz tells you that if you haven't finished that method.

---

### Post by cogadh on 2007-07-06
That's why I bolded the **to the letter** part in my original post with the instructions.

As sab0403 said, if Compiz is telling you that, then you did not finish the instructions.

---

### Post by microsoft92sucks on 2007-07-06
trust me when I say I did. But when I enabled it. It broke again. But on 7 problems it says to try somthing else if the first one deos'ent work.  So could that be the problem i'll try it latter tonight.

---

### Post by 070107 on 2007-07-06
Just adding my personal 2 cents worth to this Nvidia thread:

I've tried every method of installing the Nvidia driver I could find online.  Automatix, the script, package manager, and restricted driver method .... none of them worked for me.  I had to format and redo Ubuntu each time so I gave up.

---

### Post by microsoft92sucks on 2007-07-07
That did'ent work eather why ant this working I'm doing it all right. At least to my knowledge. Ican someone please Help me out.

---

### Post by 070107 on 2007-07-07
> **microsoft92sucks said:**
> That did'ent work eather why ant this working I'm doing it all right. At least to my knowledge. Ican someone please Help me out.

I think we've had the same experience.  I followed several different how-to guides on how to install the nVidia driver on Fiesty and none of them worked.:roll:

---

### Post by cogadh on 2007-07-08
> **070107 said:**
> I think we've had the same experience.  I followed several different how-to guides on how to install the nVidia driver on Fiesty and none of them worked.:roll:
Use the instructions I posted. If you take your time with the install and follow the instructions **precisely and fully**, the driver will install perfectly every time, regardless of user or system. More often than not, the reason the driver doesn't install is because a user tries to take a shortcut, skips a step or tries something not listed in the instructions, such as installing the official Nvidia package from within the GUI when it has to be installed from the console.

Nvidia makes the best Linux drivers available for their products. If you ever intend to try to do any 3D gaming on Linux or using one of the enhanced desktops like Beryl, I highly recommend you give the driver one last shot. If you do not, none of those will ever work properly, but, if gaming or fancy desktops aren't what you want, then stick with the generic driver, it will do everything you need.

---

### Post by 070107 on 2007-07-08
The guide at [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty) is a maze of commands with many "if this doesn't work ..." loopholes.  It's especially confusing because I installed Suse 10.1 awhile back on a machine and the Suse procedure for installing the nVidia driver took 1 minute and worked every time.

How come Ubuntu, the most user-friendly distro, has a complex set of instructions with healthy dose of technical jargon (for fun, I guess)?

---

### Post by microsoft92sucks on 2007-07-08
Well cogadh i've done all those instruction's right I really think. I've been doing this sort of stuff for only 1/2 a year so i may have mested up. But I don't think I did. 
But I did try It through a GUI first.
I think I might reinstall Ubuntu all togather. Do you think that will help? I do. But if I do that I have to remount a HDD (which is easy but still) and get a Belkin driver to work (which can be tricky). 
But if thats what it take I think i'll do it in a day or 2.
Unless someone thinks they can help me so I don't have to reinstall.

and 070107  how long did you try b4 u gave up. I'm not ready to give up just yet.

---

### Post by cogadh on 2007-07-08
> **microsoft92sucks said:**
> Well cogadh i've done all those instruction's right I really think. I've been doing this sort of stuff for only 1/2 a year so i may have mested up. But I don't think I did. 
But I did try It through a GUI first.
I think I might reinstall Ubuntu all togather. Do you think that will help? I do. But if I do that I have to remount a HDD (which is easy but still) and get a Belkin driver to work (which can be tricky). 
But if thats what it take I think i'll do it in a day or 2.
Unless someone thinks they can help me so I don't have to reinstall.

and 070107  how long did you try b4 u gave up. I'm not ready to give up just yet.

Since you've gone through this so many times and from so many different sets of instructions, it might be best to start fresh with a clean install.

> **070107 said:**
> The guide at [http://doc.gwos.org/index.php/Latest_nvidia_feisty](http://doc.gwos.org/index.php/Latest_nvidia_feisty) is a maze of commands with many "if this doesn't work ..." loopholes.  It's especially confusing because I installed Suse 10.1 awhile back on a machine and the Suse procedure for installing the nVidia driver took 1 minute and worked every time.

How come Ubuntu, the most user-friendly distro, has a complex set of instructions with healthy dose of technical jargon (for fun, I guess)?
What are you talking about? Those instructions are only 6 simple steps and the sixth one isn't actually necessary. The only part of it that has the "if this doesn't work..." stuff is the troubleshooting section. If you follow the 6 steps, then you will never need the troubleshooting section (unless you have a GeForce 420/440, but that is also listed in the instructions clearly):

**1) Identify the architecture of your kernel (e.g. generic or 386,etc. )**
Open Terminal or Konsole and type:
```
uname -r
```
(You will get something like this: 2.6.20-15-generic )
[B]
2) Now that you know the architecture (generic in my case but it could also be 386), type:[/B]
```
sudo apt-get install linux-generic
```
(of course you need to use your architecture instead of generic)
In this way you will install a dummy package which will always provide you with the latest kernel image, headers and restricted modules.
[B]
3) Install the Nvidia driver:[/B]
If your graphic card model belongs to the first list available on [this page]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") you will have to type (this command will install driver 9755):
```
sudo apt-get install nvidia-glx-new
```

OR if your graphic card model belongs to the second list available on [this page]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") you will have to type (this command will install driver 9631):
```
sudo apt-get install nvidia-glx
```

OR (If you need Legacy drivers, i.e. your graphic card is in the list at the end of the page or you need driver 7184)
```
sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings
```
[B]
4) Backup your xorg.conf[/B]
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

NOTE: if you lost your old xorg.conf or that doesn't work type this:
```
dpkg-reconfigure -phigh xserver-xorg
```

**5) Enable the driver in your xorg:**
```
sudo nvidia-xconfig --no-composite
```

NOTE: if you own a GeForce4 420/440 you should follow also point 7 of the PROBLEMS SECTION.

**6) Create a link to the &#8220;Nvidia-Settings&#8221; Panel in your application menu:**
```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

OR (if you use KDE)
```
kdesu kate /usr/share/applications/NVIDIA-Settings.desktop
```

NOTE: do not worry if the file is empty

Insert the following lines into the new file:
```
[Desktop Entry] Name=NVIDIA Settings Comment=NVIDIA X Server Settings Exec=nvidia-settings Icon= StartupNotify=true Terminal=false Type=Application Categories=Application;System;
```
Save the edited file.

Log out and press CTRL+ALT+BACKSPACE (so as to restart the xserver).

In case of problems, please read the PROBLEMS SECTION

---

### Post by 070107 on 2007-07-08
> **cogadh said:**
> Since you've gone through this so many times and from so many different sets of instructions, it might be best to start fresh with a clean install.


What are you talking about? Those instructions are only 6 simple steps and the sixth one isn't actually necessary. The only part of it that has the "if this doesn't work..." stuff is the troubleshooting section. If you follow the 6 steps, then you will never need the troubleshooting section (unless you have a GeForce 420/440, but that is also listed in the instructions clearly):

**1) Identify the architecture of your kernel (e.g. generic or 386,etc. )**
Open Terminal or Konsole and type:
```
uname -r
```
(You will get something like this: 2.6.20-15-generic )
[B]
2) Now that you know the architecture (generic in my case but it could also be 386), type:[/B]
```
sudo apt-get install linux-generic
```
(of course you need to use your architecture instead of generic)
In this way you will install a dummy package which will always provide you with the latest kernel image, headers and restricted modules.
[B]
3) Install the Nvidia driver:[/B]
If your graphic card model belongs to the first list available on [this page]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") you will have to type (this command will install driver 9755):
```
sudo apt-get install nvidia-glx-new
```

OR if your graphic card model belongs to the second list available on [this page]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html") you will have to type (this command will install driver 9631):
```
sudo apt-get install nvidia-glx
```

OR (If you need Legacy drivers, i.e. your graphic card is in the list at the end of the page or you need driver 7184)
```
sudo apt-get install nvidia-glx-legacy nvidia-xconfig nvidia-settings
```
[B]
4) Backup your xorg.conf[/B]
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

NOTE: if you lost your old xorg.conf or that doesn't work type this:
```
dpkg-reconfigure -phigh xserver-xorg
```

**5) Enable the driver in your xorg:**
```
sudo nvidia-xconfig --no-composite
```

NOTE: if you own a GeForce4 420/440 you should follow also point 7 of the PROBLEMS SECTION.

**6) Create a link to the “Nvidia-Settings” Panel in your application menu:**
```
sudo gedit /usr/share/applications/NVIDIA-Settings.desktop
```

OR (if you use KDE)
```
kdesu kate /usr/share/applications/NVIDIA-Settings.desktop
```

NOTE: do not worry if the file is empty

Insert the following lines into the new file:
```
[Desktop Entry] Name=NVIDIA Settings Comment=NVIDIA X Server Settings Exec=nvidia-settings Icon= StartupNotify=true Terminal=false Type=Application Categories=Application;System;
```
Save the edited file.

Log out and press CTRL+ALT+BACKSPACE (so as to restart the xserver).

In case of problems, please read the PROBLEMS SECTION


After all those scripts and how-to guides, the one thing that worked on my computer was to try to enable Desktop Effects and let Ubuntu install the driver and configure everything.  After that, it was just a matter of tweaking one config file to make the desired color depth, refresh rate, and resolution show up.  Works great now.

---

### Post by microsoft92sucks on 2007-07-09
> **070107 said:**
> After all those scripts and how-to guides, the one thing that worked on my computer was to try to enable Desktop Effects and let Ubuntu install the driver and configure everything.  After that, it was just a matter of tweaking one config file to make the desired color depth, refresh rate, and resolution show up.  Works great now.

How did you do that? Do you think it would work for me? What GPU do you have?

---

### Post by 070107 on 2007-07-09
Enabling Desktop Effects was in the "System", "Preferences", "Desktop Effects" menu item.

Instructions for editing the config file so you get the right settings for your monitor are here:
[http://ubuntuforums.org/showthread.php?t=83973&highlight=change+resolution](http://ubuntuforums.org/showthread.php?t=83973&highlight=change+resolution)

Not sure if your config file will be like mine, but mine had a lot of monitor modes in it that were junk.  I deleted them all and just put the setting I wanted in there.

One tip I'll give you that wasn't clear in the guide:  the color depth number isn't in 'millions of colors' (I'm a noob and assumed it was).  If you want 16.7 million colors, use the number "24" for the depth setting.  24 in that setting = 16.7 million colors.  If you put 16 in there, you get little dots all over the screen.

---

### Post by skullmunky on 2007-07-09
just my $.02 too:

for years, i only ever did the binary install from the nvidia website.  the "restricted drivers" installer in feisty is the first automated script or package that i've ever encountered that worked at all - packages in previous versions of ubuntu, in opensuse, etc. just gave me tons of grief.  

but if that method's not working for you, i'd suggest the "binary installer from nvidia website" method, particularly since you have an older card.  with some geforce's (like the 4200) i've had to use an older driver.  the archive link on the nvidia driver download page has tons of them.  the one that worked with the 4200 was, i *think*, 1.0-8776, or something else in the 8000 range.  

the packages in the repository, etc, are great, but if they're not able to handle your particular setup, this is the most tried-and-true method.

compiz or beryl isn't always the best choice to test out if the driver's working; another test is to run, from the terminal, 'glxgears'.  this is a little animation of some 3D gears.  if it runs smoothly you have the driver working.  you can also run 'glxinfo' - at the top it'll say "server glx vendor string: NVIDIA Corporation" if the driver's installed and woring, or "server glx vendor string: Mesa" if it isn't.


roughly, here's my suggestion.  this is all just repeating the tutorials and how-to's, btw, so no new information here, i'm sure.

1. have your machine working, with the graphics card, just using the standard open-source driver (nv).  
2. download the driver from nvidia.   i'll assume you figured out if you need the 32 or 64 bit version yet - if not, figure that our first.  
3. switch into console mode:

Ctrl-Alt-F1

log in

then,

sudo /etc/init.d/gdm stop

you have to have X11 (the desktop) turned off while it installs the driver.

4. go into the directory where you saved the installer.  it's probably on your desktop.

cd Desktop
chmod +x NVIDIA-Linux-x86-1.0-8774-pkg1.run
./NVIDIA-Linux-x86-1.0-8774-pkg1.run

(replace that with the actual name of whatever driver installer you downloaded).

5. if it asks whether to try and download a kernel interface, tell it no.  make it build one itself. 

6. if it asks if you want to configure your xorg.conf, say yes.

7. if it doesn't, you want to edit that yourself:

sudo nano /etc/X11/xorg.conf

look for the line

Driver "nv"

change it to

Driver "nvidia"

8. try starting X11 again:

startx

9. if you get your desktop, open a terminal and try

glxgears

and/or

glxinfo

10. see how this works.  

you probably have to blacklist the nvidia-restricted modules as specified in the howto's, as part of this too.

let us know how that works ....

---

### Post by microsoft92sucks on 2007-07-19
I think it could be something wrong with the GPU it's self. Because I tried a Knoppix live cd and it seemed to have graphic trouble and I couldn't get the GUI on it to work.
  I'm still going to try a reinstall in a week or 2 once a get a new PC.(I'll probably keep the same HDD It's not brand new. So my 2 80gigs will probably be best.(On a side question can you have 3 three HDD on 1 pc 1 of them being the slave to DVD drive.))

---

### Post by Frem on 2007-07-20
> **microsoft92sucks said:**
> I think it could be something wrong with the GPU it's self. Because I tried a Knoppix live cd and it seemed to have graphic trouble and I couldn't get the GUI on it to work.It might, if you've somehow damaged the card pulling out and sticking it in again a lot. ;-)

...But let's assume not. I haven't read anything in what you've posted that sounds like the card is damaged. 

FWIW, it took me several weeks to get 3D acceleration in this laptop. Heck, my first try with Ubuntu, it took me a while to get anything to display on the screen at all. With Fiesty, I checked a box in the "Restricted Drivers Manager" window that appeared when I first booted up and clicked OK. Took like 30 seconds for automatic configuration.
Your card will work, eventually. :-)

---

### Post by Extreme Coder on 2007-07-22
Here's something to check if your card is actually working well or not;
Try out [Mandriva One]("http://www.mandriva.com/community/mandrivaone")
Here's the download page: [http://www.mandriva.com/en/download/mandrivaone](http://www.mandriva.com/en/download/mandrivaone)
It's a Mandriva LiveCD, with the ability to be installed, and nVidia and ATi proprietary drivers, and Compiz and Beryl too so you can try the drivers out.
Try it out, and see if there's a problem with your card :P

---

### Post by microsoft92sucks on 2007-07-23
I tried
Slax
KANOTIX
and PCLinuxOS
PCLinuxOS Was taking really long so I shut it down but Slax and KANOTIX worked really good and fast there both better live cds then Ubuntu. I don't know about better distros haven't spent enough time on them. 
But any way they worked but they didn't have any thing that I could use to see if it was doing full 3d rendering or just running off the nv driver that I am right now. So thanks Extreme Coder for the idea. I'll try Mandeiva and see if compiz or beryl works

---

### Post by adityakiran on 2007-12-06
go to the restricted drivers section in the administration section on the desktop.

ubuntu automatically recognizes the graphics card . activate the checkbox and it will automatically search for drivers and download and install them

---

