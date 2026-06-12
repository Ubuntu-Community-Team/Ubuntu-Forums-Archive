---
title: "Need help Badly.  X won't load"
date: 2006-01-09
forum: Absolute Beginner Talk
---

### Post by J-B on 2006-01-09
Okay, since I installed 32 bit Ubuntu, I needed to install Neverwinter Nights again.  Went through Leech's how-to in the gaming section and the install went fine.  Got an error that the graphics failed to initialize so I figured I needed to update my Nvidia drivers.  Used this:

sudo nvidia-glx-config enable

Now X won't load, and it's saying something along the lines of the Nvidia driver version doesn't match the kernel version.  I'm dual-booting (using WinXP right now), so I don't have a way to get you an exact output of the error.   Please help.

---

### Post by aysiu on 2006-01-09
[QUOTE=J-B]
sudo nvidia-glx-config enable[/QUOTE] I'm just guessing, but could it be as simple as ```
sudo nvidia-glx-config disable
```? 

Probably not. How about ```
sudo apt-get remove nvidia-glx
sudo dpkg-reconfigure xserver-xorg
```?

---

### Post by J-B on 2006-01-09
Okay got X to load, I'm back in Ubuntu.  Did the obvious thing and ran the same command with DISable at the end instead of enable.   Sometimes it takes sheer desperation to see the obvious.  

Now, how do I install the latest Nvidia drivers without fudging X again?  Here's another interesting question....My desktop is shifted to the right a bit.  Like there's a black space on the left side of my screen about a centimeter wide.  All the resize and close buttons in the upper right of my windows off screen.   What gives?

---

### Post by J-B on 2006-01-09
Lol, you beat me by like two seconds.   I truly did not think it would be that easy.

---

### Post by aysiu on 2006-01-09
[QUOTE=J-B]My desktop is shifted to the right a bit.  Like there's a black space on the left side of my screen about a centimeter wide.  All the resize and close buttons in the upper right of my windows off screen.   What gives?[/QUOTE] Usually means your refresh rate is off. If I use 60 Hz instead of 70 Hz, I get the same thing.

By the way, [this](http://ubuntuforums.org/showpost.php?p=129379&postcount=21) has just about everything you ever wanted to know about screen resolution and Ubuntu.

---

### Post by J-B on 2006-01-09
Well, holy hell.  I think I actually fixed it.   After I got X running again, I went into synaptic and totally removed all references to Nvidia.  I did a search for Nvidia and anything that came up got completely removed, config files and all.   Then I reinstalled the base Nvidia drivers, and enabled them using the command I used earlier.  Now, I get the Nvidia splash screen, it took away the annoying desktop off-center thing, and NWN actually runs.  Damn, what a turn around.  

I think, and I could be totally wrong here, that I had accidentally installed the older legacy drivers, and that screwed me up.   Whatever it was, it works now, thankfully.  Thanks for your help, man.

---

### Post by Mustard on 2006-01-09
[QUOTE=J-B]Well, holy hell.  I think I actually fixed it.   After I got X running again, I went into synaptic and totally removed all references to Nvidia.  I did a search for Nvidia and anything that came up got completely removed, config files and all.   Then I reinstalled the base Nvidia drivers, and enabled them using the command I used earlier.  Now, I get the Nvidia splash screen, it took away the annoying desktop off-center thing, and NWN actually runs.  Damn, what a turn around.  

I think, and I could be totally wrong here, that I had accidentally installed the older legacy drivers, and that screwed me up.   Whatever it was, it works now, thankfully.  Thanks for your help, man.[/QUOTE]

I would think either that or you might have missed installing the linux-restricted-modules for you kernel. :)

Glad to see you got it all fixed.

---

### Post by J-B on 2006-01-09
[QUOTE=Mustard]I would think either that or you might have missed installing the linux-restricted-modules for you kernel. :)

Glad to see you got it all fixed.[/QUOTE]


Could very well be.  I honestly don't know what I did wrong.  You know, as many times as I've screwed up since I installed Ubuntu, I have to say it really makes me excited about computers again.   I know Windows' big selling point is the fact that it caters to the lowest common denominator, and thus has great usability, but I'd gotten really tired of it.   You actually feel like you accomplished something when you don't have a wizard there to do everything for you.  I'm really digging it, despite the problems I've had.

---

### Post by Suger on 2006-01-10
Yes, it starts this way, but there is also a depressing moment : "Gosh, I set up my computer exactly like I've always wanted my computers to be and never could do with Windows. What should I do now ?"

That's the only thing I hate with *nix in general, Ubuntu in particular.

---

