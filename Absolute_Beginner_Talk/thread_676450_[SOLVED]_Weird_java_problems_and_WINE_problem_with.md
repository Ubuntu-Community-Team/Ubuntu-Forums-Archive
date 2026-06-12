---
title: "[SOLVED] Weird java problems and WINE problem with Gusty"
date: 2008-01-23
forum: Absolute Beginner Talk
---

### Post by Tsukasah on 2008-01-23
I'm using a decent spec computer. AMD Athlon x64 4200+ 2.2ghz Dual Core Processor, Gigabyte motherboard(NVIDIA 6200 onboard video, I think), 1gb of RAM. Anyways I recently used just the 32bit Ubuntu with Feisty. After I had a strange problem with WINE and that I couldnt upgrade to Gusty because when it prepared to upgrade it couldnt find some "automatix" file and would then quit trying to upgrade. So I went to the ubuntu site and made me a 62bit Gusty Gibbon live cd, and installed. It looked weird at first, There were no Icons at the top(no ubuntu logo next to applications) and the bottom of hte screen looked like it had orangish tears. I enabled the restricted graphics driver thing, now it all looks fine. After I installed flash on mozilla firefox, I thought I was all good to go. Now no embedded video will work, and here's what youtube looks like [http://s114.photobucket.com/albums/n250/12ed_XIII/?action=view&current=Screenshot-2.png](http://s114.photobucket.com/albums/n250/12ed_XIII/?action=view&current=Screenshot-2.png)

Notice the play/pause section, etc. Also, when I pause the video it wont pay again, and if I watch the full video and hit play to replay it it shows only the first showing image. And some program called "gnash" or something is installed, and when I quit the area where the video should be turns grey.

About WINE. I go to add/remove programs and try to click the check box but it doesn't mark itself, I can't install it. What's going on?

One last thing, how do I install TuxGuitar? Here's what it said in the readme:

INSTALL:    
Extract TuxGuitar-*.tar.gz in your favorite location
$tar xfz TuxGuitar-*.tar.gz
$mv TuxGuitar-* /home/*/install_dir
       
RUN:
Run TuxGuitar script.
$/home/*/install_dir/TuxGuitar-*/TuxGuitar

I extracted TuxGuitar to a folder on my desktop, but after that I dont get the "$tar" part and what the * means. Any help would do! thanks!

:guitar:

---

### Post by yourpalal on 2008-01-23
well... my first piece of advice is to use seperate posts for seperate problems.. now that i've got that out of the way..
FLASH:
first of all gnash is the open source flash player.. it does not support all flash rather all flash up to 7 and some 8 actionscript ( the programming language used in flash) the reason you have gnash and not macromedia's proprietary flash player is because they have not produced a 64 bit flash linux player. This is one of the main issues many people have with running a 64 bit kernel... 
wine:
are you installing it through automatix?
try this:
[http://www.winehq.org/site/download-deb](http://www.winehq.org/site/download-deb)
follow the gutsy instructions.. this is how i installed wine and it works great :D
TUXGUITAR:
the * stands for what is likely a version number.. it will be in the file name.. this is done so that they can have the same readme for all versions. the $ means a command you will input into the terminal.. once you have navigated to the newly created directory
here is a handy wiki that has helped me out lots:
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
good luck!

---

### Post by yourpalal on 2008-01-23
sorry i forgot to mention..  with the embbedded videos you should add the medibuntu packages by following this guide:

[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

add everything you can find regarding gstreamer plugins and mpeg (ffmpeg included)
this should help with embedded videos :D also make sure you have the totem plugin for firefox installed

hope all this helps!

---

### Post by Kilz on 2008-01-24
[This post will help you with 64bit flash.]("http://ubuntuforums.org/showthread.php?t=476924")

---

### Post by Tsukasah on 2008-01-24
Thanks, both of you! :) Everything is up and running now. ^^ and I'll keep that "how to install ANYTHING" page in mind. :D Thanks for the flash download as well, everything is back to normal! w00t!

---

