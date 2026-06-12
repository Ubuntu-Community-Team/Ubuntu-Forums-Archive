---
title: "xgl compiz had wrought havoc!"
date: 2006-08-22
forum: Absolute Beginner Talk
---

### Post by pingbat on 2006-08-22
Okay,

I followed different guides on how to install and configure xgl/compiz.

Now when I boot up, xserver doesn't even try to start and i get shoved straight onto command line.

If I type startx, it starts but the windows cannot be moved and the X(close window) and _(minimises) buttons do not appear at the top right of the windows...

Also the mouse keeps on going haywire, it is a logitech G5 usb mouse.

I am thinking that i should start from scratch, how can I do this?

I am running a dual boot using GRUB 0.95 .

Thanks for the help guys.

---

### Post by slimdog360 on 2006-08-22
did you see the notice, there is a bug which makes x crash

---

### Post by TrendyDark on 2006-08-22
If you want to start from scratch and don't have anything on your Ubuntu partition that you really need, I would suggest just reinstalling Ubuntu.

If you need something from your Ubuntu partition and would like to reinstall, I would suggest mounting the partition from Windows (assuming that is the other operating system you have) and copying the files to a disk or usb flash drive.

---

### Post by gruffy-06 on 2006-08-22
Which graphics card, pingbat, do you use?

ATI and nVidia cards are known to have some problems with Xgl and Compiz.

---

### Post by TrendyDark on 2006-08-22
> **gruffy-06 said:**
> Which graphics card, pingbat, do you use?

ATI and nVidia cards are known to have some problems with Xgl and Compiz.

I thought XGL and compiz only work with Nvidia cards?

---

### Post by gruffy-06 on 2006-08-22
Xgl and Compiz also works on cards that support 3-D acceleration. However, it has not been thoroughly tested on graphics hardware.

i.e. I have an Mobile Intel i810 on my laptop with 256M of ram. AIGLX and Compiz run fine with a few bugs.


- AIGLX is an alternative to the Xgl X Server.

---

### Post by TrendyDark on 2006-08-22
OH, okay. I haven't tested out Xgl and Compiz at all. My hardware setup is kind of low-end. Thus my understanding of the topic is minimal lol.:)

---

### Post by pingbat on 2006-08-22
I should clarify that I have reverted to an older version of xserver.

How does one go about reinstalling ubuntu?
Should I just download and burn a cd?
I would prefer to do it over the internet.

Isn't there a way of just reverting everything to original without downloading it all again?

Finally, If i reinstall will i encounter problem with the dodgy xserver?

---

### Post by gruffy-06 on 2006-08-22
It may not be possible for you to have a 3-D desktop using Xgl and Compiz.
Wait for the official release. That will be something to get excited about.

---

### Post by gruffy-06 on 2006-08-22
The message i previously sent was for someone else. sorry for confusion.
 You can order Ubuntu 6.06.1 from ShipIt. It contains addition security updates.

---

### Post by gruffy-06 on 2006-08-22
reinstalling gives no problem with the x server.

If your card is not nvidia, you may want to try searching for aiglx instead of xgl. There are some good tutorials around.

---

### Post by pingbat on 2006-08-22
Unfortunately, I am have an nvidia 7800 gt.

How can I reinstall behind the GRUB loader without messing up GRUB (need windows to work)

---

