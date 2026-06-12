---
title: "Ubuntu on dell 640m / e1405"
date: 2006-09-06
forum: Absolute Beginner Talk
---

### Post by arijarot on 2006-09-06
I would like to hear anyones recent experiences, comments, ... with the dell inspiron 640m / e1405 ... anything would be appreciated... thanks ;)

---

### Post by tht00 on 2006-09-06
> **arijarot said:**
> I would like to hear anyones recent experiences, comments, ... with the dell 640m / e1405 ... anything would be appreciated... thanks ;)

I've got the Dell e1505, which is essentially the same.  I haven't really had any issues (had it about 2 weeks).  So far, wireless(I have the Intel PRO wireless card -- it auto detected and installed the driver), though, it has been a bit unstable.  I just reinstalled Dapper, and it seems to be much better so far, and I am seeing some weird visual artifacts this time around (I likely just need to install the nvidia driver for my card).

Other than that, everything was detected fine and worked straight up... unlike when I reinstalled Windwos.  Nothing detected with XP... resolution wrong, sound broken, not even the LAN card was configured to work. :lol: 

Edgy is a little 'rough around the edges', which is expected for now.

So far, completely positive in the Linux world.:)

---

### Post by arijarot on 2006-09-06
> **tht00 said:**
> I've got the Dell e1505, which is essentially the same.  I haven't really had any issues (had it about 2 weeks).  So far, wireless(I have the Intel PRO wireless card -- it auto detected and installed the driver), though, it has been a bit unstable.  I just reinstalled Dapper, and it seems to be much better so far, and I am seeing some weird visual artifacts this time around (I likely just need to install the nvidia driver for my card).

Other than that, everything was detected fine and worked straight up... unlike when I reinstalled Windwos.  Nothing detected with XP... resolution wrong, sound broken, not even the LAN card was configured to work. :lol: 

Edgy is a little 'rough around the edges', which is expected for now.

So far, completely positive in the Linux world.:)

re wireless: what do you mean by unstable, for example? 

have you used sleep/hibernate?

are you on the core duo or core 2 duo?

---

### Post by tht00 on 2006-09-06
> **arijarot said:**
> re wireless: what do you mean by unstable, for example? 

Sometimes it's just getting connections to work.  My University's wireless was hit-and-miss last installation (though, I think I broke something with the wireless that time).  Sometimes it would connect, sometimes it wouldn't, but it would always take 15-30 seconds to make that connection.  Now, it's a quick connection(~5 sec), though, I've had it not connect once (bad signal though).

Also, in the dorm room, I have fine signal, and everything worked fine... until I went to scp something from my desktop.  It started downloading, and then it lost signal about 10 seconds into the transfer.  Finally got it reconnected, tried again.  This time, about 20 secs and it dropped again.  I haven't had this problem after the reinstall though.

One last incident is at a friend's dorm room.  I can't get it to connect to the wireless at all, and I'm not sure why.  It's a very similar setup to what my room has.  I haven't tracked down to where the problem is, whether it be hardware/software or what.  I'm using the network-manager-applet, as it's the easiest way to setup WPA, but it's hard to troubleshoot anything from there.  I'm guessing it's related to the WPA, but I can't be sure yet. 

So yeah.  That's why I used 'unstable', as that's how it was the first time around.

> **arijarot said:**
> have you used sleep/hibernate?

are you on the core duo or core 2 duo?

Hibernate worked on the first install just fine.  Haven't tried it this time around, though, I had my boot time to ~30 sec on my last install.  I didn't use hibernate much.  Sleep seems to be disabled at the moment.  Haven't tried it yet.

1.6GHz Core Duo.

It runs very cool too (idle/light use < 40C, 45C right now).

---

### Post by arijarot on 2006-09-06
> **tht00 said:**
> Sometimes it's just getting connections to work.  My University's wireless was hit-and-miss last installation (though, I think I broke something with the wireless that time).  Sometimes it would connect, sometimes it wouldn't, but it would always take 15-30 seconds to make that connection.  Now, it's a quick connection(~5 sec), though, I've had it not connect once (bad signal though).

Also, in the dorm room, I have fine signal, and everything worked fine... until I went to scp something from my desktop.  It started downloading, and then it lost signal about 10 seconds into the transfer.  Finally got it reconnected, tried again.  This time, about 20 secs and it dropped again.  I haven't had this problem after the reinstall though.

One last incident is at a friend's dorm room.  I can't get it to connect to the wireless at all, and I'm not sure why.  It's a very similar setup to what my room has.  I haven't tracked down to where the problem is, whether it be hardware/software or what.  I'm using the network-manager-applet, as it's the easiest way to setup WPA, but it's hard to troubleshoot anything from there.  I'm guessing it's related to the WPA, but I can't be sure yet. 

So yeah.  That's why I used 'unstable', as that's how it was the first time around.



Hibernate worked on the first install just fine.  Haven't tried it this time around, though, I had my boot time to ~30 sec on my last install.  I didn't use hibernate much.  Sleep seems to be disabled at the moment.  Haven't tried it yet.

1.6GHz Core Duo.

It runs very cool too (idle/light use < 40C, 45C right now).

thanks for the details on your wireless experiences...one of my secondary connections will be in my university's "hot spot" around campus...

i don't know if this is helpful, but currently, when i am having a flaky connection, it helps to restart the access point (if you have access to this it help ;))... this works for me 8/10 times.

thanks for the info:)

---

### Post by alan53 on 2006-09-07
I am reasonably happy with my Dell/Ubuntu experience.  I'm using the 686 architecture and am finding many applications don't like this.  So far, I haven't found any graphics applications that operate smoothly,(including via Wine)except for Picasa which doesn't really count.

No problems with wireless, sound seems fine, had to play with video driver updates to get 1400 X 900 screen res.  I believe the graphic and video lapses I'm experiencing will disappear once Intel/Linux catch up with dual processors.

Alan

---

### Post by arijarot on 2006-09-07
> **alan53 said:**
> I am reasonably happy with my Dell/Ubuntu experience.  I'm using the 686 architecture and am finding many applications don't like this.  So far, I haven't found any graphics applications that operate smoothly,(including via Wine)except for Picasa which doesn't really count.

No problems with wireless, sound seems fine, had to play with video driver updates to get 1400 X 900 screen res.  I believe the graphic and video lapses I'm experiencing will disappear once Intel/Linux catch up with dual processors.

Alan

what is the nature of the 686 problem? is it common to have problems with the 686 or is this specific to the 640m? did you use the 915resolution for the screen?

---

### Post by LesleyW on 2006-09-19
I've just bought a 640m (arrived yesterday). I haven't installed Ubuntu yet, but I booted the Live CD and found it needed to be started in safe mode. I expect I'll spend a bit of time trawling through these forums and finding out how to configure the video correctly and checking for other issues before I actually go ahead with the installation. Excited but cautious!

---

### Post by iridesce on 2006-10-06
Just got the 640m today and of course am up late getting it to work.  Really like the 10 x 13 footprint ( it fits in my puter backpack ) as well as the Core2Duo processor.

*** Mine came _without_ XP disk *** a definate oops moment when I repartioned it installing ubuntu 6.06 - fortunately my partner had an old Dell disk ...

Installing ubuntu 6.06 

- Had to use the safe graphics mode, after that installation went fine.

Found [http://ubuntuforums.org/showthread.php?t=189086&highlight=640m](http://ubuntuforums.org/showthread.php?t=189086&highlight=640m) 
which seems to be a good thread


- Just found this link on the intel site for possible wireless drivers

[http://www.intel.com/support/notebook/sb/cs-006408.htm](http://www.intel.com/support/notebook/sb/cs-006408.htm)

and its way too late to start on it,  more later

Good luck

---

### Post by iridesce on 2006-10-06
_

---

### Post by Sgood1971 on 2006-10-16
My E1405 works great after installing 915resolution.

I did have to use ndiswrapper and fwcutter in order to get the wireless to work. The fn+F2 keyboard shortcut did not work to turn the wireless radio on until I used fwcutter. I too am using the 686 kernel, but I have seen no problems with it. 3D accelleration is almost non existant, but I see that intel has drivers for the 945G, so I will be giving that a try soon. All in all, I would say it's a mostly positive expierience.

---

### Post by ausbuntu on 2006-11-15
Would anyone be willing to put up a quick guide on installation? I've tried booting in safe graphics mode but still X server crashes and then hangs.. is this normal? are there any extra settings to be wary of?

Thanks in Advance

---

### Post by Sgood1971 on 2006-11-15
> **ausbuntu said:**
> Would anyone be willing to put up a quick guide on installation? I've tried booting in safe graphics mode but still X server crashes and then hangs.. is this normal? are there any extra settings to be wary of?

Thanks in Advance

Here is what I did, your mileage may vary.

I used the alternate install CD and selected text install.

I then Went through all the motions, and it gets to the point where the screen will go black, this is ok, just watch the HD activity light until it stays out for a while. This may take a little time, be patient.

If you think it has quit writing, press enter and if the cd ejects, you are good to go.

Remove CD and press enter again and the machine will reboot.

At the GRUB Menu, select recovery mode. and then

```
sudo vi /etc/apt/sources.list
```

scroll through the file using the arrows and remove and # symbols for repos using the "X" key.

Press :WQ to write the file and quit.

Then do

```
sudo apt-get update
```
next do
```
sudo apt-get install 915resolution
```
when that is done,
```
sudo reboot
```

when grub comes back up just boot the default entry.

You will want to install the 686 SMP kernel to take advantage of your core duo and see [this]("http://ubuntuforums.org/showthread.php?t=185174") thread in order to get wireless working.

Hope this helps. I am posting from work from memory, but I think I covered it all.

Good luck.

---

### Post by ausbuntu on 2006-11-16
Thanks for the quick reply,

I've got it working now but the 686-smp kernel won't boot up.. Kernel Panic: VFS: unable to mount root on 08:06

The inital edgy installation from alternate cd went-of without a hitch.

If anyone has solved the booting issue i'd like to know how... im currentlu using the same booting parameters for the 386 and 686 kernels the 386 loads yet the 686 will not.

Thanks

---

### Post by ausbuntu on 2006-11-17
Okay,

So here goes.. i've been tryign to updrage to a 686-smp kernel and after many many hrs i've come accross that if you install edgy on the 640m the dual processors will work without the upgrade. im not sure if you need to do the upgrade, probably not.

Cheers 
All

---

### Post by Sgood1971 on 2006-11-17
I am sorry, since I am using Dapper (no need to upgrade, I am happy where I am) I didn't stop to think that you might be installing Edgy.

---

### Post by ausbuntu on 2006-11-18
> **Sgood1971 said:**
> I am sorry, since I am using Dapper (no need to upgrade, I am happy where I am) I didn't stop to think that you might be installing Edgy.

No no.. your guide was great without it I'd probably still be stuck on my 915resolution problems. Finally i've also got wireless working as well... hope no more issues arise lol

Cheers 
All

---

### Post by jlcazarez on 2006-11-21
Intel Core 2 duo is EM64T, do I have to install the 64bit PC or the x86?

Thanks

---

### Post by eco751 on 2006-11-29
Still having trouble with ACPI events, on some level or another.

The key things to know: 915resolution and ndiswrapper (if you have the Dell 1390 WLAN card, which is a Broadcom 4311 and not properly supported by the default kernel).  I had to [install a newer version of ndiswrapper]("http://wiki.waningsun.net/index.php?title=Dell_E1405_and_Broadcom_4311_wireless_HOWTO") from source...

I'm trying to make this page useful: 
[https://wiki.ubuntu.com/LaptopTestingTeam/DellInspironE1405]("https://wiki.ubuntu.com/LaptopTestingTeam/DellInspironE1405")

---

### Post by johnnyloot on 2006-12-05
I had an E1505 and after a good install but some post install issues (graphics, wireless) I stumbled across....

[6400/e1505 Complete Guide]("http://www.ubuntuforums.com/showthread.php?t=257684&highlight=dell+6400+complete") 

Boy was this my saving grace, step by step though everything, really simplified everything for me.

Problem is my laptop got stolen, so now im on the market for a new one and the 640m/e1405 seems perfect (found the 1505 a bit big/heavy for my taste).

Only issue is that with the 640m you cannot upgrade video (default is Intel 950). With 1g of ram I figure I can allocate some more to the video card, any1 do this?
I am looking to run beryl/compiz on mine and Im assuming that will take some more video power. If I give the vid card something like 128M should that be sufficient? Any opnions?

---

### Post by tschneiter on 2007-02-01
Ive run beryl with no problems on my 640m (with i950 graphics). I turned of blurring, since it added a lag when trying to drag or opacify a window. Besides that though, transparency and all the other effects worked flawlessly even with a ton of windows open. 
Only problems I had was dealing with acpi business, like sleep-mode.

---

### Post by iMav on 2007-02-22
General e1405 build quality question.

How is the keyboard on this (and other modern Inspiron) laptop?  My last two Dell's were Inspiron 8600 and 3800 and both of them had horrible keyboards.  I love the keyboards on ThinkPads and my current MacBook...How do the Dell keyboards compare now days?

I'm in the market for a Linux laptop and, even though I told myself I would not buy a Dell, the low prices are such that I HAVE to at least investigate the option.

---

### Post by singetak on 2007-02-22
iam satisfied with it.Except that my wireless connection doesn't work.
Another problem is that the CPU says 50% usage when idle

---

### Post by fueg0 on 2007-04-29
I've been running Feisty Fawn now for about a week. I'm pretty disappointed that I've had to work so hard to get the graphics from 1028x764 to 1440x900, and the wireless is really hit & miss.

I'm running an e1405:
 core2 duo processor T7200
 1gb 667mhz DDR2
 14.1" WXGA+ w/truelife
 80gb 7200rpm drive
 dvd +rw
 intel PRO/wireless 3945
 Bluetooth

I loaded up a couple of other versions of linux on this machine, and the resolution automatically was configured at 1440x900, but the wireless & bluetooth wouldn't work. 

this time around (2nd time I've had ubuntu installed), I've had issues with the Fn+Esc... when I wake the machine back up, the wireless doesn't work anymore.  this has been a recent development, and I'm sure I can sort it out (hopefully).

I ran Novell Linux Desktop on an older dell notebook for the better part of a year. I didn't have as many configuration issues, but it didn't have the same kind of hardware that I have on this machine. I guess I was just expecting more out of this flavor of linux, after hearing such glowing reviews.

---

### Post by emmajane on 2007-05-17
I got my 640m today (May 17, 2007). Overall I'm really enjoying the machine. My previous laptop is an Acer TravelMate 630 (~4 years old). I was running 6.10 on it and have started with a 7.04 install on the new Dell laptop. There are currently two issues for me with this machine.

1. Wireless:
As of "now" (which may be a few months old by now) the default wireless card for this machine is NEW and does NOT have drivers for Linux. It's the 4965AGN Intel Wireless-N Card. I tried using the instructions on:  [http://ubuntuforums.org/showthread.php?t=297092](http://ubuntuforums.org/showthread.php?t=297092) with the drivers from: [http://downloadcenter.intel.com/detail_desc.aspx?strState=LIVE&ProductID=2753&DwnldID=13001&agr=N&lang=eng&PrdMap=2753](http://downloadcenter.intel.com/detail_desc.aspx?strState=LIVE&ProductID=2753&DwnldID=13001&agr=N&lang=eng&PrdMap=2753) but it does not work as of today. The driver is installed but the hardware is not detected. On looking at a few sites it seems as though Intel will release Linux-friendly drivers later this summer. I have emailed them to request the Linux drivers. You may wish to do so as well if you're in the same boat as me so that they know people want the drivers! I'm not sure if I'll be able to wait patiently in the mean time I'm irritated that I have a laptop which can only be a desktop when it comes to the Internet...

2. External monitor
When I bought the laptop I also purchased a 20" flat panel monitor from Dell (E207WFP). It got really good reviews on their site. I'm sure it's great, but the graphics card in the laptop is preventing me from using the recommended resolution of 1680x1050. The graphics card requires the i810 module (loaded by 7.04 by default with no problems) and the 915resolution (Debian) apt package. While the 915resolution package fixed the display of the laptop on reboot, I haven't been able to get it to work for the external monitor as well.

Standby function keys work great. Fn-F8 to switch to the external monitor also works (provided you only cycle once, it gets confused if you try to go back and forth between the two repeatedly). Fn-End mutes the machine (but leaves the terminal bell on).

If you have the patience: wait for the Dell-Ubuntu machines. Unfortunately this is a quiet time for me at work and I needed to have a more reliable machine going into my busy time (and therefore couldn't really wait).

I hope that helps!

---

### Post by InlawBiker on 2007-05-18
> **emmajane said:**
> I got my 640m today (May 17, 2007). Overall I'm really enjoying the machine. My previous laptop is an Acer TravelMate 630 (~4 years old). I was running 6.10 on it and have started with a 7.04 install on the new Dell laptop. There are currently two issues for me with this machine.

1. Wireless:
2. External monitor

Emmajane thank you so much for posting this.  I was all set to order this exact machine to run Ubuntu.  The wireless and external monitor are my main motivations for buying it.  That and the 1440x900 resolution.    I think I'll pass now... the external monitor is the big one, I was looking forward to a 1680 external display.

Greg.

---

### Post by slando on 2007-05-22
I've been using Ubuntu on 640m for about 2 weeks. I'm happy with it.

My 640m has a next-generation intel N wireless, intel 950 on-board video card, wxga+ screen. These are all working for me.

For the wireless, I was using ndiswrapper + windows driver. Works OK, except it freezes the whole machine when BitTorrent is used. BT has no problem on wired network though.

The most difficult part for me was setting up dual display (xinerama). I have a 19" dell LCD (not wide screen). The resolutions on both displays are highest, i.e. 1440x900 and 1280x1024 respectively. I cann't drag windows between two screens, but I'm quite happy with its current state.

What's not working/doesn't work as I expect: hibernation, sleeping, and Fn + some keys. However, I didn't spend much effort on these issues, as they are not very indispensable to me. I would like to hear opinions on this regard from your guys.

Things I didn't test: DVD burner.

---

### Post by HuskyDev on 2007-06-11
The dual core subject has been brought up a few times recently in this thread, and I was just curious how one can tell whether their dual core processor is being taken advantage of.  I'm running 386 Feisty on my E1405 with a Centrino Dual Core and it says that I have two processors (CPU0 & CPU1).  Is that it, or should I look elsewhere to make sure?

If anyone has any quick general knowledge about how dual core technology is handled by Ubuntu, I'd love to pick up on that as well, though I suppose this really isn't the thread for it.

---

### Post by InlawBiker on 2007-06-11
> **HuskyDev said:**
> 
If anyone has any quick general knowledge about how dual core technology is handled by Ubuntu, I'd love to pick up on that as well, though I suppose this really isn't the thread for it.

You would need to make sure you have the smp kernel running.  I don't have a multi-processor system (yet) so I don't know if it's detected and installed normally by Ubuntu.

Run a processor monitor or system monitor and look for two CPU graphs/charts.  If you see only one, use synaptic to find and install the latest smp kernel.   

Greg

---

