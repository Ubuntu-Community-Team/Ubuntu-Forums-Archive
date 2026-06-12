---
title: "Linux and Watercolors"
date: 2006-12-04
forum: Art &amp; Design
---

### Post by finferflu on 2006-12-04
Hi all,
I've been looking for this feature for a long time, but still I can't find anything.

Does anybody know whether there is any watercolors support for Linux? This is the only thing I miss from Windows (using Corel Painter), but I've deleted it forever anyways, so I would like to have my watercolors back...

---

### Post by Magnes on 2006-12-04
Install Krita. I read today that it has some watercolor support. Doesn't have time (I'm at work on damn slow windows machine) to test it.

---

### Post by finferflu on 2006-12-04
Last time I've installed it, version 1.5 didn't have any watercolor support.. I can try and see whether there's any improvement in version 1.6... 
I hope to find something desktop environment independent though, because KDE apps on GNOME are too slow...

Thank you :)

---

### Post by tiggs_the_cat on 2006-12-07
Well, you could try to run ArtRage through WINE, I heard that it works but I haven't tried it yet. ArtRage doesn't have actual watercolor support either, but maybe they'll add it in future versions, and it has some of the most realistic natural media support of all digital painting programs. There is a free version for download, the full one costs $19.95: [http://www.ambientdesign.com/artrage.html](http://www.ambientdesign.com/artrage.html)

The developers are former Painter developers as far as I know.

---

### Post by Magnes on 2006-12-07
> **finferflu said:**
> because KDE apps on GNOME are too slow...


I didn't noticed. KDE apps loads slow on my Ubuntu, but works fast.
I tested Krita 1.6 myself and the watercolor is there but it's not working for me. I think we'll have to wait a while.

---

### Post by finferflu on 2006-12-07
> **Magnes said:**
> I didn't noticed. KDE apps loads slow on my Ubuntu, but works fast.
I tested Krita 1.6 myself and the watercolor is there but it's not working for me. I think we'll have to wait a while.

I actually switched to KDE for good, since it seems to be way faster than GNOME, so that's not a problem for me anymore, but the version of Krita available in the repositories is only 1.5.2. How to install, without the hassle of compiling, version 1.6?


**@ tiggs_the_cat**

Thanks for your hint, I'm installing wine right now, and I'll see how it goes. 
By the way, I was thinking whether there was a Mac "emulator", since Mac is belongs to the *nix world...

Thank you!

---

### Post by Aldrik on 2006-12-07
[Krita 1.6.1 available here]("http://kubuntu.org/announcements/koffice-161.php") &  [here's a watercolors howto to get you started]("http://cyrilleberger.blogspot.com/2006/12/howto-watercolors.html"). I also use artrage, there is no longer any need to patch wine to use it which make it even more of a pleasure to use.

PS. Post on their forum we need to let em know there is a linux market. :D

---

### Post by finferflu on 2006-12-07
Whoa! thank you for those **very** useful links! 

I couldn't go further than the splash screen with ArtRage, after a successful installation, though... too bad...

---

### Post by Aldrik on 2006-12-07
> **finferflu said:**
> Whoa! thank you for those **very** useful links! 

I couldn't go further than the splash screen with ArtRage, after a successful installation, though... too bad...I just tested the free version (just for you ;)) and it works fine. Do you have a up to date version of wine? (think you do other wise you would have had problems installing it) Try running it from Konsole and post the error here (or on the long linux thread in the artrage forum).

If you don't know how (you noob! just joking) open konsole and paste the following and hit return.

wine 'c:/Program Files/Ambient Design/ArtRage 2 Free/ArtRageFree.exe'

Don't give up!... ;)

---

### Post by finferflu on 2006-12-08
Thank you again for your help, Aldirk, this is my output (I'm an elderly noob by now, I think :P):

```
$ wine 'c:/Program Files/Ambient Design/ArtRage 2 Free/ArtRageFree.exe'

fixme:actctx:FindActCtxSectionStringW 00000000 (null) 2 L"msvcr80.dll" 0x337b0c
X Error of failed request:  BadDevice, invalid or uninitialized input device
  Major opcode of failed request:  145 (XInputExtension)
  Minor opcode of failed request:  3 (X_OpenDevice)
  Serial number of failed request:  186
  Current serial number in output stream:  186
```

And then it shuts.

---

### Post by rax_m on 2007-05-04
I had that issue... basically you've got to ensure that your drawing tablet is plugged in and that the xorg.conf stylus, eraser and cursor point to the same device that your tablet is connected to. If you plug in your tablet when already logged in you may have to restart the xserver. 

/so mine looks like (notice the /dev/input/event3).. yours might be different. 


<code>
Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/event3"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/event3"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/event3"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection
</code>

---

