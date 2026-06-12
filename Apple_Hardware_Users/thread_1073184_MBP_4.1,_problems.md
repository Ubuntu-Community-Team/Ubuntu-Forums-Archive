---
title: "MBP 4.1, problems"
date: 2009-02-18
forum: Apple Hardware Users
---

### Post by anandi on 2009-02-18
Hi,

I have been using osx on my macbook pro until yesterday, and decided to install intrepid on it (though i have been running ubuntu on my desktop for couple of years)

Now i am facing multiple problems and have tried to consult the Mactel pages on ubuntu wiki, however it hasn't help. Let me try and list them out.

1. Right click not working : I cannot get the right click working in any possible manner.

2. Touchpad scrolling : The Double Finger TouchPad scrolling was working the first time i booted up ubuntu. After trying to get the right click working, the scroll now doesn't work. Is there something i can check ?

3. Default Brightness + Default Keyboard BackLit : When i boot up ubuntu, by default the screen brightness and keyboard backlit is set to default, where do i change this ? Does the light sensors which work under osx i.e. when there is less light, the keyboard backlit works automatically ?

4. Fn+F1, F2 : Inside osx, i was using Fn+F1 and Fn+F2 for changing screen brightness, however in ubuntu, i don't know how to get that working. Right now F1, F2 works for increasing and reducing brightness respect.

5. Wifi Disconnection : I have enabled the driver from restricted drivers, after which the wifi started to work. However it disconnects every now and then, and either it will auto reconnect, or i will have to do a manual reconnection. There is np with the wifi network, since it was working properly with osx and other machines in the same network.

6. Wifi Duplicate : In the NetworkManager icon on the system tray, sometimes i start to see 2 Broadcom entries.

7. Temp : The macbook pro was heating up badly, so i been using the following to control the same. Is there a better way to do this or this is ok ?

[INDENT]sudo sh -c "echo 5000 >  /sys/devices/platform/applesmc.768/fan1_min"
sudo sh -c "echo 5000 >  /sys/devices/platform/applesmc.768/fan2_min"
[/INDENT]

8. Alt+F2 Combo : The Alt+F2 combo which is used to get the run window, doesn't work.

Now i have tried to follow the wiki for mactel users and searched the forums, however have been unable to resolve the above issues.

I have loaded the mactel ppa repository in apt, and already installed applesmc-dkms, hal-applesmc, mbp-nvidia-bl-dkms. Here are the contents of /etc/modules

```

# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.

fuse
lp
sbp2
applesmc
mbp_nvidia_bl

```

Will appreciate any help / pointers in order to resolve the above.

---

### Post by Divider on 2009-02-18
Wifi: I had this problem with a laptop once, it turned out it was attempting to enter monitor mode because of a restricted driver.

is it a B43 chipset?


Overheat:
sudo apt-get install powernowd

if its not already installed. It will enable processor scaleing.

---

### Post by anandi on 2009-02-18
Hi,

> **Divider said:**
> Wifi: I had this problem with a laptop once, it turned out it was attempting to enter monitor mode because of a restricted driver.

is it a B43 chipset?


Broadcom Corporation BCM4328 802.11a/b/g/n (rev 05)
> 
Overheat:
sudo apt-get install powernowd

if its not already installed. It will enable processor scaleing.
Its already installed. The lines which i wrote do the trick of cooling the laptop down, my question was whether that is the best possible way, or a better alternative is available.

Thanks

---

### Post by anandi on 2009-02-18
Update:

I tried to use the solution mentioned at [https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl). However this results in the laptop heating up badly. When checked manually the fan1_min and fan2_min show a value of 1.

---

### Post by anandi on 2009-02-18
This is running strange now. The two finger scroll has started to work in firefox.

Hmm... this is strange, sometimes it works, and sometimes it doesn't. I rebooted again and this time, no two finger scroll. Suspended and came back, still nothing.

Things are acting very very weird, just hope someone here can help before i get tired of banging my head on this.

---

### Post by buntuLo on 2009-02-18
> **anandi said:**
> I tried to use the solution mentioned at [https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl](https://wiki.ubuntu.com/MacBookPro/SantaRosaFanControl). However this results in the laptop heating up badly. When checked manually the fan1_min and fan2_min show a value of 1.
Anandi, fanX_min=1 apparently means that the applesmc module takes care of fan speed control. i hope somebody else can help you with the specific procedure for MBP4,1. if you are worried of frying it in the meantime, try to manually set a minimum fan speed as described on the doc pages for MB5,1 and MBP5,1. ciao, Lo.

---

### Post by cyberdork33 on 2009-02-18
First make sure that you are using this page:
[https://help.ubuntu.com/community/MacBookPro4-1/Intrepid](https://help.ubuntu.com/community/MacBookPro4-1/Intrepid)

> **anandi said:**
> 1. Right click not working : I cannot get the right click working in any possible manner.

2. Touchpad scrolling : The Double Finger TouchPad scrolling was working the first time i booted up ubuntu. After trying to get the right click working, the scroll now doesn't work. Is there something i can check ?

The wiki page shows you how to setup the touchpad using the new hal-based fdi file method. In order for it to work correctly, you need to make sure that you remove any touchpad configuration sections from your xorg.conf

> **anandi said:**
> 3. Default Brightness + Default Keyboard BackLit : When i boot up ubuntu, by default the screen brightness and keyboard backlit is set to default, where do i change this ? Does the light sensors which work under osx i.e. when there is less light, the keyboard backlit works automatically ?
Make sure you have installed the corrected packages in the mactel PPA as instructed in the wiki. There has been a little work on getting the automatic scaling to work properly, but I don't think it is completely there yet.

> **anandi said:**
> 4. Fn+F1, F2 : Inside osx, i was using Fn+F1 and Fn+F2 for changing screen brightness, however in ubuntu, i don't know how to get that working. Right now F1, F2 works for increasing and reducing brightness respect. The default in Ubuntu is also the default for OSX. If you want to swap the Fn key behavior, you can do that as discussed in the wiki page. I also have a blog entry describing this here:
[http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)

> **anandi said:**
> 5. Wifi Disconnection : I have enabled the driver from restricted drivers, after which the wifi started to work. However it disconnects every now and then, and either it will auto reconnect, or i will have to do a manual reconnection. There is np with the wifi network, since it was working properly with osx and other machines in the same network.Some people exhibit these issues, and others do not. You can also try using ndiswrapper if you are unhappy with the Broadcom-provided wl driver.\

> **anandi said:**
> 6. Wifi Duplicate : In the NetworkManager icon on the system tray, sometimes i start to see 2 Broadcom entries.
make sure that thee b43 module is NOT loading on bootup as it will interfere with the wl driver (and doesn't work with this card anyway).

> **anandi said:**
> 7. Temp : The macbook pro was heating up badly, so i been using the following to control the same. Is there a better way to do this or this is ok ?
[INDENT]sudo sh -c "echo 5000 >  /sys/devices/platform/applesmc.768/fan1_min"
sudo sh -c "echo 5000 >  /sys/devices/platform/applesmc.768/fan2_min"
Make sure you have the applesmc module from the mactel ppa, but that appears to be the way to do it. It might help if you mess with the CPU scaling to get your machine to run cooler.
[/INDENT] > **anandi said:**
> 8. Alt+F2 Combo : The Alt+F2 combo which is used to get the run window, doesn't work.
That is because, with your current configuration, it would be Fn+Alt+F2. This will change if you do the Fn key function swap as mentioned above.

---

### Post by anandi on 2009-02-23
> **buntuLo said:**
> Anandi, fanX_min=1 apparently means that the applesmc module takes care of fan speed control. i hope somebody else can help you with the specific procedure for MBP4,1. if you are worried of frying it in the meantime, try to manually set a minimum fan speed as described on the doc pages for MB5,1 and MBP5,1. ciao, Lo.

Hi,

I understand it will take care of the speed control automatically, however during this time, i was monitoring the same. The speed was variating from 0 to 2000 max, and cpu temp was going off the scale. For now i have placed the manual fan speed in the bootup and wakeup scripts.

Thanks

---

### Post by deltaiscain on 2009-02-25
> **Divider said:**
> Wifi: I had this problem with a laptop once, it turned out it was attempting to enter monitor mode because of a restricted driver.

is it a B43 chipset?


Overheat:
sudo apt-get install powernowd

if its not already installed. It will enable processor scaleing.

Doesn't the processor autoscale normally? I don't have this installed, or i never installed it.

---

### Post by anandi on 2009-02-26
> **cyberdork33 said:**
> First make sure that you are using this page:
[https://help.ubuntu.com/community/MacBookPro4-1/Intrepid](https://help.ubuntu.com/community/MacBookPro4-1/Intrepid)


Thanks been following that a lot.

> 
The wiki page shows you how to setup the touchpad using the new hal-based fdi file method. In order for it to work correctly, you need to make sure that you remove any touchpad configuration sections from your xorg.conf


Works now. The two finger touch and right click all work.

> 
Make sure you have installed the corrected packages in the mactel PPA as instructed in the wiki. There has been a little work on getting the automatic scaling to work properly, but I don't think it is completely there yet.


Ok have it working partly after installing pommed from the main repository. Now it will lit the whole keyboard when waken up from sleep which is irritating.

> 
 The default in Ubuntu is also the default for OSX. If you want to swap the Fn key behavior, you can do that as discussed in the wiki page. I also have a blog entry describing this here:
[http://www.rickycampbell.com/swap-fn/](http://www.rickycampbell.com/swap-fn/)


Yes figured it out.

> 

Some people exhibit these issues, and others do not. You can also try using ndiswrapper if you are unhappy with the Broadcom-provided wl driver.\


First thing i noticed that wl driver introduced a very high latency. My local lan seems to be giving me from 5ms to 200+ms, whereas using the wired network has no problem at all. Second the ndiswrapper way just won't work for me. Even though i configured it as instructed, NetworkManager will keep on asking me the password, and not connect to the network :(

> 
make sure that thee b43 module is NOT loading on bootup as it will interfere with the wl driver (and doesn't work with this card anyway).


Checked, its not being loaded.

> 

Make sure you have the applesmc module from the mactel ppa, but that appears to be the way to do it. It might help if you mess with the CPU scaling to get your machine to run cooler.


Yup doing that already.

Now just if the network issue gets resolved, i can atleast start to use this laptop, otherwise its now a complete mess :(

---

### Post by anandi on 2009-02-26
> **deltaiscain said:**
> Doesn't the processor autoscale normally? I don't have this installed, or i never installed it.

No need to install it. It works out of the box. If you wish to do manual scaling, just add the applet for the same "CPU Frequency Scaling Monitor", and then you can choose your cpu speed.

---

### Post by deltaiscain on 2009-02-26
> **anandi said:**
> No need to install it. It works out of the box. If you wish to do manual scaling, just add the applet for the same "CPU Frequency Scaling Monitor", and then you can choose your cpu speed.

Oh, ok. Thanks. I'm using the one that actually, but i hadn't heard of the other app.

---

### Post by cyberdork33 on 2009-02-26
pommed is actually not needed anymore if you have the packages from the mactel ppa.

---

### Post by anandi on 2009-02-26
> **cyberdork33 said:**
> pommed is actually not needed anymore if you have the packages from the mactel ppa.

Thanks for the reply. I realised that when i screwed up pommed config somehow. Later i choose to purge the package and rebooted. Seeing the backlit functionality working, i realized that pommed wasn't needed.

However after removing pommed, i do have another problem

1. Backlit of keyboard comes on after i resume the computer from a locked screen saver session.
2. When waking up the laptop from sleep, the keyboard lits up.

Now its come to a situation when the keys for reducing the keyboard backlit aren't working anymore :(

Looks like more and more this mbp is driving me nuts and might force me to reload osx back on it :( which i certainly don't want to do.

Working off a wired network now, since the wifi is introducing so much high latency that i can hard work. :(

---

### Post by cyberdork33 on 2009-02-26
> **anandi said:**
> Thanks for the reply. I realised that when i screwed up pommed config somehow. Later i choose to purge the package and rebooted. Seeing the backlit functionality working, i realized that pommed wasn't needed.

However after removing pommed, i do have another problem

1. Backlit of keyboard comes on after i resume the computer from a locked screen saver session.
2. When waking up the laptop from sleep, the keyboard lits up.

Now its come to a situation when the keys for reducing the keyboard backlit aren't working anymore :(

Looks like more and more this mbp is driving me nuts and might force me to reload osx back on it :( which i certainly don't want to do.

Working off a wired network now, since the wifi is introducing so much high latency that i can hard work. :(

why not dual boot?

The default backlight issue is known, and I am sure there are some posts about it around. I am not sure where. I think someone had written a script or something that would store the current value and then set it back again when you came back to the machine.

---

### Post by deltaiscain on 2009-02-27
> **anandi said:**
> Thanks for the reply. I realised that when i screwed up pommed config somehow. Later i choose to purge the package and rebooted. Seeing the backlit functionality working, i realized that pommed wasn't needed.

However after removing pommed, i do have another problem

1. Backlit of keyboard comes on after i resume the computer from a locked screen saver session.
2. When waking up the laptop from sleep, the keyboard lits up.

Now its come to a situation when the keys for reducing the keyboard backlit aren't working anymore :(

Looks like more and more this mbp is driving me nuts and might force me to reload osx back on it :( which i certainly don't want to do.

Working off a wired network now, since the wifi is introducing so much high latency that i can hard work. :(

about the latency, how do you check if you have it? And what does it do? lag in streaming, like on youtube? 
Thanks. And my backlit does the same, haven't found a fix yet.

---

### Post by anandi on 2009-02-28
> **cyberdork33 said:**
> why not dual boot?

The default backlight issue is known, and I am sure there are some posts about it around. I am not sure where. I think someone had written a script or something that would store the current value and then set it back again when you came back to the machine.

The whole idea to load ubuntu was to run it sole os. If i have to dual boot, i will end up having osx as the only os.

As for the backlit, i can still live with it, but not with the high latency issue, which is really killing me. :(

---

### Post by anandi on 2009-02-28
> **deltaiscain said:**
> about the latency, how do you check if you have it? And what does it do? lag in streaming, like on youtube? 
Thanks. And my backlit does the same, haven't found a fix yet.

Very easy. My local lan ping itself was going from 1ms to 200ms even though i wasn't transferring much data.

I tried to get ndiswrapper working with the broadcom drivers on my osx dvd, however it doesn't work. It kept on asking me the password for my wifi network and won't join. Maybe that would have worked on the latency front (if it worked).

---

### Post by cyberdork33 on 2009-02-28
> **anandi said:**
> The whole idea to load ubuntu was to run it sole os. If i have to dual boot, i will end up having osx as the only os.
well, then I would go back to OSX. If you want to use Ubuntu only on someting then this not the right hardware. There are much more linux-compatbile machines.

---

### Post by anandi on 2009-02-28
> **cyberdork33 said:**
> well, then I would go back to OSX. If you want to use Ubuntu only on someting then this not the right hardware. There are much more linux-compatbile machines.

Yup doing that now. I realized after the linux format that my osx dvd's were bad, so have ordered a replacement, should be up in another week, after which its osx (doesn't make me happy to do so, however have no other way even)

P.S. :  I am surprised no one else is encountering the high latency issue with the broadcom driver ? Or its just me ?

---

### Post by cyberdork33 on 2009-02-28
> **anandi said:**
>  I am surprised no one else is encountering the high latency issue with the broadcom driver ? Or its just me ?
I haven't noticed it, but I generally use a wired connection. It may also be that people just don't care that much about latency.

---

