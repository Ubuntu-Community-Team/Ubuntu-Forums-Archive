---
title: "Unusual resolution problem"
date: 2006-03-19
forum: Absolute Beginner Talk
---

### Post by CronoDekar on 2006-03-19
The main problem here is that whenever I do a cold boot, the resolution appears in 640x480, and is unchangable.  The thing I find unusual though (or at least something I haven't seen in any other threads with similar problems), is that if I reboot -- even before logging in -- it comes up just right at 1024x768 with a refresh rate of 85 Hz.  But while it does work, it still is annoying that I have to boot the computer twice to get it to work in the right resolution.

I tried modifying my xorg.conf as according to [this howto](http://ubuntuforums.org/showthread.php?t=83973), but whenever I tried I got an error getting Gnome coming back up and had to restore the backup.  This is what I tried to modify the relevant xorg.conf entries to be:

```

Section "Monitor"
    Identifier    "Maxitech"
    HorizSync     30-69
    VertRefresh    50-90
# V-freq: 85.00 Hz  // h-freq: 68.79 KHz
Modeline "1024x768" 97.40  1024 1072 1192 1416   768  768  771  809 
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "NVIDIA Corporation NV5M64 [RIVA TNT2 Model 64/Model 64 Pro]"
    Monitor        "Maxitech"
    DefaultDepth    16
    SubSection "Display":
        Depth        16
        Modes     "1024x768" "800x600"
    EndSubSection
EndSection

```

I'm not sure what my video card actually is (if it's not that), but that's what it said in the file before so I didn't change that.  I took the specs from my monitor at [this site](http://www.maxtech.com/html/xt-5862.html) (yeah, it's a really old monitor) to get the HorizSync and VertRefresh (though... looking at the site again I see that they say "frequency", are these the same?).  One odd thing I did find odd on the site though was that it says my monitor can do 1280x1024, but even when WinME was installed on this computer it couldn't get higher than 1024x768, and I"m sure the model number is right.  I also tried using the X reconfiguration process mentioned in the howto, but that was still unable to restart gdm.

Any help or ideas would be very much appreciated.  Thanks!

---

### Post by Mustard on 2006-03-19
The usual course for troubleshooting with video problems is to look at the Xorg.0.log in your /var/log/ folder.  Error messages are usually preceded with an [EE] notation, if I recall correctly. With this in mind, you could try this command...

```
cat /var/log/Xorg.0.log | grep EE
```

This should show any lines with the EE notation.  Alternatively you can look through the log manually.  You might like to paste any relevant error messages in here to see if someone can help with them.  Ideally you would use the log output from the first boot that doesnt boot up correctly.

---

### Post by CronoDekar on 2006-03-19
Thanks!  This was after a boot which loaded up correctly, but I got:

```

(II) Loading extension MIT-SCREEN-SAVER
(EE) Failed to initialize GLX extension (NVIDIA X driver not found)

```

Which is weird, since I do have the nvidia driver from the automatix install.

Also, I just did a cold boot a few times to try to get it to run in 640x480, but it loaded up in 1024x780, like it's supposed to.  So that kinda leads me to think that the change to 640x480 happens after running and installing via the update manager (I usually only boot about 1/day).  Could be other reasons though.  I'll try again when/if it boots in 640x480 again to see what I get.

---

