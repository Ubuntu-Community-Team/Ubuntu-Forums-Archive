---
title: "Installing Ubuntu Studio Over Ubuntu"
date: 2008-01-29
forum: Absolute Beginner Talk
---

### Post by Wayne_T3 on 2008-01-29
Hey there, gang; yep, I'm a noob, and I'd like to know if I can install Ubuntu Studio over an existing copy of just plain Ubuntu without losing any pictures, videos or documents I already have on the hard drive. Thanks in advance for your atention, and I think Ubuntu is unbelievable....!

---

### Post by iansane on 2008-01-29
I installed the packages from synaptic several months ago when the fiesty version was out. As soon as I rebooted I had to use command line to reconfigure my x server. Apparently the config I had didn't work with the modified low latencey kernel. As far as I remember all my files were still there once I got a desktop back. Might want to make sure you know how to do that before you install it. Just search synaptic for ubuntu studio

---

### Post by ctswhole on 2008-01-29
Yes.  You can go into Synaptic and just click on the ubuntu studio packages, and they will all install on your system, essentially giving you Ubuntu Studio without the loss of any of your files.  Word or warning though, I didn't like the new kernel that was installed with it; I ended up editing my grub file to automatically choose my old kernel instead.

---

### Post by CFBauer on 2008-01-29
I'm interested in doing this as well.  May I ask (as a beginner) what was wrong with the kernel?

---

### Post by ctswhole on 2008-01-29
> **CFBauer said:**
> I'm interested in doing this as well.  May I ask (as a beginner) what was wrong with the kernel?

When I installed Ubuntu Studio through Synaptic it put in a kernel (I forget the number) with the RT extension.  RT meant "Real Time" I believe, but don't quote me on that.  What that kernel did was make my computer hang on boot up.  It got to a point and would just stop, but if I hit "enter", the boot sequence would continue and then all was back to normal.  I don't really know if anything else was affected by this different kernel, I just remember this quirk from the boot up sequence.  Hopefully someone a bit more knowledgeable in kernel matters could add to this, I was just aware of the hang in booting up.

---

### Post by epidemiks on 2008-01-29
I'm about to do this too.. didn't see anything about a different kernel in the synaptic descriptions.. fingers crossed all will be well..
in case is doesn't work out, how do I reverse the process or reconfigure x?

---

### Post by iansane on 2008-01-30
I'm pretty sure the command is 
dpkg-reconfigure xserver-xorg

this will give you a chance to tell the xserver all about your graphics, monitor, keyboard, mouse, etc.

This has to be done from a command line screen. Hopefully you won't have that problem but be prepaired. If it doesn't work you can keep going through it till you get it right but it's a little complicated to me. I think the main thing is your video card type. Don't really know why I had that problem.

---

### Post by ctswhole on 2008-01-30
> **epidemiks said:**
> I'm about to do this too.. didn't see anything about a different kernel in the synaptic descriptions.. fingers crossed all will be well..
in case is doesn't work out, how do I reverse the process or reconfigure x?

I didn't have such a problem where I considered reversing the process.  After I installed all the Ubuntu Studio packages from Synaptic, I rebooted to see what booting into this "new" OS would be like.  At the start of the boot process I was given 4 options of what to boot into:
[LIST=1]
[*]RT kernel (default choice)
[*]RT kernel safe
[*]Original kernel
[*]Original kernel safe
[/LIST]

I went with the RT kernel, as that was what was installed when I put in the Studio stuff.  That's when I noticed the hang when it booted up.  After getting through the boot process, I rebooted and this time chose my original kernel.  No problems whatsoever, and all Studio programs worked just like they did in the RT kernel.  So I edited my grub file to place my original kernel as the default kernel to boot into, and I've never had any problems.  Hope this helps you in your decision.

---

### Post by CFBauer on 2008-01-30
Rosegarden crashes due to a lower resolution kernel, as far as i can tll, which is my main reason for trying Ubuntu Studio. Hopefully your issue ctswhole won't happen for me!

---

### Post by epidemiks on 2008-01-30
> **ctswhole said:**
> I didn't have such a problem where I considered reversing the process.  After I installed all the Ubuntu Studio packages from Synaptic, I rebooted to see what booting into this "new" OS would be like.  At the start of the boot process I was given 4 options of what to boot into:
[LIST=1]
[*]RT kernel (default choice)
[*]RT kernel safe
[*]Original kernel
[*]Original kernel safe
[/LIST]

I went with the RT kernel, as that was what was installed when I put in the Studio stuff.  That's when I noticed the hang when it booted up.  After getting through the boot process, I rebooted and this time chose my original kernel.  No problems whatsoever, and all Studio programs worked just like they did in the RT kernel.  So I edited my grub file to place my original kernel as the default kernel to boot into, and I've never had any problems.  Hope this helps you in your decision.

ah, gotcha. too easy then. *rubs hands in anticipation*

---

### Post by gammakrikit on 2008-01-30
well, this is how I did it the first time, & it didn't seem to give me too much trouble... [https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy]("https://help.ubuntu.com/community/UbuntuStudio/UpgradingFromGutsy")

---

### Post by wolfius on 2008-01-31
Well I just did it today, rebooted and mi GRUB showed exactly as you guys said above.

I entered with the default option (RT kernel) and had no trouble while loading. I logged in finem but!... my wireless is missing.

I had to go out so didint stick around to figure out what happened (also im kinda a n00b) so right now I'm writting this just in case someone knows what could have happened or if someone had the same problem.

Ill try to figure it out tomorrow.

---

### Post by ctswhole on 2008-01-31
> **wolfius said:**
> Well I just did it today, rebooted and mi GRUB showed exactly as you guys said above.

I entered with the default option (RT kernel) and had no trouble while loading. I logged in finem but!... my wireless is missing.

I had to go out so didint stick around to figure out what happened (also im kinda a n00b) so right now I'm writting this just in case someone knows what could have happened or if someone had the same problem.

Ill try to figure it out tomorrow.

You might want to try booting with your original kernel one time to see what happens.  My hunch says your wireless will be back, and all your new programs should be fine.  If you try this and everything works ok for you, then your wireless issue would be solved.:)

---

### Post by wolfius on 2008-01-31
Okay I booted with the original kernel and first all I got was a gnome error and my desktop all f*ed up... but I had wireless! yay! hehe then i botted again with the RT kernel and the same... eberything was fine and looking good but no wireless, as if i didnt even had a wifi card installed. Then again, not giving up on this, i booted with the original kernel... the loading screen was the normal ubuntu screen, but then log in screen was fine, then i logged in and everyhting was also fine, no error, ubuntu studio theme, all the applications installed.. etc.. oh! and WiFi! :D

thanks!

---

### Post by epidemiks on 2008-01-31
No problems here.. booted up fine without any problems - took a little longer maybe..

everything seems fine, although I just noticed Rhythmbox just abruptly shut itself down..

otherwise happyness!

---

