---
title: "xubuntu gimp crash takes panels with it"
date: 2006-12-27
forum: Absolute Beginner Talk
---

### Post by keithpeter on 2006-12-27
Hello All

I have xubuntu running on a Dell L400 laptop with a P3 700Mhz processor and 256Mb of RAM. I have done a memory test with no problems.

I was editing some photos in GIMP and the program froze when pasting as new image. The whole desktop was frozen, so ALT-F2 didn't bring up the command box to run xkill.

I just pressed the power switch to shut the laptop down and restarted and the XFCE panels had disappeared. I found a couple of threads on restoring the panels...

[Panels missing]("http://ubuntuforums.org/showthread.php?t=241061&highlight=xubuntu+restore+panels")
[Original panels]("http://ubuntuforums.org/showthread.php?t=210021")

and I have now recreated the panels and I have unticked the box on the shutdown menu that says 'Save Session for Future Login'. 

Is there anything else I can do to make xubuntu less fragile when applications crash? Firefox falls over on a regular basis but it does not take the desktop with it ](*,) 

How many times per session do you experience crashes?

---

### Post by doobit on 2006-12-27
> **keithpeter said:**
> Hello All

I have xubuntu running on a Dell L400 laptop with a P3 700Mhz processor and 256Mb of RAM. I have done a memory test with no problems.

I was editing some photos in GIMP and the program froze when pasting as new image. The whole desktop was frozen, so ALT-F2 didn't bring up the command box to run xkill.

I just pressed the power switch to shut the laptop down and restarted and the XFCE panels had disappeared. I found a couple of threads on restoring the panels...

[Panels missing]("http://ubuntuforums.org/showthread.php?t=241061&highlight=xubuntu+restore+panels")
[Original panels]("http://ubuntuforums.org/showthread.php?t=210021")

and I have now recreated the panels and I have unticked the box on the shutdown menu that says 'Save Session for Future Login'. 

Is there anything else I can do to make xubuntu less fragile when applications crash? Firefox falls over on a regular basis but it does not take the desktop with it ](*,) 

How many times per session do you experience crashes?


I have only had one crash in several months, and I can expalin why that one happened. It made the panels disappear too, and that is explainable as well. The panels in XFce are a separate part of the interface. I just restored them and have been fine ever since. No problems, ever, with Gimp. Your problem may be related to not having enough memory for graphic intensive tasks, or not having a swap partition.

---

### Post by keithpeter on 2006-12-27
> **doobit said:**
> I have only had one crash in several months, and I can expalin why that one happened. It made the panels disappear too, and that is explainable as well. The panels in XFce are a separate part of the interface. I just restored them and have been fine ever since. No problems, ever, with Gimp. Your problem may be related to not having enough memory for graphic intensive tasks, or not having a swap partition.

Thanks for this quick reply. 

I do have a swap file as set by the installer in xubuntu, and the output from free -m is shown below

```

             total       used       free     shared    buffers     cached
Mem:           249        244          5          0          7        115
-/+ buffers/cache:        121        127
Swap:          729          0        729

```

I may be hopeful here, but I didn't consider cropping a 1024 by 768 selection from a 2000 by 1500 image and pasting the selection as a new image especially as graphics intensive. Do you find the default Firefox unstable?

Cheers

---

### Post by doobit on 2006-12-28
> **keithpeter said:**
> Thanks for this quick reply. 

I do have a swap file as set by the installer in xubuntu, and the output from free -m is shown below

```

             total       used       free     shared    buffers     cached
Mem:           249        244          5          0          7        115
-/+ buffers/cache:        121        127
Swap:          729          0        729

```

I may be hopeful here, but I didn't consider cropping a 1024 by 768 selection from a 2000 by 1500 image and pasting the selection as a new image especially as graphics intensive. Do you find the default Firefox unstable?

Cheers

That certainly doesn't seem very intensive, but your memory level is definately low. I use 512 MB. Firefox has not been unstable on my system, but again, it is a memory hog. Just for the heck of it, last night I did a clean install of Ubuntu Edgy to see what the difference would be, and it is a dog compared to Xubuntu! I was finally able to crash this computer when I tried to render a graphic in Blender. It neve crashed before with Xubuntu.

---

