---
title: "Regnum Online: need latest available drivers or Direct X version.."
date: 2007-10-28
forum: Absolute Beginner Talk
---

### Post by variableenigma on 2007-10-28
I have downloaded the game Regnum Online, and registered online. But when I try to install it, it says 
"Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version"

I'm not even sure how to check what kind of video card I have or to see if I have the lastest drivers or version of Direct X. I did check Add/Remove Applications and Synaptic for Direct X, but neither of them seem to have it.

What do I do next?

---

### Post by Grey Ax on 2007-10-29
I'm having the same problem - I'm running Feisty 64 with a New Nvidia GeForce 7600GS.  I get the following text in the xterm when I run the  ./rolauncher command:



X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  144
  Minor opcode:  3
  Resource id:  0x0
Failed to open device

It gives me the login screen and when I click on the login button I get the following error window pop up:


Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version


And the additional text in the xterm:

Failed to open device
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual


Video card's brand new and DirectX is for MS, not Linux so what drivers do I need to be installing, (where to get them, and how to install)?

---

### Post by Smutronic on 2007-12-22
I have the same problem. I am using a MacBook with Intel GMA X3100.

---

### Post by jken146 on 2007-12-22
DirectX is a Windows thing.  Only games that work on OpenGL will run natively in Linux.  Try Wine.

---

### Post by jken146 on 2007-12-22
I just found out this has a Linux client.  Hmm.  Don't try Wine then.  Not sure why it would ask for DirectX.

---

### Post by Smutronic on 2007-12-22
Well, DirectX is only one of three possibilitys. I guess that i dont have the correct drivers for my video card. But i dont know how to check that, i am still looking around, trying to find an answer.

---

### Post by RomeReactor on 2007-12-22
Hi. Try running this command in the terminal:
```
glxinfo | grep direct
```
If it says "Yes", then try running the launcher like this:
```
MALLOC_CHECK_=0 ./rolauncher"
```
If that doesn't work, run this to find the exact model of the card and its current driver:
```
sudo lshw -C display
```
Make sure your card is not in [Regnum's black list]("http://www.regnumonline.com.ar/index.php?l=1&sec=20&subsec=41") (either as "experimental" or "not supported").

---

### Post by Smutronic on 2007-12-23
Thanks for the help.

I tried your commands:
```
glxinfo | grep direct
direct rendering: No (If you want to find out why, try setting LIBGL_DEBUG=verbose)

```

My Driver:
```
sudo lshw -C display

  *-display:0
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0
```

The "Intel 965" chipset is on the experimental list. But i still hope i can activate "direct rendering" and it will work. How can i activate direct rendering?

---

### Post by matthewschwimmer on 2008-01-28
Nope, Ive got the same "sudo lshw -C display" specs, and a yes on direct rendering, but it wont work. I think we've got to wait until either a regnum or ubuntu update. :(

---

### Post by RomeReactor on 2008-01-28
Hi. What are the error messages you get when trying to run ./rolauncher? Are you running Ubuntu 32-bit or 64?

---

### Post by matthewschwimmer on 2008-01-28
I'm not getting any error messages from inside the terminal. I used  
> $ sh -c "MALLOC_CHECK_=0 ./rolauncher"like how you said, but then regnum gives me the "video card unsupported, 1...2...3..." message

32 Bit Ubuntu

> $ glxinfo | grep direct
direct rendering: Yes

> $ sudo lshw -C display
  *-display:0             
       description: VGA compatible controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga bus_master cap_list
       configuration: latency=0
  *-display:1 UNCLAIMED
       description: Display controller
       product: Mobile GM965/GL960 Integrated Graphics Controller
       vendor: Intel Corporation
       physical id: 2.1
       bus info: pci@0000:00:02.1
       version: 03
       width: 64 bits
       clock: 33MHz
       capabilities: pm bus_master cap_list
       configuration: latency=0

---

### Post by RomeReactor on 2008-01-28
Are you able to play other games that require OpenGL?

---

### Post by matthewschwimmer on 2008-01-28
like what? i can run tremulous and open arena. are those opengl?

---

### Post by RomeReactor on 2008-01-28
Yes, Tremulous and Open Arena are OpenGL games. I couldn't find anyone with an Intel 965 running Regnum in either the [Gaming & Leisure]("http://ubuntuforums.org/forumdisplay.php?f=93") section or the [Regnum Linux support]("http://www.regnumonline.com.ar/forum/forumdisplay.php?f=15") forums; most replies revolve around getting a nVidia card.

EDIT: As a last resort try running the game as suggested in [this thread]("http://ubuntuforums.org/showthread.php?t=576709"):
```
G_SLICE=always-malloc ./rolauncher
```
although the error in the thread might not be the same as yours.

---

### Post by matthewschwimmer on 2008-01-28
Thanks, but I still got the
> Unsupported video card!

There are three possible causes for this error:
1. Your video card is too old
2. You haven't installed the latest available drivers
3. You haven't installed the latest DirectX version
message. The only thing I can think of is waiting, or making regnum think I have a different video card.

I have a laptop, so I cant put a different video card in.

---

