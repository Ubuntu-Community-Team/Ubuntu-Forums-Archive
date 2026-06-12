---
title: "LFE in MacBook 5,1"
date: 2010-06-27
forum: Apple Hardware Users
---

### Post by Maletor on 2010-06-27
I'm on Ubuntu 10.4. When I run 'speakertest -c6' everything works except for LFE. In alsamixer: everything is at 100. What's going on? How do I fix this? I've googled and run into a dead end. Please help, I would love to listen to some bass on my Macbook.

Also, I've been running powertop and trying to get some efficiency out of this battery but 2:30 hours seems like maximum.This is most unfortunate and almost makes me want go back to OS X. That along with the laptop running so hot.

Does anyone else get static out of their headphone jack? This drives me crazy. Hopefully there is a fix for this.

Also, the trackpad is pretty worthless. Even with bitmath's multitouch driver.

---

### Post by Helios747 on 2010-06-27
Run alsamixer in terminal.

Can you provide a screenshot of what is being shown?

As for the other macbook issues, fallow this Ubuntu help page on configuring your MacBook for Lucid Lynx.

[https://help.ubuntu.com/community/MacBook5-1/Lucid]("https://help.ubuntu.com/community/MacBook5-1/Lucid")

You may also want to add the Mactel ppa to your repos, as they compile packages for getting better functionality in ubuntu on macs.

[https://launchpad.net/~mactel-support/+archive/ppa]("https://launchpad.net/~mactel-support/+archive/ppa")

Do in terminal after adding that ppa to your repos through the Software Sources in Administration

```
sudo apt-get install applesmc-dkms
sudo gedit /etc/modules
```

add at the end of /etc/modules

```
coretemp
applesmc
```

Save, close.

as for your battery issues, do this in Terminal (only after you have installed the NVIDIA drivers from Restricted Drivers or from NVIDIA's website)

```
sudo apt-get install nvidia-bl-dkms pommed
sudo gedit /etc/modules
```

add to /etc/modules

```
nvidia_bl shift=2
```

save, close. Brightness keys will work now. If you do not use ethernet, you can disable its driver to save some power

```
sudo gedit /etc/modprobe.d/blacklist.conf

```

add at the end

```
forcedeth
```

Save, close. Also do this to have your graphics chip go into power saving mode whenever you unplug the laptop.

```
sudo gedit /etc/X11/xorg.conf
```

add to the *Device* section

```
Option     "RegistryDwords" "PowerMizerEnable=0x1; PerfLevelSrc=0x2233; PowerMizerDefault=0x3"

```

Save, close. We can also enable laptop-mode which is a series of scripts to improve battery life.


```
sudo gedit /etc/default/acpi-support
```


find the line that says ENABLE_LAPTOP_MODE=false and change is to


```
ENABLE_LAPTOP_MODE=true

```

After you do ALL of this, you can restart to make the changes stick.

For your touchpad issues, go into Preferences > Mouse

and set your desired options (disable tap to click, two fingered scrolling, etc)

---

### Post by Maletor on 2010-06-27
Wow! Thank you for the most informative post I've found regarding Ubuntu on MacBook. I had found most of that information before, but it had been in bits and pieces. Your reply was comprehensive.

As a note though: in my /etc/default/acpi-support file there was a reference to install laptop-mode-tools from aptitude, so I did. There is so much configuration I can do now in /etc/laptop-mode/laptop-mode.conf and I can enable / disble as a startup script.

Furthermore, pommed seem to break my controls. Everything worked either great out of box or with nvidial-bl-dkms.

Also, I'm wondering if laptop-mode-tools supercedes the line in xorg.conf. 

I've got some more tweaking to do. Thanks for the help. It is greatly appreciated.

---

### Post by Maletor on 2010-06-27
Still the problems with the headphones (but I think they are documented at [https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/488103]("https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/488103")488103) and the LFE still doesn't work after doing 'speaker-test -c6'.

Here's a screenshot. It has got to do with Ubuntu not recognizing the drivers for it.

[IMG]http://lookpic.com/d2/i2/3122/BRqAvc1F.png[/IMG]

---

### Post by Helios747 on 2010-06-27
I have the same MacBook as you, so I just listed everything I did to get it working :p


You may have to recompile ALSA to get it to work.

download the alsa driver here: [ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2]("ftp://ftp.alsa-project.org/pub/driver/alsa-driver-1.0.23.tar.bz2")

The library here: [ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2]("ftp://ftp.alsa-project.org/pub/lib/alsa-lib-1.0.23.tar.bz2")

and the utilities here: [ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2]("ftp://ftp.alsa-project.org/pub/utils/alsa-utils-1.0.23.tar.bz2")

do in Terminal:

```
sudo apt-get purge alsa-base alsa-utils linux-sound-base
```

(I'm not sure if linux-sound-base has gobs of "dependancies", if it does and it looks like it's going to remove something important, don't remove linux sound base, it should be fine)

This will remove all traces of ALSA, we can now recompile ALSA. Follow the instructions here, which is a how to for compiling ALSA for the NVIDIA/Intel HDA sound chip (The one the MacBook 5,1 has)

[http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel]("http://www.alsa-project.org/main/index.php/Matrix:Module-hda-intel")

You can compile it in any directory you want. When it tells you not to run sudo ./snddevices if you're using a newer ALSA, ignore it. Run sudo ./snddevices

Then use alsamixers to set everything to max (cept master, set that to around 50 or whatever you want). After that, do

```
sudo alsactl store
```

to make the sound default to that when you boot up

To get the sound keys to work right (control the right channels) do:

```
sudo gedit /etc/pommed.conf
```

find the section that says

```
audio {
        # Use amixer or alsamixer/alsamixergui to determine the sound card
        # and the mixer elements to use here.

        # sound card to use
        card = "default"
        # initial volume [80] (0 - 100%, -1 to disable)
        init = -1
        # step value (1 - 50%)
        step = 10
        # beep on volume change
        beep = yes
        # mixer element for volume adjustment
        volume = "Master"
        # mixer element for muting the speakers
        speakers = "Master"
        # mixer element for muting the headphones
        headphones = "Master"
}

```

Make sure Volume, speakers and headphones say Master. Just set everything to Max in alsamixer and let Master channel control everything.

Reboot, and you should be good.


OH. and if you find that alsamixer's controls to not stick after a reboot, do

```
sudo gedit /etc/rc.local
```

add

```
alsactl restore
```

and save.

---

### Post by Maletor on 2010-06-29
I found an alsa upgrade script on the forums here and ran that and now I am at the latest version. It seemed to help a little with the headphones (it would have helped a lot more if each button press was actually two... like shifting by 2 instead of 1). But there is still static. Also, the LFE works now and sound out of the internal speakers is very nice.

My temps are still running very hot however. I tried to echo 3500 > fan1_min but it kept changing it back to 2000. I have coretemp as a module and applesmc-dkms installed. I wonder what else there is to do?

My battery life is still pretty poor as well. I guess Apple is just going to have to win on that one. doing sudo laptop_mode returns enabled and active.

Here's the output from my sensors.
 Laptop mode 
enabled, 
active [unchanged]
ellis@istanbul:~/Sites/multi_mls$ sensors
coretemp-isa-0000
Adapter: ISA adapter
Core 0:      +59.0°C  (high = +105.0°C, crit = +105.0°C)  

coretemp-isa-0001
Adapter: ISA adapter
Core 1:      +62.0°C  (high = +105.0°C, crit = +105.0°C)  

applesmc-isa-0300
Adapter: ISA adapter
Exhaust  :  2003 RPM  (min = 2000 RPM)
TB0T:        +36.5°C                                    
TB1T:        +36.5°C                                    
TB2T:        +34.8°C                                    
TB3T:        +37.2°C                                    
TC0D:        +63.0°C                                    
TC0P:        +56.5°C                                    
TN0D:        +64.0°C                                    
TN0P:        +55.5°C                                    
TTF0:        +65.0°C                                    
Th0H:        +63.0°C                                    
Th1H:        +54.0°C                                    
ThFH:        +53.2°C                                    
Ts0P:        +34.8°C                                    
Ts0S:        +42.8°C

---

### Post by Helios747 on 2010-06-29
Yeah, the only flaw with Ubuntu on macs (in my opinion) is the heat problem. My temps are just a little lower than that idling. and 2.5 - 3 hrs of battery. That's been known for awhile.


What I would do is get yourself a USB hard drive or a good sized flash drive, and install OS X to that. OS X WILL boot from USB if the OS on the USB is OS X... Sneaky Apple, huh?

if you want to load any other OS from USB, chainload it from GRUB, I personally uninstalled GRUB2 and reinstalled GRUB legacy. GRUB2 just feels too half-baked for a mainstream OS. (Same with Empathy but that's off topic ;))

---

### Post by Maletor on 2010-06-29
I just tried to install two fan control scripts. One of them was 
[http://github.com/xiangfu/mfc-daemon](http://github.com/xiangfu/mfc-daemon)
and that got compile warnings.

Another was for the santarosa fan [https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl)

I modified it so that it was only for fan1_min and I changed it to tee instead of echo. Finally I enabled debug and found out that it was not understanding what the let command was. What do I do? 

Also after installing pommed my nvidia backlight moves at the pace of 1/255th it would seem. I can't see where to change this in /etc/pommed.conf

Thanks for the help,
Maletor

---

### Post by Maletor on 2010-06-30
So I resolved the sound issue. 

What you need to do is upgrade to 1.0.23 for ALSA.
Then you need to add options snd-hda-intel model=mb5 to /etc/modprobe.d/alsa-base.conf

I would add this to the wiki but I don't have permission.

The heat issue will be solved with a bash script that I can write.

The battery problem is probably here to stay and will require tweaking with powertop.

Also, has anybody noticed a script where they can modify the modify the blacklight based on output from /sys/devices/platform/applesmc.768/light

I might write one if nobody has something yet.

I really can't think of anything else that's wrong. It runs sweet. Boots quick. Has excellent battery life while sleeping (way better than OS X) and compiz is sweet. 

Can't tell you how excited I am not to have white noise in my headphones anymore.

---

