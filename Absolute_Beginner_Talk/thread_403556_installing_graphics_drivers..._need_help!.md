---
title: "installing graphics drivers... need help!"
date: 2007-04-06
forum: Absolute Beginner Talk
---

### Post by Dragon665 on 2007-04-06
Right, when i try to boot up off of livecd i get this error: -

"Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the X Server output to diagnose the problem?"

When I press 'No', I get this message: -

"The X Server is now disabled. Restart GDM when it is configured correctly."

Some help would be appreciated before I get mad and smash my pc to bits!

Thanks

Roy

P.S I am a complete n00b to linux, only started yesterday!

---

### Post by crispingatiesa on 2007-04-06
What type of video card you have? 

Could you please post here the message?  Say yes to see the details and post here the details (check for the last lines of the log file)

---

### Post by zvacet on 2007-04-06
```
  sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Dragon665 on 2007-04-06
I have tried the reconfigure sudo thingy and its still comes up. Pressing yes to see the diagnosis and it has at the bottom: - "Fatal server error: no screen found"

Can anyone please help me :confused: 

Thanks

Roy

---

### Post by wpshooter on 2007-04-06
What video card type do you have ?

---

### Post by Dragon665 on 2007-04-06
nvidia 8800 gts 640 mb

---

### Post by Dragon665 on 2007-04-06
anybody?

---

### Post by Dragon665 on 2007-04-06
So far i have wasted my whole day trying to install ubuntu without success and people appear to be ignoring my posts pleaing for help.

---

### Post by wpshooter on 2007-04-06
Unfortunately, I am an ATI user so I have basically no knowledge of the Nvidia cards or I would be glad to help you.

BUT, if you will go to the Multimedia & Video forum section and look at the last STICKY at the top of the forum, I believe that may help you.  Or just put your question in the Video forum and you will probably stand a better chance of getting good information.

Good luck.

---

### Post by johnc4510 on 2007-04-06
I don't think reconfiguring x will work if your running off of the live cd. Especially if you restart for the changes to take effect. Being a live cd you lose any configurations at restart.

Try this, at the log in screen, choose sessions and then choose fail safe, or something like that and that should get you to the desktop to install if you want.

Note: If you are able to install Ubuntu, you will still have this problem when you reboot the first time. Just choose fail safe again and then look into installing the nvidia drivers for your card.

---

### Post by Dragon665 on 2007-04-07
Hi all,

Finally got Ubuntu installed and I must say, it does look smooth ans simple which I say is the best way, for me anyway. I have downloaded the nvidia 8800 gts drivers off the nvidia website and have followed the command that they said to type into a terminal but I always get: - nvidia-installer: Error opening log file '/var/log/nvidia-installer.log' for writing (Permission denied); disabling logging.¨ Can someone help me please?

Thanks

Roy

---

### Post by siciliancasanova on 2007-04-07
Are you doing this as root?  

```
sudo
```

?

---

### Post by ffxr on 2007-04-07
are you using sudo ahead of the command\?

you also need to do this outside of X..

your looking at method 2 on this howto:
[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)

---

### Post by Dragon665 on 2007-04-07
Aaaahhh yes, thats a good point, just tried that but it tells me that the X Server is running and that I have to exit it first???

Thanks

Roy

---

### Post by Dragon665 on 2007-04-07
Hang on, I used Envy to install the latest drivers which it did. Then it asked me to restart, which I also did. Now I'm getting the same error as before: - "Failed to start the X Server (your graphical interface). It is likely that it is not set up correctly. Would you like to view the output to diagnose the problem?" At the bottom of the diagnosis it says "Fatal server error: AddScreen/ScreenInit failed for driver 0"

Help?!?!

---

### Post by siciliancasanova on 2007-04-07
Ok, let me grab some code...

Get to the command line and get your x-server installed again and use vesa.  Then output us your x-server code and we will mark it up for you.

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
sudo nano /etc/X11/xorg.conf
```

then start the xserver again

```
startx
```

---

### Post by Dragon665 on 2007-04-07
Sorry to be a n00b, but how do i get into command line?

---

### Post by siciliancasanova on 2007-04-07
Well after it tells you that it failed to start x, it should ask you for your username and password (you should automatically be in the command line) after that enter the previous code

---

### Post by Dragon665 on 2007-04-07
Rightie then, I did what you said except the sudo cp /etc/x11/xorg.conf thingy as it said no such directory existed?!? err... err... what now???

Roy

---

### Post by siciliancasanova on 2007-04-07
Whoops, try this...

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Dragon665 on 2007-04-07
Sorry, i did that reconfigure code and im in linux now, but back to my original problem, how do i install drivers for my nvidia 8800 gts???

Thanks for fast replies! :)

---

### Post by siciliancasanova on 2007-04-07
What is the driver for the card in X, is it set to VESA now?

```
sudo gedit /etc/X11/xorg.conf
```

---

### Post by Dragon665 on 2007-04-07
Yes, its set to VESA now, but the one Envy downloads is &#323;VIDIA-Linux-x86-1.0-9755-pkg1.run. Any ideas?

---

### Post by siciliancasanova on 2007-04-07
Now change your directory to the location of the downloaded driver.  Install the driver and go back and edit your xserver file

[This guide]("http://us.download.nvidia.com/XFree86/Linux-x86/1.0-9755/README/chapter-03-section-02.html") shows you how to do it manually

---

### Post by Dragon665 on 2007-04-07
Do I edit it while in linux then as it wont let me save it? Its all a bit complicated... Its easier on Win XP. Or, do I edit it from outside of linux, in the terminal?

---

### Post by Dragon665 on 2007-04-07
Im confused, I edited it outside in the terminal but i still get the error!! Its a bit beyond me to edit stuff like that. Its like your all talking in chinese and expecting me to understand? I now have ¨nvidia¨ as well as ¨nv¨. But neither work. HELP!

---

### Post by Dragon665 on 2007-04-07
This is the log:

*Mode: 112 (640x480)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 480
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 114 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 1600
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 1600
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 115 (800x600)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 3200
	XResolution: 800
	YResolution: 600
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 3200
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 117 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 2048
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 2048
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 118 (1024x768)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 4096
	XResolution: 1024
	YResolution: 768
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 4096
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 11a (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 2560
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*(II) VESA(0): Not using built-in mode "1280x1024" (hsync out of range)
Mode: 11b (1280x1024)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 5120
	XResolution: 1280
	YResolution: 1024
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 1
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 5120
	BnkNumberOfImagePages: 1
	LinNumberOfImagePages: 1
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 130 (320x200)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 200
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 62
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 62
	LinNumberOfImagePages: 62
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 131 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 132 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 14
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 14
	LinNumberOfImagePages: 14
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 133 (320x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 134 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 320
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 8
	NumberOfBanks: 1
	MemoryModel: 4
	BankSize: 0
	NumberOfImages: 30
	RedMaskSize: 0
	RedFieldPosition: 0
	GreenMaskSize: 0
	GreenFieldPosition: 0
	BlueMaskSize: 0
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 320
	BnkNumberOfImagePages: 30
	LinNumberOfImagePages: 30
	LinRedMaskSize: 0
	LinRedFieldPosition: 0
	LinGreenMaskSize: 0
	LinGreenFieldPosition: 0
	LinBlueMaskSize: 0
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
Mode: 135 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 640
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 19
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 640
	BnkNumberOfImagePages: 19
	LinNumberOfImagePages: 19
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*Mode: 136 (320x240)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 1280
	XResolution: 320
	YResolution: 240
	XCharSize: 8
	YCharSize: 8
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 10
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 10
	LinNumberOfImagePages: 10
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000
Mode: 13d (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 1280
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 16
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 6
	RedMaskSize: 5
	RedFieldPosition: 11
	GreenMaskSize: 6
	GreenFieldPosition: 5
	BlueMaskSize: 5
	BlueFieldPosition: 0
	RsvdMaskSize: 0
	RsvdFieldPosition: 0
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 1280
	BnkNumberOfImagePages: 6
	LinNumberOfImagePages: 6
	LinRedMaskSize: 5
	LinRedFieldPosition: 11
	LinGreenMaskSize: 6
	LinGreenFieldPosition: 5
	LinBlueMaskSize: 5
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 0
	LinRsvdFieldPosition: 0
	MaxPixelClock: 229500000
*(II) VESA(0): Not using built-in mode "640x400" (vrefresh out of range)
Mode: 13e (640x400)
	ModeAttributes: 0x3bf
	WinAAttributes: 0x7
	WinBAttributes: 0x0
	WinGranularity: 64
	WinSize: 64
	WinASegment: 0xa000
	WinBSegment: 0x0
	WinFuncPtr: 0xc0008340
	BytesPerScanline: 2560
	XResolution: 640
	YResolution: 400
	XCharSize: 8
	YCharSize: 16
	NumberOfPlanes: 1
	BitsPerPixel: 32
	NumberOfBanks: 1
	MemoryModel: 6
	BankSize: 0
	NumberOfImages: 2
	RedMaskSize: 8
	RedFieldPosition: 16
	GreenMaskSize: 8
	GreenFieldPosition: 8
	BlueMaskSize: 8
	BlueFieldPosition: 0
	RsvdMaskSize: 8
	RsvdFieldPosition: 24
	DirectColorModeInfo: 0
	PhysBasePtr: 0xd1000000
	LinBytesPerScanLine: 2560
	BnkNumberOfImagePages: 2
	LinNumberOfImagePages: 2
	LinRedMaskSize: 8
	LinRedFieldPosition: 16
	LinGreenMaskSize: 8
	LinGreenFieldPosition: 8
	LinBlueMaskSize: 8
	LinBlueFieldPosition: 0
	LinRsvdMaskSize: 8
	LinRsvdFieldPosition: 24
	MaxPixelClock: 229500000

(II) VESA(0): Total Memory: 256 64KB banks (16384kB)
(II) VESA(0): Generic Monitor: Using hsync range of 28.00-49.00 kHz
(II) VESA(0): Generic Monitor: Using vrefresh range of 43.00-72.00 Hz
(--) VESA(0): Virtual size is 1024x768 (pitch 1024)
(**) VESA(0): *Built-in mode "1024x768"
(**) VESA(0): *Built-in mode "800x600"
(**) VESA(0): *Built-in mode "640x480"
(==) VESA(0): DPI set to (75, 75)
(II) VESA(0): Attempting to use 60Hz refresh for mode "1024x768" (118)
(II) VESA(0): Attempting to use 72Hz refresh for mode "800x600" (115)
(II) VESA(0): Attempting to use 60Hz refresh for mode "640x480" (112)
(**) VESA(0): Using "Shadow Framebuffer"
(II) Loading sub module "shadow"
(II) LoadModule: "shadow"
(II) Loading /usr/lib/xorg/modules/libshadow.so
(II) Module shadow: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.1.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules/libfb.so
(II) Module fb: vendor="X.Org Foundation"
	compiled for 7.1.1, module version = 1.0.0
	ABI class: X.Org ANSI C Emulation, version 0.3
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xd4000000 - 0xd4003fff (0x4000) MX[B]
	[5] -1	0	0xd4004000 - 0xd40047ff (0x800) MX[B]
	[6] -1	0	0xd4100000 - 0xd4100fff (0x1000) MX[B]
	[7] -1	0	0xd4101000 - 0xd4101fff (0x1000) MX[B]
	[8] -1	0	0xd4102000 - 0xd4102fff (0x1000) MX[B]
	[9] -1	0	0xd4103000 - 0xd4103fff (0x1000) MX[B]
	[10] -1	0	0xfeb00000 - 0xfeb000ff (0x100) MX[B]
	[11] -1	0	0xd4104000 - 0xd4104fff (0x1000) MX[B]
	[12] -1	0	0xd0000000 - 0xd1ffffff (0x2000000) MX[B](B)
	[13] -1	0	0xc0000000 - 0xcfffffff (0x10000000) MX[B](B)
	[14] -1	0	0xd2000000 - 0xd2ffffff (0x1000000) MX[B](B)
	[15] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[16] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[17] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[18] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[19] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[20] -1	0	0x0000b000 - 0x0000b007 (0x8) IX[B]
	[21] -1	0	0x0000c400 - 0x0000c40f (0x10) IX[B]
	[22] -1	0	0x00000b60 - 0x00000b63 (0x4) IX[B]
	[23] -1	0	0x00000960 - 0x00000967 (0x8) IX[B]
	[24] -1	0	0x00000be0 - 0x00000be3 (0x4) IX[B]
	[25] -1	0	0x000009e0 - 0x000009e7 (0x8) IX[B]
	[26] -1	0	0x0000d800 - 0x0000d80f (0x10) IX[B]
	[27] -1	0	0x00000b70 - 0x00000b73 (0x4) IX[B]
	[28] -1	0	0x00000970 - 0x00000977 (0x8) IX[B]
	[29] -1	0	0x00000bf0 - 0x00000bf3 (0x4) IX[B]
	[30] -1	0	0x000009f0 - 0x000009f7 (0x8) IX[B]
	[31] -1	0	0x0000f000 - 0x0000f00f (0x10) IX[B]
	[32] -1	0	0x0000e000 - 0x0000e0ff (0x100) IX[B]
	[33] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
	[34] -1	0	0x00004c40 - 0x00004c7f (0x40) IX[B]
	[35] -1	0	0x00004c00 - 0x00004c3f (0x40) IX[B]
	[36] -1	0	0x0000e400 - 0x0000e41f (0x20) IX[B]
	[37] -1	0	0x0000a000 - 0x0000a07f (0x80) IX[B](B)
	[38] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[39] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
(II) Loading sub module "int10"
(II) LoadModule: "int10"
(II) Reloading /usr/lib/xorg/modules/libint10.so
(II) VESA(0): initializing int10
(II) VESA(0): Primary V_BIOS segment is: 0xc000
(II) VESA(0): VESA BIOS detected
(II) VESA(0): VESA VBE Version 3.0
(II) VESA(0): VESA VBE Total Mem: 16384 kB
(II) VESA(0): VESA VBE OEM: NVIDIA
(II) VESA(0): VESA VBE OEM Software Rev: 96.128
(II) VESA(0): VESA VBE OEM Vendor: NVIDIA Corporation
(II) VESA(0): VESA VBE OEM Product: G80 Board - p356h01 
(II) VESA(0): VESA VBE OEM Product Rev: Chip Rev   
(==) VESA(0): Write-combining range (0xd1000000,0x1000000)
(II) VESA(0): virtual address = 0xb60fe000,
	physical address = 0xd1000000, size = 16777216
(==) VESA(0): Default visual is TrueColor
(==) VESA(0): Backing store disabled
(**) Option "dpms"
(**) VESA(0): DPMS enabled
(WW) VESA(0): Option "UseFBDev" is not used
(==) RandR enabled
(II) Setting vga for screen 0.
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)
error opening security policy file /usr/lib/xserver/SecurityPolicy
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us,mk"
(**) Generic Keyboard: XkbLayout: "us,mk"
(**) Option "XkbVariant" ","
(**) Generic Keyboard: XkbVariant: ","
(**) Option "XkbOptions" "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(**) Generic Keyboard: XkbOptions: "grp:alt_shift_toggle,lv3:ralt_switch,grp_led:scroll"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ExplorerPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ExplorerPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
    xkb_keycodes             { include "xfree86+aliases(qwerty)" };
    xkb_types                { include "complete" };
    xkb_compatibility        { include "complete+ledscroll(group_lock)" };
    xkb_symbols              { include "pc(pc105)+us+mk:2+group(alt_shift_toggle)+level3(ralt_switch)" };
    xkb_geometry             { include "pc(pc105)" };
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(**) Option "Device" "/dev/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(EE) xf86OpenSerial: Cannot open device /dev/wacom
	No such file or directory.
Error opening /dev/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/share/fonts/X11/TTF/, removing from list!
Could not init font path element /usr/share/fonts/X11/OTF, removing from list!
Could not init font path element /usr/share/fonts/X11/CID/, removing from list!

The last part any way. Does this help?

Roy

---

### Post by Dragon665 on 2007-04-07
bump, anyone?

---

### Post by Dragon665 on 2007-04-07
AAAAHHH GETTING F****** MAD. IF NO ONE CAN HELP, F****** SAY SO!

Dont know what to do!!!

I have checked the xorg.conf file after it has installed and its the same if i did it maually off there website.

---

### Post by Dragon665 on 2007-04-07
Right, I´ve managed to get into linux using vesa. But now when I install the graphics updates from Envy for an Nvidia 8800 gts 640mb, it asks to restart, so i press yes and i get the same failed to start the x server error. So then i have to change it back to vesa. I have also tried editing it manually to what the nvidia webpage said. which gives the same error.

Some help please. And I am getting fed up with bumping all the time. No offense people but I am really eager to get into linux! Help! :frown: 

Roy

---

### Post by Dragon665 on 2007-04-07
Right a full history: -

Tried to install Ubuntu from Livecd, couldn´t as it came up with Failed to start the x server. So then I was told to use the alternate version, which I did. It installed ok until first boot up which I again recieved the same error as before. Then I was told how to change the driver to ´vesa´. My CURRENT problem now is installing drivers fo an Nvidia 8800 gts 640 mb, which I have tried to install using Envy. To no success. I have tried editing the xorg.conf file as suggested following the instructions on nvidia´s website. No I shall ask again, CAN ANYONE HELP ME??? I may be new to linux, like only started linux 2 days ago, but when i want to know something i shall keep ´spamming´ these message boards until someone can give me an answer! Im not going to bother saying ´thanks' because this post will probably be ignored any way either because nobody knows a solution or nobody cares.

Roy

P.S. I do hope to have a solution, and who ever gives me a solution can, err... have a cookie!

---

### Post by PointSource on 2007-04-07
One solution is to use a new/different/spare video card.

Another is to try a newer version of ubuntu.

---

### Post by Dragon665 on 2007-04-07
is there a newer version of ubuntu, if so can you give me a link?

---

### Post by Swab on 2007-04-07
Another solution would be to try some manners.

---

### Post by Dragon665 on 2007-04-07
> **Swab said:**
> Another solution would be to try some manners.

I have been using manners, but after some time of seeing posts go down to the bottom page and not get answered it starts to get frustrating, BUT I do apologise sincerely to all that got offended!

---

### Post by dbott67 on 2007-04-07
I have always used Automatix to install nVidia drivers without any problems.

Go to [www.getautomatix.com](www.getautomatix.com) and select "Installation".  Choose the appropriate .deb file for your version & architecture.

Once installed, you can click APPLICATIONS > SYSTEM TOOLS > AUTOMATIX

From there, just select the "Drivers" category and install the nVidia drivers (and any other packages that you want.  Normally, I select the various codecs & what-not for MP3 and DVD support, plus a few other handy utils.

There are forums on the Getautomatix.com site for any questions/problems that you might have.

-Dave

---

### Post by overdrank on 2007-04-07
> **Dragon665 said:**
> Right a full history: -

Tried to install Ubuntu from Livecd, couldn´t as it came up with Failed to start the x server. So then I was told to use the alternate version, which I did. It installed ok until first boot up which I again recieved the same error as before. Then I was told how to change the driver to ´vesa´. My CURRENT problem now is installing drivers fo an Nvidia 8800 gts 640 mb, which I have tried to install using Envy. To no success. I have tried editing the xorg.conf file as suggested following the instructions on nvidia´s website. No I shall ask again, CAN ANYONE HELP ME??? I may be new to linux, like only started linux 2 days ago, but when i want to know something i shall keep ´spamming´ these message boards until someone can give me an answer! Im not going to bother saying ´thanks' because this post will probably be ignored any way either because nobody knows a solution or nobody cares.

Roy

P.S. I do hope to have a solution, and who ever gives me a solution can, err... have a cookie!

You might try this thread they had some luck with that card
[http://ubuntuforums.org/showthread.php?t=329635&page=2&highlight=Nvidia+8800](http://ubuntuforums.org/showthread.php?t=329635&page=2&highlight=Nvidia+8800)
Hope this helps!

---

### Post by Wim Sturkenboom on 2007-04-07
You do not really say what your problem is (*To no success* does only say that there is a problem). Instead of spending your energy on useless info about 'spamming', spend it on a proper description of the problem.

So did it install or did the install fail? If the latter, error messages can be usefull. If it installed OK , is the driver used (check Xorg.conf; driver shuld be nvidia).
When starting X, check the contents of /var/log/Xorg.0.log when you have the problem; it usually reveals a lot of info.

Further I used [this page](http://ubuntuforums.org/showthread.php?t=139264) to install the nVidia drivers for my machine with 6100 card. A similar page is available for 6.10

---

### Post by jjbean on 2007-04-07
I am new at this myself. Have you tried installing the NVidia binary X.org driver using Add/Remove applications? It is in Applications > System Tools. Just don't install the legacy version. You can also find the driver in System > Administration > Synaptic Package Manager, just do a search for nvidia-glx. Hope this helps.

---

### Post by HokkaidoHillbilly on 2007-04-07
Hey ya Dragon,

I'm new to Ubuntu myself...just installed 6.10 (Edgy) last week and am still only about 80% to how I want it to function, so don't give up just yet. :)  It's worth it.

Anyhoo...for everybody else reading this thread...is it just me or does it seem like Dragon's Live CD could have some issues, i.e. something went haywire during the burn process maybe?  

Also, Dragon...which version of Ubuntu are you using and what're the specs on your computer other than the video card?

---

### Post by Dragon665 on 2007-04-07
I installed Ubuntu from the alternate disk through the text based version and it installed fine, it was when booting up for the first time off the hdd that it came up with the error. I thought i said i could get into ubuntu through the vesa driver? Any way, I tried Automatix and now after you see the loading bar finish, it just goes blank screen. How do i get it back/change back to vesa?

Have some cookies!

---

### Post by HokkaidoHillbilly on 2007-04-07
Can you get to the non-X terminal when you boot up?

If you can, and you made a backup of your xorg.conf before changing things around via Automatix (I'd assume that automatix does this automatically, in anycase), try this at the command line:

> sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.confThis *should* make it revert to the way it was prior to the Automatix installation.

---

### Post by zdude on 2007-04-07
Did you try running "nvidia-settings"? It will detect and setup your monitor, etc. I had to use this program due to an unusual monitor.

---

### Post by KiwiNZ on 2007-04-07
> **dbott67 said:**
> I have always used Automatix to install nVidia drivers without any problems.
 
Go to [www.getautomatix.com]("http://www.getautomatix.com") and select "Installation". Choose the appropriate .deb file for your version & architecture.
 
Once installed, you can click APPLICATIONS > SYSTEM TOOLS > AUTOMATIX
 
From there, just select the "Drivers" category and install the nVidia drivers (and any other packages that you want. Normally, I select the various codecs & what-not for MP3 and DVD support, plus a few other handy utils.
 
There are forums on the Getautomatix.com site for any questions/problems that you might have.
 
-Dave
 
Dragon665 , I would suggest this advice would be usefull to you

---

### Post by rockrerun on 2007-04-07
Well, I wish I had some advice, but I am having this same issue.  Support for the 8800 is a little whacky.  I'm sure you don't have a problem with your live cd as mentioned before, because I am having the same problems.  If you do a quick search, you'll see that you are not the only one.

A lot of the methods people are suggesting here such as automatix, envy, etc. do not work.  I have installed the drivers from nvidia's website in command line, with no success.  Even Feisty Fawn is having the a lot of same problems.  I have spent days trying to get my 8800 to work, but I have pretty much given up for now.  All I can hope is that this issue is fixed before the release of Feisty later this month.

---

### Post by Dragon665 on 2007-04-07
Hi all,

Hey rockrerun, if you follow this link: [http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2)
And do exactly as it says to the letter, I found that it worked! :D

And I would like to say a MASSIVE THANK YOU to all that helped me AND the future people who will have this problem.

I would also like to make a sincere apology to anyone/everyone that I offended!

So far I´m loving Ubuntu, dont know how I lived without it! :lolflag: 

Thanks all!

Roy

---

### Post by Maestro23 on 2007-04-07
> **Dragon665 said:**
> Hi all,

Hey rockrerun, if you follow this link: [http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2)
And do exactly as it says to the letter, I found that it worked! :D

And I would like to say a MASSIVE THANK YOU to all that helped me AND the future people who will have this problem.

I would also like to make a sincere apology to anyone/everyone that I offended!

So far I´m loving Ubuntu, dont know how I lived without it! :lolflag: 

Thanks all!

Roy

Good deal man. Glad this is resolved.  Can you go back to your first post, Advanced edit and mark resolved.  

Here are some links that will help you down the road:

Useful Links:

Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)

Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)

CommandLine Beginners: [http://doc.gwos.org/index.php/CommandLineBeginners](http://doc.gwos.org/index.php/CommandLineBeginners)

Basic Commands: [https://help.ubuntu.com/community/BasicCommands](https://help.ubuntu.com/community/BasicCommands)

LinuxCommand.org(Commands & Linux File Structure): [http://www.linuxcommand.org/](http://www.linuxcommand.org/)

Graphic Card Drivers
ATI supported cards: [https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti](https://wiki.ubuntu.com/HardwareSupportComponentsVideoCardsAti)
Installing ATI Drivers: [http://wiki.cchtml.com/index.php/Ubuntu](http://wiki.cchtml.com/index.php/Ubuntu)
Installing Nvidia Drivers:[http://doc.gwos.org/index.php/Latest_Nvidia_Edgy](http://doc.gwos.org/index.php/Latest_Nvidia_Edgy)
Envy Script(ATI/Nvidia): [http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)

Super Grub Disk: [http://supergrub.forjamari.linex.org/](http://supergrub.forjamari.linex.org/)

---

### Post by overdrank on 2007-04-07
> **Dragon665 said:**
> Hi all,

Hey rockrerun, if you follow this link: [http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2](http://albertomilone.com/latest_nvidia_udsf_edgy.html#METHOD_2)
And do exactly as it says to the letter, I found that it worked! :D

And I would like to say a MASSIVE THANK YOU to all that helped me AND the future people who will have this problem.

I would also like to make a sincere apology to anyone/everyone that I offended!

So far I´m loving Ubuntu, dont know how I lived without it! :lolflag: 

Thanks all!

Roy

Great I am glad we all could help and just return the favor. Rock on :guitar:

---

### Post by rockrerun on 2007-04-07
Awesome! I just got it installed!  Thanks, I might have to re-install feisty to see if this method will work with it as well.  I also was able to get beryl installed and running great! I've been messing around w/ beryl for the past hour or so.

I'm only having one problem though:  Every time I restart, my resolution goes from 1440x900 back to 1024x768.  So far, I've just been setting it back to 1440x900 in the Nvidia X server settings panel.  When I change it, do I need to do something other than hitting "apply" and saving to the X configuration file?  Why would it keep switching back?  Anyone else having this problem?  Thanks!

---

