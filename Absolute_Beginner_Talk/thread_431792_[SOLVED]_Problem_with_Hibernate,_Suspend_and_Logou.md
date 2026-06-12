---
title: "[SOLVED] Problem with Hibernate, Suspend and Logout"
date: 2007-05-03
forum: Absolute Beginner Talk
---

### Post by Inxsible on 2007-05-03
I have Feisty installed and when I click on the 'Quit' button, it shows me a nice window of all the different 'shutdown' options.

However, apart from 'Restart' and 'Shutdown' the other functions like 'Hibernate', 'Log Out' and 'Suspend' do not seem to work.

When I click 'Hibernate', my machine does shutdown, but if i press the power button, nothing happens. This may be only because some other key is assigned to the job. If so, how do i find out which one it is. I tried the power button because thats how it is in Windows.

For the 'Log Out' and 'Suspend' options, my screen becomes unusable as in, the mouse moves but I cant click on anything. Not even right clicks. Then I have to restart X (ctrl+alt+Backspace) and then shutdown or do whatever.


As a side note: Whenever I restart X, the icons in the top panel go haywire, as in if i had Beryl running and opera, the wireless monitor, the quit button and even the time and date all change positions for some reason. Some icons will disappear altogether and its a pain to not find Wireless Monitor - especially if my wireless drops.
Is there a fix to this? I know its just a quirk...but I'd like it to stay where the icons are supposed to.


Thanks

---

### Post by rsambuca on 2007-05-03
Do you have the nvidia drivers installed?  Both suspend and Hibernate don't work very well with the nvidia drivers.

---

### Post by Inxsible on 2007-05-03
> **rsambuca said:**
> Do you have the nvidia drivers installed?  Both suspend and Hibernate don't work very well with the nvidia drivers.

Yes, as a matter of fact I do have the restricted NVidia Drivers installed. So is there no solution then ?

---

### Post by Inxsible on 2007-05-03
bump. Anyone?

---

### Post by swatF1RESTORM on 2007-05-03
I'm also having the same problem. I've probably had both the NVIDIA and ATI drivers loaded at one point. Now I have the ATI driver installed and enabled my video card by going to system->administration->restricted drivers manager and clicking the check box.

Still can't hibernate, log out, or suspend though. I wish I could offer more help but I am new to Ubuntu (from Windows) so I'm kinda in the same boat. Just thought I would post here and let it be known that I am having similar issues with the ATI drivers installed.

---

### Post by dachinster on 2007-05-05
i also have the restricted nvidia drivers installed and when i hibernate, i see a bunch of text on the screen saying failure to do this and that and then it powers off

when i power it back on, it boots up to the ubuntu progress bar and then loads a nice black screen, whereby i gleefully have to perform a hard reset

---

### Post by dachinster on 2007-05-07
any workaround as yet guys?
do i have to uncheck nvidia drivers in order to hibernate?

---

### Post by Talon2 on 2007-05-08
> **Inxsible said:**
> Yes, as a matter of fact I do have the restricted NVidia Drivers installed. So is there no solution then ?

Not that I have found.

---

### Post by yfarjoun on 2007-05-09
I was having problems with suspend and hibernate. After unchecking all the boxes in "Restricted Drivers" suspend works great! (super fast too!) Hibernate "wakes up" immediately...so I need to do more research....

Hope this helps someone.

Y

---

### Post by mbradlcu on 2007-05-10
here's the fix that worked for me, add the following in the /etc/X11/xorg.conf:
Section "Device"
    Identifier  "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
    Driver      "nvidia"
    Busid       "PCI:1:0:0"
    Option      "NvAgp"     "1"  #here's the line of intrest

for the nvidia readme it's supposed to load the nvidia agp, but dmesg says theyre's a problem and it doens't get loaded so I guess you could set the Option to "0".. you can check the state with 'cat /proc/drivers/nvidia/agp/status'  it should say "disabled",, note there's a slight performance hit.. the nvidia readme also said the kernel's agpgart needs to be disabled for it to load,, but I tried adding agp=off at the grub prompt,, but no love.. anyway suspend works on my laptop

---

### Post by kornelix on 2007-05-10
I have a desktop system with an Intel D975XBX motherboard 
and nVidia graphics card. I have gotten suspend/resume to
work for the first time with Ubuntu 7.04. 

There seems to be no documentation on how to do this
(except for some outdated stuff that does not work).
After searching around and trying various things, I
got the following combination to work:

file  /etc/default/acpi-support

    ACPI_SLEEP=true        
    ACPI_SLEEP_MODE=standby
    MODULES="agpgart"        
    SAVE_VBE_STATE=false        
    POST_VIDEO=false        
    USE_DPMS=false        


file  /etc/X11/xorg.conf            

   Section "Device"
       Driver        "nvidia"
       ...
       Option      "NvAGP"  "1"
   EndSection
   

This black magic works for me, and hopefully for some
other folks out there in Ubuntu land. I will watch this
space in hopes someone more informed will elucidate more.

I have another PC with an MSI motherboard that worked
on the first try with default everything.

---

### Post by JesterGr on 2007-05-10
i have the same problem with ati open source drivers. it's not an nVidia-only problem, or restricted-drivers-only

---

### Post by Inxsible on 2007-05-10
> **mbradlcu said:**
> here's the fix that worked for me, add the following in the /etc/X11/xorg.conf:
Section "Device"
Identifier "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
Driver "nvidia"
Busid "PCI:1:0:0"
Option "NvAgp" "1" #here's the line of intrest
 
for the nvidia readme it's supposed to load the nvidia agp, but dmesg says theyre's a problem and it doens't get loaded so I guess you could set the Option to "0".. you can check the state with 'cat /proc/drivers/nvidia/agp/status' it should say "disabled",, note there's a slight performance hit.. the nvidia readme also said the kernel's agpgart needs to be disabled for it to load,, but I tried adding agp=off at the grub prompt,, but no love.. anyway suspend works on my laptop
 
So are you saying that, after doing so we will NOT be using the NVidia card to its fullest extent?
If so, then I'd rather no do this because I can live with Hibernate and Logout not working rather than take a performance hit on my graphics !!
 
I paid extra for the graphics processor... I had better put the money to good use !

---

### Post by yaidiot! on 2007-05-10
@inxs,

mbradlcu's tip will allow you to continue to use the closed driver. -- I just got mine working recently. Attached are my full /etc/X11/xorg.conf and /etc/default/acpi-support. 

BTW, I'm using the "nvidia-glx-new" package (driver 1.0.9755). Note my config is for dual-X, no compiz/beryl.

Good luck!

-id

EDIT -- one error -- "AddARGBGLXVisuals" should be commented out or set to false. This is the culprit preventing the nvidia driver from properly suspending.

---

### Post by dlugidll on 2007-05-11
maby µswsusp will be work 
[http://suspend.sourceforge.net/index.shtml](http://suspend.sourceforge.net/index.shtml)
i use **s2ram -f **and **s2disk**
works fine for mee


**sudo apt-get install uswsusp**
pls copy text from this site
[http://ubuntu.zamber.net/hibernacja/...ibernate-linux](http://ubuntu.zamber.net/hibernacja/...ibernate-linux)
and save as file
hal-system-power-hibernate-linux

copy text from this site
[http://ubuntu.zamber.net/hibernacja/...-suspend-linux](http://ubuntu.zamber.net/hibernacja/...-suspend-linux)
and save as file
hal-system-power-suspend-linux

then
sudo cp hal-system-* /usr/lib/hal/scripts/linux/
sudo chmod 755 /usr/lib/hal/scripts/linux/*

i need change line 84 in file
/usr/lib/hal/scripts/linux/hal-system-power-suspend-linux
from /sbin/s2ram to /sbin/s2ram -f

works fine for me
on this site you can find few special steps for machine with NVidia card and ATI
[http://en.opensuse.org/S2ram](http://en.opensuse.org/S2ram)


works for mee bether, then after install Kubuntu 7.04 and 6.10

i copy this instruction from
[http://zamber.net/hibernacja-pod-ubuntu](http://zamber.net/hibernacja-pod-ubuntu)

---

### Post by Inxsible on 2007-05-11
> **yaidiot! said:**
> @inxs,

mbradlcu's tip will allow you to continue to use the closed driver. -- I just got mine working recently. Attached are my full /etc/X11/xorg.conf and /etc/default/acpi-support. 

BTW, I'm using the "nvidia-glx-new" package (driver 1.0.9755). Note my config is for dual-X, no compiz/beryl.

Good luck!

-id

Unfortunately, I do have Beryl....and I love it too !!

---

### Post by darmot7 on 2007-05-14
> **mbradlcu said:**
> here's the fix that worked for me, add the following in the /etc/X11/xorg.conf:
Section "Device"
    Identifier  "nVidia Corporation NV17 [GeForce4 420 Go 32M]"
    Driver      "nvidia"
    Busid       "PCI:1:0:0"
    Option      "NvAgp"     "1"  #here's the line of intrest

for the nvidia readme it's supposed to load the nvidia agp, but dmesg says theyre's a problem and it doens't get loaded so I guess you could set the Option to "0".. you can check the state with 'cat /proc/drivers/nvidia/agp/status'  it should say "disabled",, note there's a slight performance hit.. the nvidia readme also said the kernel's agpgart needs to be disabled for it to load,, but I tried adding agp=off at the grub prompt,, but no love.. anyway suspend works on my laptop

awesome this worked for me, suspend now works. 

im using a desktop with a 'nVidia Corporation NV44A [GeForce 6200]' running 7.04 and before when i was returning from suspend it would yield a blank screen.

edit: nm answered my own question. :)

---

### Post by Immolatus on 2007-05-15
hi all,

I've been watching this subject in two threads (this and another) maybe it would help to see the other one: [http://ubuntuforums.org/showthread.php?t=419404](http://ubuntuforums.org/showthread.php?t=419404)

also you might want to check this out: [http://www.suspend2.net/downloads/](http://www.suspend2.net/downloads/)

---

