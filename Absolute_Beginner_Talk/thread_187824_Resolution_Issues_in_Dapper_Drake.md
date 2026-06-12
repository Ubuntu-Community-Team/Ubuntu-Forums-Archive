---
title: "Resolution Issues in Dapper Drake"
date: 2006-06-03
forum: Absolute Beginner Talk
---

### Post by chimerical_brio on 2006-06-03
I just upgraded to 6.06 LTS, and I'm having issues with my screen resolution. I'm pretty much a beginner when it comes to computer hardware and Linux, so please forgive my lack of knowledge.

My problem is that the only resolution listed is 640x480, which is definitely too small for me. I know that my monitor supports higher resolutions, but I really have no clue about my video card (I don't even know the make; it came installed with the motherboard). Can anyone help me? Thanks a lot.

---

### Post by Dr. Nick on 2006-06-03
You can add resoulitions to your /etc/X11/xorg.conf file. I will post the part of mine that as a guide.



```

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV18GL [Quadro4 NVS AGP 8x]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection

```

Just add the res like 1024x768 into each depth and then save the file and logout.

If that doesnt work then your monitor may not be configured right and you can then try

sudo dpkg-reconfigure xserver-xorg 

and set up your monitor and choose your desired resoulitions

---

### Post by sugonaut on 2006-06-03
The advice from Dr. Nick worked for me.  At the command prompt, type: sudo gedit /etc/X11/xorg.conf.  I added "1280x800" at the front of each line.  I rebooted and had to go to System -> Preferences -> Screen Resolution and change to 1280x800...clicked Apply.  All is well again.

Thanks Dr. Nick!

---

