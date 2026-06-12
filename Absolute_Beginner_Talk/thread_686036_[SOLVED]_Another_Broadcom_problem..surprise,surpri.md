---
title: "[SOLVED] Another Broadcom problem..surprise,surprise... :("
date: 2008-02-02
forum: Absolute Beginner Talk
---

### Post by myddewji13 on 2008-02-02
Hi,
Its been 2 days....i just installed ubuntu b/c i've heard its awesome and it is...except for the fact that i cant get the internet up. I've basically spent the last 48 hrs looking throughh all the forums and posts, searching on google, and trying everything humanely possible including yelling at my computer (yes this is driving me crazy)... anyway... basically i have a hp pavilion dv2708ca laptop with preloaded windows vista premium...i hate vista so i decreased the partition etc and now have a double boot goin...after reading through endless posts/complaints/solution (none of which work for me)..i have sort of figured out the following:

1)according to the readout on ubuntu i have the Broadcom 4310 card... #$@$ <---ignore that

2) i have ndiswrapper installed...latest version i think

3)i have the graphical utility thing that uses ndiswrapper - basically point it at driver and viola problem solved (i wish)

4) it works fine on windows vista

Anyway,,,,u've probably heard this and will hopefully be able to help me... i am not posting this because im too lazy to go through the forums..im posting this b/c im about to give up on ubuntu...so HELLLLP ME PLEASE!!


ps...i think (not that i noe much) that my biggest prob is finding the right driver...all the ones ive tried seem to be for 431x models but not specifically for the 4310 model...

---

### Post by azimuth on 2008-02-02
Which verion of Ubuntu did you install? 7.10 has the broadcom driver in the restricted drivers manager.

---

### Post by myddewji13 on 2008-02-02
i noe...been there done that..(yea i have 7.10)...when i try to use the restricted drivers manager..i get a message saying 'Your hardware does not need any restricted drivers,"
..

---

### Post by azimuth on 2008-02-02
Things a ran into were having to blacklist the BMC43xx driver and 32 bit drivers would not work on my amd64 install. Dell did have the 64 bit drivers though.

---

### Post by azimuth on 2008-02-02
Have you seen this guide yet?  [http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

---

### Post by myddewji13 on 2008-02-02
ok...i just went to the hp site and downloaded the drivers for vista (the 32bit and the 64bit install package is the same...they have nothing for xp)...and there is a little bit of good news...but still a lot of bad...ndiswrapper managed to use bcmwl6.inf and now the hardware is actually recognized....but..now im stuck...no wireless connection shows up in the network config...no idea wat to do...help!!

---

### Post by azimuth on 2008-02-02
You may be ready for this tutorial now [http://ubuntuforums.org/showthread.php?t=571188](http://ubuntuforums.org/showthread.php?t=571188)

---

### Post by myddewji13 on 2008-02-02
it comes back as UNCLAIMED (as per tutorial) ..so driver isnt installed properly?....now wat am i supposed to do?

---

### Post by macogw on 2008-02-02
All I do to make them work, since the driver is included and not restricted, but the firmware is restricted, is download the firmware.  I uploaded it so I know where it is always :)
```
wget http://macoafi.googlepages.com/firmware.tar.gz
tar xf firmware.tar.gz
sudo cp firmware/* /lib/firmware/

```
When I've done this before (ex: on the laptop I'm using right now), it's worked immediately, no rebooting.

---

### Post by myddewji13 on 2008-02-02
nope...no luck...any other ideas?

---

### Post by macogw on 2008-02-02
is bcm43xx blacklisted or running?  you can see if it's running with ```
lsmod | grep bcm
``` and if it's not, start it with ```
sudo modprobe bcm43xx
```

---

### Post by myddewji13 on 2008-02-03
still nothing...

---

### Post by myddewji13 on 2008-02-05
ok...figured out wats wrong... basically... ubuntu recognizes it as broadcom even though its not...windows uses broadcom drivers for it...but after phoning hp i was told the only reason it seems to be a broadcom WLAN is b/c of the driver...the actual hardware is Intel PRO/Wireless 3945BG.....if anyone could get this up and running i would be extremely grateful... in the meantime im using a plug and play x-micro usb dongle which seems to work perfectly!!!

---

### Post by azimuth on 2008-02-05
the ipw3945 module may work with this card [http://hardware4linux.info/module/ipw3945/](http://hardware4linux.info/module/ipw3945/)

---

### Post by myddewji13 on 2008-02-05
i dont know how to install it... :(

---

### Post by azimuth on 2008-02-05
> **myddewji13 said:**
> i dont know how to install it... :(

Just remember, Google is your friend. Now that you know what you're looking for, it will be easier.

---

### Post by exsencon on 2008-02-05
> **myddewji13 said:**
> nope...no luck...any other ideas?

This is what I did,it worked for me.
dell laptop inspiron 1501 Broadcom 4311
dual boot WinXP and Kubuntu 7.10

I install ndiswrapper in the package manager
Then I use the command lines, not the graphical ndisgt or whatever(it didn't work for me)
Uninstall fwcutter

My first line I got from a slackware forum:

sudo modprobe -r bcm43xx 
then:
sudo ndiswrapper -i (path of your driver)
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
hope it helps,it worked for me

---

### Post by myddewji13 on 2008-02-05
ok...nothings working...any help?

---

### Post by azimuth on 2008-02-05
> **exsencon said:**
> This is what I did,it worked for me.
dell laptop inspiron 1501 Broadcom 4311
dual boot WinXP and Kubuntu 7.10

I install ndiswrapper in the package manager
Then I use the command lines, not the graphical ndisgt or whatever(it didn't work for me)
Uninstall fwcutter

My first line I got from a slackware forum:

sudo modprobe -r bcm43xx 
then:
sudo ndiswrapper -i (path of your driver)
ndiswrapper -l
sudo depmod -a
sudo modprobe ndiswrapper
sudo ndiswrapper -m
hope it helps,it worked for me

You must not have read the whole thread. The OP does not have a Broadcom chip, it is being miss read as such. The supplier has assured him that it is an intel chip. If he has BMC43xx in a wrapper then it will never work until the Broadcom driver is blacklisted and the correct module is used. I am not proficiant enough with the command line to walk him through this. Maybe now that he knows what his card is and that he already has the wrong module in place, he could repost in the Networking or Hardware forums and reference this thread.

---

### Post by myddewji13 on 2008-02-06
ok....i got my card working!!!!...used the graphical utility for ndiswrapper ... first dragged the  .sys file and then when it prompted me to get the .inf file instead i popped that in....wireless now works perfectly...Accept (here it is :( ) ... i have to reinstall the driver everytime i restart...anyway to make ndiswrapper permanent...?

---

### Post by myddewji13 on 2008-02-06
vm....just searched 'open ndiswrapper at startup' on forums to get the fix

---

### Post by azimuth on 2008-02-06
Glad you found your fix. It may have been a frustrating experience at times, but think how much faster you learned your system than if it had been plugNplay.

---

### Post by macogw on 2008-02-08
That's extremely unusual.  I have a ipw3945abg too, and it was recognized properly by every distro I've installed (umm...that'd be Ubuntu Dapper through Gutsy, Debian Etch, Fedora Core 6, and some version of Sabayon).  The distros that are OK with including "non-free" firmware (Ubuntu and Sabayon) had it set up automatically.  The other two just required installing the ipw3945 modules (as someone else said), but no ndiswrapper.  That card has very good Linux drivers.

---

