---
title: "Sapphire x850xt problems on Feisty"
date: 2007-05-31
forum: Absolute Beginner Talk
---

### Post by lostcause64 on 2007-05-31
Ok, down to my last good nerve... and it's frayed badly...:(

I've been trying on and off for the last several months to get Feisty to setup in dual boot with XP Pro. No luck at all until I tried the Alternate version. This works like a charm, as long as I DON'T have my Sapphire x850xt PCI-E installed in the pc at all. Install went smoothly, but when I rebooted after completing the install, it freezes without ever getting me to a login screen. It just hangs at the splash screen. So I wiped & reinstalled without the Ati card, everything is great... it updates as normal, lets me access my "storage partition" that has my music & data like pictures, surf the internet (I already use Firefox & OpenOffice), used Gaim to IM for the first time with no trouble, etc. And yes, I did verify that I had a good download & good burn to disk.

The pc is running an Intel Core 2 Duo x6300 with the Intel DG965WH mobo, 250gb Seagate Sata HD, & a Plextor DVD optical burner. I've ran the Ati fix from the Sticky here, while the Ati card was not installed, then powered down, added the card, same results... lockup. Running Ubuntu w/o the Ati card is not an option... I'm kinda weird... I like to play various 3d games like Doom 3, HalfLife2, Quake, Star Wars Galaxies, etc.

Every thread I've been able to find on problems like mine seem to have one thing in common... the recommended fixes for this don't seem to take into account that if I have the x850 installed, I CAN NOT load Ubuntu... it locks up tighter than a drum so I have no way of running a fraggin thing that I know of, and I haven't found a reference covering that at all. The x850xt works perfectly in XP, better than any card I've tried personally. I'm a veteran Windows pc tech, but I'm totally in the dark about Linux/Ubuntu... PLEASE, give me some help with that in mind. I don't know what commands to use from the Grub screen that might let me bypass the Xorg, which did prompt me for wanted screen resolutions during install, or modify it without booting to the desktop.

The only error reference I can determine is from booting to Recovery Mode which hangs in different points during the process, but most of the hang points seem to be immediately after references to loading Intel Agp which must be referring to the onboard video since I have PCI-E. I have seen in passing a message about Bug:Software lockup detected in CPU0! right after a Kernel panic - not syncing message.

I've already reinstalled Ubuntu 5 times, which is probably quite minor compared to most, but I'd rather spend my time off of work PLAYING on my pc, not working on it... since I fix pc's for a living so that's why I don't want to play around with this anymore and I'm about to give up until I get around to getting an nVidia card, even if I do prefer Ati.

I apologize for my frustration, don't mean to take it out on you folks!

Thank you for your help,
John

---

### Post by daimaru on 2007-05-31
since you already know that it freezes right after agp im guessing you already turned the quite splash option during boot off, so you see all the stuff thats happening right. 

i have no idea if this could work but hey what have you got to loose. boot with or other graphics card, then install the ati restricted driver by going to console and typing

```
sudo apt-get install xorg-driver-fglrx
```

after that edit your xorg.conf file (backup 1st)
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.mybackup
sudo gedit /etc/X11/xorg.conf
```
locate section device near the bottom of the file
```
Section "Device"
	Identifier	"ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]"
	Driver		"ati"  <-- this might be nvidia or nv depends on what ur other graphics card is that ur booting with
	Busid		"PCI:1:0:0"
EndSection
```
change the driver to fglrx
```
Section "Device"
	Identifier	"ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]"
	Driver		"fglrx"
	Busid		"PCI:1:0:0"
EndSection
```
as you can see i have a x800 gto but its just the identifier so you can just change that to your card name the chipset might also be R480 otherwise a quick google on that will give you urs. anyway its just a identifier it doesnt do anthing. just make sure that under the section "screen" you change the device to the identifier you game your card above:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"ATI Technologies Inc R480 [Radeon X800 GTO (PCIE)]"
	Monitor		"SyncMaster"
	Defaultdepth	24
	SubSection "Display"

...


```

oh forgot copy this at the end of your xorg.conf file if it does not exist yet
```
Section "DRI"
	Mode	0666
EndSection

Section "Extensions"
	Option		"Composite"	"0"
EndSection

```


save your xorg.conf and then shutdown put in ur ati x850 card and reboot ... hope it works
if it didnt you should be able to boot with ur other card and copy back your xorg.conf backup file in console mode.

---

### Post by lostcause64 on 2007-05-31
Well, I tried it. After needing to reinstall Ubuntu for the sixth time, as after I make any changes to install the Ati card I can't figure out how to get Ubuntu to load... it gives me some kind of X error screen that allows me to look at to help with Diagnostics, I set it all up again, followed you advise to the letter... triple checked my spelling, etc., but no change at all. 

Thanks for the advise, but I can't spend any more of what little time I have to myself trying to convince Ubuntu to get along with the hardware I currently use. I'll try again sometime down the road, maybe with 7.10 or after I get a newer video card & motherboard. Even though what I have now works perfectly otherwise...

Thanks, again...
John

---

### Post by daimaru on 2007-06-01
sorry to hear that, just one last question are you by any way using the 64bit edition of ubuntu? just asking because i've got a amd64 but since my computer froze on start of 64bit ubuntu i installed the i368 version which works fine.

---

### Post by lostcause64 on 2007-06-01
No, I've been trying to use only the 32-bit versions, as I've noticed people having even more problems using 64-bit anything over the years.

It stinks, as I love the idea of moving to Ubuntu, but...

Thanks for your efforts!

---

### Post by daimaru on 2007-06-01
ok lets give it one last try as you had your 850 card in the comp did you get to the xserver faild to start or somthing screen? if so just boot again when you get there just keep clicking ok; if your presented with a empty screen or anything try hitting "ctrl+alt+F1" that should give you a tty where it says login - so login and at the command prompt type 
```
sudo dpkg-reconfigure xserver-xorg
```
answer everything with the default options until you get to the video device section there you have to find ati and select it . in cause your not famililiar with text based navigation you can use your TAB ENTER ARROW keys to get to the different sections. Somtimes the SPACEBAR for selecting stuff (if it has boxes where you can make a little * ) 
try that and it should work thats assuming of course that you can get to the terminal with the 850 card .

---

### Post by lostcause64 on 2007-12-04
Even in Gutsy, I can never boot past the 3rd bar under the Ubuntu logo. I never get an error message of any kind, it just hangs there. Anything I try to do to get this card installed requires having the card removed before I can make the attempt, then I get to physically put the card back in... just to get the exact same fraggin' result! I'm not a big fan of installing anything that way, as I know I'm begging to have a component failure from repeated removal/addition of the card.

You know, with the kind of odds it takes to have just the one card Ubuntu won't run, I need to play the lottery and stay out of lightning storms...

John

---

