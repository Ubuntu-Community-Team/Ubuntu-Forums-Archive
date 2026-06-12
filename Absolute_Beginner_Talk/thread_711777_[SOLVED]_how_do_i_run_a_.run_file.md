---
title: "[SOLVED] how do i run a .run file?"
date: 2008-03-01
forum: Absolute Beginner Talk
---

### Post by whoscheesemine on 2008-03-01
how do i run a .run file?

I need to install this driver for this graphics card:

[http://www.nvidia.com/object/linux_display_x86_96.43.05.html](http://www.nvidia.com/object/linux_display_x86_96.43.05.html)

what is it I need to download to be able to install this type of file format?

---

### Post by Paqman on 2008-03-01
Have you already tried using the instructions on that page?

 A good way to install graphics card drivers is with [Envy](http://albertomilone.com/nvidia_scripts1.html), though.

---

### Post by JoshuaRL on 2008-03-01
First off, you'll need to run this from the Recovery Mode.

Then, make sure you do the following exactly:
```

cd /home/<username>/Desktop
chmod +x NVIDIA-Linux-x86-96.43.05-pkg1.run
sh NVIDIA-Linux-x86-96.43.05-pkg1.run

```
Then a text based GUI will run and it will install and configure your system for you.  If it asks you if you want to create kernal modules, go ahead.

If you have any problems post back here.

And you can always check out [the information here.](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28driver%29%7C%28install%29%7C%28nvidia%29)

---

### Post by whoscheesemine on 2008-03-01
> **JoshuaRL said:**
> First off, you'll need to run this from the Recovery Mode.

Then, make sure you do the following exactly:
```

cd /home/<username>/Desktop
chmod +x NVIDIA-Linux-x86-96.43.05-pkg1.run
sh NVIDIA-Linux-x86-96.43.05-pkg1.run

```
Then a text based GUI will run and it will install and configure your system for you.  If it asks you if you want to create kernal modules, go ahead.

If you have any problems post back here.

And you can always check out [the information here.](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia?highlight=%28driver%29%7C%28install%29%7C%28nvidia%29)

First off,

Thanks for being so helpful and thanks for doing it in such a timely fashion.

I got this error after i typed in the third command:

  ERROR: nvidia-installer must be run as root

Does this mean I should reboot the computer and do this from the command prompt? or do I need to use a su or sudo command?

I'm still quite the Ubuntu beginner, but I'm like a sponge.

Edit: I thought I shoudl also mention, as I don't know if it would affect anything, that I'm not currently using the graphics card, I'm using the on-board. When I try to boot the computer with the graphics card in, I get all the way to right untill its going to load the interface (xfce or whatever, I have Xubuntu gutsy). This is why I was wondering if I needed to reboot into... is it called grub?

[COLOR="Red"]**Edit #2:**[/COLOR] Okay so I tried it again using sudo for the last command and I received the following error:

  WARNING: You do not appear to have an NVIDIA GPU supported by the 96.43.05   
           NVIDIA Linux graphics driver installed in this system.  For further 
           details, please see the appendix SUPPORTED NVIDIA GRAPHICS CHIPS in 
           the README available on the Linux driver download page at           
           [www.nvidia.com](www.nvidia.com).

I then pressed enter, and I received this error:

 ERROR: You appear to be running an X server; please exit X before            
         installing.  For further details, please see the section INSTALLING   
         THE NVIDIA DRIVER in the README available on the Linux driver         
         download page at [www.nvidia.com](www.nvidia.com).

...and after another strike of the "enter" key:

  ERROR: Installation has failed.  Please see the file
         '/var/log/nvidia-installer.log' for details.  You may find            
         suggestions on fixing installation problems in the README available   
         on the Linux driver download page at [www.nvidia.com](www.nvidia.com).

Okay, first off, as I stated previously, I don't have the graphics card in the VGA slot right now as when I do so upon rebooting it won't load the Xubuntu interface. Is there a command I can type to reboot with just a terminal so that I can run this with the graphics card in?

I also am most deffinitely not running xserver, but I'm going to go out on a limb and assume that this version of ubuntu was based off of a version of an ubuntu based server called xserver, I'm probably wrong, but if so then it would make sense that it would state I have that OS installed, which I do not, when it scanned some of the files.

As for the last error... duh, I'm rather aware that it didn't work LOL.

---

### Post by Whiffle on 2008-03-01
[http://ubuntuforums.org/showpost.php?p=4284483&postcount=8](http://ubuntuforums.org/showpost.php?p=4284483&postcount=8)


:)

---

### Post by whoscheesemine on 2008-03-01
> **Whiffle said:**
> [http://ubuntuforums.org/showpost.php?p=4284483&postcount=8](http://ubuntuforums.org/showpost.php?p=4284483&postcount=8)


:)

Well, I gotta say that if that's what editing a script was... then I think I've gone from 99% sure I love Linux to 100% LOL. Even though the only change I made was changing the word "nvidia" to nv when I saw the desktop boot up for the first time all day with the graphics card in I shouted out a hardy Tim Taylor hoh hoh hoh LOL. I do have a question though. In my system tray (sorry for the Windows term please feel free to correct me) There is now an icon of a peice of hardware that says there are restricted drivers available. Does anyone else recommend this? Perhaps I should rephrase for legal technicalities. Would my graphics card truelly run better if I downloaded these restricted drivers? In all actuallity I still don't fully understand these legal technicallities, I was reading about them for a little while when I was figuring out how to get an AVI file to play on my computer yesterday. Is it something like Windows has trademarked certain file extensions? If that's the case, that's total BS. I don't understand though why these drivers are "illegal" when NVIDIA has linux support right on their website! Is it possible that I'm horribly misreading the deffinitions here? Could restricted possibly mean that they were user created and haven't been fully aproved by the upper admins of the Ubuntu Community? Oh so many questions... excuse me for being so inquisitive, I beleive I'll start another thread asking the same questions. Thanks a lot for all your help.

---

### Post by jocko on 2008-03-01
> **whoscheesemine said:**
> Well, I gotta say that if that's what editing a script was... then I think I've gone from 99% sure I love Linux to 100% LOL. Even though the only change I made was changing the word "nvidia" to nv when I saw the desktop boot up for the first time all day with the graphics card in I shouted out a hardy Tim Taylor hoh hoh hoh LOL. I do have a question though. In my system tray (sorry for the Windows term please feel free to correct me) There is now an icon of a peice of hardware that says there are restricted drivers available. Does anyone else recommend this? Perhaps I should rephrase for legal technicalities. Would my graphics card truelly run better if I downloaded these restricted drivers? In all actuallity I still don't fully understand these legal technicallities, I was reading about them for a little while when I was figuring out how to get an AVI file to play on my computer yesterday. Is it something like Windows has trademarked certain file extensions? If that's the case, that's total BS. I don't understand though why these drivers are "illegal" when NVIDIA has linux support right on their website! Is it possible that I'm horribly misreading the deffinitions here? Could restricted possibly mean that they were user created and haven't been fully aproved by the upper admins of the Ubuntu Community? Oh so many questions... excuse me for being so inquisitive, I beleive I'll start another thread asking the same questions. Thanks a lot for all your help.

The restricted drivers are drivers that come under a restricted licence (= not open source).
They are not illegal in any way, it's just that they contain code that the companies (in this case nvidia) wishes or needs to keep as company secrets, so you are allowed to use them but you are not allowed to see or change the actual source code.

In your case the restricted drivers manager would install the nvidia proprietary  drivers, which are the ones you can download from nvidias website, just conveniently made into a debian package by the ubuntu package maintainers.

If your choice is between the drivers you would get directly from nvidias website and those that the restricted manager would install, my advice is to use the restricted manager.
The drivers from nvidias website may be a newer version, but if you install them you would need to re-install them if the kernel is updated. The restricted drivers are in the ubuntu repositories and the package maintainers make sure to compile the modules for each kernel version for you.
The only exception to this advice would be if your graphics card is so new that the version in the repositories does not support it.

I think the instructions on the page Whiffle gave are wrong:
To use the drivers installed with those instructions, you need to make sure that the driver in xorg.conf is "nvidia", not "nv".
"nv" is an open source driver which, as  far as I know have very limited functionality.

---

### Post by whoscheesemine on 2008-03-01
yeah well the default was nvidia and it wouldn't load the interface, but once I changed it to nv it worked beautifully, I think i'm going to go with the repositories. Thanks!

---

### Post by Whiffle on 2008-03-02
Actually the part where I say to change nvidia to nv is what I said to do if it doesn't work...

---

### Post by whoscheesemine on 2008-03-05
yup and as you said... it didn't work LOL but its working great now, thanks alot

---

