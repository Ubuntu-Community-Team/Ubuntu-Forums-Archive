---
title: "Screen resolution problem"
date: 2006-03-24
forum: Absolute Beginner Talk
---

### Post by Nunyah on 2006-03-24
I'm having trouble reaching 1600x1200 resolution with my Samsung SyncMaster 193P TFT monitor.
Even though i choose only 1600x1200 as a resolution when i reconfigure xserver,  the resolution won't display in the screen resolution setting. Been trying to use different color depths as well.
This is when I use Nvidia driver.

1600x1200 works if i choose nv as driver, but then the monitor displays a warning that it dosen't support the current resolution, recommending me to use 1288x1024 in addition to letters being jacked up. Clearly the monitor dosen't want to display this resolution, but it works like a charm in Windows XP where I can install the drivers that followed with the screen..

Seems like when I choose Nvidia it activates some kind of failsafe or something that disallows me to choose higher than 1288x1024..
I've also tried to manually add the resolution in the conf file without any changes..

What can I do in order to solve this? Coding and other stuff gets kinda messy in the current resolution. :mad:

---

### Post by dcstar on 2006-03-24
[QUOTE=Nunyah]I'm having trouble reaching 1600x1200 resolution with my Samsung SyncMaster 193P TFT monitor.
.....
What can I do in order to solve this? Coding and other stuff gets kinda messy in the current resolution. :mad:[/QUOTE]
Screen res is also related to refresh rate.

If you run too high a refresh rate, you can be limited in the maximum screen res for a particular monitor - the messages you are getting are probably trying to protect you from using a combination that may damage your monitor.

Try dropping your refresh rate to 60Hz and then see if you can get a higher res, if you can then try and up the refresh rate to the highest for that res.

---

### Post by Nunyah on 2006-03-24
My thought exactly, alas I'm already running at 60 hertz. In order to make it as easy as possible for the monitor, I've also tried 65k colors (16 bit).

Been checking out that samsung site as well, dosn't seem like they support Linux in any way.. :/

Usually I'd think the monitor would be the weakest link when problems as these occurs, but it works fine in XP at 1600x1200.

---

### Post by Nunyah on 2006-03-25
Anyone able to tell me what to try in order to work this out?
As a temporary workaround, I've changed the Gedit font size to 8 in order to make all the sourcecode smaller so I can gain a better overview..

---

### Post by akiro.yamamoto on 2006-03-25
This seems a little strange because the little research I've done says that the
Max Resolution is 1280 x 1024 with a Max Sync Rate (V x H) 75Hz x 81kHz
However check [** THIS!!**](http://ubuntuforums.org/showthread.php?p=454217) may be of assistance, you can check the online ModeLine Tool
Hope this helps ;)

---

### Post by Gustav on 2006-03-25
Look at this thread: [http://ubuntuforums.org/showthread.php?t=83973](http://ubuntuforums.org/showthread.php?t=83973)

edit: argh, there is always someone faster :)

---

### Post by akiro.yamamoto on 2006-03-25
[quote=Gustav]Look at this thread: [http://ubuntuforums.org/showthread.php?t=83973]("http://ubuntuforums.org/showthread.php?t=83973")

edit: argh, there is always someone faster :)[/quote]

LOL :mrgreen:

---

### Post by Nunyah on 2006-03-25
Hehe, thanks to both of ya. :)
I'll check it out

---

### Post by Nunyah on 2006-03-25
Hmm, I can't seem to work out the HorizSync and VeriRefresh from the [spec sheet]("http://www.samsung.com/Products/Monitor/DiscontinuedModels/DI19PSQAQ.asp?page=Specifications").

[QUOTE='akiro.yamamoto']Max Resolution is 1280 x 1024 with a Max Sync Rate (V x H) 75Hz x 81kHz[/QUOTE]
My screen can't do 1600x1200? I've no trouble with that in Windows...

---

### Post by akiro.yamamoto on 2006-03-25
[quote=Samsung Website]
**Frequency**       Horiz. Rate (kHz)       30-81 (Analog)         **Frequency**       Horiz. Rate (kHz)       30-63 (Digital)                  Vert. Rate (Hz)       56-75                  Bandwidth (Mhz)       140[/quote]
From that it seems clear!!
Just use the info for your xorg.conf file, you can use the link from my previous post for a guide. Check out the Online ModeLine Generator as well....

---

### Post by akiro.yamamoto on 2006-03-25
I strongly suspect that Winblows is operating your monitor Out Of Spec....
This could shorten the life span of the monitor. You probably don't realise it but
it's possibly using a low refresh rate that can cause eye strain as well.
According to the Samsung Website the MAXIMUM Resolution is 1280 x 1024...

---

### Post by Nunyah on 2006-03-25
Hmm, I guess you're right...
Just to correct myself a little, my preferred resolution in Windows is 1288x1024, 1600x1200 gets a little to small for my taste, but if I choose to use it, it works like a charm.. Maybe you're right about maybe Windows tuning down the refresh at that resolution. I only use it when I'm checking web page prosjects etc would look like in that resolution, so I haven't really experimented by reading texts etc that mode.

Why I wanted 1600x1200 in Ubuntu is because it seems like a lot of the objects are of greater size than in Windows. Like desktop icons, default text size etc..
But tuning these down a couple of notches might do the trick if my screen won't support higher resolution..

Thanks for your help in this, akiro.yamamoto. Appreaciate it!

---

### Post by akiro.yamamoto on 2006-03-25
You can change the zoom level of the Icons and change the default Font size....
That may help. I know that gedit for example uses a font of 12 and thats just a little tooo much for me :)
Post back with any other questions......

---

