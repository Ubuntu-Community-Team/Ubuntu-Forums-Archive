---
title: "Interesting Ndiswrapper problem - Satellite A215"
date: 2008-01-22
forum: Absolute Beginner Talk
---

### Post by schibs on 2008-01-22
I have a Toshiba Satellite A215. Right now it dual boots between Vista and Gutsy Gibbon (looking to remove Vista once I have Ubuntu up and running perfectly.)

The problem I'm having is with Ndiswrapper. 

I've copied the Realtek 8187B windows drivers to a folder in my Home directory and installed Ndiswrapper.

What makes this interesting is when I run the Ndiswrapper program, I pick the .inf file from it's location and click "Install". But...nothing happens. I end up back at the screen where it asks me to choose the inf location.

Has anyone run into this before? If so, what is the fix?

Appreciate any help I can get.

---

### Post by Hightide on 2008-01-22
> **schibs said:**
> I have a Toshiba Satellite A215. Right now it dual boots between Vista and Gutsy Gibbon (looking to remove Vista once I have Ubuntu up and running perfectly.)

The problem I'm having is with Ndiswrapper. 

I've copied the Realtek 8187B windows drivers to a folder in my Home directory and installed Ndiswrapper.

What makes this interesting is when I run the Ndiswrapper program, I pick the .inf file from it's location and click "Install". But...nothing happens. I end up back at the screen where it asks me to choose the inf location.

Has anyone run into this before? If so, what is the fix?

Appreciate any help I can get.


Hi schibs

have you had a look at Kevdogs Ndiswrapper. It may help

[http://ubuntuforums.org/showthread.php?t=574501](http://ubuntuforums.org/showthread.php?t=574501)

or this thread from RomeReactor

[http://ubuntuforums.org/showthread.php?t=672756](http://ubuntuforums.org/showthread.php?t=672756)

regards

:)

---

### Post by schibs on 2008-01-28
Hightide - thanks for the links. From what I've read, I believe the first link will be more beneficial for me. The second hyperlink doesn't apply as I have Ndiswrapper installed.

The problem occurs when I point Ndiswrapper at the .inf file. When I choose the .inf file and click on <Install>, nothing happens.

I'm going to go through the posting by Kevdog and see what happens. With a toddler in the house, I don't get as much time to play on the computer as I would like :(

I just wanted to see if anyone else had problems once Ndiswrapper was installed. People seem to have problems with the installation of ndiswrapper, or connectivity issues once the driver is installed.

Thanks again.

---

### Post by The Tronyx on 2008-02-07
> **schibs said:**
> Hightide - thanks for the links. From what I've read, I believe the first link will be more beneficial for me. The second hyperlink doesn't apply as I have Ndiswrapper installed.

The problem occurs when I point Ndiswrapper at the .inf file. When I choose the .inf file and click on <Install>, nothing happens.

I'm going to go through the posting by Kevdog and see what happens. With a toddler in the house, I don't get as much time to play on the computer as I would like :(

I just wanted to see if anyone else had problems once Ndiswrapper was installed. People seem to have problems with the installation of ndiswrapper, or connectivity issues once the driver is installed.

Thanks again.

Sorry if it seems like I am bumping an old thread but I had the same problem with my Toshiba A215.  Unfortunately I fixed it by buying a USB wireless device.  Anyways, the internal Realtek card seems to show up as a USB device, you can probably verify this by issuing 'sudo lsusb'  You can point NDISwrapper to the USB location listed from that command and see if that works.

Sorry again for the late post and good luck dude!

---

### Post by schibs on 2008-02-08
2point0: I just logged on and saw your reply. Thanks  - that was an interesting post. It's got me sitting here going "hmm..."  :-k

I'll try that this weekend and post my results.

Thanks again.

---

### Post by schibs on 2008-02-14
[QUOTE=2point0;4289350] ...the internal Realtek card seems to show up as a USB device, you can probably verify this by issuing 'sudo lsusb'  You can point NDISwrapper to the USB location listed from that command and see if that works.[QUOTE]


I ran the lsub command, but I don't know how to point NDIwrapper to the location. Can you tell me how this is done?

Thanks,

Schibs

---

