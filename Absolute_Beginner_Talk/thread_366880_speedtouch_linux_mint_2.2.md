---
title: "speedtouch linux mint 2.2"
date: 2007-02-21
forum: Absolute Beginner Talk
---

### Post by renegade3018 on 2007-02-21
I'm new to Linux but I am not new to computers. Yesterday I installed Linux Mint 2.2 and I have decided I like Linux and want to continue to use it. However, I cannot access the internet on that pc without using my speedtouch modem. I have found the linux speedtouch firmware etc. but I am not able to do what he instructions say. Here is a link to the instuctions I am using: [http://www.linux-usb.org/SpeedTouch/ubuntu/index.html]("http://www.linux-usb.org/SpeedTouch/ubuntu/index.html"). I am using the .zip file that is mentioned. However none of the files in the achive are recognised. I do not know where to enter any of the code that is mentioned on the instructions either. Please could someone look at the link and explain to me why nothing is working.

---

### Post by Maestro23 on 2007-02-21
You need to open up a terminal to use those commands. In Ubuntu:

Applications>>>Accessories>>>Terminal


Also need to read RootSudo: [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

Good luck.

---

### Post by renegade3018 on 2007-02-21
OK I have tried using the terminal and I'm still unable to do what my intstructions say. I have extracted zzzl_3.018 from the .zip file and am trying to access it with the terminal. I do not know what to put for the ./ bit though, this is what I mean: chmod +x zzzl_3.018 &&
./(what do i put here?) /home/renegade

---

### Post by mechanic on 2007-02-21
It's the 'firmware extractor' that has the chmod instruction applied to it, not the firmware files themselves. The ./... bit seems to just be the path pointing to the location of these firmware files.

These instructions you pointed to are really appalling, can't you find any better ones on this forum or somewhere else (using Google)?

Regds m.

---

### Post by Bert the Button on 2007-03-04
Hi there!

I followed this tut, [https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch](https://help.ubuntu.com/community/UsbAdslModem/SpeedTouch), and managed to get connected.  You can copy and paste most of it straight into the terminal window or text editor, and there are only a couple of bits need editing by you.

Hope it helps  :)

---

