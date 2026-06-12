---
title: "WINE, STEAM, GNOME PANEL fullscreen"
date: 2007-06-01
forum: Absolute Beginner Talk
---

### Post by chris062689 on 2007-06-01
Whenever I go into a game in Steam, such as Counter Strike, Half Life 2, etc. it does not cover the GNOME panels, and throws the alignment of the window up (with the GNOME panel up, I can't see my Health at the bottom of the screen) and I have to readjust the VIDEO size (after I hide the panels) for it to fix itself.

Is there an easier way?

---

### Post by daimaru on 2007-06-02
dont know an answer to your question but i also got steam and counterstrike source is my favorite game. is it actually playable through wine ?

---

### Post by chris062689 on 2007-06-02
Yeah.  With my computer atleast, all I had to do was install WINE and drop Tahoma.tff in /home/chris062689/.wine/drive_c/windows/fonts, and it runs like a DREAM!
No grahpical glitches from what I can tell, and the ONLY problem is that I can't really use the microphone, because it beeps.  (don't know what the problem is with that!)

It runs at a GREAT framerate too (even with all of the grahpics pumped up to full)
I don't even notice a slowdown at all!  Prehaps even a speedup!

I couldn't be happier with WINE's preformance and Steam.
* This applices for Half Life 2, Lost Coast, etc.

---

### Post by Chris S. on 2007-06-02
Are you running Beryl, Compiz, or something similar?  I had the same problem with Starcraft and Wine, and it's supposedly an issue with Beryl and fullscreen windows in my case, so I switch to Metacity before running fullscreen apps with Wine now (that and the performance increase).  With Metacity, the Gnome panels are properly covered.

---

### Post by daimaru on 2007-06-02
> **chris062689 said:**
> Yeah.  With my computer atleast, all I had to do was install WINE and drop Tahoma.tff in /home/chris062689/.wine/drive_c/windows/fonts, and it runs like a DREAM!
No grahpical glitches from what I can tell, and the ONLY problem is that I can't really use the microphone, because it beeps.  (don't know what the problem is with that!)

It runs at a GREAT framerate too (even with all of the grahpics pumped up to full)
I don't even notice a slowdown at all!  Prehaps even a speedup!

I couldn't be happier with WINE's preformance and Steam.
* This applices for Half Life 2, Lost Coast, etc.

wow chris this is actually getting me interested because i never tried it before, since i thought well it wont work anyway or at least there wont be and performance so it will be unplayable. 
did you just wine steaminstaller.exe 
and that was it for getting steam to install?

---

### Post by daimaru on 2007-06-02
by the way can i copy my steamapps folder from windose to my wine dir so i dont have to download the whole conterstike halflife 2 stuff again?

---

### Post by daimaru on 2007-06-02
lol another question . how did you get the SteamInstall.msi to run under wine? 
tried in console wine SteamInstall.msi 
gives me an error.

edit: never mind found the solution
 ```
wine msiexec /i SteamInstall.msi
```

---

### Post by daimaru on 2007-06-02
ok i got steam installed and got counterstrike running, but .. even as i start steam it says your system does not meet hardeare requirements etc. game itself is unplayable..... chop chop damn. did you install some drivers (graphics) within wine ? i got an ati card downloaded  winxp drivers for radeon x800 but as i guessed they won t install get the message that they need to be run in admin mode ... well was far fetched anyway. 
but how did you get ur steam and css to run smoothly ???

---

### Post by chris062689 on 2007-06-02
I have a Nvida graphics card, so I didn't have any problems.
sorry about your luck.

Is there anyway to fix this without switching from metacity to beryl eachtime?

---

### Post by Chris S. on 2007-06-02
You should be switching from Beryl to Metacity, I believe.  Was that a typo?

If Beryl is what's causing the problems: There is supposed to be an option under Beryl's Settings Manager that should solve this problem (so I've heard).  The closest thing I've found is General Options->Main->Advanced->"Enable workarounds for certain Wine and legacy windows".

I never tried it because it mentions "unwanted behavior" about something or other, and I don't mind the switching.  Really, I just right click on the Beryl icon and select Metacity windows manager before starting a game, then switch back when I'm done.  It only takes about a second for the switch.

If you aren't using Beryl or other desktop effects, then this may not apply to you.

Edit: Oh, setting your panels to autohide is also supposed to help, but I hate that setting.  If that's alright by you, you could try it.

---

### Post by macabro22 on 2007-06-03
Yeah, I also have the pannel issue when Beryl is running.

One graphical glitch I have with CS:S is some objects glowing like if lighted up by a flash. It's very annoying. Does anyone else have that?

---

### Post by chris062689 on 2007-06-03
> **Chris S. said:**
> 
If Beryl is what's causing the problems: There is supposed to be an option under Beryl's Settings Manager that should solve this problem (so I've heard).  The closest thing I've found is General Options->Main->Advanced->"Enable workarounds for certain Wine and legacy windows".


Yes! This works great!  Thank you very much.

---

### Post by chuckyp on 2007-07-05
Has anyone found this option in compiz fusion settings manager?

---

### Post by chuckyp on 2007-07-06
I've played around with most of the settings I must be missing it somewhere?

---

### Post by moredhel on 2007-07-06
wine applications in general don't play nicely with compiz fusion in general :( full-screen ones that is.

---

