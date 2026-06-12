---
title: "WIdescreen on Laptop"
date: 2006-07-26
forum: Absolute Beginner Talk
---

### Post by arthurbarnhouse on 2006-07-26
I have an Averatec 1020-ED1 that I just bought.  I'm having some trouble with the wide-screen, everything's stretched.  I found this on the search page:  [http://www.ubuntuforums.org/showthread.php?t=222540&highlight=915+resolution](http://www.ubuntuforums.org/showthread.php?t=222540&highlight=915+resolution)

From what I can understand of this it would solve my problem, but Honestly, I don't really understand how to do this.  Can anyone give me a more step-by-step explination on how to do this.  I'd apprecate it.  Thanks.

---

### Post by nicbink on 2006-07-26
What video card to you have?  The first step would be to make sure you have the proper drivers installed.

I have setup three widescreen laptops and none of them have required the 915 hack.

---

### Post by arthurbarnhouse on 2006-07-26
I have intel Integrated Intel Extreme Graphics 2.

---

### Post by jimmygoon on 2006-07-26
for the time being you can change a setting in your bios to prevent the stretching... it won't be widescreen but it should prevent you some headaches...

---

### Post by arthurbarnhouse on 2006-07-26
that helps, but it isn't a long-term solution.  thanks.  :)

---

### Post by Jhongy on 2006-07-26
Hi arthur, I'm a newbie too and recently had to learn how to go through this process....

To get the correct resolution, you will need to have the right drivers selected, and the right settings chosen in the configuration file for your X server (the X server is what handles graphics display).

Just in case your drivers and X server are already configured, you can try changing the resolution in System --> Preferences --> Change Resolution

If the option is not available, then you will need to configue your X server for the correct driver and resolutions.

The easiest way to set everything up is with the automatic configuration script that comes with the X server.

First, back up the current configuration file. open a terminal window (Applications --> accessories --> Terminal), and type:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf-backup
```

The 'cp' command means "copy", and the "sudo" command allows you to perform the command as the root / super user. (since files in /etc/ are read only to normal users).

If, during the course of configuration, you bork your xorg.conf file, and your desktop doesn't start up, you can simply copy the xorg.conf-backup back to xorg.conf.

Now, you can run the automatic configuration script

```
sudo dpkg-reconfigure xserver-xorg
```

You will be presented with lots of questions - just accepting the defaults for most of them should be fine.

When you get to the question about graphics drivers, select yours from the list.

When you get to the question about resolutions, you can scroll downt he list and select the one(s) you want to be available with the spacebar.

When you're done, restart the computer.

If your resolution is not automatically selected, then System --> Preferences --> Change Resolution should now have the options you need available. 

If not, then you'll need to manually edit the configuration file.

---

### Post by Shay Stephens on 2006-07-26
I added 1280x800 in my /etc/X11/xorg.conf file. Usplash still doesn't work right, the screen gets shifted half way over.  So I disabled usplash and the text boot works fine.

---

### Post by arthurbarnhouse on 2006-07-27
ok, I'm at the part where you chose resolutions, and I've chosen the proper resolution, but it refuses to move forward.  When I choose "OK" it will just refresh the screen, it won't move forward.

---

### Post by Jhongy on 2006-07-27
You've selected the resolutions you want with the spacebar? Then enter to continue? Try selecting more than one resolution if it doesn't work

---

### Post by arthurbarnhouse on 2006-07-27
yup. selected with spacebar, seleced more than one resolution.  Hit enter.  Nothing seems to happen.  Still just doing the refresh thing.

---

### Post by Jhongy on 2006-07-27
> **arthurbarnhouse said:**
>   Still just doing the refresh thing.

Not sure what you mean? Do you mean the configure script has locked up?

After setting the resolutions, there are a bunch more questions to go through..... and nothing will happen until you finish the script, restart the computer (or restart X with ctrl-alt-backspace), and (possibly) select the correct resulution from Preferences->..

---

### Post by arthurbarnhouse on 2006-07-27
Yup, I restarted the process, and it worked like a charm.  Glorious widescreen mode.  Thanks a ton.

---

### Post by xdevnull on 2006-11-01
Jhongy:

I have an averatec 1050 (pretty much the same as the 1020) and am usuing Edgy that I downloaded and installed yesterday.

Worked great for me - thanks for the info.  After running the script I logged out and then did the trusty old ctrl+alt+backspace to restart X - it came up in the new resolution automatically (1280x768).  I didn't even have to select it.

---

### Post by xdevnull on 2006-11-04
Whoops - that kind of worked.  The problem is that the default driver is vesa - not i810.  When I went back and selected i810 and restarted it broke....eventually very badly.  I recopied my backup then went in and manually edited my xorg.conf file to add the 1280x768 modes and keep my i810 driver (which is really the only one to use for anything 3D or even watching movies).  Logged out, ctrl-alt+backspace and X restarted and correctly detected the resolution - I didn't even have to go into the Screen Resolution applet under System!

Here is the relavent part of xorg.conf in edited form.  I think this should work with all the averatec 1000 series:

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Intel Corporation 82852/855GM Integrated Graphics Device"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x768" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

```

---

