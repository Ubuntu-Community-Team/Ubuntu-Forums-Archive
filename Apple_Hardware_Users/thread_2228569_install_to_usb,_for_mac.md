---
title: "install to usb, for mac"
date: 2014-06-08
forum: Apple Hardware Users
---

### Post by jim50 on 2014-06-08
hi all

i have a macbook air 2,1 (late 2008 9400) That has a failed SSD in it. I would like to install ubuntu on a USB stick and run it from there. I've installed ubuntu on usb drives quite a few times now and had no problems, but whatever guide I follow, I can't get this to work.

The macbook air does boot of a mac OSX usb key so I know it's working. Trouble is, I can't even make a USB install disk! I've redownloaded the 64bit for mac image, used the terminal dd guide from ubuntu, used unetboootin for mac, tried using two different usb keys.

When i plug them into my linux machine i can see the files have copied, but the installer will not boot when I plug them intoo the air. I've tried waiting until the folder image comes up, and pressing alt/option - it just shows the netbook boot.

I guess I have two questions - 1) how do I make a ubuntu install usb for mac, and 2) how do I then install it t another USB key so that it will boot?

Thanks

---

### Post by zircon_34 on 2014-06-08
-Download the normal Ubuntu image (no Mac version). 

- Use this website and prepare a live USB using the terminal in MacOS X: [https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick](https://help.ubuntu.com/community/How%20to%20install%20Ubuntu%20on%20MacBook%20using%20USB%20Stick)

- instead of using /dev/diskN use /dev/diskrN (point 9).

- Boot your mac by pressing Alt.

Just tried it with Macbook air 5,1 it works. 

Maybe you have to try the 32 bit version considering these instruction for Macbook 2,1 [https://help.ubuntu.com/community/MacBook2-1/Maverick](https://help.ubuntu.com/community/MacBook2-1/Maverick)

---

