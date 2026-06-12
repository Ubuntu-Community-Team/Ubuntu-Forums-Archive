---
title: "USB wake from sleep? Is it possible?"
date: 2010-05-02
forum: Apple Hardware Users
---

### Post by X-Legs on 2010-05-02
My Macbook Pro 4,1's screen died. I decided to get an external monitor and convert it into a desktop style machine. 

I don't want to leave the computer on 24/7. But because reaching for the power button when the laptop is closed and stored in a confine space is a HUGE pain, I decided to put it into sleep mode. In OS X, I can put the computer to sleep and wake it up with my USB mouse and keyboard.

In Ubuntu 10.04, however, the USB mouse and keyboard don't wake up from suspend. Since opening the laptop is big pain with it being in a very confined space, is there any way to change it? Ubuntu Tweak and the GNOME Power Manager are no help at all.

Thanks in advance,
X-Legs

---

### Post by llamabr on 2010-05-02
Have you tried using 'suspend' rather than 'hybernate'?  the power usage is mininal, but it should wake with usb.

---

### Post by X-Legs on 2010-05-02
I tried both. The regular keyboard and mouse (on the actual laptop)  works, but not the USB.

---

### Post by X-Legs on 2010-05-05
Can anybody at least point me in the right direction? I'd love to use Ubuntu as my main OS, but this sleep thing is preventing me from doing that.

---

### Post by linuxopjemac on 2010-05-05
You might want to try wakeonlan, from another computer ?

Here is a link how it is setup from an Ubuntu machine
[http://lojic.com/blog/2008/09/03/ubuntu-804-linux-wake-on-lan/](http://lojic.com/blog/2008/09/03/ubuntu-804-linux-wake-on-lan/)

Maybe you could make it wake up with lirc with the remote control ? I dont know...

---

### Post by X-Legs on 2010-05-05
Great News! I found the solution at this thread:
[http://www.uluga.ubuntuforums.org/showthread.php?p=4466270](http://www.uluga.ubuntuforums.org/showthread.php?p=4466270)

---

