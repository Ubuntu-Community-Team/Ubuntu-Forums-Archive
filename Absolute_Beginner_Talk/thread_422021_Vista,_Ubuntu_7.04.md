---
title: "Vista, Ubuntu 7.04"
date: 2007-04-24
forum: Absolute Beginner Talk
---

### Post by BOZG on 2007-04-24
Ok, I've managed to create a partition on my drive and am now trying to install Ubuntu onto the partion.  When I get to section 4 of 7 (prepard disk space), I assume I choose Manual?  When I go to Manual, select the partion I want to use /dev/hda2 20791MB and click forward, it tells me, "No root file system is defined.  Please correct this from the partitioning menu."  What do I do from here?

---

### Post by BOZG on 2007-04-24
The lower window says something about a swap partition.  What's that?  I only have 2 partitions, one unused and one that Vista is running on.

---

### Post by carverj on 2007-04-24
SO you are attempting dual boot with Microsoft? Microsoft to be installed to the first partition of the hard drive. Then when you are manually configuring Ubuntu install, choose the size of Ubuntu partition carefully, with at least 5-10 or even more GB for system files. Then approxiamately twice the amount of RAM you have as swap. Then I would create another ext3 partition for /home.
There should be a drop down list of available mount points. Choose root (/) for the Ubuntu system partition, /home for personal ext3 data, and swap option for the swap space you have left at end of drive.
GOod luck

---

### Post by BOZG on 2007-04-24
Does that mean I need to make 2 more partitions for swap and for ext3?

---

### Post by BOZG on 2007-04-24
I'm completely lost.

---

### Post by nphx on 2007-04-24
Yes you'll need a /swap (usually double the ram size) and some people like to do a separate /boot partition also. I think you can let the installer automatically do that for you on the partition you select.

---

### Post by lamalex on 2007-04-24
just break that one you have into two, no biggie :) it'll be like sharing.

---

### Post by bobplano on 2007-04-24
you can make a root partition (/) about 5-10gb big. the swap needs to be 512mb-1gb but if you have 1gb of ram or more this won't be used much (you still need it though) and another partition /home which is all your personal files so this need to be pretty big (however big you want). the /, and /home need to be ext3 and the swap needs to be swap

---

### Post by BOZG on 2007-04-24
OK, I'll try again.  Thanks.

---

### Post by RealG187 on 2007-04-24
I may get a laptop w. Vista and chances are da Vista partition will take the whole drive, would I have to erase dat partition and reinstall Ubuntu and Vista?

---

### Post by bobplano on 2007-04-24
you can just resize the partition of vista when you are installing ubuntu. just make sure the vista partition is defragged

---

### Post by BOZG on 2007-04-24
OK, I tried to partition in the Ubuntu installer but it wouldn't let me so I went back into Vista and made a new partition for swap, new partition for root and another partition for home but it says the home one is a logical drive while the others are primary partitions.  Will it still work?

---

### Post by phr0ze on 2007-04-24
The installer will automatically repartition for you and make your system dual boot. When you get to step 4 (of 7) it asks you about partitions. You can leave it with the default option which is to give windows half of the free space and ubuntu the other half. Click next and the installer will give a little warning because it will repartition once you choose this option.  Finally you can blaze through the last 3 steps which involves choosing a user name and password.

Good luck.

---

### Post by BOZG on 2007-04-24
OK, I managed to install finally, restarted and everything booted ok.  Downloaded all the updates, went to Desktop effects to check something, enabled the driver and restarted and now it doesn't work at all.  A blue screen appears (not even Windows has that anymore =P) asking me about my graphic display or something and if I want to see the server for it.  If I click yes, it gives me a list of text and if I click now, it asks me to Login but not through the normal screen, just a pure text screen.  After I put in my name and password (which keeps flickering), it just says "stephen@Stephen: $" and let's me type but I don't know the hell is happening.

---

### Post by bobplano on 2007-04-24
your X isn't starting. it is basically the gui and what you are seeing is the commad prompt. try sudo X or sudo dpkg-reconfigure xserver-xorg

---

### Post by BOZG on 2007-04-24
Ok, the reconfigure command works but when I get to the part selecting 24bit colours, the command prompt warns me that I might be about to overwrite a configuration file and leaves me with "stephen@Stephen:~$" again.

---

### Post by Tundro Walker on 2007-04-24
If the whole "swap", "root" etc is too confusing, Ubuntu should have an option to install to the largest, free, unpartitioned space available.  To get it to do this, just delete the parition you made for "Ubuntu", then backtrack to the partitioning / install options it gives.  You should see on saying "use largest available free space" or something.  Click that, and it should keep your Vista partition, and on the free area of the drive, it'll partition it into the necessary ones for a regular Ubuntu install.

As you become more familiar with Ubuntu, you can always re-partition and move your "home" directory and other things around as you see fit.  But for starting out, it may be easier to just let Ubuntu partition itself for you.

---

### Post by RealG187 on 2007-04-25
So Ubuntu install will automatically repartition, is there a risk to this?

---

### Post by jdonat on 2007-04-25
> **BOZG said:**
> Ok, the reconfigure command works but when I get to the part selecting 24bit colours, the command prompt warns me that I might be about to overwrite a configuration file and leaves me with "stephen@Stephen:~$" again.

it's ok to overwrite the config file, since your  current one isn't working anyway, if you have more problems after that, could you post what kind of graphics hardware you're running?

---

### Post by jdonat on 2007-04-25
> **RealG187 said:**
> So Ubuntu install will automatically repartition, is there a risk to this?

resizing an ntfs partition is always risky because MS wont tell anyone else how to play nicely with their filesystem.   If it's a completely new laptop with no personal files on there, it might not be a huge deal, but if you have anything important , be sure to back it up beforehand.

---

### Post by BOZG on 2007-04-25
> **jdonat said:**
> it's ok to overwrite the config file, since your  current one isn't working anyway, if you have more problems after that, could you post what kind of graphics hardware you're running?

But how do I overwrite it?

---

### Post by jocheem67 on 2007-04-25
You can just resize your existing  vista partition. It's an option you'll be getting.

---

### Post by BOZG on 2007-04-25
No, I mean after I go through sudo dpkg-reconfigure xserver-xorg, it lets me change the settings but when I go to select the 24bit colour, it tells me that I'm trying to overwrite the original file.  How to actually tell it to go ahead and overwrite it?

---

### Post by RealG187 on 2007-04-25
> **jdonat said:**
> resizing an ntfs partition is always risky because MS wont tell anyone else how to play nicely with their filesystem.   If it's a completely new laptop with no personal files on there, it might not be a huge deal, but if you have anything important , be sure to back it up beforehand.

I think I will install Nero Suite, this means 2 things:

1. I would add thigns to the HD, this might affect it

2. I will use Nero BackItUp! to backup the HD!

Does Vista still use NTFS?

---

### Post by BOZG on 2007-04-25
Can anyone help?

---

### Post by BOZG on 2007-04-25
Bump

---

### Post by RealG187 on 2007-04-25
Dont bump, it dont think that is a good thing, and if you are just dont say bump atleast say something useful....

---

### Post by BOZG on 2007-04-25
I've nothing useful to say!

---

### Post by RealG187 on 2007-04-25
Then say nothing, if u really wanna bump wait a while [it becomes worse then, but if you still need help what can you do?]

---

### Post by BOZG on 2007-04-25
All I'm looking for is someone to tell me how to basically say "Yes, go ahead" and that's it.

---

### Post by BOZG on 2007-04-25
OK, I figured out that I just had to type "startx" and did that but was immediately met with another problem which tells me that:

NVIDIA(0): Failed to initialise the NVidia graphics device PCI:2:0:0

Screen(s) found but no usable configuration



Fatal Error:
No screens found



????

---

### Post by jdonat on 2007-04-25
> **RealG187 said:**
> I think I will install Nero Suite, this means 2 things:

1. I would add thigns to the HD, this might affect it

2. I will use Nero BackItUp! to backup the HD!

Does Vista still use NTFS?

yes, vista still uses NTFS

---

### Post by jdonat on 2007-04-25
> **BOZG said:**
> OK, I figured out that I just had to type "startx" and did that but was immediately met with another problem which tells me that:

NVIDIA(0): Failed to initialise the NVidia graphics device PCI:2:0:0

Screen(s) found but no usable configuration



Fatal Error:
No screens found
????

ok, so you boot up ubuntu, it tries to load X , but fails , bumps you out to a blue screen saying it failed , then drops you to a command prompt, right?  

the next thing you should do is run :
sudo apt-get install nvidia-glx      

this will install the binary driver and the linux-restricted-modules that you need, you may have already done this, but it won't hurt to run the command again, it'll just say that it's already installed if that's the case.

next, run :
sudo mv /etc/X11/xorg.conf  /etc/X11/xorg.conf.bak  
this will rename your current configuration file to xorg.conf.bak , it will leave you without a current configuration, which is broken , and the next command will make a new one anyway.

sudo dpkg-reconfigure xserver-xorg  

where it asks what driver to use, make sure  nvidia is selected ,  you should leave all the other settings at whatever their default is, unless you know for sure what to change them to.  it will ask if it should write default sections or something like that, say ok, then it might ask if it can overwrite a possibly customized configuration file, you should be able to choose ok at that point, once it's done, you should run 

sudo /etc/init.d/gdm restart

if all that still doesn't work, you really need to post exactly what hardware you're running.

---

### Post by jdonat on 2007-04-25
> **BOZG said:**
> No, I mean after I go through sudo dpkg-reconfigure xserver-xorg, it lets me change the settings but when I go to select the 24bit colour, it tells me that I'm trying to overwrite the original file.  How to actually tell it to go ahead and overwrite it?

just in case I need to be more explicit about this , there should be a box on the screen that says OK, you would use the arrow keys to move to it and then press enter.

---

### Post by BOZG on 2007-04-25
Still no luck with it.  Just goes back to the blue screen.

I'm running a Sparkle GeForce 8800GTS 640MB on a Gigabyte MA-M51GM-S2G with 1GB DDR.

---

### Post by BOZG on 2007-04-25
Ubuntu was running fine until I tried to enable the nvidia drivers.

---

### Post by lepz on 2007-04-25
I think your problems may have started when you ran desk top effects before you had the right drivers.If I where you, I would start again and let ubuntu do the partition, install the drivers you need , set your resolution (if needed) and then and only then have a play with compiz/beryl  ;)

---

### Post by jdonat on 2007-04-25
> **BOZG said:**
> Ubuntu was running fine until I tried to enable the nvidia drivers.

are you able to complete the dpkg reconfigure stuff?  does it write the file or just crash out? 

 you could also try to go back to using the open driver "nv"   just run dpkg-reconfigure again, but this time choose nv as the driver instead of nvidia.

---

### Post by BOZG on 2007-04-25
> **lepz said:**
> I think your problems may have started when you ran desk top effects before you had the right drivers.If I where you, I would start again and let ubuntu do the partition, install the drivers you need , set your resolution (if needed) and then and only then have a play with compiz/beryl  ;)

I'll try it though when I tried to use desktop effects, it downloaded the drivers when I clicked enable drivers.

---

### Post by BOZG on 2007-04-25
Ok, it's now working with the nv drivers.  How would I go about installing the proper ones though now?

---

### Post by lepz on 2007-04-25
if it's working ok with the nv drivers your fine.

---

### Post by BOZG on 2007-04-25
But it still asks me to enable drives whenever I go near Desktop Effects?

---

### Post by lepz on 2007-04-25
System .> Admin > Restricted Driver Manager  type in your pw and tick enable

---

### Post by jdonat on 2007-04-26
> **BOZG said:**
> Ok, it's now working with the nv drivers.  How would I go about installing the proper ones though now?

try using envy [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)   , it'll download, install , and configure the latest drivers for you .

---

### Post by RealG187 on 2007-04-26
I think I will install Nero Suite [minaly for backitup] and only that, I wonr update it or anythng, just enough so I can backup my hard drive...

Does Nero 6 WOrk w/ Vista?

---

### Post by jdonat on 2007-04-27
> **RealG187 said:**
> I think I will install Nero Suite [minaly for backitup] and only that, I wonr update it or anythng, just enough so I can backup my hard drive...

Does Nero 6 WOrk w/ Vista?

it should work since it's just regular NTFS, but I can't say for sure.

---

### Post by RealG187 on 2007-04-27
I hear lots of apps dont work with Vista...

---

