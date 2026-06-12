---
title: "Poser 7"
date: 2007-07-19
forum: Art &amp; Design
---

### Post by steevols on 2007-07-19
Just a heads up...

Poser 7 works fine in Linux! I installed it in Windows, booted to Ubuntu, and ran "wine Poser.exe". After installing the MS Core fonts pack from somewhere I can't remember, Poser ran like a top!

I'm on a 7.04 FF box with Compiz Fusion and an older NVidia card.:guitar:

---

### Post by Cannaregio on 2007-10-01
I have installed it as well, and I'm happy, because it renders _very_ quickly (twice as quickly as in windows, in fact), but I have some mysterious "missing parts" in the posing room, before rendering (a forearm missing, a trasparent cheek, that kind of things). D'you have similar problems?
What's your graphic card?

---

### Post by steevols on 2007-10-04
I have a GeForce MX400 laptop card.

I had the same problem, but I was able to fix it by setting WINE to run in virtual-desktop mode (winecfg in CLI).

---

### Post by Cannaregio on 2007-10-05
I have a NVIDIA 6200 SE
Solved with my recent Gutsy update (even if still in beta) after having installed the new NVIDIA drivers 100.14.19. (both nvidia proprietary and glx-nvidia)
Now it render ultraquick and it poses ultraquick.
I am a happy poser :-)

It will probably work in feisty as well if you update the NVIDIA drivers.

---

### Post by rayera on 2007-10-07
Please could you be more exact in the precedure, I'm a beginner in this and nothing works for me, I instaled Poser 5 in ubuntu with wine but doesn't work, uninstall doesn't work to try other versions of poser, please help.

---

### Post by Cannaregio on 2007-10-08
Well.
First of all you have to have a good graphic setting (space enough on your screen to have your wine windows "big enough" inside it, otherwise you'll have overlapping items).
Is your graphic card working perfectly with ubuntu? D'you have enough RAM?
I have for instance a nvidia 6200 with a 1400*1050 layout and 2 giga RAM available.
open glx is working, and compiz is working, all fancy effects in Gutsy work.

if  your card is up and running and you have the last wine version and the last linux kernel (either update to gutsy beta now, or wait 10 days and update to the release soon)...
...there's nothing complicated: usual wine procedure:

Insert your poser 7 dvd
Navigate to it
Install everything rightclicking and using wine, as you would do in windows
everything will appear inside your wine's virtual c drive
([COLOR="Red"]/home/your_user_name/.wine/drive_c/Program Files/e frontier/Poser 7[/COLOR])
now launch with [COLOR="Blue"]wine Poser exe[/COLOR]

Do not forget, however to launch _first_ [COLOR="Blue"]winecfg[/COLOR] and in the tab 'graphics' DO give all your appications the more space you can: choose "[COLOR="Blue"]emulate a virtual disktop[/COLOR]" and  a resolution of _at least _ [COLOR="#0000ff"]1280*960[/COLOR], for instance.

That's it. I didn't have any problems.
You'll be amazed by the rendering speed vis-à-vis windows


PS:
Uninstalling programs, in wine, is simply a matter of going to the relevant folder (inside your .wine folder) and [COLOR="Blue"]rm -rf[/COLOR] the subfolder you don't want any more.

---

### Post by menschtx on 2008-05-19
I followed your instructions about installing wine, tried to install Poser 7.exe and received this error: Cannot open /home/michael/CD_Root/AutoPlay/Docs/Install Poser 7.exe: No application suitable for automatic installation is available for handling this kind of file. 
I got the Poser 7 from a download.
What's next?

---

### Post by menschtx on 2008-06-02
any idea why the character screen would be black?

---

### Post by Cannaregio on 2008-07-04
First this point:

> **menschtx said:**
> I followed your instructions about installing wine, tried to install Poser 7.exe and received this error: Cannot open /home/michael/CD_Root/AutoPlay/Docs/Install Poser 7.exe: No application suitable for automatic installation is available for handling this kind of file. 
I got the Poser 7 from a download.
What's next?


You navigate to the iso of poser7 and run 
```
wine autorun.exe
```
you do not run [COLOR="Blue"]wine setup[/COLOR] directly

---

### Post by Cannaregio on 2008-07-04
Then this point:

> **menschtx said:**
> any idea why the character screen would be black?

No idea.
The recent hardy kernel may have been the culprit.
Can only confirm that with 
```
Linux me_box 2.6.24-19-generic #1 SMP Wed Jun 4 16:35:01 UTC 2008 i686 GNU/Linux

and

wine-0.9.59

```
I have the same stopper: black poser screen and graphic problems.
Older versions and kernel run fine (in fact better than windows), see above.
Why? Beats me.

Content update does not run either.

If anyone finds a solution PLEASE do post here.
Until then, I'll stick with a special box, extra for poser, with [COLOR="Blue"]feisty[/COLOR] or [COLOR="#0000ff"]gutsy[/COLOR] on it, instead of [COLOR="#0000ff"]hardy[/COLOR].
The rendering speed vis-à-vis windows is simply fantastic and worth the hassle of keeping a box "back" to older (yet for poser better) GNU/Linux versions.

All the zillion commercial models/poses/props, now floating for free on the web everywhere, deserve and beg a box on their own anyway :-)

---

### Post by menschtx on 2008-07-05
Cannaregio, 

Thank you for your response, I will endevor to follow your suggestions and get back to you. 

Now when you speak of iso < your speaking of Operating System Interfacing?

---

### Post by Cannaregio on 2008-07-06
> **menschtx said:**
> Cannaregio, 

Thank you for your response, I will endevor to follow your suggestions and get back to you. 

Now when you speak of iso < your speaking of Operating System Interfacing?

Nope, I am speaking of the [ISO IMAGE]("http://en.wikipedia.org/wiki/ISO_image") of the poser 7 CD.
In fact there's never any need to use "real" CDs or DVDs to run any program: you rip or create the program's CD or DVD iso image, and use that instead. No scratches, no hassles and if you should need a "no cd" or "no dvd" crack (for those programs that require a physical CD or dvd in the drive slot) you can easily find that on the web as well.

Lemme know if you or anyone else find a solution for our worries.

---

### Post by adm91 on 2009-05-13
hey, i just got the program poser 7 and everything works great except for the fact that i don't know how to load a different character besides SimonG2. I kno for a fact that there are many other characters and i have seen them in the program's folder's but there is no option whatsoever for me to choose another character, such as SydneyG2. Help is greatly appreciated.

---

