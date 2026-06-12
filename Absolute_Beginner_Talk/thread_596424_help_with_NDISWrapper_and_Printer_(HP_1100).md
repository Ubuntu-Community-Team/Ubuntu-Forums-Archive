---
title: "help with NDISWrapper and Printer (HP 1100)"
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by tdmoore on 2007-10-29
I have been subscribing to some threads but am a newbie to forums and especially to Linux.

Here is situation:
Used Live CD to understand Linux but forgot to check the wireless component (complete newb). Loaded 7.10 and loaded fine.  Picked up my 1 printer (Xerox 6110) no problem.  HP Laserjet 1000 I understand needs a driver to work with Ubuntu. Link to driver has been given and I have downloaded to a USB key and moved to desktop as my wireless is not working on Ubuntu. (dual boot machine, works fine in XP).

Threads have helped me get the driver for the Linksys WUSB54gv1 card I have and I have moved that to my desktop as well.

I now know ***_WHAT_*** NDISWrapper does, however I truly have no idea how to use it to get these drivers installed.  Can someone give me directions on exactly how to install both drivers?  Obviously the wireless one is critical for me.

Greatly appreciate advice as I am very impressed with just playing around with what I have.

BTW: moved our entire business over to Open Office 3 years ago and has worked out well.  I am planning on being the guinea pig for Ubuntu as well so if this works out over the course of the next 6-12 months then might do same for Ubuntu!

---

### Post by Denn1s on 2007-10-29
great you support open source in your bussiness!

now ill see if i can help, first ndiswrapper is a program that allows you to use windows drivers in linux  and you should use it only as a last ressort if there really arent linux restricted or free drivers, wath is the output of 

```
lspci
```

so we can see wath exact hardware do you have

---

### Post by tdmoore on 2007-10-30
Thanks Denn1s.

Thought because it was a USB I was supposed to use lusb in the command line.

Will try what you suggest and send back.  Appreciate the help.

---

### Post by Atreus12 on 2007-10-30
> **tdmoore said:**
> 

I now know ***_WHAT_*** NDISWrapper does, however I truly have no idea how to use it to get these drivers installed.  Can someone give me directions on exactly how to install both drivers?  Obviously the wireless one is critical for me.


I have the same wireless card, WUSB54GV1 external USB wireless card. It's a bit rare these days, as almost everyone has the WUSB54GV4. You might want to double check exactly which one you have. They use completely different chipsets

If you do have V4, check out [this thread](http://ubuntuforums.org/showthread.php?t=588045)

The V1 card worked great (well, in a relative sense anyway) in Dapper 6.06, but I could not get it to work in 7.04. I'm not sure what the status is with 7.10, but you can give it a shot and let me know how it works out ;)

I am no linux expert, so someone may be able to provide better help than me, but as far as I know there are two methods to doing this. The second method yields better results, but I'm not sure if it works in Ubuntu (it definitely works in Debian Etch).

In any case, before we get started it would be helpful to have internet access. If possible, run a cord. If not you can try to install the packages from the CD, but that's an additional hassel, and I'm not sure if the packages are on the cd or not.

If you go the CD route, you'll need to add the cd to your repos. Run ```
sudo gedit /etc/apt/source.list
``` delete the # from the beginning of the cdrom line.

Ok, ** Method 1**
First open the terminal (Applications->Accessories->Terminal) and copy and paste the following code:

```
sudo aptitude install ndiswrapper
```

You may already have it installed. If so, then aptitude will report it already is installed

Now run

```
sudo ndiswrapper -l
```

This will list the drivers that are installed. If you haven't used it before, there should not be any.

Now find your Windows XP driver (the one that ends in .inf) and put it somewhere on your computer where you can find it. If you don't have it / can't find it, I can send it to you.

For instance, if you put it in your home directory, the path would be /home/your_username/WUSB54G.inf

Run (replacing /path/to/... with the actual path to the driver). Remember, you can use the TAB key to auto-complete stuff in the terminal.

```
sudo ndiswrapper -i /path/to/WUSB54G.inf
```

Make sure it installed correctly

```
sudo ndiswrapper -l
```

And it should report both your driver, and something like "hardware present" as long as the card is plugged in.

Then run

```
sudo depmod -a
``` and ```
sudo modprobe ndiswrapper
```

And then reboot.

Now run
```
sudo iwlist scanning
```

If it worked, then you should get a report of any wireless signals it sees. If not, it will say something like "interface does not support scanning"

Sometimes (in Dapper 6.06) it was picky about being plugged in during bootup. For this reason I would suggest plugging it in AFTER your computer boots up.


OK, so if that didn't work, we can try plan B. This works for sure on Debian Etch, which I am using. I would think it should probably work on Ubuntu as well? Worth a shot anyway.

**Method 2**

First, you are going to need an internet connection or a cd to install from.

```
sudo aptitude install module-assistant
```

Then run
```
sudo module-assistant prepare
```
and then
```
sudo aptitude install ndiswrapper-source
```
and
```
sudo module-assistant build ndiswrapper
```
and
```
sudo aptitude install ndiswrapper-utils-1.9
```
and
```
sudo module-assistant install ndiswrapper
```
and (replacing /path/to.... with the actual path)
```
sudo ndiswrapper -i /path/to/WUSB54G.inf
```
and
```
sudo depmod -a
```
```
sudo modprobe ndiswrapper
```

reboot and then run

```
sudo iwlist scanning
```
and see if it comes back with anything. This can take ~10 seconds to scan so be patient.

Looks complicated...but it isn't.
Keep in mind that ndiswrapper is a messy work around for wireless devices who's manufacturers don't offer any linux support. If you ever buy another wireless card, vote with your money.

-Andrew

PS Keep me updated, I would like to know if it works in Gutsy

If this fails and you still want to try more stuff, look [here](http://ubuntuforums.org/showthread.php?t=574462) as someone offers advice on building ndiswrapper from svn source. Might be worth a shot.

---

### Post by tdmoore on 2007-10-30
Atreus12,

Appreciate the great instructions but it stalled on me when I got to actually installing the .inf driver.

Here is what I got:
[I]tim@tim-desktop:~$  sudo ndiswrapper -i/home/WUSB54G.inf 
install/manage Windows drivers for ndiswrapper 

usage: ndiswrapper OPTION 
-i inffile       install driver described by 'inffile' 
-a devid driver  use installed 'driver' for 'devid' (dangerous) 
-r driver        remove 'driver' 
-l               list installed drivers 
-m               write configuration for modprobe 
-ma              write module alias configuration for all devices 
-mi              write module install configuration for all devices 
-v               report version information 

where 'devid' is either PCIID or USBID of the form XXXX:XXXX, 
as reported by 'lspci -n' or 'lsusb' for the card 
tim@tim-desktop:~$ [/I]

Card was plugged in (had booted into Windows and it worked fine), and followed instructions to the letter.  Not sure what to do from there.

Your link to building ndiswrapper from svn source I had too so both were helpful.

Some questions for you/anyone willing to assist (before I go buy a new adapter:
1. In the other set of instructions it says to put the tar file in ~/ndiswrapper directory.  I am so windows oriented (self taught I confess) that I cannot even FIND THAT...just feeling a little embarrassed...but willing to keep going!
2. I have a USB hub (Targus) that the adapter was plugged into as opposed to the PC itself.  Worked in Windows but could not get it to work in Gutsy.  Question is: if I purchase a new adapter should I plug directly into the PC or can I go through the hub?  I wonder if I lose anything.

Will keep trying...be patient please all and again, THANKS!

EDIT: noticed that I did not include user name in path when installing driver.  After doing this, still did not work, kept asking for "where 'devid' is either PCIID or USBID of the form XXXX:XXXX, 
as reported by 'lspci -n' or 'lsusb' for the card "

I then noticed another posting and followed that instruction:
sudo lshw -C network

and received this information (of which I have no idea what to do with frankly but feel closer anyway!)
tim@tim-desktop:~$ sudo lshw -C network 
  *-network               
       description: Ethernet interface 
       product: 82801BA/BAM/CA/CAM Ethernet Controller 
       vendor: Intel Corporation 
       physical id: 8 
       bus info: pci@0000:02:08.0 
       logical name: eth0 
       version: 03 
       serial: 00:09:6b:d8:e4:55 
       size: 10MB/s 
       capacity: 100MB/s 
       width: 32 bits 
       clock: 33MHz 
       capabilities: pm bus_master cap_list ethernet physical tp mii 10bt 10bt-fd 100bt 100bt-fd autonegotiation 
       configuration: autonegotiation=on broadcast=yes driver=e100 driverversion=3.5.17-k4-NAPI duplex=half firmware=N/A latency=66 link=no maxlatency=56 mingnt=8 module=e100 multicast=yes port=MII speed=10MB/s 

OK...now what do I do good people?

---

### Post by Atreus12 on 2007-10-30
I forget the exact name of the driver, I thought it was WUSB54GV1.inf , but you will have to double check that. Maybe it is just WUSB54G.inf ?

First, a couple of hints. Did you know that you can simply highlight text and then paste it via middle click? Also, you can 'auto-complete' in the terminal using the tab key. A double tap of the tab key will list all possible options.

Onward,

Where is the driver file located? If it is in your home directory, then the code would be

```
sudo ndiswrapper -i /home/username/WUSB54GV1.inf
```

Note there is a space between the -i and the /home

Here's how it works. Lets say your username is bob. You put a folder called Drivers in your home folder, and inside the Drivers folder there is another folder called Linksys, and then a file called WUSB54G.inf inside of that

the path to that file would be /home/bob/Drivers/Linksys/WUSB54G.inf

Go to Places->Home Folder via the top menu, take a look at what is in your home folder, and find the name and location of the .inf driver that you put in there

Then go to the terminal and retry the ndiswrapper -i command with the correct location. Linux paths are case sensitive so Drivers is not the same as drivers.

**Edit: Use the CVS option as your last resort. That is a more difficult approach**

Also, not sure about the hub. I would say try it without the hub, and lets get it working that way. Then switch back to the hub and see what happens. So far that is not what is causing any problems.

---

### Post by tdmoore on 2007-10-30
Atreus12...thanks!

The key was that you said it was case sensitive and the actual driver name was WUSB54G.INF (note the extension is CAPS)...voila, I now have " the driver wusb54g is already installed on my screen.

Now to try and get the rest of it done....

Thanks...any other tips?

---

### Post by tdmoore on 2007-10-30
OH OH...

Now have typed in sudo ndiswrapper -l and get message wusb54 : invalid driver!

Will reboot and try again as an option....

---

### Post by Atreus12 on 2007-10-30
Yeah, don't sweat the small stuff ;)

I started the exact same way. Trying to figure out what the heck ndiswrapper was, and how to get it installed. Don't worry, you start picking this stuff up pretty quick.

I'll be around for about an hour more tonight, give me a holler if you get stuck. I'm interested to see the result

**Edit: You might have the wrong driver. Are you SURE you have a WUSB54GV1? Are you using the WUSB54GV1 driver? My cd has V1 and V2 drivers**

---

### Post by tdmoore on 2007-10-30
Atreus,

No go...still same message.

OK..I give up.  Too many issues here so will look to purchase new adapter.

Our company IT guy (who has gotten me involved in Ubuntu :) ) is recommending a 
	
Blanc Wireless-G USB Adapter (BW-54U11) however I don't see it on the list of recommended devices.

Any recommendations as you have been so helpful...owe you a bevy of your choice (virtually speaking of course).

Thanks.

---

### Post by tdmoore on 2007-10-30
Will look.

---

### Post by tdmoore on 2007-10-30
Have CD in drive and exploring.

I only see 1 driver there...actually the one I copied originally off the disc.

---

### Post by Atreus12 on 2007-10-30
Shoot me a PM with your email, and I will send the driver I have. If you really have V1, I have the most up to date driver.

---

### Post by tdmoore on 2007-11-02
Atreus,

Received message "interface does not support scanning" after getting driver to load.

Then tried rebooting, pulled USB and plugged in AFTER rebooting and still nothing.

Then tried Method 2 (had Gutsy install CD in drive) however it stumbled early as sudo aptitude install module-assistant did not load that package (I guess) as when I tried the command sudo module-assistant prepare it gave me the error message command not recognized.

Have rebooted again with CD in drive and tried following instructions there as well.  Have not been able to get anything to work past this point.

Any more assistance would be appreciated.

---

