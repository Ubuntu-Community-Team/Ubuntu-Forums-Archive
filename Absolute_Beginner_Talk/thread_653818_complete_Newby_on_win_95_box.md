---
title: "complete Newby on win 95 box"
date: 2007-12-30
forum: Absolute Beginner Talk
---

### Post by benh on 2007-12-30
Hello world,

I have installed 6.06 on my old box and most of the install went well except for the RDSP issue.  I modified the Kernal commands and then Xubuntu seemed to load properly- at least the desktop looked as if I was going to get into a GUI.  What happened instead was to end up at a command line as OEM.  

Now, what do I do, at the command line,  so that I can always boot to the GUI  and also, how do I save the modified Kernal command?  

There are no user accounts other then sudo and OEM.  Does that have to be set first- the guest user?

Thanks,
Ben

---

### Post by jas0 on 2007-12-30
Could you elaborate please? Which kernel bootup command did you use? Did you actually end up installing the OS successfully? Are there any error messages on the screen when you find yourself unable to boot into a GUI environment?

---

### Post by benh on 2007-12-30
> **jas0 said:**
> Could you elaborate please? Which kernel bootup command did you use? Did you actually end up installing the OS successfully? Are there any error messages on the screen when you find yourself unable to boot into a GUI environment?


Thanks Jas0 for responding:

1.  Here's the kernal modification I used.  This was added to the already existing kernal commands:  quiet splash noacpi acpi=off apm=0

These commands were added from a  group responding to the issue of ACPI=unable to locate RSDP.

So, once I pressed "b" command, it started up the Ubuntu window, things were loaded with the OK message, then it went to the command prompt and that's where I am stuck right now.

2.  No, there is no error message displaying, only the command prompt.

3.  I have no idea whether the OS properly installed.  I am running only 64Megs of ram and it did the low memory install but it appeared to go properly.

Thanks for the reply and looking forward to seeing if this OS will work on this old, old, old box.

Ben

---

### Post by benh on 2007-12-30
Just to let you know that your question regarding whether the OS was installed correctly led me to reinstall in text mode not OEM mode.  That eliminated all of the problems and I have a xubuntu system up and running.

So, thanks for the assitance.
Ben

---

### Post by jas0 on 2007-12-31
> **benh said:**
> Just to let you know that your question regarding whether the OS was installed correctly led me to reinstall in text mode not OEM mode.  That eliminated all of the problems and I have a xubuntu system up and running.

So, thanks for the assitance.
Ben

I'm glad that you solved the problem. Have fun experiementing with xubuntu! :)

---

