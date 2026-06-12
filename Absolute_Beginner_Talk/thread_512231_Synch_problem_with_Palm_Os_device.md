---
title: "Synch problem with Palm Os device"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by kc5hwb on 2007-07-28
I am trying to get Ubuntu to synch with my Palm Treo 650 and when I do the initial setup I am getting an error when trying to synch.  It is saying....


> Failed to connect using device "Treo" on port /dev/pilot.  check your configuration, as you requested old-style usb-serial "ttyUSB" synching, but do not have the usbserial 'visor' kernal module loaded.  You may need to select a USB device.


Now, this doesn't make sense, since the only settings in the Device Setup on the PalmOS device program build into Ubuntu has 4 choices for connection, and I have chose the only one that says USB.  The other choices are serial. irDa and Network.  So what the heck is it talking about, and is there a way to install this visor module?  I checked in Synaptic and didn't see it.

---

### Post by TransitMan on 2007-07-29
Are you using the USB connection provided with the Treo or the old style serial?
 
 If you are using the USB, just check USB and follow the directions to sync.
 It will be a bit hairy at first, but once you get it to sync, you should be good to go.
 
 
 
 .wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Arial [monotype]", "Arial [monotype]", "Helvetica [Adobe]", "Arial [monotype]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }.wysiwyg { background-attachment: scroll; background-repeat: repeat; background-position: 0% 0%; background-color: #ffffff; background-image: none; color: #666666; font-family: "Arial [monotype]", "Arial [monotype]", "Helvetica [Adobe]", "Arial [monotype]"; font-style: normal; font-variant: normal; font-weight: 400; font-size: 10pt; line-height: normal } p { margin: 0px; }

---

### Post by kc5hwb on 2007-07-29
I am using the USB device that came with the Treo, not a serial device.  And I am following the instructions when I get this error.

---

### Post by kc5hwb on 2007-07-29
Anyone else have an idea on this?

---

### Post by kc5hwb on 2007-07-30
anyone at all...

---

### Post by kc5hwb on 2007-07-30
Does anyone use the Palm OS Devices feature under the System -->Preferences menu?

---

### Post by chudder on 2007-07-31
I have the exact same problem.  

It gives me the popup "warning":

[PHP] Failed to connect using device `(device name)', on port `/dev/ttyUSB0'. 
Check your configuration, as you requested old-style usbserial 
`ttyUSB' syncing, but do not have the usbserial `visor' kernel
module loaded.  You may need to select a `usb;' device.
[/PHP]

I look in the /dev folder and the tty0 and tty1 are unavailable and ttyUSB0 or 1 aren't existent.

check your /dev folder and see if you have any of the following:
/dev/pilot
/dev/tty0 or 1
/dev/ttyUSB0 or 1

Like I said I have the tty0 and 1 but they are "x"'d out as in it's not a working file or at least that's how it seems.

Anybody who knows about this, please help.  
Thanx

---

### Post by chudder on 2007-07-31
Hey I found a thread that solves the problem!  Go here, it works for me, It doesn't go to completion as I say in my post on the thread but everything seems backed up so I'm happy.  I run a treo 680.

[http://ubuntuforums.org/showthread.php?t=430124&highlight=ttyUSB]("http://ubuntuforums.org/showthread.php?t=430124&highlight=ttyUSB")

Hope it works

Chud

---

### Post by Francis60 on 2007-07-31
I just tried mine for fun as I have a Treo 650 also.
the message I am getting is unknown PDA-no PDa matches Id 1000.
I do not know where to get my PDA number.

---

### Post by chudder on 2007-08-01
hmm...That's the one I used, it was the default, the only thing I can think of is having gnome-pilotfind it for you.  You may have already tried that.  

The only other suggestion I have is to try different numbers.  Try single digits up through 5 digits.  

That's a little beyond me.  Sorry

---

### Post by kc5hwb on 2007-08-01
I think the device ID is the same one that you use in the windows version of the backup software.  I used 650.  But I also left mine set to default of 1000 on Ubuntu and I dont get that error.  Of course it may come later if I can get the USB problem solved first.

---

### Post by Francis60 on 2007-08-01
I tried different numbers and it worked- It hot sync. and said completed- when i go to search files and type in palm one all that i can find is my pictures from my treo-cannot find calendar or contacts or any other files- just the pictures-do you know where they would be. I went to gnome pilot and enabled everything. As it is Hot sync. I can see it is saving all the items, but cannot find where they are in the computer
Thanks
Allan

---

### Post by BobLand on 2007-08-01
I have an old Palm Vx.  Supposedly, it is supported by U and all its attendant programs.  I've been unable to transfer the contents of the device to any program.  Most say they do but usually it's either a very small subset - typically 32 records or the first record repeated preceded by a sequential number.

I've given up trying to sync this data on U.  I keep it all on my wife's computer since she's still on W2K.  I'm hoping that the next or other near future release fixes this very annoying problem.

As a result, I don't use the Palm anymore.  Not a big deal but I have important historical data that I have to keep and refer to.

bobland

---

### Post by Francis60 on 2007-08-02
Thanks
 for now i will just use my treo 650 with windows as i have dual boot anyway and my desk top is still Windows XP which I am not changing until I know all about Ubuntu- do not want to mess up my main computer by any chance- my laptop is two years old, so I need an reason to buy a new one if something goes wrong
Allan

---

### Post by chudder on 2007-08-11
> **Francis60 said:**
> I tried different numbers and it worked- It hot sync. and said completed- when i go to search files and type in palm one all that i can find is my pictures from my treo-cannot find calendar or contacts or any other files- just the pictures-do you know where they would be. I went to gnome pilot and enabled everything. As it is Hot sync. I can see it is saving all the items, but cannot find where they are in the computer
Thanks
Allan

If you used Gnome-pilot, it should be in the Evolution mail client.  That's where it goes by default.
Applications>Internet>Evolution Mail

Hope that helps, sorry for the delay.

---

