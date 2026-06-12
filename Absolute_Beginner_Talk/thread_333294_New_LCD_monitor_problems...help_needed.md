---
title: "New LCD monitor problems...help needed"
date: 2007-01-07
forum: Absolute Beginner Talk
---

### Post by nite owl on 2007-01-07
Hi I've just recently(Today) purchased a new 19" LCD monitor for my computer with both the VGA and DVI inputs. I first had it in VGA mode and everything was working fine(resolution was running at 1280 X 1024, and was at 75HZ). Then I connected the DVI connection(which I thought was supposed to be better quality), It's only giving me a top resolution of 1024 X 768, running at 60HZ??????. Isn't DVi supposed to be better then a normal connection? Or is this a flaw in Dapper?. Also since it is Digital does it take up CPU time?? Thanks guys :)

---

### Post by gh0st on 2007-01-07
> **nite owl said:**
> Hi I've just recently(Today) purchased a new 19" LCD monitor for my computer with both the VGA and DVI inputs. I first had it in VGA mode and everything was working fine(resolution was running at 1280 X 1024, and was at 75HZ). Then I connected the DVI connection(which I thought was supposed to be better quality), It's only giving me a top resolution of 1024 X 768, running at 60HZ??????. Isn't DVi supposed to be better then a normal connection? Or is this a flaw in Dapper?. Also since it is Digital does it take up CPU time?? Thanks guys :)

What graphics card are you using? I have a 19" widescreen TFT and I use an NVidia Geforce 5600FX with it. I don't think using a DVI connection would add any load to your CPU, your graphics card should deal with any graphical rendering tasks I would have thought, even if you use an integrated graphics card. I'm no expert so maybe someone will correct me on that but I'm pretty sure thats the case.

I think your graphics card is the most important factor here. Can you let me know what it is and I'll see if I can help?

---

### Post by teaker1s on 2007-01-07
sudo dpkg-reconfigure xserver-xorg

secondly you will need to manually edit xorg file as I know you need modeline

look at this
[http://ubuntuforums.org/showthread.php?t=719&highlight=modeline]("http://ubuntuforums.org/showthread.php?t=719&highlight=modeline")

---

### Post by nite owl on 2007-01-07
My graphics gard is an NVIDIA GEFORCE 6600 GT...i have not yet installed the driver for it.  What is modeline?. But am I right in that DVI is better?..Is all this trouble worth it? or would I be betta just staying with the normal connection?(VGA at 1280 X 1024, 75HZ)

---

### Post by gh0st on 2007-01-07
> **nite owl said:**
> My graphics gard is an NVIDIA GEFORCE 6600 GT...i have not yet installed the driver for it.  What is modeline?. But am I right in that DVI is better?..Is all this trouble worth it? or would I be betta just staying with the normal connection?(VGA at 1280 X 1024, 75HZ)

Right ok, you might want to install the Nvidia drivers from Automatix for your card. It certainly let me use resolutions I couldn't access without a proper 3D driver, you can install the drivers in other ways but I found this the easiest, I also installed Google Earth with it at the same time to check out my 3D rendering. This is the place to go for automatix [http://www.getautomatix.com/](http://www.getautomatix.com/) it makes installing all kinds of software that doesn't come with Ubuntu easy.

Can't help you with the modeline thing sorry, I expect whoever suggested it will help out with that. 

As for DVI quality I think it's a matter of opinion. I use VGA at the moment but we have another machine in the house using DVI on a TFT monitor and I can't see much difference to be honest, maybe I need an eye test or something though :) 

Give it a try by all means but I didn't see much advantage to DVI personally, I'm sure other people will correct me here saying how great DVI is but I'm perfectly happy with VGA. It's your choice at the end of the day.

Hope that helps in some way.

---

### Post by nite owl on 2007-01-07
Hi thanks alot everyone and gh0st thats exactly what I needed to hear, I'll probably just abandon this whole exercise :)

---

### Post by gh0st on 2007-01-07
> **nite owl said:**
> Hi thanks alot everyone and gh0st thats exactly what I needed to hear, I'll probably just abandon this whole exercise :)

No problem. Glad to be of service :D 

You should really install a 3D driver to get most out or your card though even if you forget about DVI. Unless you don't plan to use any 3D applications or games in which case you can probably just forget the whole thing as you said.

---

