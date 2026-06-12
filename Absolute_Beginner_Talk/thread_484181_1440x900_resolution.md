---
title: "1440x900 resolution"
date: 2007-06-25
forum: Absolute Beginner Talk
---

### Post by Mostlyharmless42 on 2007-06-25
i can't figure out how to set any wide screen resolutions on edgy eft

---

### Post by pavpan on 2007-06-25
You can usually set it through System > Preferences > Screen Resolution.

However, with your resolution, a better bet would be to run :

```

sudo dpkg-reconfigure xserver-xorg

```

And choose your resolution there. That's because your screen size isn't normal, and so it's not selected by default.

---

### Post by Mostlyharmless42 on 2007-06-25
so i tried the code, and went through the configuration.  I tried starring just 1440x900 and that didn't change anything.  I tried starring all resolutions but 1440x900 and that didn't work.  The problem w/ doing it w/ the graphical interface is that 1449x900 isn't available on that list

---

### Post by Martin Witte on 2007-06-25
well you need to know which video driver you need. a little browsing learned me that i needed to do the same thing as described in this thread, [http://ubuntuforums.org/showthread.php?t=434297](http://ubuntuforums.org/showthread.php?t=434297) - but if you have a diferent video chip you need to install the appropriate driver, command lspci can tell you which chipset you have

---

### Post by Mostlyharmless42 on 2007-06-25
Arg now when i rebooted it said it couldn't start xserver

What settings do i need to set to get it to run????????????????????????
when it asked me to input data that i didn't know i left the prompts either blank or w/e they already had written

Is there a way to undo my settings just to get my xserver at least running????????

---

### Post by Joakim Stokland on 2007-06-25
sudo cp /etc/X11/xorg.conf.20070502093823 /etc/X11/xorg.conf

should restore your previous settings. The looong number represents the date when the backup was stored. Just hit tab when you have written .....xorg.conf, and it should appear automatically.

I had the same problem with my Fujitsu Siemens. In my case I only needed to install the 915resolution package from synaptic package manager. Check make and model of your graphics card and come back :)

Joakim

---

### Post by Mostlyharmless42 on 2007-06-25
i can't find the 915resolution package on synaptic.  What is the package called????

---

### Post by 3rr0r on 2007-06-25
> **Mostlyharmless42 said:**
> i can't find the 915resolution package on synaptic.  What is the package called????

did you try 915 and see what search function found?

---

### Post by Mostlyharmless42 on 2007-06-25
it didn't turn up anything accept an already installed intel video driver

---

### Post by Mostlyharmless42 on 2007-06-25
my graphics card is an nvidia geforce  6800  (NV41.1)

---

### Post by Mostlyharmless42 on 2007-06-25
bumpity

---

### Post by g0t0 on 2007-06-26
> well you need to know which video driver you need. a little browsing learned me that i needed to do the same thing as described in this thread, [http://ubuntuforums.org/showthread.php?t=434297](http://ubuntuforums.org/showthread.php?t=434297) - but if you have a diferent video chip you need to install the appropriate driver, command lspci can tell you which chipset you have

Thank you for the help! My eyes were KILLING me with only 1248X768. 1440 is MUCH better. My gateway 17inch Laptop lcd was looking kind of fuzzy!

---

### Post by Mostlyharmless42 on 2007-06-26
i've got the 915resolution package, but i don't particularly understand how to use it.   

Also, where would i be able to find which driver i need for my graphics card??

---

### Post by Joakim Stokland on 2007-06-27
What do you mean with "got the package"? Did you download it manually?
You simply start Synaptic Package Manager, search for 915resolution, mark for installation and click Apply changes. You may need to select all the repositories from Settings -> Repositories. And i suggest you click Reload at the top left of SPM before downloading, to make sure you get the latest update.

Note that the package only applies to 800
and 900 series Intel graphics chipsets. This includes the 845G,
855G, and 865G chipsets, as well as 915G, 915GM, and 945G chipsets.

Joakim

---

