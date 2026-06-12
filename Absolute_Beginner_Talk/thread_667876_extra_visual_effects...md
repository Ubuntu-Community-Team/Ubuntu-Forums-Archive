---
title: "extra visual effects.."
date: 2008-01-14
forum: Absolute Beginner Talk
---

### Post by jatiesch on 2008-01-14
hi i love using extra visual effects on my ubuntu system but i m facing a problem here...

1) some components like terminal, volume indicator are washed out white when used/run 
2) no close, minimize options at corner in a window...

plz help....
thanks

---

### Post by nikoPSK on 2008-01-14
Can I have a screenshot please?

---

### Post by jatiesch on 2008-01-14
hi thanks for interest shown...
this is the snapshot( attachment)

white window behind is terminal window...

---

### Post by nikoPSK on 2008-01-14
Most likely your theme is messed up. Try applying the human theme and see if the close buttons and such are working again.

Best,
nikoPSK

---

### Post by overdrank on 2008-01-14
> **jatiesch said:**
> hi i love using extra visual effects on my ubuntu system but i m facing a problem here...

1) some components like terminal, volume indicator are washed out white when used/run 
2) no close, minimize options at corner in a window...

plz help....
thanks

HI and by chance are you using a nvidia graphics card and if so what model?
Edit and Please don't make multiple threads on the same topic
[http://ubuntuforums.org/showthread.php?t=667877](http://ubuntuforums.org/showthread.php?t=667877)
:(

---

### Post by nikoPSK on 2008-01-14
> **overdrank said:**
> HI and by chance are you using a nvidia graphics card and if so what model?
Edit and Please don't make multiple threads on the same topic
[http://ubuntuforums.org/showthread.php?t=667877](http://ubuntuforums.org/showthread.php?t=667877)
:(

most likely an accidental double post.

---

### Post by RomeReactor on 2008-01-14
Hi. jatiesch, what video card do you have? please press ALT+F2 and post the output of:
```
gedit /etc/X11/xorg.conf
```
Note: To close a window without using the "X" (close) button, press ALT+F4.
Also try running this by pressing ALT+F2:
```
gtk-window-decorator --replace
```
If this brings the window borders back, you need to add the comand in CompizConfig-Settings-Manager to keep the changes. If you don't have CompizConfig-Settings-Manager installed, run:
```
sudo apt-get install compizconfig-settings-manager
```
After it's installed, go to 'System->Preferences->Advanced Desktop Effects Settings'; there, press the "Window Decoration" button and on the "Command" section enter:
```
gtk-window-decorator --replace
```

Hope this helps.

---

### Post by FenderGuy2112 on 2008-01-14
Beryl is cool for effects....

---

### Post by nikoPSK on 2008-01-14
> **FenderGuy2112 said:**
> Beryl is cool for effects....

compiz fusion is the new merger of beryl and compiz

---

### Post by limac on 2008-01-14
is compiz enabled? if yes, is windows decoration enabled? install compizconfig-settings (something like that) thriu synaptic and enable windows decoration. should work! :D

---

### Post by SOULRiDER on 2008-01-14
What kind of video card do you ahve, i think problems like this can appear with ATI cards.

---

### Post by jatiesch on 2008-01-15
hi thanks to all ppl...
hi i have nvidia geforce 6100 graphic card...
i dont have compiz etc installed
and problem has nothing to do with theme...same error occurs with human theme...

---

### Post by nikoPSK on 2008-01-15
that is very odd, no ATI either....

---

### Post by sailor2001 on 2008-01-15
alt/f2  and type ' metacity --replace '    ...... if that doesn't work. home ctrl/h and find gnome or gnome 2 and remove config then ctrl/alt backspace to set new config  .. someone correct me if I'm wrong, please

---

### Post by Jelmoh on 2008-01-15
If I get this right, you like visual details?
I had the exact same thing with Beryl, please don't install this, uninstall...
And replace with Compiz  (Package manager, search for compiz)
You should install:
Compiz
Compiz-Settings-Manager
Emerald

These 3 packages make for excellent visual effects and work fine for Nvidia! :)
With me, I might add... I've got a 8800GTS 640, so that might just do the trick for me...
But as I said earlier, the Beryl thing screwed up my system just like your system is screwed up now...
Uninstalling Beryl and installing those packages did the job for me..

Once again, great visuals!  No need of a superb GraphicsCard! :)

---

### Post by nikoPSK on 2008-01-15
Ah, so it's beryl... I misunderstood... :oops: well, fusion is very nice.

nikoPSK

---

### Post by nikoPSK on 2008-01-15
> **nikoPSK said:**
> Ah, so it's beryl... I misunderstood... :oops: well, fusion is very nice.

nikoPSK

thought you were using compiz... :|

---

### Post by Jelmoh on 2008-01-16
> **nikoPSK said:**
> Ah, so it's beryl... I misunderstood... :oops: well, fusion is very nice.

nikoPSK


If you think he uses beryl because of my post don't do that.. :P
But I had the same symptoms when I installed Beryl, so I presumed he is using Beryl! ;)
He could as well use Compiz, but I don't know really... Didn't read it in any of the posts so..

---

### Post by ian2000gsxr on 2008-01-16
> **sailor2001 said:**
> alt/f2  and type ' metacity --replace '    ...... if that doesn't work. home ctrl/h and find gnome or gnome 2 and remove config then ctrl/alt backspace to set new config  .. someone correct me if I'm wrong, please

hey this fixed the problem for me.  thanks a lot!

edit:  actually now that I switched themes it happened again, weird

---

### Post by ian2000gsxr on 2008-01-16
the problem re appears when after typing metacity --replace i go into system>pref>appearace and set visual effects to either normal or extra

---

### Post by nikoPSK on 2008-01-16
> **Jelmoh said:**
> If you think he uses beryl because of my post don't do that.. :P
But I had the same symptoms when I installed Beryl, so I presumed he is using Beryl! ;)
He could as well use Compiz, but I don't know really... Didn't read it in any of the posts so..

okay, misunderstood again... :lolflag:

---

