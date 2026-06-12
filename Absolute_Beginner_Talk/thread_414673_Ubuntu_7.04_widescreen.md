---
title: "Ubuntu 7.04 widescreen"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by fubar_bg on 2007-04-20
Hi,

i just installed the newest Ubuntu distribution on my laptop ACER TravelMate 4064WLMi (915 graphics adapter i guess)

And surprise, my desktop looks "ugly", the reason -> i cannot switch to 1280x800 resolution.
I have the possibility to choose from 800x600 to 1024x768...

Could someone help and tell me how to change the resolution on my laptop.

And why it isn't supported ? When i saw "newest and best, support for laptop and so on" i thought that finally this widescreen resolution issue have been fixed.

Most of people i know, use laptops or have widescreen monitors, that apparently aren't supported by this distribution ( and most of the others )...

And it's hard to work on such a machine, when the display is blurry, smashed and so ugly...

Please, help!

PS: i think this is great community, and i'll find help here. But also, i think it's a good idea to put WS support in next version or in an update patch...

Thanks in advance for your help!

---

### Post by fubar_bg on 2007-04-20
Does anybody know how this issue can be fixed ?

---

### Post by mehmet_cann on 2007-04-20
open console and try this
 sudo dpkg-reconfigure xserver-xorg

when you see resolutions, select what you want.

---

### Post by Cappy on 2007-04-20
I just installed 7.04 a few minutes ago and I had to manually set my (non-widescreen) resolution also, even though Edgy had detected it perfectly before. 
If you're not scared of editting a file you can 
```

sudo nano /etc/X11/xorg.conf

```

If you scroll down you should see something like 
```

SubSection "Display"
                Depth   24
                Modes           "1280x1024"     "1024x768"      "800x600"
        EndSubSection

```

and you can just add your resolution onto the list at the beginning so it looks like

```

SubSection "Display"
                Depth   24
                Modes           "1280x800"    "1280x1024"     "1024x768"      "800x600"
        EndSubSection

```

It's just that your wide screen isn't automatically configured "out of the box". It's not that widescreen isn't supported. It will work perfectly after you configure it.

As far as I know, the best thing about 7.04 for laptops is easy and stable WiFi.

---

### Post by DrLilo on 2007-04-20
I have the same problem. I tried added extra resolutions to that file, but how do I then set my screen to use one of the new ones? Not from the screen resolution option in the System menu, it seems...

---

### Post by rxtx on 2007-04-20
Hello!

I made the move to Unbuntu 7.04 yesterday (along with many other people I am sure), and have been very impressed. Almost everything was fine "out of the box", bar widescreen res.

Running "sudo dpkg-reconfigure xserver-xorg" and going through the X setup again would result in a bugout where I'd have to restore the xorg.conf backup.

In the end, I resorted to using 915resolution (google is your friend) to alter the bios' display modes to suit 1280 x 800 then edited xorg.conf accordingly.

This seems to work fine, apart from the "spinning cube" workspace effect which now refuses to kick in. Oh well, I suppose being able to see in native res rather than use some nice eye candy is more beneficial anyway. (Although if anybody knows any workarounds, I'd be interested ;) )

Other than that, I'm now a convert. I'm going to keep 7.04 on my laptop and use it to learn more about linux and it's workings. Ace!

---

### Post by Jhongy on 2007-04-20
This is no different than installing Windows for the first time -- graphics drivers and monitor drivers not being installed / set up properly by default. It's better that there are sane lower resolutions so everyone can at least see what is going on until they set up. 1440x900 resolution was a real pain for me on Windows until I downloaded a driver from the monitor manufacturer's site. 

I've had widescreen working (dual monitor widescreen, I might add) in all versions of Ubuntu I have tried.

Follow mehmet's suggestion above to run the X server configuration program. Open a console and type:
sudo dpkg-reconfigure xserver-xorg

This gives you access to the X server (the display manager)'s configuration script.

It will allow you to select a driver and your resolution. Then, reboot and set the option from your System->Preferences menu.

---

### Post by Meatcart on 2007-04-20
Following this guide worked for me : [http://ubuntuforums.org/showthread.php?t=414194](http://ubuntuforums.org/showthread.php?t=414194)

I firstly booted into safe mode, then I installed Ubuntu. Then I followed the guide and now I've got 1280x800 working properly.

---

### Post by adolph on 2007-04-20
Thanks for the posts.. will check it out right away.., I have also downloaded the latest 7.04.. then try the suggestions.
Appreciate the help!.
Adolph.

---

### Post by fubar_bg on 2007-04-20
Hi,

i've fixed the problem with **auto915resolution**.

Now it really beutifull...
And the bouncing effect is great..

The WiFi is working even better than in windows with the original intel wifi drivers...
Just great distro...

---

### Post by compmodder26 on 2007-04-20
> **DrLilo said:**
> I have the same problem. I tried added extra resolutions to that file, but how do I then set my screen to use one of the new ones? Not from the screen resolution option in the System menu, it seems...

You have to restart the X server for any changes to take effect.  You can do that with the keyboard combination of Ctrl+Alt+Backspace

---

### Post by stonecold23 on 2007-04-21
i cant get widescreen to work
i have looked at the thing cappy suggested entering my own resolution manually but the one i want already appears "1440x900"
but when i go back and click 
system/preferences/ screen resolution 
the highest res is still 1024x768
how do i get it to work.
not great with code really i'm 17 and just started learning vba. so not very experienced
and this is why i have had no success with any of the links given to different threads aswell.
can someone give me the simplest answer please?
thanks in advance xx :D

---

### Post by rxtx on 2007-04-23
@ stonecold - What chipset you using?

---

### Post by mkjarema on 2007-04-23
So where do i put in my 1280x1024?
Right now I can only get 600x800 and somthing even lower
This is what i get in this file /etc/X11/xorg.conf 

```
Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
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
EndSection


```

---

### Post by compmodder26 on 2007-04-23
You're config file is messed up.  Replace everything beginning with the first 'SubSection "Display" '  to the last 'EndSubSection' with:

```
SubSection "Display"
                Depth           1
                Modes          "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection 
        SubSection "Display"
                Depth           24
                Modes          "1280x1024"  "1024x768" "800x600" "640x480"
        EndSubSection
  
```

---

### Post by mkjarema on 2007-04-23
well i put it in.  I didn't see anywhere to save it, so did it take?  I didn't see any different options in prefrences, so I am going to reboot i guess to see if that does anything, i just hope i get a screen back..... (keep your fingers crossed)

---

### Post by compmodder26 on 2007-04-23
You aren't sure if it is saved?  How did you edit it?  Assuming it saved properly, a restart of the X server is needed.  Your method of a complete reboot works, but a quicker method is to press Ctrl+Alt+Backspace.

---

### Post by mkjarema on 2007-04-23
> **compmodder26 said:**
> You aren't sure if it is saved? NO, I just ran ```
sudo nano /etc/X11/xorg.conf
```   How did you edit it?  Assuming it saved properly, a restart of the X server is needed. 
>  Your method of a complete reboot works, but a quicker method is to press Ctrl+Alt+Backspace.  I actually did the keyboard command, what is the difference?  I am just used to old windows terms I guess

and i am assuming i did it incorrectly since everyhting is the same (which is better than worse)

---

### Post by mkjarema on 2007-04-23
OK, I found out how to save changes, ecs+x.  I felt like a total idot for about 15 min, during this.  I am going to try replacing the code again and try again.

THX again for helping

---

### Post by mkjarema on 2007-04-23
Ok, I changed it, and crtl+alt+backspace, but no change and no options in preferences either.  And, yes I saved the file :-)

---

### Post by stonecold23 on 2007-04-24
via chipset how is that relevant?

---

