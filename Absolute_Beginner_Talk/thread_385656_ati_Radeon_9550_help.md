---
title: "ati Radeon 9550 help"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by metroknight on 2007-03-15
I need some help. I installed envy to update my ati drivers and after it installed, my video card wouldn't work. The frequency was defaulted to high, so I went searching and tried to follow some suggestions and stupidly removed my drivers.  I did this in the recovery bootup and now it says that the FGLRX module doesn't exist and WACOM drivers are not there. 

I've been searching the forums with various keywords but I haven't found how to reinstall my drivers from the recovery mode. Can anyone help me with instructions or (better yet)  give me a link to read and try to follow.

Thank you for any and all help/info.

---

### Post by metroknight on 2007-03-16
Quick update. I found the Edgy Installation guide for my video drivers and I followed it. I did install my drivers but I'm still getting the out of frequency range for my video card. It shows 74/55 mhz or so. All I'm getting is a black screen with my monitor showing that warning. Any suggestions?

---

### Post by freebird54 on 2007-03-16
Can you edit the contents of the

```
/etc/X11/xorg.conf
```

file?  Maybe using "sudo nano?"  If so - I would try to set the section in your file corresponding to this code fragment to the values that your monitor can handle.  If you don't know, you should use 43-60 for VertRefresh just to get going - and ask an expert later!

```
Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection
```

Good luck

---

### Post by metroknight on 2007-03-16
> **freebird54 said:**
> Can you edit the contents of the

```
/etc/X11/xorg.conf
```

file?  Maybe using "sudo nano?"  If so - I would try to set the section in your file corresponding to this code fragment to the values that your monitor can handle.  If you don't know, you should use 43-60 for VertRefresh just to get going - and ask an expert later!

```
Section "Monitor"
        Identifier   "Samsung_900iFT"
        HorizSync    30.0 - 100.0
        VertRefresh  50.0 - 160.0
        Option      "DPMS"
EndSection
```

Good luck


So how do I access this file in text mode. I'm still learning how to work with command line because that is all I have to work with. I'm using my WinXP to post and read here.

---

### Post by freebird54 on 2007-03-16
Sorry - wasn't sure of your comfort level with this stuff!  Anyway...

 ```
sudo nano /etc/X11/xorg.conf
```

will start up a text mode editor with your file in it.  The basic commands for operating the editor are 'listed' at the bottom of the screen - the important ones being <ctrl>o to write OUT your changes, and <ctrl>X to eXit.

After trying these changes - IF it doesn't work to

```
startx
```

then try this

```
sudo dpkg-reconfigure xserver-xorg
```

Which will put you into a text mode interface to resetting your x server options (essentilly rebuilding your xorg.conf file).  Most of what you see will be OK to leave either empty, or as default - except the bits about the monitor and resolution settings.  By the way - you can <tab> to highlight the ok/cancel prompt in lists that you are not there already :) 

When you get to the monitor setting, try to autodetect the monitor.  Give it a name when asked.  Choose 'MEDIUM' for setting it up.  Choose the 'BEST' safe resolution that you know of (perhaps 1280x1024 @ 60 Hz refresh??).  When you have the list of possible resolutions, use the space bar to toggle the 'mark' beside it as you wish - BEING SURE NOT TO MARK ANY UNSAFE (too high) RESOLUTIONS!

When you are done - WRITE DOWN the name it saved the backup under - in case you made things worse :) (unlikely)  If at first try it does NOT work (startx still does not get you in) then re-run the dpkg-reconfigure command again, choosing 'vesa' as your driver, and doing the rest as before.  You can change things back to fglrx more comfortably from within the windowed environment.

Hopefully this isn't TOO much detail - and enough detail at the same time :)  Post back if it works for you - and if you need more help to get things RIGHT after you get them WORKING...

---

### Post by metroknight on 2007-03-16
> **freebird54 said:**
> Sorry - wasn't sure of your comfort level with this stuff!  Anyway...

(snipped for brievity)

Hopefully this isn't TOO much detail - and enough detail at the same time :)  Post back if it works for you - and if you need more help to get things RIGHT after you get them WORKING...

Actually that was just about the right amount of detail and basic explaining. I'm going to be trying it shortly. I'm smart enough this time to copy and print out your instructions so I'm not scratching my head while trying to remember how to do it. :lolflag: 

Thanks for the help and wish me luck.

---

### Post by freebird54 on 2007-03-16
Good Luck :D

---

### Post by ravis_31 on 2007-03-16
> **metroknight said:**
> So how do I access this file in text mode. I'm still learning how to work with command line because that is all I have to work with. I'm using my WinXP to post and read here.

mine is a ati radeon x700 and opened the conf file in vi(will it cause a prob?)and edited ati to radeon and i'm able to hear the startup sound but the screen is still blank.i searched for fglrx_dri.so but it doesn't exist.How do i get it?
FYI,i'm installing on my laptop and haven't got my network configured yet.

travis

---

### Post by metroknight on 2007-03-16
> **ravis_31 said:**
> mine is a ati radeon x700 and opened the conf file in vi(will it cause a prob?)and edited ati to radeon and i'm able to hear the startup sound but the screen is still blank.i searched for fglrx_dri.so but it doesn't exist.How do i get it?
FYI,i'm installing on my laptop and haven't got my network configured yet.

travis

Have you read these threads?

[http://ubuntuforums.org/showthread.php?t=375810](http://ubuntuforums.org/showthread.php?t=375810)

[http://ubuntuforums.org/showthread.php?t=276650](http://ubuntuforums.org/showthread.php?t=276650)

This are two threads that I read and tried to understand. I'm very new at this so all I can do is point out what I've read.

Hey Freebird54, It worked.  \\:D/  I'm now back up with my Ubuntu gui and thank you for the help.

---

### Post by freebird54 on 2007-03-16
Thanks - but all I provided was a little translation!  Now - are things running at fill speed?  :)  you may have a little more configuring to do, depending on your intended uses of the machine....

---

### Post by metroknight on 2007-03-16
It is up and running like it was when I first started using Ubuntu which is just fine. This is mostly my internet surfing machine along with text work. Again thanks for the help.

---

