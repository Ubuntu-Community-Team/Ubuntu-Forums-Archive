---
title: "Graphics card questions, X3100 &amp; 9600GT"
date: 2008-02-23
forum: Absolute Beginner Talk
---

### Post by norfair on 2008-02-23
I'm sorry for posting such a newbie-ish question, but that's what I am! Anyway, I am looking to buy a desktop with Ubuntu as the sole operating system. The system comes with an Intel graphics chip, the X3100. The only upgrades from that are within the Nvidia 8000 series (which I've heard aren't grand). So, I thought I'd stick with the X3100 for a bit and get comfortable with Ubuntu and upgrade from there.

However, there are some things I'm not clear on. First, I really want to be able to run Compiz-Fusion, but I've read that the X3100 is black listed and the two can't coexist. Is this still true? I've searched the boards here and other places, and am getting conflicting answers. I wondered if the situation has improved. I would plan to upgrade the graphics card to the new Nvidia 9600 GT in time, which then brings me to my second question. If I bought the card from NewEgg and popped it into my new system, would it work right off the bat? I checked Nvidia's site, and while it lists Linux in a generic sort of way, I don't see any drivers for it on their site. I've installed things into a computer before, but only in Windows PCs. Also (and here's the part that'll really exemplify my stupidity), if I get the 9600 GT and it works, Compiz-Fusion would then work so long as I set it as my primary video card thereby bypassing the X3100, correct? 

Whew. Sorry for all that. Can anyone shed light on my predicament of sorts?

---

### Post by A4006 on 2008-02-23
I'd go for the 8000 series GPU.  They're great cards, I have a 8500 at the moment, thinking of upgrading to a 9800 when they come out.  I used Envy [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") to install the proper drivers, it worked like a charm, and would've stayed working if I hadn't decided to mess with it (long story).  Using Ubuntu, there's really no need for a 9000 series card, that's what you call "overkill".  Unless you plant to dual boot with Windows and play the latest DX10 games (which I do) you don't need that great of a card.  But, if you were to install a 9600 GT, it should work fine, and your Compiz settings would stay the same.  When you install a new GPU, it automatically switches to that card, bypassing the onboard video, and all you have to do is install the drivers within the OS. Hope this helps.

---

### Post by norfair on 2008-02-23
> **A4006 said:**
> I'd go for the 8000 series GPU.  They're great cards, I have a 8500 at the moment, thinking of upgrading to a 9800 when they come out.  I used Envy [http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html") to install the proper drivers, it worked like a charm, and would've stayed working if I hadn't decided to mess with it (long story).  Using Ubuntu, there's really no need for a 9000 series card, that's what you call "overkill".  Unless you plant to dual boot with Windows and play the latest DX10 games (which I do) you don't need that great of a card.  But, if you were to install a 9600 GT, it should work fine, and your Compiz settings would stay the same.  When you install a new GPU, it automatically switches to that card, bypassing the onboard video, and all you have to do is install the drivers within the OS. Hope this helps.

Thanks a bunch for your input. You were most helpful indeed. I'm glad to hear that you're happy with the 8500 card you have, as that's one of my options (along with 8400 & 8600). I know the 9600 would be more than I need, seeing as how I have no plans to dual boot (at least not yet) and the latest and greatest games aren't designed to run on Ubuntu/Linux, but I just didn't want to settle on a card. The 8500 isn't that costly of an upgrade, so maybe I'll try that? I thought about the cheapo 8400 GS too, but I've read a lot of posts saying that it's no better if not worse than integrated graphics. I don't know. Anyway, thanks again for posting your thoughts.

---

### Post by herbster on 2008-02-23
> **norfair said:**
> the Nvidia 8000 series (which I've heard aren't grand)

Ugh, you heard wrong holmes, real wrong ;)

And yeah, if you get another card and install it, it should be autodetected as the default video device by your mobo.

---

### Post by A4006 on 2008-02-23
The 8500 and 8600 are both Direct X 10 cards (with OpenGL 2.0 also).  You might want to keep DX10 in mind in case you ever dual-boot, since it would most likely be with Vista.  When I built my custom rig, I was going to use a 8600 GTS, but I was too cheap and instead I went with a 8500. However, now that the 9000 series is out, prices of other cards will drop some.

---

### Post by justsixspaces on 2008-02-24
Hey guys. I recently installed the Nvidia 9600 GT. Beautiful, beautiful piece of equipment =P.

Everything runs fine in Windows Vista. I didn't have an issue at all installing the drivers (surprisingly), but I do have an issue with Ubuntu however. 

I currently dual-boot Ubuntu 7.10 (Gutsy) with Vista SP1 RC2. I had originally had the ATI X1300 card, which worked fine with Ubuntu, but wasn't so hot on the gaming side. After I upgraded, my Ubuntu will only run Safe Graphics Mode =(. I have tried to use Envy to install the correct drivers, but there aren't any Nvidia drivers for the card on Nvidia's website, and I tried to manually install the newest version of the driver that Envy offers, but that was a big mistake. The card didn't like that, and I couldn't even see my screen. As a result, I've just finished a reinstall of Ubuntu. 

Now, my desktop is no longer stuck at 800 x 600 as it was when I originally installed the card. It's now running at 1280 x 1024, which is nice, but it's not using the full hardware acceleration that the 9600 offers, as the system is still using the VESA driver.

My question is, does anybody know of a driver that utilizes the full hardware capabilities of the 9600 GT, and if so, where I could find it? If not, does anybody know when Nvidia will release said driver, and why they haven't made one?

Any help is greatly appreciated, and thank you very much in advance.

--Mitch

---

### Post by A4006 on 2008-02-24
Interesting, I just started a thread the other day asking the exact same question [http://ubuntuforums.org/showthread.php?t=705795]("http://ubuntuforums.org/showthread.php?t=705795")
They basically told me to chill, and that drivers will come out later.  Hopefully by the time the 9800's roll out, they'll have the proper drivers available.

---

### Post by herbster on 2008-02-24
[http://www.nvidia.com/object/IO_18897.html](http://www.nvidia.com/object/IO_18897.html)

No 9xxx there yet.

---

### Post by justsixspaces on 2008-02-24
Well, thank you gentleman. I guess I'll just ride it out. 

I can't wait to check out Compiz-Fusion and see how it looks. I'm a geek for graphics =P

Anyway, thanks again. I appreciate the help.

---

### Post by theproc64 on 2008-03-11
To the guy with the nvidia driver problem, just boot into recovery mode in the grub menu and type> sudo dpkg-reconfigure xserver-xorg and select the nvidia driver when it prompts you too.  Then just reboot and it should just work fine.

---

