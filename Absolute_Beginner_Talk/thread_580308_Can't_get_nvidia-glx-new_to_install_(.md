---
title: "Can't get nvidia-glx-new to install :("
date: 2007-10-18
forum: Absolute Beginner Talk
---

### Post by moerl on 2007-10-18
My problem is pretty much identical to what's described here: [http://ubuntuforums.org/showthread.php?t=574847](http://ubuntuforums.org/showthread.php?t=574847)

I also looked at the following:
[http://ubuntuforums.org/showthread.php?t=209106](http://ubuntuforums.org/showthread.php?t=209106)
[http://ubuntuforums.org/showthread.php?t=60591](http://ubuntuforums.org/showthread.php?t=60591)
[http://ubuntuforums.org/showthread.php?t=574847](http://ubuntuforums.org/showthread.php?t=574847)
[http://ubuntuforums.org/showthread.php?t=393857](http://ubuntuforums.org/showthread.php?t=393857)

They're all similar, but as I said, the first link is closest to what's happening here. During setup, I had the "scanning mirror" hang problem, so I simply unplugged my ethernet cord and restarted setup. This time it finished quite quickly, and of course I got this error message/warning during setup as a result:

"The security updates on security.ubuntu.com couldn't be accessed, so those updates will not be made available to you at this time. You should investigate this later.

Commented out entries for security.ubuntu.com have been added to the /etc/apt/sources.list file."

I have an Nvidia 8800GTS card and want to install nvidia-glx-new so I can get compiz fusion to work and so I can have, in general, 3d acceleration functioning (and I suppose 2d acceleration as well).

I tried the steps from the first link I mentioned but got stuck with the "sudo password" command, which at first did offer me an option that appeared to ask for a password, so I typed one in, but once I did I got "password command not found" or something of that nature.

This isn't quite as smooth as I had hoped or expected :/

I tried installing Flash both via Firefox and via add/remove as well, and that's not working either. Some two translation related files always fail to download/install and I'm forced to cancel, but that's a whole different problem..

---

### Post by Vandread on 2007-10-18
Im getting the same exact problem. Ugh this is a huge headache I thought I would be able to come home and install it and be done.

---

### Post by 001100 on 2007-10-18
wow i am having the same problem and then i can even update anything.  I think I should have wated at leace a week untill I switched now im back in 7.04 and the downloads are dead slow but if i download from anyother website it is fast around/above 300kb/s i think ubuntu is have some problems

---

### Post by maxxym on 2007-10-18
Guys, I am currently working on this as well...I guess you all want to turn on your Desktop Effects huh? hehehe

Did you try:

System>Administration>software sources and made sure every source is checked? 

I was getting error message when I tried to enable my Nvidia Proprietary drivers:

"The software source for the package nvidia-glx is not enabled"

I checked my software sources and made sure they are all checked and now, it's trying to download package file when I tried to enable my Nvidia 3d stuff.. we'll see if it gets there but it's further than I got before.....

---

### Post by maxxym on 2007-10-18
Update:

The download finally kicked in, so make sure you have your software sources checked!!!

i will let you know how far I get..stand by :)

---

### Post by 001100 on 2007-10-18
yes it will work but its like everything i busy maybe we need to try downloading/updating in the next 48hrs. the ubuntu servers might be buzy?

---

### Post by maxxym on 2007-10-18
Well the drivers downloaded and installed....and I was able to enable Nvidia Proprietary drivers...I went to turn on desktop effects and it WORKS!!! WOOHOOO!!!!!!

Good lord.. I love this OS!!!! It runs soooo smooth on my slow desktoP!!!!

---

### Post by Vandread on 2007-10-18
Yes I made sure everything was checked and it basically just sits there downloading 27 out of 47. Also when I go to add/remove programs to install amarok or vmware it tells me that the vendor does not support amd64?? Weird because its working on my desktop which has 7.04. I did not know it would be this hectic just to upgrade.

All day at work I couldnt wait to run home and see the features all these sites were speaking of and BAM roadblock. I guess I will just wait a few days until this is all cleared up.

---

### Post by maxxym on 2007-10-18
> **001100 said:**
> yes it will work but its like everything i busy maybe we need to try downloading/updating in the next 48hrs. the ubuntu servers might be buzy?

It didn't take that long for me... it was waiting for about 3 minutes and then it started the download...just be patient :)

I am all set now....:)

Now if I could only figure out the way to install Office 2003 via crossover for ..uuhhhh free...

---

### Post by RomeReactor on 2007-10-18
Hi. moerl, in the first thread you posted, the command is **sudo passwd**, not **sudo password**.

Regarding the availability of the nvidia-glx-new drivers, open Syanptic (System->Administration->Synaptic), there go to "Settings->Repositories" and check all the boxes (optionally, you can uncheck the box for the CD-ROM below). Close that window and, still in Synaptic, press the blue "Reload" button. After it finishes updating the repository information, nvidia-glx-new should be available for installation. An easy way to install it is to go to "System->Administration->Restricted Drivers" and check the case for the nVidia card.

EDIT: wow, too slow. And yes, the servers are getting hammered now, so you'll probably should wait a while.

---

### Post by moerl on 2007-10-18
Thanks for all your posts guys! Finally I have hope :)
Sadly, the combo of a BIOS update last night, a sort of failed PC-BSD install and then an Ubuntu installation today seem to have made my 8800GTS. Suddenly, the drivers are not recognized anymore in Windows Vista and are listed in the device manager under "other devices" with the following title: "Video Controller (VGA Compatible)".

I've tried uninstalling the drivers in Vista, rebooting into safe mode, cleaning everything out with DriverCleaner.NET, then rebooting into normal and reinstalling, and for some strange reason Vista just won't recognize my card anymore.

Very weird.. and very sucky. I'll see if I can at least get Ubuntu to work properly now, and then I'll have to deal with Vista :/

Thanks a lot, RomeReactor, for clearing up the confusion! With this advice, I should get somewhere :)

I'll keep you posted.

---

### Post by moerl on 2007-10-19
The Windows problem is fixed. Looks like the latest driver release from NVidia has a serious bug in its installation procedure somewhere that is triggered only if some conditions are met.. I installed the latest beta driver and it worked beautifully.

Everything in Ubuntu is working perfectly as well. I can't figure out how to use the desktop cube.. (how to even trigger it) effect, but other than that everything is running smoothly!

Thanks for everyone's help.

---

### Post by RomeReactor on 2007-10-19
moerl, to enable the cube [look here]("http://ubuntuforums.org/showpost.php?p=3564117&postcount=2"). After you've installed compizconfig-settings-manager, disable **Desktop Wall** and enable **Desktop Cube** and **Rotate Cube**. Also you would probably want to increase the number of workspaces to four; for that, right-click on the workspace switcher , go into "Preferences", and increase the number of columns.

---

### Post by moerl on 2007-10-20
Thanks! I actually already had the cube enabled.. (I was able to install compizconifg-settings-manager via Synaptic) and I had a chance to look through the advanced settings for desktop effects. There's a ton of stuff in there!
I also noticed that as you enable things in the settings, the system will actually tell you what provides the same functionality and prompt you to disable any superfluous enabled elements. Pretty clever.

What I was wondering is how to actually initiate the desktop cube.. some of the effects have standard keyboard shortcuts already assigned. Others don't seem to have anything like it--like Desktop Cube. How do I actually USE it?

Aside from that, everything works beautifully. Thanks again!

---

### Post by sayuki288 on 2007-10-20
try using envy :)

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

---

### Post by chips24 on 2007-10-20
it keeps on telling me to restart the computer when i have a new graphics card grahhhhhh

---

### Post by Cariboo1938 on 2007-10-20
> **moerl said:**
> .......a BIOS update last night, ........Can you please give some details how to do that?:confused:

Edit:
I had to edit /boot/grub/menu.lst:

1) Find this section and add "iommu=noaperture":
Quote:
## ## Start Default Options ##
## default kernel options
## default kernel options for automagic boot options
## If you want special options for specific kernels use kopt_x_y_z
## where x.y.z is kernel version. Minor versions can be omitted.
## e.g. kopt=root=/dev/hda1 ro
## kopt_2_6_8=root=/dev/hdc1 ro
## kopt_2_6_8_2_686=root=/dev/hdc2 ro
# kopt=root=UUID=e4af70f0-d555-49ab-8dd0-687cc3e7f81c ro [COLOR="Magenta"] iommu=noaperture
[/COLOR]
2) Save the file and type:
Code: "sudo update-grub"

and then
3) restart my computer!

BTW:
There must be a conflict between my BIOS (Phoenix Award Ga -K8NS Ultra-939 F5) and the kernel so that AGP aperture is not reported correctly. 
It works right now with the nvidia-glx-new driver but sooner or later I have to figure out how to upgrade the BIOS.

---

### Post by RomeReactor on 2007-10-20
> **moerl said:**
> What I was wondering is how to actually initiate the desktop cube.. some of the effects have standard keyboard shortcuts already assigned. Others don't seem to have anything like it--like Desktop Cube. How do I actually USE it?

If you have a wheel mouse, you can 'scroll' between workspaces and see the cube rotating--just remember to increase the number of workspaces to four for a 'true' cube. Otherwise, press and hold CTRL+ALT, then left-click (and hold) anywhere on the desktop (not on an application); now move your mouse to either left or right. To switch workspaces through the keyboard shortcuts, press CTRL+ALT+LEFT arrow, or CTRL+ALT+RIGHT arrow. With the cube enabled, you should see it flip every time you switch from one workspace to another.

---

### Post by Raj_Dharwad on 2007-10-24
Hi Guys,

thanks it actually helped me also get my cube to work, all i had to do is increase the number of desktops to 4, under general options.

Regards,

Raj

---

