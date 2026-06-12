---
title: "adding files"
date: 2007-02-16
forum: Absolute Beginner Talk
---

### Post by roylond on 2007-02-16
Hello I am a complete beginner with this. I have managed to install 6.06 onto a 6.1 gb drive with no other os. I am attemping to get my Speedtouch 330 installed, after following a thread written by darrell. It seems to have gone ok up the point of cp the sppedtch txt into the /etc/hotplug/usb/speedtch file. 
I get the error message 'no such file or directory' 
My question is how do get the file needed ?
Do I write it myself ? if so how?
Thanks for any help

---

### Post by dbott67 on 2007-02-16
Try:
```
gksudo gedit /etc/hotplug/usb/speedtch
```

And add the appropriate text.  Save & close.

-Dave

---

### Post by highneko on 2007-02-16
If you have the "sppedtch txt" then you could open nautilus and change the directory to /etc/hotplug/usb then in the nautilus gui click > file > create document > empty file >name it speedtch > then open the newly create file and paste the contents of "sppedtch txt" into it. 

Good luck, have fun.

---

### Post by roylond on 2007-02-17
Thanks for replying dbott67 & highneko.
I'm doing as suggested so will take a little time but hope I'll get there.

roylond

---

### Post by roylond on 2007-02-19
Hello Again

I thoght that everything went ok but when I hot plug the modem I get the following error message.

Feb 19 15.49.04 collie kernel: [4297003. 678003] usb 1-1: new full speed USB device using ohci-hcd and adress 4
Feb 19 15.49.04 collie kernel: [4297004. 444000] usb 1-1 reset new full speed USB device using ohci-hcd and adress 4
Feb 19 15.49.05 collie kernel: [4297004. 873000] speedtch 1-1: 1.0: no stage 1 firmware found !

Can anyone tell what this means - apart that it still doen't work. The firmware seemed to install ok and the speedtch.txt file is also installed.

Thanks in advance

---

