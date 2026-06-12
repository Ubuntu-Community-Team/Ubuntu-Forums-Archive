---
title: "iSight works just tweak firmware  location"
date: 2009-07-18
forum: Apple Hardware Users
---

### Post by tripundra on 2009-07-18
To all that have a Macbook specially2,1 as I do!

My experience was becoming a bit frustating, in getting iSight to work.

If you are getting errors after following all the posts and threads possible, check one thing

lsusb

it will quote something like this

Bus 001 Device 007: ID 05ac:8501 Apple, Inc. Built-in iSight [Micron]
Bus 001 Device 003: ID 0951:1625 Kingston Technology 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 005 Device 003: ID 05ac:8205 Apple, Inc. Bluetooth HCI MacBookPro
Bus 005 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 004 Device 002: ID 05ac:8240 Apple, Inc. IR Receiver [build-in]
Bus 004 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 003 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub
Bus 002 Device 002: ID 05ac:021b Apple, Inc. Internal Keyboard/Trackpad
Bus 002 Device 001: ID 1d6b:0001 Linux Foundation 1.1 root hub


If you have the firmware correctly loaded , if not it will say bellow the isight line no firmware.
if that is your case as it was mine,

Go to Synaptic and completely remove isight-firmware-tools,
Don't just remove it as it will keep configuration files.

Go to terminal and
sudo apt-get install isight-firmware-tools

then take a good look where you have your macOSX system.
when it prompts to say the location of your firmware, scoll back and add
/media/MacOSX .....
if it does not come it will not load firmware

Also change MacOSX by whatever your partition is called (mine is R2D2)

After that is done, in terminal do
  ls /lib/firmware/isight.fw

it it says
/lib/firmware/isight.fw

then you're fine.. if not go to the begining and check your MacOSX partition name.

check gstreamer-properties and see your self!!! lol

by the way I installed the libv4l-0 from Karmic

[http://packages.ubuntu.com/karmic/libv4l-0](http://packages.ubuntu.com/karmic/libv4l-0)

It now works perfectly

---

### Post by WillJeffery on 2009-07-28
Confirmed on MacBook 3,1

These steps work correctly. However, I still needed to fix the "green screen" issue. See the [Mactel iSight wiki]("https://help.ubuntu.com/community/MactelSupportTeam/AppleiSight#Green%20Capture%20Issue"). This fix is only for gstreamer, and does not fix the problem globaly, i.e. the problem still occurs in Cheese.

Anyone know of a global fix?
Here is the [bug report]("https://bugs.edge.launchpad.net/mactel-support/+bug/349255").

---

### Post by Rog-Mahal on 2009-07-28
The only global fix is downgrading the driver to the intrepid version. Follow the instructions [here.]("http://https://help.ubuntu.com/community/MacBook2-1/Jaunty#iSight") If you're running 64 bit, you'll also have to downgrade lib32v4l as well.

---

### Post by tripundra on 2009-07-28
You can also upgrade to Karmic like I said.
Both are stated to work, although I chose to upgrade and no more green fuzzyness!!
;)
This post was mainly for people that had an error on importing the firmware. Like I did, for not checking the address!!! TWICE!!

---

