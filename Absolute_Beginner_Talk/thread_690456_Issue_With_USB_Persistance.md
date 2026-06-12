---
title: "Issue With USB Persistance"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by wanfahmi on 2008-02-07
Hi,
I have Ubuntu 7.10 on USB stick. Things work well. I've done the upgrade and the system is up to date.
The problem is my casper-rw partition will have error EVERYTIME I shut down.
I don't get any error if I boot up -> do nothing -> shutdown
I'll get error if I bootup -> do something -> shutdown.
To fix it, I need to boot on live cd and run fsck.

I suspect the USB stick is slow and the system is unable to flush the cache to USB stick during shutdown.

EDIT:My second USB stick also is having the same error.

Can any body help me?

Thanks

---

### Post by wanfahmi on 2008-02-07
Anybody?

---

### Post by Herman on 2008-02-08
Yeah, I'd be interested to know too if anyone can explain this, it happens to my USB flash memory stick Ubuntu installations too.  They still seem to work okay. but it would be nicer to be able to shut down without any errors. I wonder if Autofsck would be a good solution to this problem? 
Have a read of this thread,  			 			 			 			[fsck on shutdown]("http://ubuntuforums.org/showthread.php?t=605748&highlight=fsck").

I might give musther's Autofsck a try myself in my flash memory stick and see what it can do.

Regards, Herman :)

---

### Post by wanfahmi on 2008-02-08
The thing is, This issue doesn't occur on my HP 4 Gig Stick.Unfortunately, I left my HP Usb stick in my pants' pocket and my wife put it thru the washer.

That's why I suspect its the speed of the USB stick. The HP Stick boots up really fast and my current, from PenDrive Mini, is not really fast.

If somehow we can increase the delay during shutdown and give time for the USB stick to write it's stuff.
(Maybe a delay  in executing casper)

---

### Post by Herman on 2008-02-08
I have a Kingston Data Traveller, it seems to be quite fast to me, I'm not sure if there's a way to make an accurate measurement.

I installed [Autofsck]("https://wiki.ubuntu.com/AutoFsck") and set it to run fsck at every shutdown or reboot. It seems as if it's doing something but I'm not really sure, it takes longer to shut down and the USB disk LED flashes more I think, but then the same file system errors still appear a few seconds after the message about removing the disc (if any) and pressing 'Enter'.

---

### Post by wanfahmi on 2008-02-10
I think I have the solution. Tested on 2 USB sticks.
You need to disable casper

Install sysv-rc-conf
Scroll till you see casper
DESELECT casper at every runlevel
Done.
Reboot.

This gets rid of "Press enter...." and the shutdown errors. It seems casper umounts partitions and caches some folders on shutdown which causes the IO error.

Give it a try. Please report if good.

---

### Post by Herman on 2008-02-10
Thanks wanfahmi,
I tried that and it did get rid of those error messages but mine must be different from yours. 
[Sysv-rc-conf]("http://wiki.kartbuilding.net/index.php/Sysv-rc-conf")
In my Ubuntu USB Persistent flash memory install the error messages were replaced with other error messages instead, so it didn't seem to be an improvement for mine. However, it may still help other people, I'm not sure.
Regards, Herman :)

---

### Post by wanfahmi on 2008-02-11
On my USB install, It got read of write errors on shutdown, but some network error message does appear. As long as there's no write error, I'm happy.

So far this method get rid of bootup errors.

---

