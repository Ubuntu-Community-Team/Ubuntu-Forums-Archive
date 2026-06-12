---
title: "Stuck in Terminal, Can't Display After Driver Update"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by doubleplus on 2007-06-20
Hi.  I'm a newb as of yesterday.  I made a post earlier regarding nVidia driver updates, and I followed someone's instructions to use "sudo apt-get install nvidia-glx-new".  This worked to download the driver, but after I went to RDM to enable, it told me to restart my system, then:

I got an error screen saying something about my X Windows and my devices not being configured properly. The detail screen mentioned a var.log.Xorg.0.log file, then dumped me into terminal mode. I located that log file and at the bottom it said, essentially: "Failed to initialize the NVIDIA kernel module! Ensure there is a supported NVIDIA GPU, and that the NVIDIA device files have been created properly." And it told me to read a README that I couldn't locate.

I did some poking around on the internets and I found a post somewhere suggesting that one do the following:

[I]sudo apt-get install nvidia-glx-new
Then at next boot type on the Konsole:
sudo kate /etc/X11/xorg.conf
under Device replace "nv" by "nvidia"
Reboot
Again open the konsole and type:
sudo nvidia-settings
There do all the settings that you need, hit Apply and then hit Save to X Configuration File[/I]

Now I know that's for KDE and I have Gnome, so I looked around some more and found that gedit is Gnome's kate.  So I found the xorg.conf file and tried to open gedit, but the system printed "Cannot open display."  Then I tried typing sudo nvidia-settings and got the same message.

As of now, I'm stuck in Terminal, I don't know how to get back to the GUI, and I'm not quite sure what "device files" I should be creating or editing. Welcome to Linux! :)

Any help would be appreciated. Thanks,

dp

---

### Post by MonkeyNet on 2007-06-20
> **doubleplus said:**
> 
I did some poking around on the internets and I found a post somewhere suggesting that one do the following:

[I]sudo apt-get install nvidia-glx-new
Then at next boot type on the Konsole:
sudo kate /etc/X11/xorg.conf
under Device replace "nv" by "nvidia"
Reboot
Again open the konsole and type:
sudo nvidia-settings
There do all the settings that you need, hit Apply and then hit Save to X Configuration File[/I]

Now I know that's for KDE and I have Gnome, so I looked around some more and found that gedit is Gnome's kate.  So I found the xorg.conf file and tried to open gedit, but the system printed "Cannot open display."  Then I tried typing sudo nvidia-settings and got the same message.

As of now, I'm stuck in Terminal, I don't know how to get back to the GUI, and I'm not quite sure what "device files" I should be creating or editing. Welcome to Linux! :)

Any help would be appreciated. Thanks,

dp

You will need to use a terminal based text editor like 'vi' or 'pico'. Then you will be albe to modify the file and reboot. Vi can be hard to use though

---

### Post by doubleplus on 2007-06-20
> **MonkeyNet said:**
> You will need to use a terminal based text editor like 'vi' or 'pico'. Then you will be albe to modify the file and reboot. Vi can be hard to use though

That Vi is evil.  I used Pico, but there didn't appear to be anything wrong - there was no "nv," everything read "nVidia."  I tried rebooting and I just got the same error message and drop to Terminal.  Grr.  Thanks for the reply.

Edit:  The marker used on the error message says it's related to my "Default Setting" as opposed to the config file.

---

### Post by Crafty Kisses on 2007-06-20
> **doubleplus said:**
> Hi.  I'm a newb as of yesterday.  I made a post earlier regarding nVidia driver updates, and I followed someone's instructions to use "sudo apt-get install nvidia-glx-new".  This worked to download the driver, but after I went to RDM to enable, it told me to restart my system, then:

I got an error screen saying something about my X Windows and my devices not being configured properly. The detail screen mentioned a var.log.Xorg.0.log file, then dumped me into terminal mode. I located that log file and at the bottom it said, essentially: "Failed to initialize the NVIDIA kernel module! Ensure there is a supported NVIDIA GPU, and that the NVIDIA device files have been created properly." And it told me to read a README that I couldn't locate.

I did some poking around on the internets and I found a post somewhere suggesting that one do the following:

[I]sudo apt-get install nvidia-glx-new
Then at next boot type on the Konsole:
sudo kate /etc/X11/xorg.conf
under Device replace "nv" by "nvidia"
Reboot
Again open the konsole and type:
sudo nvidia-settings
There do all the settings that you need, hit Apply and then hit Save to X Configuration File[/I]

Now I know that's for KDE and I have Gnome, so I looked around some more and found that gedit is Gnome's kate.  So I found the xorg.conf file and tried to open gedit, but the system printed "Cannot open display."  Then I tried typing sudo nvidia-settings and got the same message.

As of now, I'm stuck in Terminal, I don't know how to get back to the GUI, and I'm not quite sure what "device files" I should be creating or editing. Welcome to Linux! :)

Any help would be appreciated. Thanks,

dp

Try this:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by doubleplus on 2007-06-20
> **Codename said:**
> Try this:
```
sudo dpkg-reconfigure xserver-xorg
```

I went through the reconfigure twice.  The first time, it didn't work.  The second time, I finally got back in.  I feel like I won the lottery.  The original problem... that the RD Manager won't enable the nVidia driver for me... is back, but I'm giving up for now.  By the time I actually need accelerated 3D graphics for something, I'll know a lot more.  Thanks!

---

### Post by doubleplus on 2007-07-03
In case anyone with the same problem lands on this thread, I ended up finding out about Envy: [http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)  Download it and let it do the work.  Make sure you uninstall the existing nvidia-glx first - "sudo apt-get remove nvidia-glx"  Otherwise you'll have completing drivers... or something...

---

### Post by GeeZor on 2007-07-03
You could also go here:

[http://www.nvidia.com/content/drivers/drivers.asp](http://www.nvidia.com/content/drivers/drivers.asp)

here you will find the driver you should be able to compile and install. 
one note though, make sure you have your kernel's header files and source files installed properly. 
Meeting this dependency i am sure you will be able to get your graphics up and running smoothly. 
second note. After downloading the driver file, chmod 777 <downloaded file> to make it executable. Otherwise it will not run (Duuh!)

good luck, let me know if you need any help..

---

