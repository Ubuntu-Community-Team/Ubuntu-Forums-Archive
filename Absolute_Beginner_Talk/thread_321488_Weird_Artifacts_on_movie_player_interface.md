---
title: "Weird Artifacts on movie player interface"
date: 2006-12-19
forum: Absolute Beginner Talk
---

### Post by nyxynyx on 2006-12-19
Hello! When i try to play any movie using totem, i get weird artifacts on the movie player's interface like on the screenshot below. Any idea how to fix it? I'm on nvidia 6600gt. Seems the same before and after upgrading to Edgy. Thanks!

EDIT: Only the red marks are done by me.

[IMG]http://img526.imageshack.us/img526/349/screenshotyb8.png[/IMG]

---

### Post by Fully216 on 2006-12-19
how did you install totem?  Did you use automatix?

---

### Post by nyxynyx on 2006-12-19
my totem came with the Dapper installation

---

### Post by Fully216 on 2006-12-19
the reason I asked is because I was wondering if the artifacts are related to in installation/setup of restricted formats.

[https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Automatix would have taken care of that.

Have you tried to play the file using a different player (vlc for example)?

---

### Post by nyxynyx on 2006-12-19
Thanks for the reply. I tried VLC and it gave the same kind of artifacts on the interface only.

[IMG][[IMG]http://img342.imageshack.us/img342/9103/screenshot1ca9.png[/IMG]](http://imageshack.us)[/IMG]

---

### Post by Fully216 on 2006-12-19
Hmm, so it is not the media player.  Do you use the nvidia driver or the "nv" driver?

Check you /etc/X11/xorg.conf to see.

You might need to install the proprietary drivers.  

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

My guess would be to select the GeForce and TNT2 drivers > then linux (either IA32 or amd depending on your system)

---

### Post by Fully216 on 2006-12-19
I think automatix does that installation for you, which would make the process easier.  

[http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38](http://www.getautomatix.com/wiki/index.php?title=Installation&Itemid=38)

---

### Post by xinoos on 2006-12-19
hi...im new to these as well. do you mean the default drivers are giving problems ? i read from the documentation it says have support for 6600GT.

---

### Post by Fully216 on 2006-12-19
Well, the default drivers work very well, don't get me wrong.  This is especially the case with the Nvidia cards, which offer linux support.  However, you will not be able to use more of the advanced features of the card, like 3d acceleration and such until you install the proprietary drivers.  

In the case of playing an encoded video file, it might be the problem which causes the artifacts, although we shall see.  ;)

---

### Post by nyxynyx on 2006-12-19
Thanks Fully, my xorg.conf uses 'nvidia' in the device subsection. I tried downloading the newer nvidia driver but i cant install. It says that i cant have x running. How do i kill x? Also, i cant get automatix2 to work because it keeps saying its unable to retrieve some keys when starting even though i followed the instructions on the wiki and imported the keys.

---

### Post by Fully216 on 2006-12-19
to restart x:

control + alt + backspace

to stop x:

$ sudo /etc/init.d/gdm stop

Ctrl + Alt + F1-6 will get you to a virtual console where you can log on.

to start x:

startx (simple enough right)

---

### Post by Fully216 on 2006-12-19
Well, edgy does install the nvidia driver by default.  It would guess that the default installation/dapper upgrade went okay because you have not had any other problems so far (that I know of at least).  

You can also restart and login with the command line option in your grub menu if non of those other options work (as sometimes people change their shortcut keys).

It is very strange the the key did not import properly from the automatix site.  How far did you get exactly and what was the specific error, although I assume it is unrelated to the video artifacts?

---

### Post by ciscosurfer on 2006-12-19
> **nyxynyx said:**
> Thanks Fully, my xorg.conf uses 'nvidia' in the device subsection. I tried downloading the newer nvidia driver but i cant install. It says that i cant have x running. How do i kill x? Also, i cant get automatix2 to work because it keeps saying its unable to retrieve some keys when starting even though i followed the instructions on the wiki and imported the keys.These are taken from: [http://tinyurl.com/yhntg2](http://tinyurl.com/yhntg2)

From terminal do the following 
**(ONE LINE AT A TIME HITTING ENTER AFTER EACH STEP)**: 
```
echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo tee -a /etc/apt/sources.list
wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
gpg --import key.gpg.asc
gpg --export --armor 521A9C7C | sudo apt-key add -
```To finish off: 
```
sudo apt-get update
sudo apt-get install automatix2
```

---

### Post by Fully216 on 2006-12-19
Other people have reported a similar problem as well (just background info, no help there unfortunately)

[http://www.linuxforums.org/forum/linux-newbie/29474-video-artifacts.html](http://www.linuxforums.org/forum/linux-newbie/29474-video-artifacts.html)

You might also try lowering your color depth in xorg.conf (24bit -> 16bit for example).  This would help if the system could not keep up with the demands to play the file.  It tends to happen only for certain video cards but common on all XFree servers.

---

### Post by nyxynyx on 2006-12-19
Thanks for the help so far! I managed to stop x server from running. (Was doing ctrl alt backspace but x kept coming back lol)

When i ran the nvidia driver installer, I got

No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel frmo the NVIDIA ftp site?

When i ran the nvidia driver installer, I got

> No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel frmo the NVIDIA ftp site?

I selected yes, but it said
> 
No matching precompiled kernel interface was found on the NVIDIA ftp site; this means that the installer will need to compile a kernel interface for your kernel.

...

Unable to find the kernel sources tree for the currently running kernel.... If you know the correct kernel source files are installed, you may specify the kernel source path with the '--kernel-source-path' command line option.

I got beryl running so i guess i got the drivers right...


As for automatix, yea dun think its related to the video problem. I did all the instructions on the wiki and the post above, I started Automatix, the splash screen appears, after Retrieving Keys appear in the status bar, I get a popup alert box that says "Sorry Automatix can not continue because some keys could not be downloaded, please try again later."

---

### Post by nyxynyx on 2006-12-19
I tried changing the color depth to 16bits. Well, the movie player interface is now free of artifacts, but the rest of my desktop got messed up lol. Seems like things that require transparency isnt displaying properly, and my login screen displays a distorted background image. I changed back to 24bits and its back to normal where the movie player displays some funny artifacts on the interface(not the movie).

---

### Post by Fully216 on 2006-12-19
It might be that they automatix site is down.  They have been having trouble with hosting/bandwidth issues.  It sounds like it installed correctly but you cannot run the tool I wager.  You might just need to wait a while and try again if that is the issue.

Not having a kernel interface is okay (as I did not either).  You do however need to have the kernel source files downloaded from the repos.  This is probably easiest via the snaptic package manager.  

Open Terminal or Konsole and type these commands

uname -r (so as to see what kernel you are using)

Go to SPM and search for linux-tree to get the source files you need.

It is also good to have the following packages installed as well:

sudo apt-get install build-essential
sudo apt-get install kernel-package
sudo apt-get install gcc

Another option is to get the version from the repositories.  I would wager since you did an upgrade, this is the version you have.  It will not be the latest/greatest because the repos are slightly behind what is released.  With that being said, this is the repos install procedure, which only would help if you upgraded to edgy a while ago.

sudo apt-get install nvidia-glx
sudo apt-get install nvidia-settings
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

---

### Post by Fully216 on 2006-12-19
Grrr ... how funny is that??  It would fix one issue and create another ...  ](*,) ](*,) This does mean that the player is demanding too much from your video card.  Based on your description, I would stick with 24-bit as well.  :-| 

Lets see if we cannot get the latest driver installed, and hope that fixes the problem.

---

### Post by nyxynyx on 2006-12-19
I typed uname -r and got 2.6.17-10-386 but i cant find the kernel tree in the repos, only version 2.4.27-12 is there. Should i get it?

When i did the alternative approach, sudo apt-get install nvidia-settings caused nvidia-glx to be removed, and 'sudo nvidia-glx-config enable' gave a "command not found". Hmm im stuck.

---

### Post by Fully216 on 2006-12-19
It seems we can do nothing right I guess ~ lol.

No, that package you mentioned is for the old kernel and will not help.  Try typing 'linux-source' and 'linux-headers' into SPM.  Then you should get what we need.

Specifically:

linux-source-2.6.17
linux-headers-2.6.17-10-386

---

### Post by nyxynyx on 2006-12-19
Btw, i tried playing a movie on a slower system(slower processor with half the ram) running nvidia Quadro4 750 XGL with 'nv' driver on Drapper which i think is slower than the 6600GT im having the problems on, and didnt have the artifacts on the movie player interface.

---

### Post by Fully216 on 2006-12-19
the command not found is because nvidia-settings removed nvidia-glx.  I might have gotten the command order backwards.  You could try it in reverse to see it it works:

sudo apt-get install nvidia-settings
sudo apt-get install nvidia-glx
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nvidia-glx-config enable

Although, the best thing is to get the headers & source installed so we can use the latest and greatest driver you downloaded from the nvidia website.

---

### Post by Fully216 on 2006-12-19
Yes, these artifacts are specific to the video card itself.  For some cards there are these problems, and others there is not.  It is kind of a hit or miss thing unfortunately.  :-?  The driver is somewhat generic in nature and certain cards do not act well with it (hence the constant updates from nvidia).  Your card just happens to be one of those.

---

### Post by nyxynyx on 2006-12-19
Oh no now i cant start x!
I managed to get the nvidia installer running until just before it compile the kernel module, there is a CC version check failure saying about gcc4.1 used to compile kernel not matching current compiler gcc4.0 . I selected no, and during the building of the kernel module i get an error:

> ERROR: Unable to load the kernel module 'nvidia.ko'. This happensmost frequently when this kernel module was built against the wrongor improperly configured kernel sources, with a version of gcc that differs from the one used to build the target kernel, or if a driver such as rivafb/nvidiafb is present and prevents the NVIDIA kernel module from obtaining ownership of the NVIDIA graphics device(s).

i tried apt-get install nvidia-xgl and now x cant start!

---

### Post by nyxynyx on 2006-12-19
When i try to run x, i get

> (EE)Failed to load /usr/lib/xorg/modules/libglx.so
(EE) Failed to load module "glx" (loader failed, 7)
(EE) Failed to initialize the GLX module; please check in your X log file that the GLX module has been loaded in your X server, and that the module is the NVIDIA GLX module.
Error: API mismatch: the NVIDIA kernel module has the version 1.0-9631, but this X module has the version 1.0-8776. Please make sure that the kernel module and all NVIDIA driver components have the same version,
(EE): Failed to initialize the NVIDIA kernel module! Please ensure that there is a supported NVIDIA GPU in this system, and that the NVIDIA device files have been created properly.
(EE) Screen(s) found, but none have a usuable configuration.

Fatal server error:
no screens found

Do i have to reinstall ubuntu?

---

### Post by Fully216 on 2006-12-19
You don't have to reinstall.  Just use the CLI to change your xorg.conf.  Use the "nv" driver for now until the glx or proprietart driver gets installed properly.

EDIT: sorry to leave you hanging last night, had to get some sleep.

---

### Post by Fully216 on 2006-12-19
the new version of the gcc compiler, version 4.1 was relased back in May.  I am surprised that your install does not have it, as my edgy came with version 4.1.20060928.  This might have been an issues since you upgraded from dapper versus a fresh install.  Since your kernel was compiled using this version of gcc, any kernel patches, drivers, etc need to be compiled using the same version, ie version 4.1.  Check SMP or updates to see if you can upgrade to it via the repos.  If not, you can download it from [http://gcc.gnu.org/](http://gcc.gnu.org/)

It sounds like we still have a bunch of minor issues.  I wonder if a fresh install would not fix them?  Just a thought.

---

### Post by nyxynyx on 2006-12-21
I got new drivers and now they;re fixed! Thanks!

---

