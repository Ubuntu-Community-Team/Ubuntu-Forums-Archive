---
title: "resolution error on ibook g3 700"
date: 2008-01-10
forum: Apple PPC Users
---

### Post by mangurt on 2008-01-10
Greetings all,
I have a old ibook g3 700 that I resurrected recently.  The only operating system (via mac) that I had for it was OS 10.1  I could not find any software to work with it (firefox, ect) so I put kubuntu 6.06 on it.  I did the install from the alternate disk.  The installation went great, but the screen resolution is locked on 640x420 or something like that (I am currently at work).  Is there any way I can change the screen resolution?  I tried looking around the forums for this, but I am not sure what I need to I need to do.
Thanks for the help.

---

### Post by fouba on 2008-01-10
> **mangurt said:**
> Greetings all,
I have a old ibook g3 700 that I resurrected recently.  The only operating system (via mac) that I had for it was OS 10.1  I could not find any software to work with it (firefox, ect) so I put kubuntu 6.06 on it.  I did the install from the alternate disk.  The installation went great, but the screen resolution is locked on 640x420 or something like that (I am currently at work).  Is there any way I can change the screen resolution?  I tried looking around the forums for this, but I am not sure what I need to I need to do.
Thanks for the help.I had same kind of problem that I solved by changing the resolution to 800x600. I still have the problem when I put my Computer (iBook G3) on, the screen is like cut from almost the middle.. I took picture because it is hard to explain the problem, and sorry about the bad quality.
And yes you can change the resolution, I'd say that it solves the problem, with me it worked. And the problem dissapears when I log in, the resolution goes 800x600 and I can use computer normally. And I recommend Xubuntu, with Ubuntu it didn't work, about Kubuntu I dont know..



[IMG]http://koti.mbnet.fi/marttita/IMG_0096.JPG[/IMG]

---

### Post by mangurt on 2008-01-10
I wish I could change the resolution.  I went to screen resolution and tried changing it, but it's locked (even if I go in adminstrative mode).

---

### Post by curly_nostrill on 2008-01-11
hey!  It looks like you may have a similar problem to mine on my iBook dual usb 600.

I had to ctrl+alt(option)+f1 to get a virtual console and login.  If you're installing from the live cd I think you can just login in as root here then you can forget the 'sudo' part of the commands below.

I had to edit xorg.conf.  First ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.whackyx
``` to make a backup in case something goes wrong.  

Then ```
sudo nano /etc/X11/xorg.conf
``` and go down to ' Section "Screen" '.  Comment out any subsections that are higher than what your screen/vid supports.  You can look up the supported depths and resolutions for your particular machine at the apple site.  
Below is an exerpt from my xorg.conf, your's may be different.
```
Section "Screen"
             Identifier           "Default Screen"
             Device               "ATI Technologies Inc Rage Mobility M3 AGP 2x"
             Monitor              "Color LCD"
             DefaultDepth     16
             Subsection "Display"
                          Depth                       1
                          Modes                       "1024x768
              EndSubSection
              -----------------
              ---blah blah other modes--
              -----------------  
              Subsection "Display"
                          Depth                        16
                          Modes                        "1024x768"
              EndSubSection
              #Subsection "Display"
              #          Depth                        24
              #          Modes                       "1024x768"
              #EndSubSection
EndSection
```
I just left the highest supported mode as the default to keep it simple.

While you're there you should check the horizontal sync and vertical refresh rates and put whatever apple tells you into the section 
```
Section "Monitor"
             Identifier            "Color LCD"
             Option                "DPMS"
             HorizSync            28-51
             VertRefresh        43-60
EndSection
```
Those are my specs so your's may be different.

Save the changes by 'control key' +(the letter) 'o' key, nano will prompt for the file name to save as with xorg.conf as the default, hit 'Return'. then 'control key' + 'x' to exit.

You will have to restart or logout and back in to see the changes.

make popcorn:popcorn:

---

### Post by havoc_joe on 2008-01-14
What size screen does your iBook have? I have the 12.1" iBook G3 700 MHz and I know that it only supports resolutuions of up to 1024x768 with 16-bit display depth. Anything higher than that and it won't be able to cope well. Like the above example, you have to set this in /etc/X11/xorg.conf under the "Screen" section.

I hope this helps.
~Joe

---

