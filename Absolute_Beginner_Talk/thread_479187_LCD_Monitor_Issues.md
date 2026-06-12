---
title: "LCD Monitor Issues"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by Tyscorp on 2007-06-20
Ok so here's the thing, I just purchased a new 19" Widescreen LCD monitor (ASUS VW192T) to replace my old 17" CRT one. And, in both Ubuntu 7.04 and XP, the it wont go into its native res of 1440x900. The max for both Ubuntu and XP is 1024x768, and its really starting to bug me because everything is stretched. I have an on-board graphics card for the time being (Planning on buying a nVidia GForce 8700 GTS 640mb)

Please render assistance, its really annoying me.

---

### Post by atria on 2007-06-20
If it doesn't work in windows too, chances are that your graphics card does not support 1440x900. What is the model of your current onboard graphics card?

---

### Post by Tyscorp on 2007-06-20
Umm... I have no idea. It came with a GIGABYTE GA-945GM-S2

---

### Post by nutz on 2007-06-20
Integrated Intel® Graphic Media Accelerator 950

---

### Post by atria on 2007-06-20
Hmm.. i'm not sure if this is going to help, but give it a try anyway if you really can't bear with the low resolution:

```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf~
sudo nano -w /etc/X11/xorg.conf

```

look for this section under Screen
```

        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection

```

Change it to
```

        SubSection "Display"
                Depth   1
                Modes           "1440x900"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1440x900"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1440x900"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1440x900"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1440x900"      "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1440x900"      "1024x768"      "800x600"       "640x480"
        EndSubSection

```

and restart your xserver by doing a control-alt-backspace.

If it doesn't work or if your xserver does not start, do this:
```

sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf

```

and try starting xserver/gdm again by doing a system reboot or
```
/etc/init.d/gdm restart
```

Hope that helps

---

### Post by Tyscorp on 2007-06-20
I tried it and nothing changed...

---

### Post by atria on 2007-06-20
Weird stuff, because it works with my configuration. I think the driver that you have does not support that resolution. 

You might want to open /var/log/Xorg.0.log and /var/log/Xorg.0.log.old and look for the errors associated with that resolution, or search the forums since there might be other people who had experienced that problem as well.

---

### Post by Tyscorp on 2007-06-20
I don't know what to look for in /var/log/Xorg.0.log... It just has a bunch of text memory addresses. Also, could my PC still be configured to use the CRT?

Edit: How do I update my driver?

---

### Post by atria on 2007-06-20
After editting xorg.conf and restarting your xserver, the resolution should be 1440x900 without any further modifications.

If it doesn't work do make sure to do a
```
sudo mv /etc/init.d/X11/xorg.conf~ /etc/init.d/X11/xorg.conf
```
so that your changes are rolled back.

> Also, could my PC still be configured to use the CRT?
Yep you can, absolutely.

---

### Post by Tyscorp on 2007-06-20
Hmmm... I changed /etc/X11/xorg.conf instead of /etc/init.d/X11/xorg.conf because the latter did not exist. Is that a problem?

---

### Post by atria on 2007-06-20
Oops!
Dear god, i guess i need more sleep.

```
sudo mv /etc/X11/xorg.conf~ /etc/X11/xorg.conf
```
is the correct version.

Give me a moment while i edit them correctly.

//edit
Committed my edits; check out post #5. Refollow the instructions. Sorry about that!

---

### Post by Tyscorp on 2007-06-20
I tried again and it didn't work, still no 1440x900 res is present.

---

### Post by atria on 2007-06-20
Perhaps the drive/hardware doesn't support that resolution then. You'll have to do a forum search regarding that resolution and hardware, or wait till someone else helps.

---

### Post by Tyscorp on 2007-06-20
How do I get a driver...?

---

### Post by atria on 2007-06-20
I'm not sure what driver is needed for your graphics card. You'll have to search for "Graphic Media Accelerator 950" using the forum search function.

---

### Post by Tyscorp on 2007-06-20
Yay! I fixed. Thanks a lot for your help atria. I couldn't have done it without you.

---

### Post by atria on 2007-06-20
Woot! How did you do it? You might want to enlighten me there, heh.
People who encounter this problem in future will definitely find it helpful too.

[quote=Tyscorp]Thanks a lot for your help atria.[/quote]
Welcome, glad it works now ;)

---

### Post by Tyscorp on 2007-06-20
```
sudo apt-get install xserver-xorg-video-intel
```

After a lot of mucking around and making it so xserver didn't even work for a while. So I tried this:

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

And chose intel and 1440x900 as the options thingys. Simple...

---

