---
title: "Dapper on Old World AIO"
date: 2006-07-27
forum: Apple PPC Users
---

### Post by smileyme on 2006-07-27
I just wanted to say, I upgraded from 5.10 to 6.06 via the update manager, and all is well. The machine is tweaked with 83 MHz front side bus and a 450 G3 pushed to 498 MHz. Unfortunately, I only have 128 MBs RAM in it, which may account for its being a little slow. My next tweak will be a PCI video card in it. (and more RAM of course)

Rick :)

---

### Post by greenstar on 2006-07-27
For better performance on older machines, try the XFCE desktop.

```
sudo apt-get install xubuntu-desktop
```

Then you choose XFCE from the sessions menu on the login screen.

Welcome to Ubuntu - enjoy the freedom.

Greenstar

---

### Post by Uta on 2006-07-27
Are you using BootX to boot? I am assuming you are if you have an Old World Mac. So when you updated via the Update Manager, on restart did you copy the newly created kernel to the Mac's system folder, plus the ramdisk image? Also what kind of drive did you install linux to, the main scsi HD or IDE HD via an adapter card? Thanks--

---

### Post by smileyme on 2006-07-28
Hi Uta,

I am using BootX. 

I copied the kernel and ramdisk image before rebooting, then changed to them in BootX when I rebooted.

The drive is IDE via the built in ATA bus.

I haven't tried SCSI with Dapper, but had read through your posts looking for information prior to updating. Wish I had the time to set up a Legacy Mac. I do have a 9600 I want to set up with triple boot, and was planning to use Ultra 2 Wide LVD SCSI, and will post with my progress when I get the time to play more.

Rick :)

---

### Post by Uta on 2006-07-28
Thank you for the information, it's encouraging. I have many computers running Ubuntu and all are very stable except my Old World Mac which has 5.10. I have been tempted many times to upgrade via the Update Manager rather than an iso image which is still the old dapper kernel. Is there any suggestion/tips I should beaware of or is it rather straight forward? Is the copying of the new kernel and ramdisk image the very last thing before a reboot? thanks for being adventurous!

---

### Post by smileyme on 2006-07-28
The update was very straight forward, but took several hours, and yes, copying the kernel and ramdisk image was the very last thing I did before rebooting. The Update Manager gives the option to reboot or close. I chose "close", then proceeded to copy the kernel and ramdisk image to the OS 9 partition, followed by rebooting.

I haven't had time to play with it though, so don't know anything about its stability.

Rick :)

---

### Post by Uta on 2006-07-29
I did manage to update to Dapper but not via the Update Manager. My update via that method bombed near the end, so I reinstalled, clean install of Dapper via the ALternate Cd. That went fairly well, my system is absolutely more stable than it was with 5.10 BUT there are a few nagging issues. I am using the  2.6.15-23-powerpc kernel in BootX because after updating to the latest kernel  2.6.15-26-powerpc and copying it over to the System Folder and choosing it in bootX it won't load, it can't find the hdg7 (which is where Dapper is installed) it hangs at loading the root system files. I am not sure what to do other than trying to update the kernerl again? Also I had sound working perfectly in 5.10 but no sound in Dapper, my sound card is not listed anywhere? I would like to know what kernel version other OWM people are using in BootX and if you have sound. Thanks
Edit: I did manage to update to the latest kernel and got BootX to utilize it, which is great but still no sound. Does anyone have sound with Dapper on an OWM? Thanks.
Edit: I got sound working. For some reason snd_powermac module was not being loaded, so I added it to my /etc/modules so on boot it loads, I have beautiful sound and my 1996 PowerTower Pro is stable with  the latest PPC Ubuntu kernel. Amazing! Thank You developers--

---

