---
title: "iBookG4 - 11.10 : Howto make screen backlight/brighness controls + sleep/suspend work"
date: 2011-10-24
forum: Apple Hardware Users
---

### Post by jumil on 2011-10-24
If you don't like stories and just want the solution skip the first paragraph.
Sorry for the long title by the way, I did that for searchability.

**[SIZE=2]The story so far:[/SIZE]**

After installing 11.10 on my iBookG4 basically everything execpt the backlight controls worked out of the box. I got it to work after a week of research. Currently I am running Xubuntu 11.10 on the machine, but I have no reason to believe this would not work under Ubuntu with Unity2D or Lubuntu.

I looked all over the internet for solutions and found a lot of outdated fixes including the one on the Ubuntu PPC FAQ. It seems this functionality has been coming and going with various Ubuntu PPC releases. All the solutions had one thing in common. They involved tinkering with the frame buffer in one way or another.

It also became clear that the systems disability to control the  backlight was what was likely keeping it from suspending. Since trying  to suspend the screen turned of and got locked, but immediately turned on  again instead of also switching off the backlight.
The only two reports I found who specifically said they got this particular function to work however were the ones who also compiled a custom kernel.

I had never done this before but said to myself "How hard can it be." and tried it. The first Kernel I made did nothing but speed up my boot  time. The second one solved the problem.

It all came down to one kernel option not being set in the 3.0.0 PPC kernel which allows the radeon card to act as a framebuffer device. So without this there just is now framebuffering going on at all.

[SIZE=1][FONT=Courier New]*-ATI Radeon display support (FB_RADEON)*
            -DDC/I2C for ATI Radeon support (FB_RADEON_I2C)
            -Support for backlight control (FB_RADEON_BACKLIGHT)[/FONT]
[/SIZE]
The result is, that not only the backlight controls are working, but the system also sleeps/suspends properly. Also fps seems higher on the desktop and window tearing is much reduced.
I did not do any xorg.conf tinkering with this yet, but I think there is still some room for improvement here.


**[SIZE=2]The solution:[/SIZE]**

Compile a new kernel as per the *[SIZE=1]Alternate Build Method: The Old-Fashioned Debian Way[/SIZE]*[SIZE=1] instructions [here]("https://help.ubuntu.com/community/Kernel/Compile#AltBuildMethod") and make sure to use the [/SIZE][FONT=Courier New]make localmodconfig[/FONT][SIZE=1] option.
After this do [FONT=Courier New]make xconfig[/FONT] and make sure the following options are being included:
I have put some options in italics, with those I am unsure if they truly are needed for the iBookG4.


[/SIZE][SIZE=1]Theese options are needed by pbbuttons as specified in the pbbuttons manual:[/SIZE]

[SIZE=1][FONT=Courier New][SIZE=1]-Macintosh Device Driver
    -Backlight control for LCD screens (PMAC_BACKLIGHT)
        -Provide legacy ioctl's on /dev/pmu for the backlight (PMAC_BACKLIGHT_LEGACY)[/SIZE][/FONT]

[/SIZE][SIZE=1]
[/SIZE]Here I had to manually include FB_RADEON option and its subsets, the others had already been enabled. I also took out the FB support for nvidia cards since it would not be needed on this  particular machine.
[SIZE=1]
[FONT=Courier New]-Graphics Support
    -Direct Rendering Manager (XFree86 4.1.0 and higher DRI support) (DRM)
       -ATI Radeon (DRM_RADEON)
    -Support for frame buffer devices (FB)
        -Open Firmware frame buffer device support (FB_OF)
      [I]  -Apple "control" display support (FB_CONTROL)
        -Apple "platinum" display support (FB_PLATINUM)
        -Apple "valkyrie" display support (FB_VALKYRIE)
        -Chips 65550 display support (FB_CT65550)
        -Asiliant (Chips) 69000 display support (FB_ASILIANT)
        [/I]-ATI Radeon display support (FB_RADEON)
            -DDC/I2C for ATI Radeon support (FB_RADEON_I2C)
            -Support for backlight control (FB_RADEON_BACKLIGHT)
[FONT=Arial]
I have attached my .config file for the lazy, but must warn you that this is a work in progress and might even break functionality that I did not yet notice to be broken on my own system[/FONT]
[/FONT]
[/SIZE]

---

### Post by canhoto on 2011-10-25
> **jumil said:**
> 
After installing 11.10 on my iBookG4 basically everything execpt the backlight controls worked out of the box. [SIZE=1]
[/SIZE]

You managed to install it? Didn't you have boot problems after installing it?

---

### Post by rsavage on 2011-10-25
Jumil, this is excellent stuff.  When I finally get around to mending my iBook (I'm stubbornly refusing to pay the silly prices on ebay for spares at the moment) I'm going to definitely try this out!

I've played around with compiling kernels once before.  That was to try and get KMS to work and I didn't really know what I was doing with linux at the time.  I made the mistake first of using the standard ubuntu 'oldconfig' (following the instructions on an iBook tutorial [http://ubuntuforums.org/showthread.php?t=1498559](http://ubuntuforums.org/showthread.php?t=1498559)) and it took hours and hours to compile and failed!  Then I tried following the instructions on the PowerPCFAQ which was a lot quicker, but I always thought there must be a better way.  And I think you've found it with the localmodconfig option!

Some background stuff I've found from kernelnewbies.org:

> To make the process of configuration easier, a new build target has been  added: make localmodconfig. It runs "lsmod" to find all the modules  loaded on the current running system. It will read all the Makefiles to  map which CONFIG enables a module. It will read the Kconfig files to  find the dependencies and selects that may be needed to support a  CONFIG. Finally, it reads the .config file and removes any module "=m"  that is not needed to enable the currently loaded modules. With this  tool, you can strip a distro .config of all the unuseful drivers that  are not needed in our machine, and it will take much less time to build  the kernel. There's an additional "make localyesconfig" target, in case  you don't want to use modules and/or initrds. I notice on your config file that you've got some random stuff that I wouldn't expect on an iBook. Some of these I think could be new kernel options (included since the 11.10 kernel config) that are sucked in by the "make menuconfig/xconfig" command.  I think possibly you could try running "make localmodconfig" followed by "make oldconfig".  This will give you yes/no questions to whether you want to add the new kernel options.  I'm guessing other options maybe brought in erroneously because of the way localmodconfig works.  Or I could have that completely wrong!

It's interesting that in the quote above they mention a "make localyesconfig".  Flicking through your config file earlier I thought you didn't have many =m options.

You are probably seeing an increase in boot speed because of fewer =y options.  I think I've read that the =m modules don't reduce speed unless they are used/loaded.  Again, I could have that wrong.

Do you know if the backlight/suspend works if you include the radeon framebuffer options as =m? Then possibly you wouldn't have to compile the whole kernel, but could add the module to the existing kernel?  I may have that wrong, but there is something called kernel headers that I think is used/involved in this.  

Finally, going back to KMS have you tried enabling this in Oneiric?  I should imagine this or some new kernel thing is now supposed to take care of the backlight. Maybe it doesn't work because pbbuttons has not been updated, but I think I saw something on the debian mailing list that somebody was thinking of updating it?  It's great that people are still prepared to invest time in ppc stuff!

Right I think that's all I had to say.  I just thought I better post to say good job!

---

### Post by rsavage on 2011-10-25
No, I did forget something!  Because it is checking what modules are used maybe it is a good idea to plug in all the usb devices (flash/hard drives, mice, printer etc) that you use while running the "make localmodconfig" command?  Otherwise they may not work.  It's probably a good idea too to double check manually what is enabled in the config file.

---

### Post by rsavage on 2011-10-25
Now I've got my brain in gear I've edited the original post I made.  Hopefully, it makes sense now!

Also, check your ibook fan is working correctly as I think some development has gone on with that module recently.

---

### Post by jumil on 2011-10-25
@canhoto

None at all. I have installed 11.10 by upgrading an 11.04 cmi installation [FONT=Courier New]"do-release-upgrade"[/FONT] and then installing either the Ubuntu or Xubuntu Desktop via the [FONT=Courier New]"tasksel"[/FONT] command.

@rsavage

Thank you.

I have not tried including the radeon framebuffer options as modules yet. Since this was my first try on compiling a kernel I did not really know what I was doing either. Thanks for the suggestion, thats an interesting area to further my learning in.

[Manpage for the current radeon driver]("http://manpages.ubuntu.com/manpages/oneiric/man4/radeon.4.html")

I have thought about trying to enable KMS and seeing how far I'd get with that. I had the same thought about the backlight as you.
There was also the interesting possibilty to use the EXApixmaps option (KMS only) to get EXA to work (it produces garbled colors on window moving and so on at the moment) and maybe even get vsync to work with EXAvsync. Though tearing really is minimal now.

There is another interesting change for the radeon driver that you might want to ad to your tutorial thread.
The DynamicClocks Option has been changed to

       **Option** **"ClockGating"** **"**_boolean_**"**               Enable dynamic clock gating.  This  can  help  reduce  heat  and               increase  battery  life  by  reducing  power  usage.  Some users               report reduced 3D performance with this enabled.  The default is               **off.**And

       **Option** **"DynamicPM"** **"**_boolean_**"**               Enable  dynamic power mode switching.  This can help reduce heat               and increase battery life  by  reducing  power  usage  when  the               system is idle (DPMS active). The default is [B]off.

[/B]has been added.

This explains why DynamicClocks never did anything for me before. With both of these set though the machine runs far quieter and cooler.

Edit:
So yes, the fan is working properly, but it doesn't have a lot to do in 2D Desktop rendering at the moment. Unless the CPU load increases, like when building a kernel ;) I didn"t know it could get that loud.

Also the FBDev Option is not mentioned on the page. Could that be connected to enabling the framebuffer through the Kernel? I don't know if this kernel option is new in 3.0 or not.

Finally it seems to me that localmodconfig does not remove drivers for common peripheral devices since it left in the support for a USB mouse which was not connected while running the command. Flashdrives and a USB hard drive work fine too. It even left in support for PS2 keyboards and all kinds of SCSI and raid devices which I didn't bother to kick out at the time. But I noticed it while checking through the xconfig. Also I didn't (and to some degree still don't) know what I was doing.

Also compiling this stripped down kernel only took the iBook between two and three hours. So it was easily doable over night. I have no idea how long it would struggle on compiling a full sized one.

Not that I have any spares, but may I ask which part of your iBook is broken?

---

### Post by rsavage on 2011-10-26
Have you tried enabling KMS by simply putting radeon.modeset=1 as a yaboot parameter?  KMS doesn't like other framebuffers so that is probably why fb_radeon etc has been omitted from the kernel.  I don't know what is the matter with EXA recently as it worked perfectly in lucid.

Have never tried the dynamic clocks setting, but I had noticed the name change too.  That is why I think it is always a good idea to configure your own xorg.conf since you get all the available settings printed.  One thing I've learnt in linux is there is no substitute for reading the manual.  I'll add it to the radeon tweaks section since you say it makes a difference.

The other big source of heat in the ibook is the hard drive.  You can change the power saving settings of that too.  The hdparm command does it temporarily.  By default there isn't much power saving when on charge so some people like to change this.  However, some people think the default power saving when on battery is too aggressive and spins down the disks too much.  That's because there is a finite number of times you can spin down the disk before it breaks.

Yes the fan can get scarily loud!

FBDev is deprecated I think.  Well that is what it used to tell me on the xorg log in natty.  The fbdev module (I think) would load and then unload with a deprecated message.

I think the PowerPCFAQ method took less time than 2 hours so it maybe worth looking what they enable in a kernel?  I really can't remember though.

Regarding my iBook:  I really need a new base.  I bought it with a logic board problem which I was able to mend easily with a hot soldering iron.  Unfortunately, it didn't last and when I tried the more complex "reflow" method (adding more solder to the joint) I made a right bodge!  You can't imagine how tiny the chip pins are.  I had to get two magnifying glasses lined up to see it!  So I'm not very happy with that, but then I broke the metal frame (you can't imagine how flimsy that is).  To top it off I then dropped my hard drive on the floor.  It's been a disaaahster.  So I've been faffing around trying to decide whether to ditch the ibook and switch to arm embedded.  I think I'm sticking with the ibook for the mo....

---

### Post by jumil on 2011-10-28
I'll have to reinstall tonight it seems.
I experimented with Powerprefs and was able to deduct that most of what pbbuttons currently does, apart from controlling the backlight and the eject key, is getting in the way of the power manager. Resulting in double suspend commands and the like.

Right now however the system has become fiercly unstable and does not usually leave me enough uptime (screen turns black or shows snowy artefacts) to analyse the problem. I asume this is due to some sleep/suspend settings conflict I produced.
Next time I'll back up the config files so I can restore them from a command line.

Well, this way I get to test installing from the current live CD.

---

### Post by rsavage on 2011-10-28
Can you not even boot into single user mode?  That way you could try removing/purging pbbuttonsd and powerprefs before the drastic step of reinstalling?

---

### Post by jumil on 2011-10-28
Right now I actually think its a hardware fault. It is showing the same behavior while running from a live cd. And sometimes doesn't even get through the boot cycle.
Its an old machine that did a lot of work in its time. I wouldn't be surprised if the graphics card or its memory had given in now.
Maybe I'll give it another look tomorrow.

---

### Post by rsavage on 2011-10-28
I think the most common thing to go is the U28 chip which is what happened on mine.  You can test it out by actually pressing down on the chip when running the ibook.  Lots of guides on the internet about shims, but I can't see them working well to be honest.  You are best to try and re-solder.  It's quite easy unless you try and add more solder....
 
If it's the GPU then that's more difficult.....
 
Good luck!

---

