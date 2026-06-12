---
title: "KVM Mouse Problems"
date: 2005-08-05
forum: Absolute Beginner Talk
---

### Post by brainsick on 2005-08-05
Hello,

I have a KVM that I use to switch between two Ubuntu machines.  From time to time when switching between machines I lose the scroll wheel functionality of my mouse.  No matter how many times I switch back and forth, it stays lost.  If I unplug the USB mouse and plug it back in, I get the scroll wheel back.

Is there a way (a command I can issue perhaps?) that I can "soft" detach the mouse and reattach it so I don't have to crawl under my desk everytime this happens?

Does anyone know why I would be losing my scroll wheel yet the rest of the mouse continues to function?

It's a Microsoft Wireless IntelliMouse Explorer 2.0.  I've done no special setup for the mouse.

---

### Post by aaarg on 2005-08-05
i also use the microsoft intellimouse 2 on a 4 port KVM and i had strange things happen similar to yours. my problem was not only the scroll but the back buttons and the right click....i dont think it was the KVM, but the mouse itself. i checked out a couple forum posts that explained how to setup the intellimouse and it solved my problems... have you checked them out? i am in a hurry tonight, but i will post the links to them tomorrow and maybe it will help.

---

### Post by brainsick on 2005-08-06
Well, I did some digging on how to setup an IntelliMouse and followed the instructions here:  [http://ubuntuforums.org/showthread.php?t=28374](http://ubuntuforums.org/showthread.php?t=28374)  which yielded:

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "7"
EndSection

This gained me the use of the two buttons on the side for forward and backward, but it's not what I was after.  I started this with the mouse in a "bad" state where the wheel didn't work and I had restarted X a couple times but the buttons never started working until I crawled under my desk, unplugged the mouse, and then plugged it back in.  That's what I'm really trying to fix.

I use ScrLk,ScrLk,(Up|Down) to switch between machines.  ScrLk doesn't effect the mouse in any way, does it?

---

