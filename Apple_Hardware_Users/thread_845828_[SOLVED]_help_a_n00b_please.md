---
title: "[SOLVED] help a n00b please?"
date: 2008-07-01
forum: Apple Hardware Users
---

### Post by spencercarran on 2008-07-01
Hey,
I've got a MacBook (Intel Core 2 Duo, 2.2 GHz) and was trying to set up Ubuntu and and OSX on a dual-boot system. I failed, repeatedly. After installing Ubuntu, I would go to the boot menu and only have OSX as an option. I followed the instructions in an online guide for installing Ubuntu on a MacBook, but after what seems to be a successful installation of Ubuntu, I still only have OSX. I did finally manage to get Ubuntu running (by telling it to use my entire hard disk, thus deleting OSX) but I couldn't get internet access on Ubuntu, so I had to start over with OSX again.

So, I really have two questions:
1)How exactly do I partition the hard drive properly for a dual-boot? When I re-installed OSX, I left 75 gig of free space to Ubuntu in later. Still haven't gotten it to work.

2)How do I configure Ubuntu for a wireless network? It's in "roaming mode" but doesn't seem to find my wireless network.

I'm using Ubuntu 8.04AMD64 (well, trying to).

Anyone wanna help the n00b?:confused:

---

### Post by lisati on 2008-07-01
1) Assuming that you didn't put anything in the 75G partition when you reainstalled OSX, and that OSX is still there: When the installation process asks how you want to set up your partition, use "Guided - use largest contiguous free space".

2) Might be best to wait until you've figured out getting both Ubuntu & OS-X on your machine......

---

### Post by spencercarran on 2008-07-01
> **lisati said:**
> 1) Assuming that you didn't put anything in the 75G partition when you reainstalled OSX, and that OSX is still there: When the installation process asks how you want to set up your partition, use "Guided - use largest contiguous free space".
I tried that the first attempt after reinstalling OSX. Still gave me just one option in the boot-up menu.:confused:If I install Ubuntu and then restart as it says (not holding down alt/opt key or anything) will it boot in Ubuntu by default?

> **lisati said:**
> 2) Might be best to wait until you've figured out getting both Ubuntu & OS-X on your machine......
Yeah, I figured the same thing. But I also thought that if I got an internet connection on Ubuntu, I could either switch to it exclusively or try to repartition my disk from that side, since BootCamp doesn't seem geared to being Linux-friendly.

---

### Post by cyberdork33 on 2008-07-01
> **spencercarran said:**
> I tried that the first attempt after reinstalling OSX. Still gave me just one option in the boot-up menu.:confused:If I install Ubuntu and then restart as it says (not holding down alt/opt key or anything) will it boot in Ubuntu by default?

The MBR gets wiped. Install rEFIt first, you can uninstall it after you fix everything.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

---

### Post by spencercarran on 2008-07-01
> **cyberdork33 said:**
> The MBR gets wiped. Install rEFIt first, you can uninstall it after you fix everything.
[http://ubuntuforums.org/showthread.php?t=767677](http://ubuntuforums.org/showthread.php?t=767677)

Thanks, it worked!\\:D/ Is there a reason I would want to uninstall rEFit? I like the boot menu it gives, and since it's working now, I'd rather not mess with it too much.

Still need to figure out how to get Ubuntu to recognize my wireless network, but at least now I have Ubuntu on my machine and can work from there. Any tips?

---

### Post by cyberdork33 on 2008-07-01
> **spencercarran said:**
> Thanks, it worked!\\:D/ Is there a reason I would want to uninstall rEFit? I like the boot menu it gives, and since it's working now, I'd rather not mess with it too much.
No, I just thought you didn't want it since you hadn't already installed it.

> **spencercarran said:**
> Still need to figure out how to get Ubuntu to recognize my wireless network, but at least now I have Ubuntu on my machine and can work from there. Any tips?
Depending on the Macbook version you have, you could different wifi hardware.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

---

### Post by spencercarran on 2008-07-02
> **cyberdork33 said:**
> Depending on the Macbook version you have, you could different wifi hardware.
[https://help.ubuntu.com/community/MacBook](https://help.ubuntu.com/community/MacBook)
[https://help.ubuntu.com/community/MacBook_Santa_Rosa](https://help.ubuntu.com/community/MacBook_Santa_Rosa)

Crap, I have the Santa Rosa one. The instructions you linked to require that I get ndiswrapper through the add/remove application function, which I can't do because I don't have internet access on Ubuntu.](*,) Lovely little Catch-22 I've been caught in. Any advice on a work-around? What I've read so far gives me the impression that ath5k and OpenHAL do  not work for the Macbook's Wifi chip, but I could be wrong there.

---

### Post by cyberdork33 on 2008-07-02
> **spencercarran said:**
> Crap, I have the Santa Rosa one. The instructions you linked to require that I get ndiswrapper through the add/remove application function, which I can't do because I don't have internet access on Ubuntu.](*,) Lovely little Catch-22 I've been caught in. Any advice on a work-around? What I've read so far gives me the impression that ath5k and OpenHAL do  not work for the Macbook's Wifi chip, but I could be wrong there.
yep, besides, if you have the Santa Rosa Machine, you have a Broadcom card anyway, not an Atheros card (which madwifi is for). That's why you have to use ndiswrapper.

Plug your cable in temporarily to get the package(s) you need. You can also install some packages from the LiveCD. just add it as a source in your sources.list file.

---

### Post by rifak on 2008-07-02
how can you tell if you have a santa rosa or the other version. i bought a black macbook in january of 2008, brand new from an apple store...and i dont know how to figure out which one i have.

---

### Post by spencercarran on 2008-07-03
@cyberdork: Yeah, but I don't have a cable. Just wireless right now. I'm going to try downloading ndiswrapper, putting it on a flash disk, and then transferring it over to Ubuntu.

@switham: Yours is a Santa Rosa. It's almost certainly the exact same model as mine (I got a new black MacBook a month before you did). Apple Menu->About this Mac->More info (leads to System Profiler) and the second line of info is "model identifier." 3.1 and on is Santa Rosa.

---

### Post by rifak on 2008-07-03
alright, thats what i thought. i tried to use the instructions on the ubuntu help page, and it did not work for me. i put the whole line in (wget ...) and then followed with  (sudo ndiswrapper...) and it says its unable to unzip R151517.EXE file...which i thought was weird anyway. i dont know, i cant figure this out.

---

### Post by rifak on 2008-07-03
yeah, i checked and have a macbook3,1. so i followed the santa rosa instructions here [https://help.ubuntu.com/community/Macbook8.04?highlight=(Macbook](https://help.ubuntu.com/community/Macbook8.04?highlight=(Macbook)) and cannot figure it out. i placed the driver directory, unzipped the file, ran ndiswrapper. when i run the sudo ndiswrapper -l command now, it says this:

bcmwl5 : driver installed
	device (14E4;4328 ) present

is that right? i added the line to my start-up module document. but when i restart and log back in, nothing happens and i still have to have my ethernet cable in. i dont know, this is getting pretty frustrating. why cant madwifi get on this?

---

### Post by spencercarran on 2008-07-03
Well, our Santa Rosa machines don't use Madwifi, as CyberDork pointed out. I'm still trying to figure it out too, I'll let you know if I find something that works for me.

---

### Post by cyberdork33 on 2008-07-03
> **spencercarran said:**
> @switham: Yours is a Santa Rosa. It's almost certainly the exact same model as mine (I got a new black MacBook a month before you did). Apple Menu->About this Mac->More info (leads to System Profiler) and the second line of info is "model identifier." 3.1 and on is Santa Rosa.
yep. If you have a new macbook, it should be a MacBook4,1

that output looks right. It should be working. If you have the Ethernet cable plugged in, it will default to that. Unplug it, then click on the network manager icon to select the network. If you still don't see networks, then post back.

---

### Post by rifak on 2008-07-03
@cyberdork33: when i unplug the cable, an exclamation mark comes up in the network monitor icon. i click on "edit wireless connection" and a window pops up with nothing in it. all the boxes are blank and what not. i then try the manual configuration option, under the connections part is options for the wired network, and a point to point connection.

---

### Post by cyberdork33 on 2008-07-03
what is the output of 'ifconfig'?

---

### Post by rifak on 2008-07-04
@cycberdork33: output of ifconfig...

eth0      Link encap:Ethernet  HWaddr 00:1e:c2:02:c7:96  
          inet addr:10.248.0.118  Bcast:10.248.0.255  Mask:255.255.255.0
          inet6 addr: fe80::21e:c2ff:fe02:c796/64 Scope:Link
          UP BROADCAST RUNNING MULTICAST  MTU:1500  Metric:1
          RX packets:207094 errors:0 dropped:0 overruns:0 frame:0
          TX packets:134822 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:1000 
          RX bytes:118369046 (112.8 MB)  TX bytes:16158533 (15.4 MB)
          Interrupt:17 

lo        Link encap:Local Loopback  
          inet addr:127.0.0.1  Mask:255.0.0.0
          inet6 addr: ::1/128 Scope:Host
          UP LOOPBACK RUNNING  MTU:16436  Metric:1
          RX packets:1992 errors:0 dropped:0 overruns:0 frame:0
          TX packets:1992 errors:0 dropped:0 overruns:0 carrier:0
          collisions:0 txqueuelen:0 
          RX bytes:99600 (97.2 KB)  TX bytes:99600 (97.2 KB)

---

### Post by spencercarran on 2008-07-06
@switham: This thread [http://ubuntuforums.org/showthread.php?t=849947]("http://ubuntuforums.org/showthread.php?t=849947")has good help on getting wifi to work on the Santa Rosa MacBook. Use the guide linked to, and follow "anewguy's" instructions for getting ndiswrapper from the disc. That worked for me, and we're on almost identical hardware.

---

### Post by cyberdork33 on 2008-07-08
well, it looks as though you loaded the windows driver, but ndiswrapper is not loaded into the kernel. Try doing:
```
sudo modprobe ndiswrapper
```
then the wlan0 device should be available in the output of ifconfig.

---

### Post by rifak on 2008-07-08
@cyberdork: thank you so much. it worked! awesome.

---

### Post by cyberdork33 on 2008-07-08
> **switham said:**
> @cyberdork: thank you so much. it worked! awesome.
Just a note, if it is broken again on reboot, you need to add 'ndiswrapper' to the /etc/modules file. Then it will be loaded automatically at boottime.

---

### Post by rifak on 2008-07-08
this is what i added to modules file:

lp mousedev psmouse ndiswrapper

is this right? or do i just need a 'ndiswrapper' line?

---

### Post by cyberdork33 on 2008-07-08
> **switham said:**
> this is what i added to modules file:

lp mousedev psmouse ndiswrapper

is this right? or do i just need a 'ndiswrapper' line?

Those are several different modules. You should only need 'ndiswrapper' and I think each module should go on it's own line. If those other items were there already, do not remove them.

---

