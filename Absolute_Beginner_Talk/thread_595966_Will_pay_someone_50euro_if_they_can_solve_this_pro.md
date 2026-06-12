---
title: "Will pay someone 50euro if they can solve this problem."
date: 2007-10-29
forum: Absolute Beginner Talk
---

### Post by zakeen on 2007-10-29
I have a program that need a USB-Serial convertor to work in WINE. It seems WINE is not so easy to setup a USB connecting, but its possible I have read.

If your willing to help me to get this to work, Im willing to pay the 50euro(paypal or banktransfer). I will follow the steps given in order of who post them first. The first one that works will get 50euro.

To give you some reading on it from winehq.org it seems it should work:

[http://www.winehq.org/?issue=331#USB](http://www.winehq.org/?issue=331#USB) Support in Wine

Ive tried to link the USB to Com1 in doesdevices(which is what most people say here to do), it links and I can see it but this didnt work. Or maybe there is more to it.

I also think this would be a great help for a lot of other people because I have searched the forums here and it seems a lot of people have ran into errors also trying to get this to work. Ive tried everything that I know(which is not much in linux world) and it didnt get me to far.

Please make the steps simple to follow.

---

### Post by bwallum on 2007-10-29
Just a thought but you close to paying for a whole years official Ubuntu support. They'll fix it. I wish i could help but have no knowledge of your kit.
Regards
Bob

---

### Post by 3rdalbum on 2007-10-29
> **bwallum said:**
> Just a thought but you close to paying for a whole years official Ubuntu support. They'll fix it. I wish i could help but have no knowledge of your kit.
Regards
Bob

Wine is not in Main, so no; Canonical does not support Wine.

---

### Post by bwallum on 2007-11-01
Big response eh? Possibly because commercial gain is not on most peoples minds (that reside here)? That's a real weird concept eh? Think about it and just ask an intelligent question as though you were amongst friends. If that's too difficult a concept in our modern world, take a shower and think about it. You'll be a contributor next!

---

### Post by Arthur Archnix on 2007-11-01
I read your link. I doubt you'll find someone willing to take on this project for 50Euros. Here are the four ways they say it's possible:

>    1.  Make a kernel module in your OS (eg. a Linux kernel module) that exports the same interface that the software expects and works the same way as the Windows driver. Using USBSCAN.SYS as an example, reading does a USB bulk read, writing does a USB bulk write, and 13 or so i/o control codes do various other things, among them USB control and interrupt transfers. Change kernel32's CreateFileW() to open the /dev device node used by the kernel module and send it to the wine server using wine_server_fd_to_handle(), then reading and writing will go to your kernel module, where you can implement them by doing USB reads and writes. Change ntdll's file.c's NtDeviceIoControlFile to capture i/o control codes used by your device, call wine_server_handle_to_fd(), and do an ioctl() on that fd to send that i/o control call to the kernel module, which then reacts appropriately. This way has been tested by me, it works and it's fast, but it's non-portable (eg. Linux-only, and Linux's USB interface keeps changing so an out-of-tree module will only work on some versions, the usual problems...), difficult (kernel-mode code is hard to write), and generally a royal PITA.
   2. Like (1) but use a framework like FUSD (the xiph.org version works on 2.6 kernels) to write the driver in user-space and then do USB I/O using libusb. I'm currently testing this approach, I suspect it's slow (how significantly remains to be seen), but at least it's more portable between Linux versions and easier to write and maintain.
   3. Integrate your device into wine directly the way eg. serial ports have been done. This is hard, and requires introducing a new FD_TYPE, changing ntdll's file.c's NtReadFile, NtWriteFile, and NtDeviceIoControlFile (and asynchronous versions of those) to use special behavior for that FD_TYPE, and managing global device state (eg. i/o timeouts) in wineserver (look at server/serial.c). With a lot of time, and some changes to both wine and libusb, you could get it to work properly. This should IMO only be done for generally useful drivers, not drivers for just 1 type of device.
   4. Integrate NTOSKRNL.EXE into wine, add USB infrastructure to NTOSKRNL.EXE so that kernel-mode drivers can access USB (probably through libusb), and modify ntdll to forward the appropriate reads, writes, and i/o control requests to NTOSKRNL.EXE so that the .SYS file can handle them. This is the only way that works with .SYS files out-of-the-box, the others all require a rewrite of the .SYS driver's functionality. Architecturally, this is the best way, you wouldn't need to change any code in wine to add a new driver.

Not that I really understand what you're trying to do, from your post, but my guess is that at this point you should turn your attention to virtualization or look into other hardware solutions.

---

### Post by inversekinetix on 2007-11-01
> **bwallum said:**
> Big response eh? Possibly because commercial gain is not on most peoples minds (that reside here)? That's a real weird concept eh? Think about it and just ask an intelligent question as though you were amongst friends. If that's too difficult a concept in our modern world, take a shower and think about it. You'll be a contributor next!


meeow!  how about thinking of it this way.  Someone has a problem they can't fix, they've tried but still can't do it themselves.  They're asking someone to volunteer their time and expertise to help fix said problem.  As a gesture of gratitude for getting the requested help they would like to give something back.  Appreciating  someone for their kindness, think about it.  If that's too difficult a concept in our modern world, take a shower and think about it again.  You could have contributed more!

---

### Post by bwallum on 2007-11-01
Thanks is good if it is rightly placed. Payment sort of takes away a little bit of the soul. It is quite subtle, the human spirit wants to contribute. Others hijack that given for personal gain. We all die. Is it better to contribute than to exploit? A life choice; no doubt those that get a kick out of contributing will contribute, those that want to exploit will. We are not immune to the attractions to both views and see both types. Maybe we just choose a path because it is what we want to do. I DO NOT WANT TO EXPLOIT, I would very much like to contribute where I can. Some say what they think quietly, others grab, and some are quite rude in public and use capitals.

---

### Post by inversekinetix on 2007-11-01
> **bwallum said:**
> Thanks is good if it is rightly placed. Payment sort of takes away a little bit of the soul. It is quite subtle, the human spirit wants to contribute. Others hijack that given for personal gain. We all die. Is it better to contribute than to exploit? A life choice; no doubt those that get a kick out of contributing will contribute, those that want to exploit will. We are not immune to the attractions to both views and see both types. Maybe we just choose a path because it is what we want to do. I DO NOT WANT TO EXPLOIT, I would very much like to contribute where I can. Some say what they think quietly, others grab, and some are quite rude in public and use capitals.


Did you forget to take something?  Where does exploitation come into it?  If the horse you're riding is really as high as it appears, you probably don't see all the exploitation behind most things in your everyday life,  where were your sneakers make?  I think you need to dismount and get yourr feet back on the ground.

---

### Post by Arthur Archnix on 2007-11-01
While interesting, you two should take this debate over to the cafe and not add any unecessary confusion to this OP's thread.

---

### Post by zakeen on 2007-11-02
I have spent hours on this, but have fail, I have read heaps of posts and all leading to nothing. Im not saying its not possible, because the people that try to help make it seem easy, simple link. But Im sure its more I dont know ubuntu enough to get it work, before I say they were wrong. I just need a serial port to work, then I dont need windows. There are heaps of unsolved post here about this problem also. So Im happy to be the person to pay someone to get this to work and have the others use it also.

Do a search on USB Serial WINE and you will see heaps of threads with needing help. But there is not anyone that has got it working.

Ive just come in contact with a crossover worker where I might be paying him to do it for me. He makes it sound pretty easy.

But for sure i would like to help someone here and pay them first.

Sorry if someone thought it was wrong to give payments for something thats very important to me.

---

### Post by philinux on 2007-11-02
[http://www.linuxforums.org/forum/wine/94500-serial-ports-wine.html](http://www.linuxforums.org/forum/wine/94500-serial-ports-wine.html)

---

### Post by zakeen on 2007-11-02
Thanks philinux, but that didnt work. The link appears in the doesdevices under .wine, in the properties it say it works. However it doesnt seem to be picking it up.

What I dont get is, eveyone says its a simple link. Ive tried them all, to COM1 COM01 com1 com01 and then I created links to com1-com9 for each without luck. But on the wine site as Arthur Archnix says, its much more complicated.

So has anyone got this usb to serial to work with just the links?

---

