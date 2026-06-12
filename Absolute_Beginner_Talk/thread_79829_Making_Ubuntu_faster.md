---
title: "Making Ubuntu faster?"
date: 2005-10-20
forum: Absolute Beginner Talk
---

### Post by IvanGrozny on 2005-10-20
I'm on quite a slow computer, i believe its only 400 or 600mhz, 192mb of ram, and a very old ati rage 16mb graphics card.

I just don't like the lag im getting with gnome, is there a few settings I can alter so i can do to speed it up?

Im using Ubuntu 5.04, should I upgrade will this help out the speed performance any?

---

### Post by aysiu on 2005-10-20
Install XFCE through Synaptic Package Manager. Use that instead of Gnome.

---

### Post by Deacon Nikolai on 2005-10-20
1. Linux loved RAM, Max yourself out.
2. Breezy is faster IMO.
3. Your computer is old and slow, ssoftware cannot always change that. :KS

---

### Post by Underhill on 2005-10-20
Get Boot-Up Manager (BUM) and stop unnecessary services: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)

---

### Post by IvanGrozny on 2005-10-20
I don't see any options for XFCE in the Synaptic Package Manager, and  i did press the refresh button.

---

### Post by funkydan2 on 2005-10-20
You'll need to enable the "universe" repository.

Some people would also recommend installing 'xubuntu-desktop' which gives you XFCE4 & a few other things.  I haven't tried it myself yet (still need to upgrade to breezy) but it sounds promising for slower machines.

---

### Post by aysiu on 2005-10-20
[QUOTE=IvanGrozny]I don't see any options for XFCE in the Synaptic Package Manager, and  i did press the refresh button.[/QUOTE] I'm sorry. You actually have to enable the Universe repositories to get XFCE4. Follow these directions:

[http://www.psychocats.net/sources.html](http://www.psychocats.net/sources.html)

Then, refresh Synaptic.

---

### Post by fuscia on 2005-10-21
[QUOTE=Underhill]Get Boot-Up Manager (BUM) and stop unnecessary services: [http://www.marzocca.net/linux/bum.html](http://www.marzocca.net/linux/bum.html)[/QUOTE]

if my machine doesn't explode in the next half hour, this suggestion and switching to xubuntu are awesome.

uh-oh...what's that smoke...?

---

### Post by Perfect Storm on 2005-10-21
Bum is Availble in the universe.
```

sudo apt-get install bum
```

Drop Firefox and use Epiphany

```

sudo apt-get install epiphany-browser epiphany-extensions
```

---

### Post by patrick295767 on 2005-10-21
[QUOTE=IvanGrozny]I'm on quite a slow computer, i believe its only 400 or 600mhz, 192mb of ram, and a very old ati rage 16mb graphics card.

I just don't like the lag im getting with gnome, is there a few settings I can alter so i can do to speed it up?

Im using Ubuntu 5.04, should I upgrade will this help out the speed performance any?[/QUOTE]

for old pc: u can read that [http://www.ubuntuforums.org/showthread.php?t=64557](http://www.ubuntuforums.org/showthread.php?t=64557)

I have a 380 mhz
I tried twm and fvwm 
The best for me is fvwm ... 

Regards,

Patrick

---

### Post by patrick295767 on 2005-10-21
[http://www.ubuntuforums.org/showthread.php?t=64557&page=5](http://www.ubuntuforums.org/showthread.php?t=64557&page=5)

a little story :
---------------------------------------
Hi, 

my last new : 
I replaced twm by fvwm on my old pc :
( apt-get install fvwm )

Robert Nation created fvwm in 1993 for 33 MHZ 486 laptop PC with only 4 MB of RAM: 


"RN> There were two or three reasons for starting FVWM and RXVT. First, I had
RN> a need 33 MHZ 486 laptop PC with only 4 MB of RAM, and I thought linux and X11 were 
RN> way better than the windows versions of the day. X11 with TWM and xterm would run on 
RN> my PC, but just barely. Second, I had a need at work to analyze spectrograms which
RN> were about 4000 x 200 pixels when displayed at full resolution (analyzing acoustic 
RN> signatures for the DOD) - twm couldn't display 
RN> that, although some other window managers could (they used more memory though!). Finally,
RN> I thought it would be nice to learn a few GUI software skills.

RN> I think I did rxvt first. The source code fro xterm was pretty hard to understand,
RN> so I found xvt on the net somewhere. I cleaned it up a bit and improved its vt-100 
RN> compatibility in a few areas. Next, I tore apart twm to find out why it was so big, and
RN> generated a very simple, low memory, low-flexibility version of a window manager. I added
RN> the virtual desktop stuff and started using it at work too, since it could display my
RN> spectrograms very nicely. 

RN> After I put the these things on the net, it was fun and educational for a while, as
RN> the programs became more capable. But as my kids got a little older and needed more
RN> attention from me), and the maintenance function got to be mostly integrating patches 
RN> from various people (and the patches had little or no utility to me), the fun went
RN> away, and Chuck Hines stepped up to take over.
"


Fvwm is great !! 
(Highly customizable too)
---------------------------------------

---

### Post by patrick295767 on 2005-10-21
I quote from from [http://fvwm.lair.be/viewtopic.php?t=880](http://fvwm.lair.be/viewtopic.php?t=880) , author : taviso
Kitten (like in journals):

"Actually, twm is very slow and inefficient. It may not do much, but what it does do it does badly. An equivalent fvwm configuration would be many times faster and more efficient."

---

### Post by patrick295767 on 2005-10-21
I have a question concerning speed : is installing XDM or GDM or WDM, is it taking RAM and making slowlier the PC ... 
Is it better to start the X server (fvwm for me) via : 
tty1 :
typing : startx 
  
Who knows the solution ?
 
Thanks, 

Regards,

Patrick

---

