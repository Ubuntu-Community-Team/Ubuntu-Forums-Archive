---
title: "Can I use Wine to run my WMP 10 in my media/hda1/Program Files/????"
date: 2006-12-04
forum: Absolute Beginner Talk
---

### Post by crimesaucer on 2006-12-04
I have an iRiver T-30 mp3 player/device that ONLY will use WMP 10 for it's syncing. I just installed wine, and I'm wondering how to use it for the WMP 10. 

Do I download a new WMP 10 for my xubuntu, and then add a folder of music for the library, or can I just write

wine /media/hda1/Program Files/Windows Media Player/wm player.exe

and if that is what I'm supposed to write, then how do I represent a "space" when writing in terminal?

Thanks for any info,
-c.

---

### Post by rbprogrammer on 2006-12-04
i'm a noobie to wine myself, but i might suggest downloading the WMplayer installer executable, and run that under wine.  try installing the program to some space on a writable partition, such as the wine directory created in your [/home] folder created by default.

i'm not an expert, but if that doesnt work, you can always just delete the created folders/files.....

---

### Post by Afteraffekt on 2006-12-04
place "" around like use this:
```

wine "/media/hda1/Program Files/Windows Media Player/wm player.exe"
```

---

### Post by Kimm on 2006-12-04
I doubt that you will get WMP10 running in wine, but if you really want to try, your best bet is to install WMP10 again in xubuntu, since it will add some system keys and libraries for sure.

Are you sure that a natice alternative like Xine or MPlayer might not be better? Look into w32codecs, using them with MPlayer you can play pretty much anything

---

### Post by crimesaucer on 2006-12-04
I tried to download from the WMP 10 page and it said I couldn't because of my OS. 

I'm still a newb too, and this is the first time I've tried to use wine. I just am trying to see if I can load my iRiver without having to change OS.

I'm wondering if I could just drag and drop the /wm player.exe into the correct .wine folder from my /media/hda1/Program Files/Windows Media Player/ folder.

And I learned from a post below that "\" is for spaces in terminal, so don't worry about that.

Also, maybe this isn't the correct way to start a program in wine: 

wine /media/hda1/Program\Files/Windows\Media\Player/wm\player.exe

...if someone knows the correct terminal procedure, then please tell me. 

Thanks.

---

### Post by crimesaucer on 2006-12-04
Thanks, I have all of the codecs already and use Listen Music Player and Beep Media Player as well as ui-xine movie player, I just happen to have the worst mp3 device possible that only interfaces to sync with WMP 10.

So I either have to use my windows partition or try to do it with wine (my first attempt), and I'd prefer to not shut my xubuntu system down to reboot Windows Xp, just to change my iRiver's music.

***edit***Also the quotes didn't work:

blah@blah-blah:~$ wine /media/hda1/Program\Files/Windows\Media\Player/wm\player.exe
wine: cannot find '/media/hda1/ProgramFiles/WindowsMediaPlayer/wmplayer.exe'
blah@blah-blah:~$ wine /media/hda1/Program\Files/Windows\Media\Player/wm\player.exe/
wine: cannot find '/media/hda1/ProgramFiles/WindowsMediaPlayer/wmplayer.exe/'
blah@blah-blah:~$ wine "/media/hda1/Program\Files/Windows\Media\Player/wm\player.exe"
wine: cannot find '/media/hda1/Program\Files/Windows\Media\Player/wm\player.exe'
blah@blah-blah:~$

---

### Post by tbroderick on 2006-12-04
You can convert your T30 from MTP (requires WMP) to UMS (mounts as USB drive in Linux). Try here;

[http://mtp-ums.net/](http://mtp-ums.net/)

---

### Post by tbroderick on 2006-12-04
> **crimesaucer said:**
> 
wine /media/hda1/Program Files/Windows Media Player/wm player.exe

and if that is what I'm supposed to write, then how do I represent a "space" when writing in terminal?

Thanks for any info,
-c.

Spaces are "\ ", so wine /media/hda1/Program\ Files/Windows\ Media\ Player/

or you can just hit the Tab key for auto-completion.

---

### Post by crimesaucer on 2006-12-04
Thanks tbroderick, so if my iRiver is updated to 1.71, then I should be able to use linux to load music?***edit***ok, I re-read that page, and I see that I would have to download their version of the ums music library (the iriver plus 2 version 2.4.1.0), to work with the 1.71 firmware I already have. Cool, now I don't have to use wine at all. Thank you.

and pressing tab will insert "\" into the blank spaces in a terminal code? So write the code then press "tab" then "enter"?

---

### Post by kakalaky on 2006-12-04
WMP just puts the music in a folder called MY_MUSIC on the device.  You can just copy the music files you want there and it should work.

---

### Post by crimesaucer on 2006-12-04
Actually when re-reading it again, I saw that it said (2nd down) that iRiver devices that came with the WMP 10 install CD (like mine), can not use the iRiver plus2 music library. So back to the wine question.

-.This is iriver plus 2 version 2.4.1.0 for UMS T Series(T10/T20/T30), H10 Jr., U10, N11, N12, E10.
-. If your product came with Windows Media Player, your device can not work with iriver plus 2.
-. You have to register your product to download iriver plus 2.
-. You can download user manual or refer to online Help of iriver plus 2.
-. iriver plus 2 is a software that efficiently manages the music files in PC and provides the convenient user interface for using the connected portable player. The functions for efficient management of music files and portable player are as below.

---

### Post by tbroderick on 2006-12-04
> **crimesaucer said:**
> Actually when re-reading it again, I saw that it said (2nd down) that iRiver devices that came with the WMP 10 install CD (like mine), can not use the iRiver plus2 music library. So back to the wine question.


I don't think you need Plus2 all you need is the first link. Your firmware should be able to switch from MTP to UMS.

[http://www.iriver.com/html/support/faq/sufq_view.asp?idx=387](http://www.iriver.com/html/support/faq/sufq_view.asp?idx=387)

---

### Post by crimesaucer on 2006-12-04
I'm pretty sure it said that the 1.70 ums and 1.71 ums firmwares worked with iRiverplus2, but if I owned the iRiver that came with the WMP 10 CD (which I do), then my 1.71 mtp firmware would not be able to be used as ums. 

I think it's only iRiver T30's that come with the iRiverplus2 CD that are able to use both mtp and ums.

***edit*** I  clicked that first link and I'll give it a try to see if it will work with mine. Worst possible thing is that I'll have to resync my device.

Yeh, it seems to have worked, it's actually really simple, now to try the plus2.

---

### Post by tbroderick on 2006-12-04
> **crimesaucer said:**
> 
Yeh, it seems to have worked, it's actually really simple, now to try the plus2.

Once you switch it to UMS, Ubuntu/Linux should recognize it when you plug it in and automount it.. You can then use any file manager to drag songs to it.

---

### Post by crimesaucer on 2006-12-04
When you say automount, how does it let you select music.

---

### Post by crimesaucer on 2006-12-04
Yes, that was VERY simple, a usb icon appears on my desktop which opens up an iRiver file, I created a folder called Music, and then drag and droped mp3's and ogg files into it from my my /home/blah/ripped music folder and it worked. Thanks, now I don't need any WMP 10/11 or iRiver plus 2 music jukebox/library programs.

It may of been a little slower syncing, but it sure beats having to shut down xubuntu to open up the Windows Xp partition to sync with MP10.

Thanks for the help.

A new question, will I be able to sync my device using terminal code to select songs and file?

---

