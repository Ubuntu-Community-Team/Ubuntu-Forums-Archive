---
title: "Would like to get my Canon digital camera working."
date: 2007-03-25
forum: Absolute Beginner Talk
---

### Post by Outrunner on 2007-03-25
Hello again fellow forumites! I have a Canon Powershot A430 digital camera, and it doesn't seem to want to work on my Ubuntu box. You see I start up the camera and plug it in my Ubuntu box via a USB cable. Everything's fine, it detects the camera and asks me if I want to import my photos. OK, and then I notice an error:

```
An error occurred in the io-library ('Could not claim the USB device'): Could not claim interface 0 (Operation not permitted). Make sure no other program or kernel module (such as sdc2xx, stv680, spca50x) is using the device and you have read/write access to the device.
```

OK, the most probable answer is that I don't have read/write permissions(as suggested in the error). Well then I should give myself permission through the terminal right? Unfortunately there's no sign of where the camera is mounted(it surely isn't on the desktop, /mnt or /media). There doesn't seem to be much to give permission to right now...

OK, thats fine, I download gtkam through Synaptic and make it detect my camera. Everything's fine until I try using the OK or Apply buttons, because if I do that I get "Could not initialize camera." Yay, party... I'm not sure what to do now. I'm a bit lost actually, can I get it to work at all, or this is a lost cause?

It's just a photo of my PSU specs, why not let me see the photo Mr Ubuntu? :cry:

---

### Post by luc_o on 2007-03-25
See the last 2 messages of this thread.  Worked for me.  Hope it works for you too.
[http://www.ubuntuforums.org/showthread.php?t=325324](http://www.ubuntuforums.org/showthread.php?t=325324)

---

### Post by Outrunner on 2007-03-25
Ohh. My. God. It worked! I read the links in the last two posts and it worked :) Thanks alot

---

### Post by Lupurus on 2007-03-25
Same problem, didn't work for me though... *sniffle*
Any other suggestions?
EDIT: Tried some other stuff, all is well.

---

