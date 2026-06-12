---
title: "beryl manager system freeze"
date: 2006-11-09
forum: Absolute Beginner Talk
---

### Post by kman14 on 2006-11-09
hey there

i installed beryl using this guide:

[https://help.ubuntu.com/community/CompositeManager/InstallingBeryl]("https://help.ubuntu.com/community/CompositeManager/InstallingBeryl")

when i got to the part where it said to type: beryl-manager, into the terminal - my system flickers once, places the red diamond in the system tray and then freezes.

i can move the mouse around but can't open or close anything.

it also comes up with the following:

klmc@klmc-desktop:~$ beryl-manager
klmc@klmc-desktop:~$ XGL Absent, checking for NVIDIA
Nvidia Present
Relaunching beryl with __GL_YIELD="NOTHING"
XGL Absent, checking for NVIDIA
Nvidia Present

.....and that's it.

then when i restart there is the berryl settings manager and the emerald theme manager in "system" - "admin".

any help would be greatly appreciated.

cheers

---

### Post by barney_1 on 2006-11-10
I'm having a similar problem.  The difference is that mine goes on to say nvidia absent, assuming AIGLX.  Then I get the same freeze.  Anyone have a workaround for this?

Thanks

---

### Post by Belathor on 2006-11-10
Reply to kman14: 

If you let it sit there a few minutes, does anything else happen? I ask because I just posted the same problem an hour ago. I tried it again and then began making some posts on my laptop. When I looked up at the screen, beryl was loaded but was doing weird things. Then I found found the following:

> About Beryl-on-Gnome-Startup weirdness:

I've just toyed with it a lot, and found out mostly that its the fault of beryl-manager. To have GNOME load into beryl without all the epileptic borders or eventual computer-freezing (due to two instances of emerald being open, pegging the CPU to 100%):

1) System -> Preferences -> Sessions -> "Current Session" tab: remove metacity, push the apply button.
2) "Startup Programs" tab: add "beryl" and "emerald" as two separate entries.

You'll be missing the cool jewel icon in your system tray upon restart, but Beryl and Emerald (only ONE Emerald) will start with gnome, and slightly faster because Gnome won't load Metacity first. The beryl-manager jewel icon also provides a shortcut to beryl-settings, but that same shortcut is in the System menu (along with Emarald settings, as well).

Seems pretty solid for me right now. I just wish I knew how to prevent the CTRL+ALT+F1 bug (switching to a virtual terminal too many times seems to kill the display - when I CTRL+ALT+F7 back to X, the display is black with only the mouse pointer on it. The pointer moves, but no keystrokes seem to work - I must hard-reset the machine to get anything back. I haven't scanned the forums for workarounds on this yet, so if anyone knows anything, let me know).

After I did that, it worked.

I hope that helps.

EDIT: Here is the link to those posts I made:

[http://www.ubuntuforums.org/showthread.php?p=1741149#post1741149]("http://www.ubuntuforums.org/showthread.php?p=1741149#post1741149")

---

### Post by barney_1 on 2006-11-10
Solved my own problem after sifting around for a while.  Added this at the bottom of my xorg.conf file:
```
Section "Extensions"
        Option "Composite" "true"
EndSection
```

I hope this helps.

---

### Post by kman14 on 2006-11-10
belathor!!!!

thank you.

that seems to have done it.

one question?
now that i have stopped meta city - i've lost my frame (min, max, close)
is there a simple way to fix this?

thanks again.

---

### Post by Belathor on 2006-11-10
hmmm... adding emerald and beryl in the sessions as per the instructions gave me window borders from emerald.

---

### Post by bulldog on 2006-11-10
I had similar problems and add the following to gdm.conf-custom```
gksudo gedit /etc/gdm/gdm.conf-custom
```

The next lines should be placed under the server section
```

0=Xgl

[server-Xgl]
name=Xgl server
command=/usr/bin/Xgl :0 -fullscreen -ac -accel glx:pbuffer -accel xv:fbo
flexible=true
```

---

### Post by Belathor on 2006-11-10
What driver are you using kman14? Do you have the 9629 driver? Jusk asking because I didn't see anything about installing the 9629 driver on that howto you linked to.

---

### Post by kman14 on 2006-11-10
belathor after i started this thread and didn't get a response.......until you, i re-installed beryl using PRICECHILD's guide [here]("http://ubuntuforums.org/showthread.php?t=263851")

it seemed to be up to date.
sorry, but i don't know how to check my driver.
i tried "sudo nano /etc/X11/xorg.conf"
that just told me i'm using nvidia as my driver.

maybe i'll try bulldogs suggestion.

thanks.

---

### Post by Belathor on 2006-11-10
You can find the version number by searching for nvidia in synaptic.

I don't think Bulldog's suggestion would work because he appears to be running xgl and not aiglx.

---

### Post by kman14 on 2006-11-10
belathor

in synaptic it says: nvidia-glx          1.0.**9629**+2.6.17.6.-  .......and some more numbers.

i'm assuming the **9629** is the driver version.

thanks.

---

### Post by JoshHendo on 2006-11-10
> **barney_1 said:**
> Solved my own problem after sifting around for a while.  Added this at the bottom of my xorg.conf file:
```
Section "Extensions"
        Option "Composite" "true"
EndSection
```

I hope this helps.
To save starting a new thread, I had a similar problem too. I found this and changed it to true, and now beryl-manager will start. The only problem is that there isn't any window borders, making it useless.

I found this page [http://wiki.beryl-project.org/index.php/Troubles/nVidia](http://wiki.beryl-project.org/index.php/Troubles/nVidia), and saw "My windows don't have any decorations (title bar, resize handles, minimize/maximize/close buttons)", but when I look in xorg conf file, the DefaultDepth is already set at 24.

Any ideas on what I should do?

(I have the beta version of the nvidia drivers installed).

Thanks, Josh.

---

### Post by Jenda on 2006-11-18
Same problem at a friends computer... neither of the above fixes works.

---

### Post by partriv on 2006-11-20
not sure what driver version i am running (i can go home after work and check) but i was having the same problem, turns out I needed to install the BETA nvidia drivers.

i used this guide:
[http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA](http://wiki.beryl-project.org/index.php/Install/Ubuntu/Edgy/nVIDIA)

and i used method one to install the nvidia drivers.

---

### Post by barney_1 on 2006-11-20
Try using an earlier linux kernel.  I found that my system runs beryl with all everything funcioning when I boot to 2.6.15-27-386.

---

### Post by Leed on 2006-11-21
thanx a million for the quote Belathor, works a treat now... in fact it's much faster than the far simpler 3ddesk application

---

