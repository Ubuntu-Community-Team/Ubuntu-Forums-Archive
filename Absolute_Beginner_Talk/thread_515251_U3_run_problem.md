---
title: "U3 run problem"
date: 2007-08-01
forum: Absolute Beginner Talk
---

### Post by Archoniam on 2007-08-01
I cannot run my new Cruzer(R) SanDisk 4gig micro flash drive. My wine had this output in terminal:
```
archoniam@claptop:~$ wine '/media/disk/LaunchU3.exe' 
fixme:wave:ALSA_AddCaptureDevice Add support for DSCapture
fixme:win:RegisterDeviceNotificationW (hwnd=0x20024, filter=0x7bdfe9c0,flags=0x00000000), STUB!
fixme:setupapi:SetupDiGetClassDevsW returning empty list
fixme:setupapi:SetupDiEnumDeviceInfo 0x1a4718 0 0x33f3d4
fixme:setupapi:SetupDiGetClassDevsW returning empty list
fixme:setupapi:SetupDiEnumDeviceInfo 0x172168 0 0x33fab8
```

---

### Post by bodhi.zazen on 2007-08-01
Yep

U3 is not supported in Linux

You can remove it if you like ... 

		[http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html](http://www.geekyjock.com/pages/blog/2006/05/remove-u3-software-from-your-usb-flash.html)

		[http://www.u3.com/uninstall/](http://www.u3.com/uninstall/)
	
	[http://cse.msstate.edu/~rwm8/hackingU3/](http://cse.msstate.edu/~rwm8/hackingU3/)

I also suggest you request linux support for U3 and Cruzer

---

