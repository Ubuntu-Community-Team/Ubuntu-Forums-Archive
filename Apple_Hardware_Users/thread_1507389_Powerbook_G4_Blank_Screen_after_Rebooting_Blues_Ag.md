---
title: "Powerbook G4 Blank Screen after Rebooting Blues Again"
date: 2010-06-11
forum: Apple Hardware Users
---

### Post by enderandpeter on 2010-06-11
Hello excellent developers and computer aficionados. Sadly, I am having an issue that I have seen others have similarly experienced. But from what I can tell researching, my problem may be a little different.

My computer has these specifications:


[LIST]
[*]Powerbook G4
[*]867MHz PowerPC G4 processor; 1MB level 3 cache
[*]700+ MB of PC133 SDRAM
[*]40GB hard drive
[*]15.2-inch (diagonal) active-matirix TFT color display
[*]32MB of DDR SDRAM video memory
[/LIST]
I don't remember the video card model. I believe it's by NVIDIA. Once I get the operating system loading, or a rescue disk to work properly on it, I'll check it out.

Basically, my PPC Ubuntu experience was going amazingly well at first, as I was able to load Ubuntu on it with no problem and restart without a hitch.

At this point, of course, it wanted to download and install updates. It even found an update that acutally let me use the Airport card, which Fedora 12 for PPC failed to do, even after following many guides for installing that b43-fwcutter program.

Anyway, I download the broadcom driver, restarted, and everything was okay. This time, I decide to download and install all the updates. After restarting , the computer hangs up with a black screen, but not before making a popping sound which I believe is the sound of the monitor turning on/off. Before it hangs up, I see a black screen that says Ubuntu 10.04 in the middle with five or so little dots that it looks like are all supposed to light up yellow. Usually, it only gets to the first dot and then the blank screen, or it will even say [OK] all the way to the right, but still the same result.

I can't help but to think an update is causing the issue. I found a guide on the [FONT=Lucida Console][SIZE=2][PowerPCKnownIssues]("https://wiki.ubuntu.com/PowerPCKnownIssues#Ubuntu%208.04%20PowerPc%20alternate%20install")[/SIZE][/FONT] page (albeit for Ubuntu 8.04 PPC Alternate installers) that seemed to refer to this very problem. It recommends making changes to my configuration using the rescue tool on the Alternate CD. When I load the rescue tool, however, it reports that it can't find any partitions. Navigating with the shell doesn't help me find my system either. I chose the default partitioning setup when I installed, so I'm definitely not doing anything fancy.

Others who have had such an issue have been able to overcome it by entering "Linux video=ofonly" or even "video=nvidiafb" or "video=radeonfb" at the yaboot prompt. I've tried all these, even adding "nosplash", but the problem remains.

If anyone can offer any help or advice, it would be much appreciated. If you need more info about my system, I'll try to obtain it. Even if I can't get a rescue cd to work, I guess I could get it back to the state of asking me which new software updates to install. This has been quite a painstaking process and I'm hoping to narrow down the issue without installing and rebooting this machine all day. Thank you for your time and any help you can offer!

---

### Post by linuxopjemac on 2010-06-12
You have a Radeon card in your PowerBook. This will not work well with Lucid Lynx. You have to disable KMS. Add the following to /etc/modprobe.d/radeon-kms.conf:

```
options radeon modeset=0
```

Can you give me the output (in a terminal, maybe from the terminal) of the following:

```
cvt 1280 854
cvt 1152 768
cvt 896 600, 
cvt 720 480
cvt 640 480
```

---

### Post by enderandpeter on 2010-06-12
Thank you very much for responding!!!

I am pretty sure that I have an nVida video card. When I enter the command [FONT=System]lspci[/FONT], it says the following for the video:
```

0000:00:10.0 VGA compatible controller: nVidia Corporation NV17 [GeForce4 440 Go 64M] (rev a3)
```Here are the results of the commands you asked me to enter:

```
$ cvt 1280 854
# 1280x854 59.89 Hz (CVT) hsync: 53.12 kHz; pclk: 89.25 MHz
Modeline "1280x854_60.00"   89.25  1280 1352 1480 1680  854 857 867 887 -hsync +vsync

$ cvt 1152 768
# 1152x768 59.78 Hz (CVT) hsync: 47.71 kHz; pclk: 71.75 MHz
Modeline "1152x768_60.00"   71.75  1152 1216 1328 1504  768 771 781 798 -hsync +vsync


$ cvt 896 600,
# 896x600 59.96 Hz (CVT) hsync: 37.41 kHz; pclk: 42.50 MHz
Modeline "896x600_60.00"   42.50  896 928 1016 1136  600 603 613 624 -hsync +vsync


$ cvt 720 480
# 720x480 59.71 Hz (CVT) hsync: 29.85 kHz; pclk: 26.75 MHz
Modeline "720x480_60.00"   26.75  720 744 808 896  480 483 493 500 -hsync +vsync

$ cvt 640 480
# 640x480 59.38 Hz (CVT 0.31M3) hsync: 29.69 kHz; pclk: 23.75 MHz
Modeline "640x480_60.00"   23.75  640 664 720 800  480 483 487 500 -hsync +vsync

```I found [FONT=Lucida Console][SIZE=2][a thread]("http://ubuntuforums.org/showthread.php?t=1478372")[/SIZE][/FONT] of a user who has a computer most similar to mine, I think. He was asked to use the nouveau video drivers as opposed to the more standard nv ones and it seemed to work out. What do you think of that plan? I will give it a try... Unlike him, I don't have any remote desktop service set up, so I think I'm going to have to reinstall:mad:  Please let me know your thoughts!

---

### Post by linuxopjemac on 2010-06-12
don't reinstall. I will give you a working xorg.conf file soon..

---

### Post by linuxopjemac on 2010-06-12
Can you give me the output of:
```
cat /proc/cpuinfo
```

it looks you have this one (same video)
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.0_17.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_1.0_17.html)

---

### Post by enderandpeter on 2010-06-12
> **linuxopjemac said:**
> don't reinstall. I will give you a working xorg.conf file soon..

Oh, now you tell me! :p I've reinstalled Ubuntu like three times already, but in the process, I've learned that it doesn't matter if I install updates of any kind or not after restarting the machine. It always gives me a blank screen. When the computer restarts after Ubuntu is installed, it boots just fine. But even if at the login screen I choose restart after having changed nothing whatsoever, it will give me the same problem. I could have sworn that I once restarted after just updating the Broadcom driver and it did so just fine...

Well, anyway, here is the output of that cpuinfo file:
```

processor    : 0
cpu        : 7455, altivec supported
clock        : 1000.000000MHz
revision    : 3.3 (pvr 8001 0303)
bogomips    : 83.20
timebase    : 41600571
platform    : PowerMac
model        : PowerBook5,1
machine        : PowerBook5,1
motherboard    : PowerBook5,1 MacRISC3 Power Macintosh
detected as    : 287 (PowerBook G4 17")
pmac flags    : 0000000a
L2 cache    : 256K unified
pmac-generation    : NewWorld
Memory        : 768 MB
```It indeed looks like the computer you linked to has the same video card as mine if the [FONT=System]lspci[/FONT] query is truthful, but the other features are a little different.

Thank you again for helping me get to the bottom of this!! I will praise the name of Ubuntu from the highest mountain if you can help me get this to work!

---

### Post by linuxopjemac on 2010-06-12
So I was right, it's a 17 inch PowerBook G4/1GHz

> model        : PowerBook5,1
machine        : PowerBook5,1
motherboard    : PowerBook5,1 MacRISC3 Power Macintosh
detected as    : 287 (PowerBook G4 17")

I need more info
```

cvt 1440 900
cvt 1152 720
cvt 1024 768
cvt 1024 640
cvt 800 600
```

---

### Post by enderandpeter on 2010-06-12
You got it, sir:

```
$ cvt 1440 900
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync

$ cvt 1152 720
# 1152x720 59.97 Hz (CVT 0.83MA) hsync: 44.86 kHz; pclk: 66.75 MHz
Modeline "1152x720_60.00"   66.75  1152 1208 1320 1488  720 723 729 748 -hsync +vsync

$ cvt 1024 768
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync

$ cvt 1024 640
# 1024x640 59.89 Hz (CVT 0.66MA) hsync: 39.82 kHz; pclk: 52.25 MHz
Modeline "1024x640_60.00"   52.25  1024 1072 1168 1312  640 643 649 665 -hsync +vsync


$ cvt 800 600
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
```

---

### Post by linuxopjemac on 2010-06-12
Here you got the xorg.conf file sir. Replace it with the one you have (/etc/X11/xorg.conf) Please let me know if it works. If it does not work, give me the output of

```
sudo cat /var/log/Xorg.0.log
```

```
Section "Device"
Identifier "Configured Video Device"
BusID   "PCI:0:16:0"
Driver  "nouveau"
Option "NoInt10" "true"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
# 1440x900 59.89 Hz (CVT 1.30MA) hsync: 55.93 kHz; pclk: 106.50 MHz
Modeline "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
# 1152x720 59.97 Hz (CVT 0.83MA) hsync: 44.86 kHz; pclk: 66.75 MHz
Modeline "1152x720_60.00"   66.75  1152 1208 1320 1488  720 723 729 748 -hsync +vsync
# 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
# 1024x640 59.89 Hz (CVT 0.66MA) hsync: 39.82 kHz; pclk: 52.25 MHz
Modeline "1024x640_60.00"   52.25  1024 1072 1168 1312  640 643 649 665 -hsync +vsync
# 800x600 59.86 Hz (CVT 0.48M3) hsync: 37.35 kHz; pclk: 38.25 MHz
Modeline "800x600_60.00"   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync
Option "PreferredMode" "1440x900_60.00"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1440x900" "1152x720" "1024x768" "1024x640" "800x600"
           EndSubSection
           SubSection        "Display"
             Depth            16
             Modes             "1440x900" "1152x720" "1024x768" "1024x640" "800x600"
           EndSubSection
SubSection "Display"
		Depth		15
		Modes		"1440x900" "1152x720" "1024x768" "1024x640" "800x600"
	EndSubSection
SubSection "Display"
		Depth		8
		Modes		"1440x900" "1152x720" "1024x768" "1024x640" "800x600"
	EndSubSection
SubSection "Display"
		Depth		4
		Modes		"1440x900" "1152x720" "1024x768" "1024x640" "800x600"
	EndSubSection
SubSection "Display"
		Depth		1
		Modes		"1440x900" "1152x720" "1024x768" "1024x640" "800x600"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

---

### Post by enderandpeter on 2010-06-12
Once again, thank you for helping me so much.

Sadly, I'm a little unclear on how to implement this, exactly. I can't seem to find my current xorg.conf file. This Ubuntu [driver guide]("https://help.ubuntu.com/community/BinaryDriverHowto#Xorg.conf.d") tells me I'll find it in [FONT=System]/usr/lib/X11/xorg.conf.d[/FONT]. I see three other configuration files in there, but no xorg.conf. Should I just create the file in there? How should I do this? :confused:

---

### Post by enderandpeter on 2010-06-12
Well... this is getting interesting...

I was advised to load the xorg.conf file you made into [FONT=System]/usr/lib/X11[/FONT]. After doing so, instead of just giving me a blank screen, an incompletely displayed error appears at the top that says:
```

[   24.564224] fb: conflicting fb hwusuage noveaufb vs OFfb NVDA,Displ - removi
```Now I've seen this message before, as it shows the first time Ubuntu restarts after you install it. Below this message is the name of my computer followed by "login". Earlier, it would flash this screen and then indeed show the login screen in X.

Now, I'm given an error in X in the form of a window that says:

```
Ubuntu is running in low graphics mode

(EE)Failed to load module "nouveau" (module does not exist, 0)
(EE) No drivers available
```Clicking okay gives me a few options:


[LIST]
[*]Run Ubuntu in low graphics mode for just one session
[*]Reconfigure graphics
[*]Troubleshoot the error
[*]Exit to console login
[*]Restart X
[/LIST]
I can just smell the success!! Do you think perhaps I didn't have the nouveau driver installed in the first place? What are your thoughts from here?

---

### Post by ddecator on 2010-06-12
Should have been installed by default. 'Run Ubuntu in low graphics mode' doesn't give you a session with even basic graphics?

---

### Post by enderandpeter on 2010-06-12
Loading in low graphics mode actually looks no different than normal, strangely. So this issue is so close to being solved!

So, my thoughts were that I didn't have the nouveau driver installed. I went to Ubuntu Software Center, searched for "nouveau" and found a "nouveau-firmware" program and something that says it's an experimental nouveau display driver. I installed nouveau-firmware, restarted, and I still get the error messages, but again choosing the low graphics options loads everything just fine, it appears. Maybe I should try the experimental driver?

It was suggested to me that I find a proprietary driver, but the Hardware Drivers utility doesn't find such a thing for me. I went to nvidia.com and tried to manually search for my video card, but it is not listed there, and so I'm starting to think nouveau may be the way to go.

Any thoughts?? Thank you so much everyone for getting me this far!

---

### Post by linuxopjemac on 2010-06-13
```
sudo apt-get install xserver-xorg-video-nouveau
```

Weird that Ubuntu does not install such drivers by default, but as people know here I am not a big fan of Ubuntu for PPC.

---

### Post by enderandpeter on 2010-06-13
> **linuxopjemac said:**
> ```
sudo apt-get install xserver-xorg-video-nouveau
```Weird that Ubuntu does not install such drivers by default, but as people know here I am not a big fan of Ubuntu for PPC.

[SIZE=4]OH MY GOD! THAT TOTALLY DID THE TRICK!!!!!!!!!!![/SIZE]

Good sir, you are a frickin' genius!! I don't know why I didn't just install that experimental driver earlier. I guess that word "experimental" freaked me out or something.

Wow, are all Netherlanders as ingenious as you? And they say legalizing drugs destroys society... ;)

---

### Post by mrufino1 on 2010-07-06
I'm having exactly the same issue, installation was a success, I then installed some stuff recommended for mouse, hotkeys, etc, and I also disabled the therm_windtunnel module to see if that helped the heat problem. When I restarted the machine, I am now getting the ubuntu screen, then the white dots, then the clicking noise, then no picture, but the machine is still running I think. 
If there is no picture, how am I installing the nouveau driver? or am I supposed to? It is a 12" powerbook g4 867. Thanks.

---

### Post by linuxopjemac on 2010-07-06
what is your xorg.conf file ?

---

### Post by mrufino1 on 2010-07-06
I'm about to go to bed, it's 2:45 am here, but if I am looking in the right spot, /etc/X11/xorg.conf, it is blank. If I hit crtl-alt-f1 when the screen shuts off, then it gets a little brighter black (backlight turned on?) then if I hit ctrl-alt-f7-f8 (maybe not f7 and f8, I just seem to be hitting them together) then I can see my ubuntu desktop. This is weird, and repeatable.

---

### Post by linuxopjemac on 2010-07-06
that is not so weird. CTRL-ALT-F1 should give a terminal. CTRL-ALT-F7 should give X.

---

### Post by linuxopjemac on 2010-07-06
12 inch powerbook G4/867:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867_12.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867_12.html)

First install the nouveau driver:
```
sudo apt-get install xserver-xorg-video-nouveau
```

Then use this xorg.conf file:
```
Section "Device"
Identifier "Configured Video Device"
BusID   "PCI:0:16:0"
Driver  "nouveau"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1024x768" "800x600" "640x480"
           EndSubSection
           SubSection        "Display"
             Depth            16
             Modes             "1024x768""800x600" "640x480"
           EndSubSection
SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

From [here]("http://mac.linux.be/content/xorgconf-file-powerbook-g415-12-lucid-lynx").

Please tell me if it works.

---

### Post by mrufino1 on 2010-07-06
Looks like it worked! Thanks so much. A few other small issues, like hibernate or sleep, if even possible, the right click emulation, address the heat issue if it is still there, and I think we're in business. This isn't my main machine anyway, so trying things out is not a problem. I was given the mac for free and I don't like OSX. I do like the 12" form factor though, so if I get all this ironed out it will be very useful to me as a traveling computer for work. Thanks for your help! If for some reason it doesn't stay solved I'll report back.

---

### Post by mrufino1 on 2010-07-06
I decided to install your debian/ mint combo (currently finishing installation). Will I need this same xorg.conf file? Looking forward to trying mint out, thanks so much for your help.

---

### Post by markosjal on 2010-07-07
CAUTION
I really believe (and I am speculating to some degree) that because Ubuntu PPC does not install the CPU control (to cycle it down) by default, that this causes overheating issues on models like yours. I had a G4 machine that was loaned to me and after installing ubuntu and using ubuntu for a few months it died and gives me now only a black screen. 

Looking around on the net I learned that many that started using ubuntu suddenly ended up with similar black screen issues. I think that Apple had such control over the hardware and OS interaction that their OS had features to control heat, particularly on those models. 

I also know that by default this CPU tool (which I do not remember the name) is not installed by default! I learned about it after it was too late and had read about other users complaining about excessive heat when running Ubuntu compared to OSX, and I observed the same. I think that heat burns out something with the video!

I see this as a HUGE risk when installing ubuntu on some G4 machines!


DEBIN LENNY MINT
It is not MINT! It is Debian Lenny in a  Mint skin (or facade) . I am not saying this to speak badly about it but it is nothing like Mint! I actually wish them well on the project, but think they shoul;d call it something else. Mint is based on Ubuntu. Their Lenny Min PPC is based on Debian Lenny. I do not believe it is an official release of Mint in any form. Furthermore the mint menu here 
[http://www.webupd8.org/2010/05/install-linux-mint-main-menu-mintmenu.html](http://www.webupd8.org/2010/05/install-linux-mint-main-menu-mintmenu.html)
runs on Ununtu 10.04 PPC. I run it on a G3 iMac. It requires about 13.4 Meg of memory on my system. WIth 768 Meg and Ubuntu 10.04, my G3 runs better than it ever has. It boots faster than My main 2.8 Ghz PC running Mint 8 too.

---

### Post by linuxopjemac on 2010-07-07
> DEBIN LENNY MINT
It is not MINT! It is Debian Lenny in a Mint skin (or facade) . I am not saying this to speak badly about it but it is nothing like Mint! I actually wish them well on the project, but think they shoul;d call it something else. Mint is based on Ubuntu. Their Lenny Min PPC is based on Debian Lenny. I do not believe it is an official release of Mint in any form. Furthermore the mint menu here
[http://www.webupd8.org/2010/05/insta...-mintmenu.html](http://www.webupd8.org/2010/05/insta...-mintmenu.html)
runs on Ununtu 10.04 PPC. I run it on a G3 iMac. It requires about 13.4 Meg of memory on my system. WIth 768 Meg and Ubuntu 10.04, my G3 runs better than it ever has. It boots faster than My main 2.8 Ghz PC running Mint 8 too.

I never said it was an official Mint distribution. It is based on Mint Helena LXDE and Debian. It does not have the fancy Mint menu as that is used in GNOME, not in LXDE. You won't find that menu either in Mint LXDE x86.

---

### Post by LinNub on 2010-08-27
> **linuxopjemac said:**
> 12 inch powerbook G4/867:
[http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867_12.html](http://www.everymac.com/systems/apple/powerbook_g4/stats/powerbook_g4_867_12.html)

First install the nouveau driver:
```
sudo apt-get install xserver-xorg-video-nouveau
```

Then use this xorg.conf file:
```
Section "Device"
Identifier "Configured Video Device"
BusID   "PCI:0:16:0"
Driver  "nouveau"
EndSection

Section "Monitor"
    Identifier    "Configured Monitor"
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Monitor        "Configured Monitor"
    Device        "Configured Video Device"
        DefaultDepth    24
           SubSection       "Display"
             Depth            24
             Modes             "1024x768" "800x600" "640x480"
           EndSubSection
           SubSection        "Display"
             Depth            16
             Modes             "1024x768""800x600" "640x480"
           EndSubSection
SubSection "Display"
		Depth		15
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		8
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		4
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
SubSection "Display"
		Depth		1
		Modes		"1024x768" "800x600" "640x480"
	EndSubSection
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

Section "DRI"
	Mode	0666
EndSection
```

From [here]("http://mac.linux.be/content/xorgconf-file-powerbook-g415-12-lucid-lynx").

Please tell me if it works.


I am having the same issue and got the installation of nouveau from the information provided in this forum BUT--how do i add this information to the xorg.conf file--AND where do I find it?

running Ubuntu 10.04 LTS on a 12" powerbook G4 1.33ghz with 1.25 gb's ram. 

Also-- this is my third time installing Ubuntu on this machine because every time i install/update the drivers for the airport wireless card it goes to a blank screen after restarting--i think this may be the solution i need, if someone can just help me by showing me how to edit the xorg.conf file. 

I also came across some information about cleaning up the installer files so the computer doesn't overheat--should i be concerned about this? I'd like to make this build as streamline as possible. 

While I'm at it-- does anyone know how i can sync my iphone to my linux machine once it's done? (can i put linux on my iphone too lol)


Thanks!!

Thanks!

---

### Post by linuxopjemac on 2010-08-28
to get the xorg.conf file do the following:

```
wget http://mac.linux.be/files/xorg/powerbook4.txt
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo mv powerbook4.txt /etc/X11/xorg.conf
```

reboot

---

### Post by linuxopjemac on 2010-08-28
for iPhone google or look in this forum. It's supported in 10.04.

---

### Post by LinNub on 2010-08-28
> **linuxopjemac said:**
> to get the xorg.conf file do the following:

```
wget http://mac.linux.be/files/xorg/powerbook4.txt
sudo mv /etc/X11/xorg.conf /etc/X11/xorg.bak
sudo mv powerbook4.txt /etc/X11/xorg.conf
```

reboot

I got 

mv: cannot stat '/etc/X11/xorg.conf /etc/X11/xorg.bak

After the second line.

---

### Post by linuxopjemac on 2010-08-29
just perform the following then:

```
wget http://mac.linux.be/files/xorg/powerbook4.txt
sudo mv powerbook4.txt /etc/X11/xorg.conf
```

---

### Post by LinNub on 2010-08-29
Thank you so much!! 

I think it's working (I'm using my linux/powerbook right now to type this :)

---

### Post by bovinius on 2010-10-04
assuming you have the black screen on bootup after installing lucid:
try switching to a virtual terminal and then back to the gui as follows:

<ctrl><option/alt><f3>  then <ctrl><option/alt><f7>

that should allow you to see the 
from there you can see the login gui
login as usual

from here update and upgrade the system to fix the bootup screen:
sudo apt-get update
sudo apt-get uprade
sudo shutdown -r now

this will reboot and the upgrades should fix the prob.
you can always do the toggle to virtual terminal and back again if you have to.

---

