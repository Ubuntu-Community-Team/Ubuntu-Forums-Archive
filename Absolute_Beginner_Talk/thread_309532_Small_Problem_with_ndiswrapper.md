---
title: "Small Problem with ndiswrapper"
date: 2006-11-29
forum: Absolute Beginner Talk
---

### Post by Cameron. on 2006-11-29
I just installed Ubuntu the other day, and after sorting everything else out, Wireless is giving me some troubles.](*,) I have an Atheros 5211 wireless adapter in this laptop, so it isnt natively supported.(as far as i can tell) I installed ndiswrapper easily, got the drivers to work, but one of the later commannds in the article are coming up with errors.

When i attempt step 3: Loading the module i get this. 

turkey@Turkey:~$ sudo depmod -a
turkey@Turkey:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

What do I need to do to fix this? Or can I just proceed to the next step and hope for the best?
Thanks for any help in advance.


Edit: I just read something else, Should i be using 6.10? Or 6.06? Will 6.06 have drivers for my hardware? In essence should I downgrade to 6.06?

---

### Post by MasterOfDisaster on 2006-11-29
For me, running 'modprobe rt2570' where rt2570 is the name of the wireless module you are loading and then 'modprobe ndiswrapper' worked.

---

### Post by msak007 on 2006-11-29
> **Cameron. said:**
> I just installed Ubuntu the other day, and after sorting everything else out, Wireless is giving me some troubles.](*,) I have an Atheros 5211 wireless adapter in this laptop, so it isnt natively supported.(as far as i can tell) I installed ndiswrapper easily, got the drivers to work, but one of the later commannds in the article are coming up with errors.

When i attempt step 3: Loading the module i get this. 

turkey@Turkey:~$ sudo depmod -a
turkey@Turkey:~$ sudo modprobe ndiswrapper
FATAL: Error inserting ndiswrapper (/lib/modules/2.6.17-10-generic/kernel/drivers/net/ndiswrapper/ndiswrapper.ko): Invalid argument

What do I need to do to fix this? Or can I just proceed to the next step and hope for the best?
Thanks for any help in advance.


Edit: I just read something else, Should i be using 6.10? Or 6.06? Will 6.06 have drivers for my hardware? In essence should I downgrade to 6.06?
Well first to answer your edit, 6.06 (Dapper) is an "LTS" release meaning it's supposed to be more stable, while 6.10 (Edgy) was supposed to be an edgier release, trying out new and (possibly) unstable things to lay the groundwork for future releases leading to another LTS release in a few years. To be honest Edgy has been as stable (if not moreso) than Dapper and I've had absolutely no issues. Worth a try, and if you have any issues you can always install Dapper.

Now in response to the error you're getting. I assume since you've installed ndiswrapper that the machine has an alternative way of connecting to get new packages? If so, install **ndiswrapper-utils-1.8** and try again. I got the same error until I installed that version of the utils for some reason. Try it out and see if helps.

---

### Post by Cameron. on 2006-11-29
> **msak007 said:**
> Now in response to the error you're getting. I assume since you've installed ndiswrapper that the machine has an alternative way of connecting to get new packages? If so, install **ndiswrapper-utils-1.8** and try again. I got the same error until I installed that version of the utils for some reason. Try it out and see if helps.


Well, I can connect via a network cable and the ethernet port, however I was updating this with the DVD iso I downloaded. TO try your suggestion, I figured I would just insert the dvd. However now it wont open the upgrade browser as it did previously. I'm not really sure what to do now. Is there a command to update to 1.8 in the Terminal?

---

### Post by msak007 on 2006-11-29
Well it's not really an "upgrade" to anything you have installed, as it's a separate ndiswrapper package. I don't have the DVD so I'm not sure what comes on it, but you can try the following:

1. Open a terminal / console
2. Type ```
sudo aptitude install ndiswrapper-utils-1.8
```

If it's on the DVD, it will find and install it. I don't believe there were any upgrades to that package since Edgy was released, so it's safe to use the version on the DVD without being outdated. Of course once you do get it working (and you *will* get it working :), you should switch to online repositories and update all your software.

---

### Post by Cameron. on 2006-11-29
Thanks for all the help.
I've done all the steps correctly, but it still does not recognise my wireless card. There are a few options in the drop down menu (wifi0, and ath0. These are both listed as unknown devices) and as such I cannot change and settings for them 
It seems I may be tethered by a network cable until i gain more understanding of Ubuntu

---

### Post by msak007 on 2006-11-29
So you were able to find the package on the DVD and install it? If you did install it, did you try the modprobe again to insert the ndiswrapper module?

---

### Post by Cameron. on 2006-11-29
> **msak007 said:**
> So you were able to find the package on the DVD and install it? If you did install it, did you try the modprobe again to insert the ndiswrapper module?


I did insert the module again, but it still will not recignise my wireless.](*,)

---

### Post by msak007 on 2006-11-29
> **Cameron. said:**
> I did insert the module again, but it still will not recignise my wireless.](*,)If you inserted the module and didn't get any errors, post the output of
```
ndiswrapper -l
``` (that's a lower case "L", not an I). This will tell us if the proper driver was even installed. Once we have the output of that and verify that it was installed, type
```
iwconfig
```This will show us which network adapters in your machine have wireless capabilities, and what they are called. Post the output of that as well. Once we verify that your card is indeed installed and shows up, type the following in the terminal:```

sudo aptitude install network-manager network-manager-gnome
```Network Manager (in case you haven't heard of it) is an awesome utility to manage wireless networks and makes connecting so much easier. I'm not sure if it's on the DVD, so if it isn't you will need to connect via ethernet and install it from the repositories. Finally, once you install Network Manager, start the app by typing ```
nm-applet
``` which will put the Network Manager applet in your System Tray. Try that, and let us know what the result is.

---

### Post by Cameron. on 2006-11-30
> **msak007 said:**
> If you inserted the module and didn't get any errors, post the output of
```
ndiswrapper -l
```
> Installed drivers:
net5211         driver installed, hardware present 

```
iwconfig
```
> iwconfig
lo        no wireless extensions.

sit0      no wireless extensions.

ath0      IEEE 802.11g  ESSID:"Cameron Home"  
          Mode:Managed  Frequency:2.437 GHz  Access Point: Not-Associated   
          Bit Rate:54 Mb/s   
          Link Quality:0  Signal level:0  Noise level:0
          Rx invalid nwid:0  Rx invalid crypt:0  Rx invalid frag:0
          Tx excessive retries:0  Invalid misc:0   Missed beacon:0

eth0      no wireless extensions.

I did the other steps and now i have to little icons in the system tray. woops :-k

Also is it possible for the wireless connection to use a pre shared WPA key. for its extra security?

---

### Post by Cameron. on 2006-12-03
Please can anyone help me?

---

