---
title: "Nvidia Drivers question"
date: 2007-03-10
forum: Absolute Beginner Talk
---

### Post by gmc1200 on 2007-03-10
Hey everyone,

I have an nvidia mx440 and i was trying to figure out how to install the drivers for it.  I know my card is a little older so i used the directions [here]("http://www.ubuntuforums.org/showthread.php?t=338526&page=2&highlight=mx440") given by kvonb.  It went through pretty smoothly, but when I open up the settings for the video card, there's nothing there that I can tweak (see attached pic).  

Is there supposed to be things I can adjust in the settings?

The reason why I want to make sure everything is good with the video drivers is because I want to run beryl.  If anyone has this card and is able to run beryl, could you breakdown what I have to do?  Ive been having a lot of trouble getting it working.

Thanks

---

### Post by Perfect Storm on 2007-03-10
[http://ubuntuforums.org/showthread.php?t=272104](http://ubuntuforums.org/showthread.php?t=272104)

---

### Post by gmc1200 on 2007-03-10
Thanks, I'm going to read through that.  But back to my first question, should I be able to have settings with the nvidia driver installed?  It doesnt give me anything to play with in the settings.  I thought this was weird because on a different computer that has an nvidia card, I was able to adjust the settings.  I want to make sure the driver is installed properly before I try to install beryl.

---

### Post by Perfect Storm on 2007-03-10
Which version of drivers do you use? (and which version do you have?)

yours looks a bit sparse, here's one with my GF 6600 GT 256mb with the 9746 nvidia driver.

---

### Post by rusty4r on 2007-03-10
My card runs Beryl and it is older and smaller than yours, GeForce2 MX 400.
I used the Envy script at
[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")
because my old card uses the 96xx drivers or the Legacy drivers but Envy chooses the right one for you.

Then to install Beryl I used the guide here with AIGLX
[http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu]("http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu")

Hope that helps you

---

### Post by gmc1200 on 2007-03-10
Well i followed the directions from that link i put in my original post and it said to use download the NVIDIA-Linux-x86-1.0-9629-pkg1.run drivers.

Also about envy, I tried installing the drivers with that, but the I would get problems when it was installing.  I dont remember what it said exactly, but it was something about building the kernel.  

:mad: damn my newbieness.

---

### Post by Perfect Storm on 2007-03-10
Properly because you need the headers of your kernel to install it.

For edgy:
```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run
sudo /etc/init.d/gdm start
```

---

### Post by gmc1200 on 2007-03-10
> **Artificial Intelligence said:**
> Properly because you need the headers of your kernel to install it.

For edgy:
```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev
sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common
sudo rm /etc/init.d/nvidia-*
sudo /etc/init.d/gdm stop
sudo sh NVIDIA-Linux-x86-1.0-XXXX-pkg1.run
sudo /etc/init.d/gdm start
```

I tried this out, went through without a problem.  I still have the same options with the video settings like before.  Is it possible that the video card doesnt have the ability to be customized?

---

### Post by Perfect Storm on 2007-03-10
I can't answer that one, sorry. But it's a possibility.

---

### Post by getaboat on 2007-03-10
Apologies if  I'm not adding anything to this but........

I've just put on Edgy and Beryl to my development PC and the BIG problem was getting the nvidia drivers installed. I tried lots of threads from here but it was Envy that did the the job BUT only when I realised that it should not be run in terminal from the GUI as it zaps your current nvidia drivers. I ran it directly from the "command line" and voila it worked!  On the strength of Envy I'm upgrading my 64mb graphics card to a 128mb nvdia card.

If I ever go to Italy I'm going to buy that guy a beer.......

---

### Post by gmc1200 on 2007-03-10
I took a look at this link: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX) and it says "nVidia cards require the non-free drivers to be installed, as the default "nv" driver does not support acceleration."  I think my problem when it comes to running beryl is that im running the default "nv" drivers.  How do I use the drivers that let me use the 3d acceleration?

---

### Post by Perfect Storm on 2007-03-10
```
sudo nano /etc/X11/xorg.conf
```

Check section "Device"

If you have installed the nvidia driver and it still says "nv" change it to "nvidia"

save and exit, restart X ctrl + alt + backspace

---

### Post by rusty4r on 2007-03-10
> **gmc1200 said:**
> I took a look at this link: [http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX](http://wiki.beryl-project.org/wiki/Install_Beryl_on_Ubuntu_Edgy_with_AIGLX) and it says "nVidia cards require the non-free drivers to be installed, as the default "nv" driver does not support acceleration."  I think my problem when it comes to running beryl is that im running the default "nv" drivers.  How do I use the drivers that let me use the 3d acceleration?

Yes these instructions only work if your driver problem is solved first.

---

### Post by rusty4r on 2007-03-10
> **getaboat said:**
> Apologies if  I'm not adding anything to this but........

I've just put on Edgy and Beryl to my development PC and the BIG problem was getting the nvidia drivers installed. I tried lots of threads from here but it was Envy that did the the job BUT only when I realised that it should not be run in terminal from the GUI as it zaps your current nvidia drivers. I ran it directly from the "command line" and voila it worked!  On the strength of Envy I'm upgrading my 64mb graphics card to a 128mb nvdia card.

If I ever go to Italy I'm going to buy that guy a beer.......

I think there are a lot of us who would gladly buy him a beer

---

### Post by overdrank on 2007-03-10
Sorry this is off topic but when I saw rusty4r signiture I just died laughing!
Correct Answers = 2 Beans
Answers that are not necessarily correct but sound like you know what you're talking about = 1 Bean
Point Two Pistols at the Staff Members = All the Beans You Want
Great one!:)

---

### Post by gmc1200 on 2007-03-10
ok, i changed the device to nvidia, but then when i restart , the screen is all black.  I have to change it back to nv to fix it.  :confused: :confused: :confused:

---

### Post by rusty4r on 2007-03-10
> **overdrank said:**
> Sorry this is off topic but when I saw rusty4r signiture I just died laughing!
Correct Answers = 2 Beans
Answers that are not necessarily correct but sound like you know what you're talking about = 1 Bean
Point Two Pistols at the Staff Members = All the Beans You Want
Great one!:)

Thank you, it was even funnier when you look at my avatar and when it said "Just give me the beans" next to it

Sorry for the off topic gmc1200

---

### Post by gmc1200 on 2007-03-10
It's no problem.  If anyone that has a mx440, could you let me know what you did to install drivers and get beryl working?

Sincerely,

Frustrated Ubuntu User.

---

### Post by Perfect Storm on 2007-03-11
I just realize....in which class do a mx440 belong? And which driver did you install (normal or legacy)?

---

### Post by rusty4r on 2007-03-11
I'm pretty sure that it would be the same class as mine which is the 96xx driver. Mine is the GeForce2 MX 400.

---

### Post by gmc1200 on 2007-03-11
Ive tried the 96xx and 7xxx drivers.  The thing where I hit a wall is when I try to use the drivers.  Everytime i try to use them, the screen goes black.  Only the nv setting works.

---

### Post by kvonb on 2007-03-11
Hello,

I came running when I heard my name mentioned :)

gmc1200, I would STRONGLY recommend downloading and installing "envy", I've used it now on several machines, and have even installed the Nvidia drivers AND Beryl on remote machines using ssh!

It is extremely well written, and it will install the latest Nvidia drivers, which I believe will support your card, (check at [www.nvidia.com]("http://www.nvidia.com") first).

It looks to me (from your included pic) that you are using the OLD version of the Nvidia config tool, the one that comes with Ubuntu.

In my original instructions, this line should have removed it:

```
 sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common

```However, ENVY will take care of all that old guff for you.

Go to this page and follow the instructions to the letter:

[URL="http://albertomilone.com/nvidia_scripts1.html"]```
http://albertomilone.com/nvidia_scripts1.html
```[/URL]

Good luck :)

---

### Post by Perfect Storm on 2007-03-11
> **rusty4r said:**
> I'm pretty sure that it would be the same class as mine which is the 96xx driver. Mine is the GeForce2 MX 400.

So it's actually the legacy driver he should use.

---

### Post by kvonb on 2007-03-11
No, you can use the standard driver, there is no need to use the legacy driver AI :).

I have a Geforce2-mx/400 in another machine and the standard driver works perfectly, even Beryl works amazingly fast!

---

### Post by gmc1200 on 2007-03-11
Ok, I'm going to do a fresh install and try envy out again.  I'll report back with my results.  But with using all these differnt methods, it screws up when I change the xorg.conf to use "nvidia" rather than "nv"

---

### Post by gmc1200 on 2007-03-11
Ok, I tried again with Envy, and I get this message: "Buld of the package nvidia-kernel-source failed!"  The give me a bunch of options.  Look at the screenshot to see the exact message.  If there's anyhtign else that I could provide that will help diagnose a solution please let me know!

---

### Post by gmc1200 on 2007-03-11
bump

---

### Post by kvonb on 2007-03-12
Select that first option and see if you can post back the major errors it gives.

Which version of envy did you use?  The new one has a graphical interface, just curious as to why you would use the text version?

---

### Post by gmc1200 on 2007-03-12
I was using the latest version of Envy.  When I install it using that first option, it pops up a window that displayed the what you saw in my screenshot.  I'll run envy again when I get home and post up the errors.  Where can I get the error log from?

Thanks for all the help so far everyone.

---

### Post by gmc1200 on 2007-03-12
ok, i completely reinstalled, mustve been the 10th time in 3 days, and i didnt upgrade anything, just got envy installed and ran it.  Envy ran with no problems and i thought everything was good, but when i restarted it booted to a blank screen.  i know it got to the log in screen, because i heard the drum sound.  I did sudo dpkg-reconfigure xserver-xorg to get rid of the blank screen (everytime i reinstall ubuntu i have to do this for some reason).  I selected "nv" rather than "nvidia" because "nvidia" wasnt working.  It would still boot to a blank screen.  I checked to see if the nividia settings menu was there, and it is, but i have nothing to tweak.  it looks exactly like the screen shot in my original post. I really dont know what to do.  Someone please help!!!

---

### Post by kvonb on 2007-03-13
Put the nvidia driver back on, just run "envy" once you are booted up again, then reboot back to your black screen.

Now press <CTRL><ALT><F1>, that should take you to the first virtual terminal.

Is there any text on the screen?  You should see a login prompt.

To get back to your desktop you press <CTRL><ALT><F7>.

Also there should be a hidden file in your home folder named ".xsession-errors", and in /var/log/ there is one called "Xorg.0.log" post those here, maybe they will give us a clue.

Erm, just a thought, what version of Ubuntu are you using?

---

### Post by Slim Odds on 2007-03-13
> **kvonb said:**
> No, you can use the standard driver, there is no need to use the legacy driver AI :).

I have a Geforce2-mx/400 in another machine and the standard driver works perfectly, even Beryl works amazingly fast!

Not according to NVidia's website. Their readme file makes it clear the the GeForce2 MX/MX 400 uses the 96XX driver and not the 97XX driver.

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

---

### Post by gmc1200 on 2007-03-13
> **kvonb said:**
> Put the nvidia driver back on, just run "envy" once you are booted up again, then reboot back to your black screen.

Now press <CTRL><ALT><F1>, that should take you to the first virtual terminal.

Is there any text on the screen?  You should see a login prompt.

To get back to your desktop you press <CTRL><ALT><F7>.

Also there should be a hidden file in your home folder named ".xsession-errors", and in /var/log/ there is one called "Xorg.0.log" post those here, maybe they will give us a clue.

Erm, just a thought, what version of Ubuntu are you using?

I was able to install the driver without a problem the last time I did it, the only thing different is that I didn't install any updates prior to installing the drivers.  

After I installed the drivers, I rebooted and it booted to the blank screen (it was the login screen because I could hear the drums).  I pressed ctrl+alt+f1 and i was able to log into the virtual terminal, but I had to change the drivers back to "nv" from "nvidia" because using "nvidia" kept booting back to the blank screen.  Im not home right now, but when I get back I'll post up those error logs.  Again, thanks for all this help, I really appreciate it!

---

### Post by freerick on 2007-03-13
If Nvidia says to use the 96XX drivers for your card, then my suggestion is to stick with what they suggest. Even if you can get later drivers to work there's no guarantee that they'll be stable. I have a newer Nvidia card, the 6200, and I installed Beryl as well; I finally got everything to work after I installed Nvidia's binary drivers downloaded from their web site. The drivers will automatically compile and install a kernel module for you. Please note that regardless of your card, you can't use GNU drivers that you get from Synaptic if you want to run Beryl / OpenGL, because those drivers to my knowledge have little to no 3D support. You can get the binary drivers from Synaptic, I think, but they probably won't be the right version.

Fortunately, installing the drivers from Nvidia's web site is easy. When you are on the driver download page, you'll have to click on the link to the driver archive to get the 96XX drivers that you need for your card.

You need to shut down your X server and install the drivers from the command line. In your xorg.conf file, make sure the "Drivers" line reads "nvidia" not "nv".
After you install the kernel module from Nvidia's site, your X server might not start. The problem that I found was that it still tries to use the previous kernel module that I had installed from Synaptic, which was a 71XX driver (or 8754, depending on the package), so I had to explicitly disable the kernel module. If you run into this problem, let me know and I'll post the link to the instructions.

Envy helped me get everything working right away as well, but it might not install the right driver version, if you specifically need 96XX. If that's the case, I think your best bet is to try and install the drivers from Nvidia's site.

---

### Post by gmc1200 on 2007-03-13
I was aware that I was supposed to use the 96xx drivers, I thought that envy would automatically install the 96xx drivers.  Im going to post up the log and then i'll try out the method from nvidia's site.  Thanks for chiming in!  The Ubuntu community rocks!  :guitar:

---

### Post by freerick on 2007-03-13
> **gmc1200 said:**
> I was aware that I was supposed to use the 96xx drivers, I thought that envy would automatically install the 96xx drivers.  Im going to post up the log and then i'll try out the method from nvidia's site.  Thanks for chiming in!  The Ubuntu community rocks!  :guitar:
I just used envy and it installed 9746. The latest version from Nvidia is 9755 that was released on March 7th, so you may want to try just running Envy and if that doesn't work, simply downgrade to 96XX. I don't understand why Nvidia doesn't make their drivers backwards compatible, but the repos also have the nvidia legacy package, which I'm guessing is for those cards and below.

---

### Post by gmc1200 on 2007-03-13
> **kvonb said:**
> Put the nvidia driver back on, just run "envy" once you are booted up again, then reboot back to your black screen.

Now press <CTRL><ALT><F1>, that should take you to the first virtual terminal.

Is there any text on the screen?  You should see a login pr```

```ompt.

To get back to your desktop you press <CTRL><ALT><F7>.

Also there should be a hidden file in your home folder named ".xsession-errors", and in /var/log/ there is one called "Xorg.0.log" post those here, maybe they will give us a clue.

Erm, just a thought, what version of Ubuntu are you using?

I can see the login text when i ctr+alt+f1.  Also, I'm using edgy.

Ok, here's the stuff you asked for:


The .xsession-errors

```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "cass"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/ubuntu:/tmp/.ICE-unix/4217
Gnome-Message: gnome_execute_async_with_env_fds: returning -1
evolution-alarm-notify-Message: Setting timeout for 2245 1173830400 1173828155
evolution-alarm-notify-Message:  Tue Mar 13 20:00:00 2007

evolution-alarm-notify-Message:  Tue Mar 13 19:22:35 2007
```

I cant post up the Xorg.0.log because its too long

---

### Post by gmc1200 on 2007-03-13
I just tried changing the x server driver from "nv" to "nvidia" and then pressed ctrl+alt+backspace, but then the screen went to this:

"Failed to start the X server (you graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?"

I say yes

Has a bunch of text, but the most important part i think is:

"FATAL: Module nvidia not found.
(EE) NVIDIA(0): Failed to load the NVIDIA kernel module!
(EE) NVIDIA(0): *** Aborting ***
(EE) Screen(s) found, but none have a usable configuration.

Fatal Server error:
no screens found"

Freerick, if you could let me know what you did to install your drivers, it would be awesome

THanks

---

### Post by kvonb on 2007-03-14
> **Slim Odds said:**
> Not according to NVidia's website. Their readme file makes it clear the the GeForce2 MX/MX 400 uses the 96XX driver and not the 97XX driver.

[http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html](http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/appendix-a.html)

Yes, but have a look at this page which is the "supported cards" list for the 9755 driver:

[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

Fourth from the top is the Geforce2/MX400, as well as several mx440s!

Very odd :)

GMC, I really need to see Xorg.0.log, you can archive it, or just rename it to Xorg.0.log.txt and attach it to the post.

You **DO NOT** need to follow ANY other method of Nvidia driver installation, envy did all the work already.  Doing it the manual way is **NOT** going to achieve anything different, other than teach you what to do  if you want to install a different version.

Also **DO NOT** install ANY nvidia drivers from synaptic, it could mess up your system at this point.

Envy correctly removes all the old stuff when it runs, saving you doing all the messing about.

OK, open a terminal, and type this:

lspci | grep VGA

And post the output here please.  I really need to know exactly which card you have.  A lot of people have problems with the "go" series of cards, as well as the PCI versions and also onboard cards.

---

### Post by freerick on 2007-03-14
> Fatal Server error:
no screens found"

Freerick, if you could let me know what you did to install your drivers, it would be awesome


ok, please post the other information that was included on that screen. You can also get this from /var/log/xorg.log. You can hit ctrl+alt+F1 to get a command prompt btw, in case your X server doesn't start.
Chances are that the version of the kernel module that you have doesn't match the module for the X server. This happened to me when I tried to install the nvidia driver from nvidia's web site even though another kernel module driver was installed from synaptic already. To rule out any version conflict, do the following:

sudo vi /etc/default/linux-restricted-modules

The header part of this file explains what it does: you can prevent pre-existing kernel modules from loading, and it says that you can disable both the nvidia drivers in the kernel with "nv". This is what you want (you don't want to use the existing kernel module, you want to use the one that you just compiled). Add the following to the end of this file:

DISABLED_MODULES="nv"

Save the file and reinstall the kernel module. Make sure that your X server isn't running when you  run the installer script from nvidia's web site. Hit ctrl+alt+F1 to get into a command line.
Type 

sudo /etc/init.d/kdm stop

or, if you're using gnome, type

sudo /etc/init.d/gdm stop

That will kill the X server and any current gnome or kde sessions that you may have open. (in this case this shouldn't be necessary since your X server doesn't start anyway). Execute the .run file (as root) that you downloaded from Nvidia's web site. I downloaded the latest 9755 drivers, so I would recommend you try those first. If they're not compatible with your card, we will see some indication of that once the drivers are installed correctly.

If everything went well so far, the script should now ask you to accept the license. Afterwards, it checks if there are existing drivers. Make a note of which drivers, if any, it finds on your system, so you have a reference in case you need to go back. It will uninstall those drivers and proceed to compile the current drivers for your kernel. There are several error and warning messages that might appear at this stage. The only messages you should be getting are the ones that say that it doesn't have a precompiled kernel module, so it's going to compile one right now. Afterwards, everything goes by itself. At the end, if there are no further warning, it should ask you if you want it to modify your xorg.conf file to use the nvidia drivers; say yes.

If you received any warning or error messages from this script that I haven't mentioned, post them here. I was not able to get the drivers to run until I had taken care of all warnings.

When the script completes, it will drop you back to your shell. Reboot with

sudo shutdown -r now

You need to reboot your entire system, not just the X server, this time, because we compiled a new kernel module (so you have to reload the kernel).

When your system starts back up, it should start the X server properly. You will know that the install you just did succeeded if you see the Nvidia logo when the X server starts. If it does not start, post the output of /var/log/xorg.log here. If it misbehaves, describe the behavior as detailed as possible.

I noticed that there is not much more to installing the nvidia drivers, since nvidia's script does most of the work for you. I was able to do the install as described above even without running envy first. There are a few synaptic packages that you need to have installed in order for this to work, such as linux-kernel-headers. That package is required so that the nvidia installer can compile a new kernel module for you. If you're missing anything else, we'll be able to figure that out based on any warnings from the nvidia script.

---

### Post by gmc1200 on 2007-03-14
Here's the output of lspci | grep VGA

```
01:00.0 VGA compatible controller: nVidia Corporation NV18 [GeForce4 MX 440 AGP 8x] (rev a4)
```

Attached is the Xorg.0.log

I have a file that's called linux-restricted-modules-common and it has the correct settings:

```
# This file is sourced from the linux-restricted-modules-common init
    # script and is used to disable the link-on-boot feature, one module
    # at a time.  This can be useful if you want to use hand-compiled
    # versions of one or more modules, but keep linux-restricted-modules
    # installed on your system, or just to disable modules you don't use
    # and speed up your boot process by a second or two.
    #
    # Use a space-separated list of modules you wish to not have linked
    # on boot.  The following example shows a (condensed) list of all
    # modules shipped in the linux-restricted-modules packages:
    #
    # DISABLED_MODULES="ath_hal fc fglrx ltm nv"
    #
    # Note that disabling "fc" disables all fcdsl drivers, "ltm" disables
    # ltmodem and ltserial, and "nv" disables both the nvidia drivers.
    # You can also name each module individually, if you prefer a subset.
    
    DISABLED_MODULES="nv"

```

No Nvidia splash screen pops up, just the blank screen.  To get back to the gui i have to do the sudo dpkg-reconfigure xserver-xorg and set the the x server drivers to "nv"

Also, there wasn't any xorg.log file in that folder.  It's not even hidden...why does linux hate me...

---

### Post by kvonb on 2007-03-14
The Xorg.0.log you posted shows that you are using the "nv" driver, which makes no sense because the darn thing is blacklisted :confused:.

Anyway, if you ran "envy" everything will have been setup correctly.  When it asked you if it should update xorg.conf did you say yes or no?

Other than following freerick's instruction on installing the LATEST driver, all I can suggest is looking in your computers CMOS (usually press DEL or a function key to get in there) just as the computer comes on, and check the Video card settings.

Make sure you set it to AGP 8x, 128 meg memory aperture, and toggle the VGA interrupt, ie if it is assigned one, then un-assign and vise/versa.

Also if you have an onboard video card as well, make sure it is disabled.

Other than that, all I have left is to suggest trying to borrow an nvidia card from a friend just to see if it works on your system,

Regards, Kev :)

---

### Post by gmc1200 on 2007-03-15
When it asked me to update the xorg.conf, I said yes.  

Is the CMOS the same thing as the BIOS?

Also, how do I check if the computer has an onboard video card?  I looked at it, and there isn't any other VGA outputs on the back.

I'm going to try freericks method next if this all goes to hell.

It's really baffling why this won't work!

---

### Post by gmc1200 on 2007-03-15
> **kvonb said:**
> The Xorg.0.log you posted shows that you are using the "nv" driver, which makes no sense because the darn thing is blacklisted :confused:.

Anyway, if you ran "envy" everything will have been setup correctly.  When it asked you if it should update xorg.conf did you say yes or no?

Other than following freerick's instruction on installing the LATEST driver, all I can suggest is looking in your computers CMOS (usually press DEL or a function key to get in there) just as the computer comes on, and check the Video card settings.

Make sure you set it to AGP 8x, 128 meg memory aperture, and toggle the VGA interrupt, ie if it is assigned one, then un-assign and vise/versa.

Also if you have an onboard video card as well, make sure it is disabled.

Other than that, all I have left is to suggest trying to borrow an nvidia card from a friend just to see if it works on your system,

Regards, Kev :)

Ok, I had another nvidia card in a different PC i had around, its a Geforce2 mx400.  I used envy to install the driver and it went fine, no errors or anything.  I let it update the xorg.conf and rebooted and guess what happened...blank freakin' screen.  I think something is up with my computer itself thats preventing this from happening.  Im going to try a different computer and see if it works.

---

### Post by steve101101 on 2007-03-16
I got it to work but im at school right now. when i get home ill send you some instructions on how i did it.

---

### Post by steve101101 on 2007-03-16
I installed the 96.31 nvidia driver downloaded from [www.nvidia.com](www.nvidia.com) after installing and booting into beryl the x session would not start (*****YOU MUST USE THIS DRIVE*******). to fix this i went into the failsafe terminal and editing the following file with this command...

```
 sudo nano /etc/default/linux-restricted-modules-common 
```

In this file look for the line....

```
DISABLED_MODULES=""
```

and change to ...

```
DISABLED_MODULES="nv"
```

then reboot. now it should boot into Ubuntu and beryl without any errors.

---

### Post by steve101101 on 2007-03-16
Just send me a PM if any more problems arise.

---

### Post by Griffiss on 2007-03-16
gmc,

I have an nvidia GeForce2 mx/mx400 on Edgy.

I had a good look around at the various methods given on the forums for installing the drivers and found a very simple solution. I'm new to ubuntu myself so don't know if this will help, especially given the changes you've made so far, but all I needed to do was:```
sudo aptitude update
sudo aptitude install nvidia-glx
sudo nvidia-xconfig
```
and that seems to have done the trick. Maybe someone more experienced can tell you whether this method is in/applicable for your system at this time...

Griff

---

### Post by gmc1200 on 2007-03-19
Ok, here I going to document every step I do installing the drivers.

I completely reinstall ubuntu 6.10 using the alternative cd.  It installs without a hitch, but when it finally boots up after the install, it comes to a blanks screen.  

I experienced this everytime I installed Ubuntu and all I do is do ctrl+alt+f1 and then

```
sudo dpkg-reconfigure xserver-xorg
```

I use the "nv" drivers because that's the only one that will work and the rest of the options I use the default settings

Then I restart x

```
sudo /etc/init.d/gdm restart
```

Then the login screen appears.  I login and open the software sources and enable the universe repos in addition to the default repos.  I then proceed to update my system.

It needs to be restarted, so that's what I do.  When it boots back up there are two other things that need to be installed:

linux-headers-generic and linux-image-generic: 2.6.17.10 to 2.6.17.11

I install those and have to restart again.

Now im going to install the driver using the nvidia script. It's version 9631.  I used the instructions at [http://doc.gwos.org/index.php/BerylOnEdgy#Option_2:](http://doc.gwos.org/index.php/BerylOnEdgy#Option_2:)

```
sudo apt-get install linux-headers-`uname -r` build-essential gcc gcc-3.4 xserver-xorg-dev sudo apt-get --purge remove nvidia-glx nvidia-settings nvidia-kernel-common sudo rm /etc/init.d/nvidia-* sudo /etc/init.d/gdm stop
```

When installing the driver using the nvidia script I did the following:

It said "No precompiled kernel interface was found to match your kernel; would you like the installer to attempt to download a kernel interface for your kernel from the NVIDIA ftp site?
I said yes

Then this message appeared, "No matching precompiled kernel interface was foung on the ftp site; this means that the installer will need to compile a kernel interface for your kernel"

I said ok

It was builfing the kernel module, search for conflicting x and open gl files and so on.

Then it said "would you like to run the nvidia-xconfig utility to automatically update your x configuration file so that the nvidia x driver will be used when you restart x?  Any preexisting x configuration file will be backed up."

I said yes

THen it said "your x configuration file has been successgully updated. Installation fo the nvidia accelerated graphics driver for linux-x86 version 1.0-9631 is now complete"

Then i said ok

Then I did:

```
sudo nvidia-xconfig --add-argb-glx-visuals 
sudo /etc/init.d/gdm start
```

Then i restarted

Did it work? No. Damn.  It booted to a blank screen.  The only way I could get the gui back is if i do 

```
sudo dpkg-reconfigure xserver-xorg
```

and use te "nv" drivers.

---

### Post by freerick on 2007-03-20
> **gmc1200 said:**
> Ok, here I going to document every step I do installing the drivers.

[...]

Did it work? No. Damn.  It booted to a blank screen.  The only way I could get the gui back is if i do 

```
sudo dpkg-reconfigure xserver-xorg
```

and use te "nv" drivers.


Sorry I've been away from the forum for a couple of days.

Ok, it looks like you followed the correct procedure when you installed your drivers from nvidia (same as what worked for me). There weren't any error messages or warnings when the .run script compiled your kernel module, etc. If I read your posts correctly everything worked fine when you used a different card. I also came across the black screen problem and it turned out that my modes were set incorrectly (this means that the resolution or refresh rate is incompatible with your video card or with your monitor). First, pull up the specs for your video card and for your monitor and find a mode that works for both, for example 1280x1024 @ 60hz. That should work for most configurations. You also need to figure out the VSync and HSync rates (in Hz) for your monitor. You can find this info on the back of the monitor or on the manufacturer's web site.

Normal video cards, monitors and graphics drivers have a way of communicating with each other to determine the appropriate mode, so the user doesn't get a blank screen (this feature is called EDID). However, in some situations, support for EDID doesn't work (or is disabled in xorg.conf), so the system can't correctly determine what resolution it should set your monitor to after it boots and you get the black screen problem.

**After you figure out what mode(s) your configuration supports, follow the instructions at [http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-j.html](http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8178/README/appendix-j.html) to edit your xorg.conf file to enter the correct modes.** If you follow that link, also go back to the index of that manual and read other relevant sections, such as the troubleshooting section, as nvidia has posted a lot of useful information for getting their drivers to work on linux, including a description of all xorg.conf options. Note that you will most likely have to edit your xorg.conf file by hitting ctrl+alt+F1 and using the command line after you boot.

If you have trouble, try setting your mode to something low, such as 800x600 @60Hz, but you should be ok even at a normal resolution, such as 1280x1024. What you can also do is use the modes that are generated automatically in the xorg.conf file by 
```

sudo dpkg-reconfigure xserver-xorg

```
since you know that those modes work. Don't forget to also set the HSync and VSync values for your monitor (the instructions above also explain how to do this).

If the above doesn't work, post the end of your /var/log/xorg.log file; from there we will be able to see what the problem is. (also describe in greater detail what exactly happens when you boot the computer).

Good luck.
 :popcorn:

---

### Post by gmc1200 on 2007-03-20
Holy crap. freerick.  i freaking love you.  You dont even know how happy i am!!!$@#$%#@$%!  GUI!!!! YES!  Setting the resolution and syncs did the trick, although its a really crappy resolution right now, but im just glad i could see the damn desktop again.  I know im using the drivers now because now i have a load of settings i could mess with for the nvidia drivers so Im going to try to get the correct resolution going.  Gonna go mess around with my computer.  I'll probably have more questions.  

Again...THANK YOU EVERYONE for helping, espcially freerick.  The ubuntu community is seriously the best!

---

### Post by freerick on 2007-03-20
> **gmc1200 said:**
> Holy crap. freerick.  i freaking love you.  You dont even know how happy i am!!!$@#$%#@$%!  GUI!!!! YES!  Setting the resolution and syncs did the trick, although its a really crappy resolution right now, but im just glad i could see the damn desktop again.  I know im using the drivers now because now i have a load of settings i could mess with for the nvidia drivers so Im going to try to get the correct resolution going.  Gonna go mess around with my computer.  I'll probably have more questions.  

Again...THANK YOU EVERYONE for helping, espcially freerick.  The ubuntu community is seriously the best!

No problem, I worked on it for two days almost cause I tried to get beryl to work (and I did, finally) but I can't use it with my three screens, so I went back to my regular desktop. I figured someone else can use what I figured out cause I had to spend a lot of time on it. I'm glad you got it to work, let me know how it plays out.

Here is my three-screen setup although not all screens are on in this picture:


[URL="http://inmyholyopinion.com"]
[IMG]http://inmyholyopinion.com/images/scanner-triple-screen-sm.jpg[/IMG][/URL]
:popcorn:

---

### Post by freerick on 2007-05-29
A quick update: after installing the latest updates for the linux kernel modules packages, my nvidia drivers broke. I was able to start ok, by I was not able to get into KDM / Gnome because the screen would just stay black.

If you're experiencing this problem, don't panic. I'm not sure what caused it, but this is easily fixed by reinstalling the nvidia drivers using the binary package that they provide on their web site. See my previous post for instructions on how to install it.

After I reinstalled the drivers (same version, 9755) KDM was starting up ok. Just wanted to give everyone a heads up.

:popcorn:

---

### Post by Vitalhb on 2007-08-15
Hello,

How can I run Ubuntu in command line mode?
I am trying to install the nvidia drivers and I  think this will be necessary.

thanks in advance!

---

### Post by freerick on 2008-03-30
Vitalhb, you can start up into your normal desktop, then log out and switch to a console using ctrl+alt+F1. Then log in at the command prompt and type 

**sudo /etc/init.d/gdm stop**

or for Kubuntu

**sudo /etc/init.d/kdm stop**


That should stop the display manager and allow you to install the drivers.

---

