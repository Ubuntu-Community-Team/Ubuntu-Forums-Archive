---
title: "Funky colors at usplash screen [ibook g3]"
date: 2009-10-22
forum: Apple Hardware Users
---

### Post by candyiz4kidz on 2009-10-22
I've been trying to figure out this problem for about 2 weeks or so, but I've run out of ideas and I'm hoping someone can think of something I haven't thought of....


When booting the Ubuntu loading screen (usplash/bootsplash) is all funky coloured, the blacks are green, the orange black, reds white etc etc. I was thinking maybe the usplash/bootscreen was corrupted, so I installed a different usplash, to no avail. I've played with a lot of settings, only to end up setting them back to the defaults so I can ask someone else what I REALLY should be doing to fix this. 

My thoughts are that the module for the graphics card isn't loaded at the beginning of the boot, and i'm not too sure about what the graphics module name is or how to get it to load with the kernel at boot.

Once the ibook reaches the ubuntu login screen, the colours are fixed, and inside ubuntu everything works great. The graphics card in this ibook is a ATI Radeon Mobility M7 (7500), or at least thats what Ubuntu tells me, although I could have sworn it was an ATI Rage or something.

If anyone has any ideas, don't be shy. As I mentioned before this is something I've been trying to fix for a few weeks and it would be so nice to have a fully 100% working ubuntu ibook. 

HELP!!!!!!!

---

### Post by Dodeca on 2009-10-22
I also have a odd color usplash screen but at pc power down ( boot usplash is perfect colors )

So I will be watching here for this answer ... thx

---

### Post by anubhavrocks on 2009-10-22
Is this the bug
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/365246](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/365246)

---

### Post by candyiz4kidz on 2009-10-22
> **Dodeca said:**
> I also have a odd color usplash screen but at pc power down ( boot usplash is perfect colors )

So I will be watching here for this answer ... thx

My shutdown is also a bit messed up, but not funky coloured, it's just black and white.


> **anubhavrocks said:**
> Is this the bug
[https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/365246](https://bugs.launchpad.net/ubuntu/+source/usplash/+bug/365246)


That's pretty darn close, only difference is that's for nvidia cards. They even used the term "funky" when describing the colours.




How would one go about loading the graphics module at the same time as the kernel? 
I just ran the "system testing" function from the system>administration> menu and near the bottom of the report I noticed it didn't say that the graphics were loading with the kernel, which would explain the issue, no?



[FROM SYSTEM TESTING REPORT]


**/etc/modules**

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

snd_powermac
apm_emu
sbp2
snd-powermac
therm_windtunnel

---

### Post by candyiz4kidz on 2009-10-22
[ALSO FROM TESTING REPORT]


** Radeon Mobility M7 LW [Radeon Mobility 7500] **

PropertyValueinfo.subsystem pci 
info.product Radeon Mobility M7 LW [Radeon Mobility 7500] 
info.udi /org/freedesktop/Hal/devices/pci_1002_4c57 
info.vendor ATI Technologies Inc 
info.parent /org/freedesktop/Hal/devices/computer 
pci.product Radeon Mobility M7 LW [Radeon Mobility 7500] 
pci.vendor_id 4098 pci.vendor ATI Technologies Inc 
pci.product_id 19543 pci.device_protocol 0 
pci.subsys_vendor ATI Technologies Inc 
pci.device_subclass 0 pci.subsys_vendor_id 4098 
pci.device_class 3 pci.subsys_product_id 19543 
pci.linux.sysfs_path /sys/devices/pci0000:00/0000:00:10.0 
linux.hotplug_type 2 linux.subsystem 
pci linux.sysfs_path /sys/devices/pci0000:00/0000:00:10.0

---

### Post by candyiz4kidz on 2009-10-22
[MORE FROM TESTING REPORT]



** Direct Rendering Manager Device **

PropertyValueinfo.category drm 
info.subsystem drm 
info.product Direct Rendering Manager Device 
info.vendor ATI Technologies Inc 
info.parent /org/freedesktop/Hal/devices/pci_1002_4c57 
info.capabilities  drm   access_control  
info.udi /org/freedesktop/Hal/devices/pci_1002_4c57_drm_radeon_card0 info.callouts.add  hal-acl-tool --add-device  
info.callouts.remove  hal-acl-tool --remove-device  
drm.dri_library radeon 
access_control.type video 
access_control.file /dev/dri/card0 
linux.device_file /dev/dri/card0 
linux.hotplug_type 2 
linux.subsystem drm 
linux.sysfs_path /sys/devices/pci0000:00/0000:00:10.0/drm/card0

---

### Post by anubhavrocks on 2009-10-22
Are you using Karmic?

---

### Post by candyiz4kidz on 2009-10-22
i'm using jaunty, haven't checked out karmic yet.

---

### Post by candyiz4kidz on 2009-10-22
> **candyiz4kidz said:**
> i'm using jaunty, haven't checked out karmic yet.
But I will be upgrading upon official release... which may fix this problem all together. Is anyone who is currently using karmic on ibook g3 having this issue?

---

### Post by Dodeca on 2009-10-22
Here is a paste from lspci

01:00.0 VGA compatible controller: nVidia Corporation NV44A [GeForce 6200] (rev a1)


Here is a pix ...  LOGOUT and LOGIN

[IMG]http://i621.photobucket.com/albums/tt300/Dodeca/ubuntu/turnoffnon.jpg[/IMG]

I can live with this issue

---

### Post by candyiz4kidz on 2009-10-23
My boot screen is waaaay funkier than that. It reminds me of when the original nintendo was loading a game but the cartridge wasn't put in all the way. 
The shutdown screen is just in black and white. (which i can live with)

I'm not too sure on how to take screenshots of the boot screen. But i'd post them if i did.

---

### Post by candyiz4kidz on 2009-10-26
I ended up taking a picture with my cell phone, but it just doesn't show exactly how crappy the screen looks. I also re-installed usplash packages, but the problem persists. has anyone got any ideas?

---

### Post by atirox on 2009-10-26
I was wondering, were the colours on the screen something like the ones here? 

[IMG]http://www.macbook-fr.com/IMG/jpg/ibook_screen.jpg[/IMG]

If it is, then I think your GPU is on its way out... 
I also found some instructions to fix it here ([http://geektechnique.org/projectlab/726/diy-obsolete-ibook-logic-board-repair](http://geektechnique.org/projectlab/726/diy-obsolete-ibook-logic-board-repair)).

---

### Post by fslezak on 2009-10-26
Take a look at this thread.

[http://ubuntuforums.org/showthread.php?t=1128341](http://ubuntuforums.org/showthread.php?t=1128341)

---

### Post by candyiz4kidz on 2009-10-31
well actually, my screen doesn't look like that. It's ONLY at the loading screen, and the shutdown screen. When it says "UBUNTU" and has the loading bar. When it boots up, it's all these weird colors, green, purple, grey etc etc... When it runs ubuntu, it's flawless. When it shutsdown, the same screen that was messed up during boot, is not so messed up, just black and white. I can easily solve this by turning of the usplash and changing it to text. 


I know of the video problem your showing us there. It has something to do with the logic board and how it distributes heat. There was a huge deal about this a few years back... like... 2003 i think. And lots of people were getting brand new ibooks or getting their machines repaired for free. unfortunately most of us nowadays are getting ibooks second hand with no warranty. I guess thats why we help each other, cyz deep down, were all cheap bastards.

---

### Post by SdGH on 2009-12-12
I used to have the same problem on my iBook G3, the colour looked like in 8bits.

Then I found this thread : [http://ubuntuforums.org/showthread.php?t=1057804](http://ubuntuforums.org/showthread.php?t=1057804)

and changed in my yaboot.conf

append="quiet splash video=ofonly"
to 

append="quiet splash video=radeonfb:1024x768"
Colour becomes normal afterward.

I verified that my iBook is using an ATI Radeon from [http://www.apple-history.com/](http://www.apple-history.com/)

---

