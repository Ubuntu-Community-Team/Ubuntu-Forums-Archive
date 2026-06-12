---
title: "battery life for a macbook pro 8.2(ubuntu 13.04) and catalyst driver's"
date: 2013-07-09
forum: Apple Hardware Users
---

### Post by bootlessxfly on 2013-07-09
Ive been running ubuntu 13.04 with a fair amount of success on my macbook for a few months. There are only really a couple of problems.

-First off the battery life
Im not expecting to get the same amount of battery life from ubuntu as mac OSX. But i'd like to try to maximize it. I have tlp installed and running and at full charge i only get ~2 hours. This might be because i can't switch between intel and ati, but does anyone have any tips or links to tips that could help me get some better battery.

Also, Every time i install the catalyst driver, it does not work. If i load it without putting the kernel made after the installation into my /EFI/ubuntu folder, I get booted into a terminal that won't boot the X-server because it can't find the drivers. If i put the new kernel in the folder the computer hangs at boot time.

-I have read somewhere that this is do to a problem between the radeon/intel compatibiliy. Has anyone had any luck installing catalyst?

-Also, has anyone been able to get this setup running on just the integrated intel chip. Im thinking not but i can always hope some has had luck.

-Im pretty sure switching to intel from ati still causes a blackscreen, but if this is not the case and someone has been able to switch that would be a nice thing to hear.

Im thinking about trying to configure a new xorg file but i dont really see how this could help. I would think that everything needed would be made when i reinstalled the opensource radeon/intel driver and removed fglrx. But i may be wrong about this

Any comments would be useful.

---

### Post by lukeiamyourfather on 2013-07-09
Have you looked into vga_switcheroo or Bumblebee? They are software projects meant for switching between video devices like you have. The battery life is almost certainly because of the discreet graphics running constantly.

---

### Post by bootlessxfly on 2013-07-09
Thanks for your reply. I would have to use vga_switcheroo since from my understanding Bumblebee is for nvidia only. 
Thats what i was thinking the battery problem was.

-the problem is that there is a bug with the intel driver that causes a black screen every time i do the switch. Even if i try to boot with the intel card it still gets a black screen.

-Also the reason im curious in catalyst is because from what i can gather it provides better battery life and supports switching(although ive also read that their are a lot of bugs with the switch).

-Ill take whichever methods works out(either switheroo or catalyst)

-The problem is i get a black screen with the switch to the intel card and everytime i install catalyst it seems to not be able to recognize my card.

Thanks for your input though. If you or anyone has any more ideas on this, i'd be grateful to hear them.

[SIZE=4][B]edit:
[/B][/SIZE]I decided to try my luck at installing catalyst again. I was not successful but i did get a couple of log files that may help to shed some light on the problem.


I tryed to use both the new beta 13.6 and the newest standard 13.4 driver. My procedure went as follows.


-Installed needed things for building driver and making sure 64-bit worked.
-removed anything that may habe been left over from a previous attempt to install catalyst.
-built .deb files for Ubuntu/raring. Then installed.
-Replaced the current kernel be used by my EFI stubloader with the kernel produced by the installation. Then restarted my computer.


-With 13.6 my computer would boot up and then freeze right before lightdm would ussualy start. 


-13.4 had a little bit more success but still didnt work.
-it booted up but lightdm didn't(or couldn't) start so it brought me to a terminal prompt. I attempted to set up a xorg.conf filr by:
"sudo aticonfig --initial -f"
-this made a conf file(ill post it at the bottom)
-I then downgraded libudev as recommended in a post.
-Attempting to start lightdm at this point made my system hang(I would go past starting services, but did do a shutdown sequence when i pressed power.
-I then tryed changing to the intel card and starting lightdm. This had the same outcome as before.
-I downgraded xserver-xorg-video-intel to version 2.20 and tried both again and still had the same results.


-When i ran "aticonfig --pxl ig this output:
"PowerXpress: Discrete GPU is active (High-Performance mode)." So apparently it is being picked up. Maybe the problem is in the xorg setup.


-running both fglrxinfo and glxgears got me:
"Error: couldn't open display (null)"


-running "tail /var/log/Xorg.0.log" got me this"
"[    26.891] 
Fatal server error:
[    26.891] no screens found
[    26.891] (EE) 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[    26.891] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[    26.891] (EE) 
[    26.901] Server terminated with error (1). Closing log file." Im thinking that the card is working in the sense that is being picked up but for whatever reason can't display to the screens


The xorg.conf file generated reads like this:
"Section "Monitor
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
EndSection


Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "fglrx"
	BusID       "PCI:1:0:0"
EndSection


Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
	EndSubSection
EndSection"
 - from what i can tell the only problem is that the display isnt working correctly with the driver. 
-If anybody has any ideas on if this is the problem and if they know a way to make it work. I would be very grateful.

Thanks.

---

