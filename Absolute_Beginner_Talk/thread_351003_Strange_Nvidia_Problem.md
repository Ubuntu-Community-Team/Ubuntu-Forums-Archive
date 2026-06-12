---
title: "Strange Nvidia Problem"
date: 2007-02-01
forum: Absolute Beginner Talk
---

### Post by HiddenElephant on 2007-02-01
howdy, i have nvidia installed and working well, then i installed beryl, and was having fun with that but this mourning when i logged in and tried to change the resolution for my Nvidia card this error came up in the terminal window along with the standerd Nvidia-Settings only stripped down so that the only thing in the box to the left is nvidia-settings Configuration

```
ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':1.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':1.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':1.0'.


ERROR: Invalid X Screen 0 specified on line 19 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 20 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 21 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 22 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 23 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 24 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 25 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 26 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 27 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 28 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 29 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 30 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 31 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 32 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 33 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 34 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 35 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 36 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 37 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 38 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 39 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 40 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 41 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 42 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 43 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 44 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 45 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 46 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 47 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 48 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: Invalid X Screen 0 specified on line 49 of configuration file
       '/root/.nvidia-settings-rc' (NV-CONTROL extension not supported on X
       Screen 0).


ERROR: NV-CONTROL extension not found on this Display.


ERROR: Unable to determine number of NVIDIA GPUs on ':1.0'.


ERROR: Unable to determine number of NVIDIA Frame Lock Devices on ':1.0'.


ERROR: Unable to determine number of NVIDIA VCSCs on ':1.0'.


```

everything seems to be going ok but i cant change the resolution, which is annoying, but at least  everything else seems to be in order, let me know if this is fixable thanks!

---

### Post by simsen on 2007-03-01
I get error messages too! Not as many as you, but some of them are the same. I already started a [thread regarding my problem (link)]("http://ubuntuforums.org/showthread.php?t=372855") because I didn't find this thread until now. Though it didn't help much.

Hopefully someone could point us to the right direction. Where do we begin problem-solving this? What forum? What manual? Who can we ask?

- S

---

### Post by simsen on 2007-03-01
I found a [post in a FreeBSD forum (link)]("http://www.nvnews.net/vbulletin/showthread.php?t=78214") where a guy suggests that the Nvidia driver is too old for nvidia-settings. I will try upgrading my driver and see if it helps.

HiddenElephant: have you found a solution?

- S

---

