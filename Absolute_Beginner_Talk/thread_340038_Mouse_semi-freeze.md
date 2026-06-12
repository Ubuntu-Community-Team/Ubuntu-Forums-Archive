---
title: "Mouse semi-freeze"
date: 2007-01-16
forum: Absolute Beginner Talk
---

### Post by LexAevum on 2007-01-16
Ok. So I've been trying to figure this out for a week now.

Sometimes (not every time) I leave my computer long enough for it to shut down the screen (like... 2 hours) I'll come back, hit my mouse to bring it back up. It'll come back up, then I'll notice that I can't move my mouse cursor. All of my keyboard functions are fine, and I can even use my mouse buttons. But the mouse won't move.
I can fix this with either a reboot or by pulling the mouse cable and reinserting it.

It's a USB laser mouse.

Anyone have any ideas why it's doing this? I don't have another mouse right now or I'd try switching them.](*,)

---

### Post by nonpareilpearl on 2007-01-16
Does the mouse have a driver? Also, I'm assuming that since you are using an USB mouse that you are using a laptop, so does the laptop mouse work normally?

---

### Post by LexAevum on 2007-01-16
no, the mouse doesn't have a driver.
I'm not on a laptop, my mobo is just one of those strange jobbies that has no ps2 ports. So actually my keyboard is usb too. And my printer. lol.

This is a new thing BTW. It just started happening after I shredded my HD and reinstalled with no windows partition. I reinstalled rather than modding because I had "played around" so much I had broken all sorts of stuff. hehe. So I wiped and reinstalled.

---

### Post by nonpareilpearl on 2007-01-16
Are the mouse and keyboard wirelessly connected (i.e. do they both connect to the same wireless point, which then connects to the computer via USB), or are they separate? If they are separate are you experiencing any difficulty with the keyboard (or any other USB device for that matter)?

Sorry for the rush of questions, the consultant in me is coming out.

Although the mention of Windows does bring something to mind. Usually when Windows detects a new external device it will automatically install any necessary drivers and "mount" it. You may need to do this manually in Ubuntu, since Windows is gone.

---

### Post by LexAevum on 2007-01-16
No, I have no wireless devices on this system. Both the keyboard and mouse are connected directly by wire to separate usb ports. Switching which devices uses which port does not seem to solve.
No difficulties with any other devices.

I would think that this might be some sort of install/mount issue, but the mouse works fine most of the time. I am using it right now and have been for several months. The only time it seems to have an issue is perhaps 1 out of 4 times that my system goes idle for more than 2 hours.
I would giggle to think that this could have anything to do with windows, since even when I had both installed they were on separate partitions and did not mount each other or interact in any way.

---

### Post by standards on 2007-01-24
I've been having the same problem for the last few months. It's completely random for me though, maybe every half an hour the mouse just gets stuck until i unplug/replug. It's really starting to drive me insane. 

I suspect fglrx. I have almost the same exact computer/setup at work but it's an nvidia card, and works fine.

---

### Post by hamil on 2007-02-11
Sorry for bumping this thread, but I do have the same issues, and as you say; It is really annoying to have to unplug it every half an hour of work... Any ideas to how it is possible to resolve this?? Some one hav suggested to use a USB-hub, but with it, it is not even possible to use the mouse on my machine...

I have found one thread, that may solve the issue [ USB hang, mouse](http://www.ubuntuforums.org/showthread.php?t=311462&page=2&highlight=usb+mouse+freeze), but I do have to reboot the machine, to see if it solves my problems..

---

### Post by bmichel on 2007-03-04
Hi,

Don't know if you've found a solution but I had the same issue with my usb mouse (logitech) hanging many times a day since few months (perhaps since my upgrade to 6.10).

I found this solution which seems ok for now. The post comes from another forum in french. it says to replace in the /etc/xorg.conf the usb mouse section:

Section "InputDevice"
  Identifier "Configured Mouse"
  Driver "mouse"
  option "CorePointer"
  option "Device" "/dev/input/mice"
  option "Protocol" "ExplorerPS/2"
  option "ZAxisMapping" "4 5"
  option "Emulate3Buttons" "true"
EndSection

must be replaced by

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "Device"                "/dev/input/mice"
        Option      "SendCoreEvents"   "true"
        Option          "Protocol"              "IMPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Buttons"               "5"
EndSection


Hope this will help

---

