---
title: "XFree86 problems"
date: 2006-07-23
forum: Absolute Beginner Talk
---

### Post by Josh_b on 2006-07-23
Hey,

I just installed Ubuntu (warty warthog). The install went fine. But when I boot it up, it can't load XFree86 at the login screen (in command line).

I searched the net (on my Windows partition, I did not configure Linux for network during set-up) and found a site telling me to type in; sudo XFree86 -configure. I do that and it appears with an error message about not being able to load shared library for Glide: "libglide2x.so". It then states I need to make a soft link to the library for Xfree86 in /usr/X11R6/lib/modules.

There are a few more errors says failed to load module 'glide'(a required submodule could not be loaded,2), XFree86 is not able to detect mouse and to run a test server, type XFree86 -xf86config /home/josh/XF86Config.new. So I do that with the sudo command.

The screen goes blank and a monitor messae appears with an error about the sync. It then goes back to the command line, with a heap of errors stating about no symbols found and could not open device /dev/mouse.

It also created a log file in /var/log/Xfree86.0.log

So, my question is, why isn't it working, and how do I get it working?

Appreciate any help,
Josh

---

### Post by philippe_carlo on 2006-07-23
First off, you'd be better of posting this at the Warthog forum, I think.

Any reason you're still running warthog? Upgrading will give you Xorg and probably less problems too. You can order free CD's with Dapper!

For solving your issue below, you better do as the error messages tell you.
```

cd /usr/X11R6/lib/modules
sudo ln -s /usr/lib/libglade-2.0.so

```

Also, you probably have to replace /dev/mouse with /dev/psaux in XF86Config.

---

### Post by Josh_b on 2006-07-23
Hey,

I thought I should post it in this forum because I am new to linux.

I'm using warty because it is an old CD I had from a PC mag. I would update it, except I didn't do the network config during set-up (thought I could do it later).

I tried the code and it didn't work (also tried with libglide2x.so instead of libglade-2.0.so). I wasn't sure how to replace the /dev/mouse.

Can I upgrade warty to dapper using apt-get? If so, it'll probably be more beneficial for me to get the network setup and upgrade from there.

Thanks

---

### Post by adam.tropics on 2006-07-23
using apt-get would be difficult, as you would I believe have to first upgrade to Hoary Hedgehog, then again to Breezy, then finally to Dapper. The odds of getting through all that trouble free are not good. Not to mention, that would involve some fairly substantial downloading! It would be FAR simpler to log onto your windows partition and download Dapper. Much quicker.

---

### Post by steve.horsley on 2006-07-23
I agree with Adam. By the time you have downloaded 3 complete upgrades, you could have downloaded have downloaded the Dapper installer CD twice over. I recommend that you just grab the Dapper installer. I also recommend the "alternate" installer - it seems more stable than the GUI installer on the live CD, and you're not wanting the live CD for evaluation at the moment.

---

### Post by Josh_b on 2006-07-23
Thanks for that. I'm downloading it now.

---

### Post by Josh_b on 2006-07-23
Actually, before I start downloading it. I have a 64-bit AMD CPU. I just read that by installing the 64-bit version I won't be able to run some programs like Flash and WINE. Should I install the 32-bit or 64-bit version?

---

### Post by adam.tropics on 2006-07-23
Yeah you may have less hassle going with the 32-bit for now.

---

### Post by Josh_b on 2006-07-23
Cool. It should be downloaded in an hour. :)

---

### Post by adam.tropics on 2006-07-23
I want your internet connection....very jealous!

---

### Post by Josh_b on 2006-07-23
*hugs his 1.5Mbs connection*

I'd prefer to live in America and get their connection speeds though.

---

### Post by Josh_b on 2006-07-24
Yep. I installed Ubuntu 6.06 and it works like a charm. :D

---

