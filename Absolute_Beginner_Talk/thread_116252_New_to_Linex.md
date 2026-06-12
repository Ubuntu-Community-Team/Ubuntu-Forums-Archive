---
title: "New to Linex"
date: 2006-01-12
forum: Absolute Beginner Talk
---

### Post by priyank on 2006-01-12
Hi
I am quite new to Linex and also to Ubuntu

Have a Compaq laptop having Windows XP installed on it
Have installed the Microsoft Virtual Machin 2004 in the PC
NOw I had tried to installed the Ubunto in the virtual drive and setup went smoothly

after installation it reboot and then I am not able to see anything
When I try to change the view to full screen it says 

The Virtual machine is using a video mode that is too large for your monitor
Virtual PC has switch from full screen mode back to windowed mode

in this mode also the  screenn resolution is not ok ....
I am not able to figure out the problem ... can anyone help me on this

---

### Post by humanity_to_others on 2006-01-12
Use [VMware]("http://www.vmware.com/") instead that Ms stuff

---

### Post by bscbrit on 2006-01-14
I'm not sure, but this doesn't sound like an Ubuntu problem, but rather one of trying to run Ubuntu under Microsoft Virtual Machine.  I cannot help with getting ubuntu to work under MVM.

I assume that you want to keep windows on the laptop as well as Ubuntu?

Are you able to (i.e. have you got permission to do) to set the machine up as a dual boot?  That way, you can have the choice of _either_ windows or Ubuntu at boot time and neither will interfere with the other.  To set up a dual boot, you will need sufficient spare room on your HDD.  Resize the existing windows partition to give you at least 6 Gb of free space (you can run with much less but it doesn't make things easy - I've got ubuntu working in 2.5Gb, or a command line only version ('server') in about 1.5Gb).  Then use the 6Gb for your new ubuntu installation.

---

### Post by priyank on 2006-01-14
Thanks for responding.
As I told earler that I am totally new to Linux and even in my knowns no one is using the linux.  I just want to use it and if feel fit will install in my all systems and will promote this too..

I have windows XP installed in the system.
I don't want the duel OS.

Micorsoft has a product with the name Microsoft Virtual Machine 2004.  This software create one virtual machine in the system in which we can install any other OS or can be the same os. and without duel OS system yu can run the other Virtual machine within XP.

I had tried to install ubuntoo in this virtual machine (which created a virtual drive for 17 GB)

Had installed the everything... of ubuntoo ... and it goes smoothly ....
When I start Linux in that it shows the screen resolution problem .... 
I am wondering if anything there may be installation file ... or may be like entering to safe mode (in linux) where I can reset the resolution properties of Ubuntu.

---

### Post by bscbrit on 2006-01-14
OK, well I will try to help if I can.

The screen resolutions for linux are held in a file called /etc/X11/xorg.conf, along with a lot of additional data for configuring X.  The part of _my_ xorg.conf which controls the screen is shown here

```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV5 [RIVA TNT2/TNT2 Pro]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection


```

In each "Display" subsection, it shows the depth (i.e. bits per pixel) of the screen and the various resolutions that my video combination (i.e. graphics card and monitor) can manage.  The first value in each Modes line is the resolution at which the screen will try to configure itself as default.  

Check your file and ensure that the _first_ entry on each line is set to something reasonable or achievable by any monitor i.e. I would try "1024x768" as the first value on each line for my copy of xorg.conf. 
e.g.

                Modes           "1024x768" "800x600" "640x480" "1280x1024"

Reboot the computer in normal mode and see if the problem is resolved.  If that doesn't work, try the next lowest resolution until you either get one that works or you discover that it is not a problem with X but is caused by something else.  

Let me know how you get on.

---

### Post by priyank on 2006-01-14
thanks bscbrt

But my problem is I am not able to do this ....
as the linux books and automatically reaches to main window, where the display is not proper....
at the same time as I had installed the same in virtual drive usingthe ms virtual machine 2004 ... I am not able to explore the HDD

so I am back to zero again ...

---

### Post by bscbrit on 2006-01-14
Boot the computer in _recovery_ mode i.e. when the Grub menu appears, select recovery mode and this will take you to the command line as root.  You will have to use vim, emacs or pico editor because you will not have access to a GUI desktop and the editors that it provides - pico is probably the best if you haven't used a command line editor before.  However, that is what makes linux more powerful than some other Operating Systems - even when things are not all fully working there is usually a way of fixing it!

---

