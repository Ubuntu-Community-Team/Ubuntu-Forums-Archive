---
title: "[SOLVED] Scroll Wheel not working properly in Firefox"
date: 2007-11-20
forum: Absolute Beginner Talk
---

### Post by BassKozz on 2007-11-20
I am using a Logitech M_x_500 mouse with my new Xubuntu install, and when I scroll (with the scroll-wheel) in Firefox it scrolls up and down the page just fine, but after I stop scrolling the (right-click) context menu pops up, like so:
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/FF-scrollwheel.png[/IMG]
This is really odd behaviour... I also use this mouse on my WinXP machine, and it never exhibits this behaviour...
Why is this, how can I correct?
Thanks in advance,
-BassKozz

---

### Post by NT4usB on 2007-11-20
Lets look at some stuff...
type:```
about:config
```in Firefox address bar. Search for:```
mousewheel.withnokey
``` There should be three settings. Post what they are set to.
Next,
In a terminal, type:```
cat/etc/X11/xorg.conf
``` Copy and paste here (Ctrl+Shift+c to copy in terminal) the section "Input Device" for the mouse... something like this:```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection

```

---

### Post by BassKozz on 2007-11-20
> **NT4usB said:**
> Lets look at some stuff...
type:```
about:config
```in Firefox address bar. Search for:```
mousewheel.withnokey
``` There should be three settings. Post what they are set to.
[IMG]http://i4.photobucket.com/albums/y105/basskozz/xubuntu/FF-mousewheel.png[/IMG]
> **NT4usB said:**
> Next,
In a terminal, type:```
cat/etc/X11/xorg.conf
``` Copy and paste here (Ctrl+Shift+c to copy in terminal) the section "Input Device" for the mouse... something like this:```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "Buttons"               "8"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "false"
        Option          "ButtonMapping"         "1 6 3 2 4 5"
        Option          "Resolution"            "100"
EndSection

```
```
Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection
```
Thanks for your help NT4usB :)

---

### Post by NT4usB on 2007-11-20
about:config looks ok.
now go back and copy the input device that is for the mouse. The one you copied is for wacom. 
Tip: look for the word _mouse_.

---

### Post by BassKozz on 2007-11-20
Sorry about that :p
Here it is...
```
Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection
```

---

### Post by NT4usB on 2007-11-20
Are you familiar with editing xorg.conf using a terminal and non graphical editor?

Meanwhile, lets try something.
open a terminal and type```
xev
```
Then put the cursor over the window and scroll the wheel. You should see 4, then 5. If you also get a 3 now and then, somethings whack. (If you right click, you should get a 3.)

---

### Post by BassKozz on 2007-11-20
> **NT4usB said:**
> Are you familiar with editing xorg.conf using a terminal and non graphical editor?
Unfortunately no :(
> **NT4usB said:**
> 
Meanwhile, lets try something.
open a terminal and type```
xev
```
Then put the cursor over the window and scroll the wheel. You should see 4, then 5. If you also get a 3 now and then, somethings whack. (If you right click, you should get a 3.)
Yup, I am getting an occasional 3 thrown in there randomly. :confused:

---

### Post by NT4usB on 2007-11-21
Somethings screwy with the scroll wheel if it's throwing random threes. We may be able to lower the sensitivity of the mouse but, it requires editing the xorg.conf... and I don't know wtf I'm doing so we'd just be experimenting. 
What do you get if you click the scroll wheel? Should be a 2.
When you clicked the right button, did you also get 3?
Got another scroll mouse you can plug in and scroll... see if it acts different.

If we're going to edit xorg, you'll need to take a crash course in vi. It's the only editor I know. 
[http://www.tuxfiles.org/linuxhelp/vimcheat.html](http://www.tuxfiles.org/linuxhelp/vimcheat.html)
There are others, nano, etc. but I don't know them.

---

### Post by teejcee on 2007-11-21
I'm also experiencing this "problem".

I have a Microsoft wireless keyboard & mouse hooked up to a 4 port KVM switch.

If I boot a windows box & then gutsy while not switched to it, the problem occurs.

If I re-boot gutsy while switched to it, I have no problems at all.  Nor do I have any further problems switching back & forth between the two.

I have only just installed gutsy after running dapper for a couple of years.

It didn't occur with dapper and it's not confined to Firefox - it will happen scrolling up in Evolution as well.

---

### Post by BassKozz on 2007-11-21
> **teejcee said:**
> I'm also experiencing this "problem".

I have a Microsoft wireless keyboard & mouse hooked up to a 4 port KVM switch.

I am also using a 4-port KVM, and wouldn't you know it a quick re-boot while staying on the Xubuntu Box fixed it =D>
Thanks for all the help NT4usB & teejcee :D

---

### Post by NT4usB on 2007-11-21
oh, so **now** you mention the KVM switch...

---

### Post by BassKozz on 2007-11-21
> **NT4usB said:**
> oh, so **now** you mention the KVM switch...

Sorry about that :p
Thanks again for all your help NT4usB :D

---

### Post by NT4usB on 2007-11-21
No worries. Glad you got it worked out.
Be sure to mark the post solved, under thread tools, upper right.

---

### Post by BassKozz on 2007-11-21
> **NT4usB said:**
> No worries. Glad you got it worked out.
Be sure to mark the post solved, under thread tools, upper right.

Ahh, didn't relize you had to mark the threads... Thanks again ;)
Geez, NT4usB you sure are a wealth of information :D
Maybe you could help me with VNC issues: [http://ubuntuforums.org/showthread.php?p=3815128](http://ubuntuforums.org/showthread.php?p=3815128)
If your up to it, if not no biggie, Thanks again

---

