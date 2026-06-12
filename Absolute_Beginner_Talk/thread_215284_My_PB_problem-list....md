---
title: "My PB problem-list..."
date: 2006-07-13
forum: Absolute Beginner Talk
---

### Post by silversurfer2025 on 2006-07-13
Hello,

I am pretty happy with my ubuntu installation on my powerbook, although some minor things are still improvable:

1. How can I let ubuntu find my bluetooth keyboard and mouse by itself? Right now I have to enter "sudo hidd --search" everytime I want to use a BT device.. I tried to add a shortcut through a command, but this does not seem to work... Kubuntu found both elements right away..btw.

2. I am really into using the apple (win) key for copying and pasting as well as selecting all, etc etc. (short: everything which is now done via control+key). Is there a way to change all this to work with win+key instead?

2b. Anjutas change-shortcuts does not seem to work.. is there a trick?

To come to the minow-important problems:
1. As already mentioned in another thread: The powerbook does not go to sleep when I close it although pbbuttonsd is able to let is sleep through "pbbcmd sleep"

2. When I changed the x11-conf file in order to get my trackpad to work the way I wanted the system crashed and no graphical output was being able untile I restored everything.. Is there a tutorial oin how to alter the files such that I could right click and scroll with the trackpad?

3. WLAN does not seem to work, although I read that the drivers which support apple airport should be included.. is there a tutorial for this as well?


It would be very nice if the one or the other could tell me how to solve some of the problems described above... I have been looking through google and forum-searches, but could not find any satisfying results..

Thanks so much in advance,
greetings
Tim

---

### Post by chasisaac on 2006-07-13
> **silversurfer2025 said:**
> 
3. WLAN does not seem to work, although I read that the drivers which support apple airport should be included.. is there a tutorial for this as well?



Try
[http://ubuntuforums.org/showthread.php?t=185174](http://ubuntuforums.org/showthread.php?t=185174)

---

### Post by silversurfer2025 on 2006-07-14
Thanks for the tip, I'll try right away..

Anybode else for the other topics? 
Thanks again in advance..
Tim

---

### Post by silversurfer2025 on 2006-07-14
Concerning the sleep-problem, I found a solution: I found out that the "what-to-do-on-closed-lid" preference of the gnome-power-manager was not set to suspend...

Argh... Sorry for the trouble, the system sleeps now ;)

Greetings
Tim

---

### Post by silversurfer2025 on 2006-07-15
Isn't there anybody who could help with the other questions? I found a good toturial on airport-usage, so this is not a problem anymore, but the rest still is ;)

Here they go once more:

1. How can I let ubuntu find my bluetooth keyboard and mouse by itself? Right now I have to enter "sudo hidd --search" everytime I want to use a BT device.. I tried to add a shortcut through a command, but this does not seem to work... Kubuntu found both elements right away..btw.

2. I am really into using the apple (win) key for copying and pasting as well as selecting all, etc etc. (short: everything which is now done via control+key). Is there a way to change all this to work with win+key instead?

2b. Anjutas change-shortcuts does not seem to work.. is there a trick?

3. When I changed the x11-conf file in order to get my trackpad to work the way I wanted the system crashed and no graphical output was being able untile I restored everything.. Is there a tutorial oin how to alter the files such that I could right click and scroll with the trackpad?


Thanks onc more for your help!

---

### Post by cyclopsface on 2006-07-30
Hi - I've managed to get my trackpad working reasonably well and also to change the command key to act like the control key (mostly by searching these forums -there should probably be a faq/howto for powerbook users as I'm sure there are a lot of us and the solutions are scattered at present)

First: to get your trackpad to work right you want to edit your xorg.config file.  you can do something like:
```

sudo vi /etc/X11/xorg.conf

```
then type 'i' to go into typing mode and change the file so that the part concering your touchpad reads:
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
        Option          "MinSpeed"              "0.4"
        Option          "MaxSpeed"              "1"
        Option          "AccelFactor"           "0.04"
        Option          "FingerLow"             "55"
        Option          "FingerHigh"            "60"
        Option          "MaxTapTime"            "0"
EndSection

```

then tpye 'esc' and then ':wq'.  When you restart you should have a functional trackpad.

Second - to map command to control you have to create a file called .xmodmap like this:
```

sudo vi ~/.xmodmap

```
whose contents should be:
```

remove control = Control_L
keycode 115=0xffe3
add control = Control_L

```

then you type 'xmodmap .xmodmap' and you should be able to cut and paste using the command key (like I did to get the code into this post)

I still have a couple problems I haven't figured out yet though:  my mouse behaves resonably in the horizontal direction but is still a little slow in the vertical direction (just *a little* but it's *a little* annoying) - does anyone know how to fix that?  Also, the command key works fine for cutting and pasting but, for instance, '<command>f' won't start a search in firefox.  any advice would be appreciated.  And if someone wanted to start and faq for getting ubuntu working on an apple laptop I'd gladly contribute what I've learned so far.

---

### Post by cyclopsface on 2006-07-30
By the way - the code I gave for the trackpad will not allow you to tap to click (because I don't like doing that) but if you look around (like do a search for "Synaptics Touchpad ubuntu powerbook") you cna find the code for scrolling a clicking and buttom emulation etc.

---

### Post by x1um1n on 2006-07-31
hi,
this isn't going to be a huge amount of help i'm afraid, but i'm running dapper on a powerbook pismo (firewire) and my airport works fine out of the box, as it did on gentoo..  the modules are enabled in the kernel by default.. the same may not be true for airport extreme, is yours def just an airport?

if so, then the problem is either with your airport card, config or your router..
if you're dual-booting OSX, does wifi work there?

as far as BT's concerned i can't help at all, i have a BT dongle which allows me to send files to and from my mobile, tho i've only managed to have this working on dapper, not gentoo or breezy; but thats OBEX not i/o, so no help..

unfortunately gnome-volume-manager doesn't do BT devices, as far as i can make out, gnome-bluetooth isn't an official part of gnome, and this is the problem, perhaps that'll change with 2.16, (out soon, yay!)

finally, your apple key can be assigned for shortcuts in gnomes keyboard shortcuts gui, on the preferences menu..

anyway, sorry for the limited help, best of luck getting it all sorted..

---

