---
title: "Resolution issue - first Feisty now Gutsy-HELP"
date: 2007-11-06
forum: Absolute Beginner Talk
---

### Post by Tony3286 on 2007-11-06
I have read and reread posts concerning the 'Out of range" for the video and have had no luck! I went into startup manager - it originally showed 640 x480 - I changed  it to my
correct resolution 1024X768. I then rebooted and same thing - Black screen , no splash screen, get a red out of range box that keeps moving down and to the right and finally get logon screen.  I'm using a OptiQuest 19 inch monitor Q9 and I'm running a Sony Vaio desktop model PCV-RX850. In Windows, it states the video chipset type is SIS 651 Rev00 and lists it as SIS 650-651-750. When I try and choose these setting in "Screens and Graphics" under System-administration and do a TEST , I get a small herringbone design and then get a message "Configuration test failed" and it reverts back to Graphic driver of - Vesa - generic vesa.  I also went into my Xorg.config and can't  figure heads or tails what resolution is my default. Other than the "out of range" red box at boot up and shutting down, the rest of Gutsy works perfectly . Below is a copy of my Xorg.conf.
PLEASE, if anyone could help, it would be greatly appreciated. I am running Gutsy but had the same problem under Feisty for the last 2 months. If I have to edit the Xorg.config, I would appreciate step by step directions - very new to Linux.
Thanks soooooooo much

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       30-80
        VertRefresh     55-75
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by juantovarm on 2007-11-06
try this in the terminal :

sudo dpkg-reconfigure xserver-xorg

---

### Post by so7777777os on 2007-11-06
It's to difficult for me,i'm very new to Ubuntu and english...well..i cant help you...

---

### Post by Tony3286 on 2007-11-06
I'm at work now, but will definitely try ANYTHING when I get home! Thanks for the suggestion . It's more of a nuisance but driving me crazy - I try to read every post on resolution but no success.
If anyone else has ANY suggestions, I would really appreciate it! Gutsy is GREAT and if I can get this resolution thing fixed, it would be perfect.

Tony

---

### Post by eldhaber_unit on 2007-11-06
I already typed the command in the terminal, juantovarm. What will I do next?

---

### Post by eldhaber_unit on 2007-11-06
Please guys help me to fix this thing!

---

### Post by SpiritIsReality on 2007-11-06
howdy
eldhaber_unit ... press enter key, then answer questions best you can. I would recommend
checking for your monitor's horizontal and vertical refresh rates, by going to the manufacturer's
web page or to google.com and entering the make, model. Most of the questions can be
left at the default, and press enter.
trails

---

### Post by Tony3286 on 2007-11-06
For me -I had checked the Vertical and Horizontal refresh rates last nite with the LCD monitor manual - all fall within limits - any other suggestions? Also -is there suppose to be a SPLASH SCREEN and then the login screen or are they one in the same? I get a login screen AFTER the red box does its traveling to the
end of my screen

---

### Post by SpiritIsReality on 2007-11-06
howdy
Tony3286 ... vertical and horizontal refresh rates ... I used sudo dpkg-reconfigure xserver-xorg and set the rates to the limits. works.
 ... splash screen first, then login window. ... what I do is edit the /boot/grub/menu.lst
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.backup
Alt-F2(press and hold Alt key, tap F2 key) type in run box
gksudo gedit /boot/grub/menu.lst
so the kernel line looks like this:
/boot/vmlinuz-2.6.22-14-generic root=UUID=a10146c1-ff01-426e-91b1-1b14f186e17f ro 
(removed the quiet splash)
and change the 
# defoptions=quiet splash  ... line to:
# defoptions=
and save and close the file.
Then I see the ... what you get when you enter 
dmesg | less 
in the terminal., and then I get the login window.
(from here
at terminal command prompt, type
zless /usr/share/doc/upstart/README.Debian.gz
press enter, use up down arrows to view,
press q to quit.)
If it is not to your liking, you can edit it back. or enter the command
sudo cp /boot/grub/menu.lst.backup /boot/grub/menu.lst
then you will get the splash screen before the login window.

trails

---

### Post by Tony3286 on 2007-11-06
Thanks Spirit! Truthfully, I'm not as concerned in getting a splash screen as I am getting rid of the
"Resolution out of range"  Will the maxing the vertical and horizontal setting clear that up?
If I can boot straight to the Login screen WITHOUT the resolution error box, I would be in heaven.
Thanks soo much for taking the time with your post - I'll play with it tonite!

---

### Post by SpiritIsReality on 2007-11-06
howdy
I haven't had the "resolution out of range"  or "configuration test failed" errors yet., and I know you said you've read lots of them, but all I got for you now is this:
[http://www.google.ca/search?hl=en&q=%22configuration+test+failed%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=%22configuration+test+failed%22&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=%22Resolution+out+of+range%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=%22Resolution+out+of+range%22&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22resolution+out+of+range%22&btnG=Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22resolution+out+of+range%22&btnG=Search&meta=)
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22configuration+test+failed%22&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+%22configuration+test+failed%22&btnG=Google+Search&meta=)

in order to answer you further I'd have to find someone who knows.
I'd try the sudo dpkg-reconfigure xserver-xorg and see what it does.
trails

---

### Post by Tony3286 on 2007-11-06
Thanks so much again for the researching - I guess I have alot of reading and trial and error testing  LOL

---

### Post by SpiritIsReality on 2007-11-06
howdy
I don't think you have to do a lot of reading. But it won't hurt.
I'd try the sudo dpkg-reconfigure xserver-xorg and see how it works.
I should have done some searching for your hardware specs too., not just the error message.
It looks like if sis is not a choice for graphics driver in dpkg-reconfigure xserver-xorg, choose vesa.
If sis is available as a choice and it doesn't work too good, run dpkg-reconfigure xserver-xorg again
and choose vesa. If you get to a place where gui graphics are not working, try 
Alt-F2 (hold down Alt key, tap F2 key, release all)  or Ctrl-Alt-F2 (hold down Ctrl and Alt and tap F2)and log in , run dpkg-reconfigure xserver-xorg.
When it's done, run
sudo shutdown -r now
to reboot.
might find a bit here.
[http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+SIS&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=site%3Aubuntuforums.org+SIS&btnG=Google+Search&meta=)
[http://ubuntuforums.org/showthread.php?t=562366](http://ubuntuforums.org/showthread.php?t=562366)
SIS 651 Rev00 
[http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o](http://www.google.com/coop/cse?cx=002165917076592449621%3Ay8jmiivon3o)
[http://www.google.com/cse?cx=002165917076592449621%3Ay8jmiivon3o&q=SIS+651+Rev00&sa=Search&cof=FORID%3A1](http://www.google.com/cse?cx=002165917076592449621%3Ay8jmiivon3o&q=SIS+651+Rev00&sa=Search&cof=FORID%3A1)
[http://www.google.ca/search?hl=en&q=linux+hardware&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+hardware&btnG=Google+Search&meta=)
have you found a support page from the manufacturer or retailer for your rig?
I didn't get too far looking for one:
Sony Vaio desktop model PCV-RX850
[http://www.google.ca/search?hl=en&q=linux+hardware&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=linux+hardware&btnG=Google+Search&meta=)
[http://www.google.ca/search?hl=en&q=Sony+Vaio+&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=Sony+Vaio+&btnG=Google+Search&meta=)
[http://www.sony-asia.com/support/SupportModelSearch.action?site=hp_en_AP_i&sectiontype=support](http://www.sony-asia.com/support/SupportModelSearch.action?site=hp_en_AP_i&sectiontype=support)
[http://www.google.ca/search?hl=en&q=Sony+Vaio+desktop+model+PCV-RX850&btnG=Google+Search&meta=](http://www.google.ca/search?hl=en&q=Sony+Vaio+desktop+model+PCV-RX850&btnG=Google+Search&meta=)
[http://www.amazon.com/Sony-PCV-RX850-Desktop-Pentium-drive/dp/B00006LHEU](http://www.amazon.com/Sony-PCV-RX850-Desktop-Pentium-drive/dp/B00006LHEU)
can't find the motherboard specs to check for it on the hardware compatability list.
trails
I was in New Jersey a few years back. Took some survival training from Tom Brown Jr. in the Pine Barrens.
On the way back I was dressed in camo, and smelled of wood smoke. I had my baggage checked quite thoroughly.

---

