---
title: "Beginner^10 - Internet &amp; Possible Compatibility Issues. Any ideas?"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by tali3sin on 2007-12-19
[SOLVED]

Ok. Hi. First post here, and already begging for help (:
C'est la vie.

But, the thing is. I got a sudden urge to see what this linux business was all about. Heard that Ubuntu was probably the best first place I could go with it. Burnt the LiveCD, started it, had a look, liked the polish of what I saw - and the price tag.
So, I know my way around Windows pretty well. Minor geek.
Made a partition, installed Ubuntu. Awesome.

It detected my wireless straight up, sweet, I punched in my WEP, and it connected. Hooray.
I went to Prefs>Appearance and like a true aesthetics addict, attempted to switch on Desktop Effects.
Oh, I need an Nvidia driver. That's cool. Download plz.

It um.. didn't even try. Now, I'm at work, so I can't give you the exact error messages. Suffice to say it said something along the lines of "Nvidia xgl new" package was not enabled.
Ok.. cool. I went to the Restricted Drivers Manager. Attempted to tick the box next to Nvidia. Again "nvidia xgl" not enabled.
The really odd thing about this, is that I attempted to enable them from the LiveCD, and.. it downloaded the driver.

I also attempted to update the software that came default with the installation.. and... it detected the list, it downloaded that much, but in terms of downloading the packages themselves.. complete no-go.
Weirdly, it happily downloaded all of this when running from the LiveCD - silly though that may be, with it all disappearing on restart.

I followed some resources on these forums (godsend!) and updated the apt lists as best I could. I got *more* of the list, still couldn't download.
Except this time, it's telling me that my machine is incompatible i386. <-- I'm not sure what this means exactly.

uname -a <-- tells me that I've got i686? Architecture?

I believe the internet issue is carried over from some problems I've been having with WinXP, or my ISP in general, for some time now.
I think it's MTU related.
I can browse TO gmail, but I can't log in to gmail.
I can browse TO ebay, but I can't perform advanced searches, OR log in.
I can connected TO my work VPN, but I am unable to remote desktop to my workstation.

What I'm hoping.. is that someone has heard of these kinds of things before, and can help me sort out a fix (:
Driving me mad!

Btw, I'm running on a Dell XPS M1710 lappy.
Core Duo T2600 2.16ghz.
2gig of RAM
Nvidia GeForce Go 7900 GTX - 512mb.

Sorry so damn long (:
And very, very grateful for anything that can help me work towards solving these issues. Am very excited at the prospect of escaping Microsoft.

---

### Post by overdrank on 2007-12-19
HI and welcome, I would suggest first checking your repos and making sure they are all enabled. Here is a link to help with that 
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
Then to install your nvidia driver I would point you to Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
And good luck!

---

### Post by tali3sin on 2007-12-19
> **overdrank said:**
> HI and welcome, I would suggest first checking your repos and making sure they are all enabled. Here is a link to help with that 
[https://help.ubuntu.com/community/Repositories/CommandLine](https://help.ubuntu.com/community/Repositories/CommandLine)
Then to install your nvidia driver I would point you to Envy
[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)
And good luck!

Cheers for the quick response, although I have to say... In my attempts to make this all work last night, I went through and manually enabled all those. They were commented out, for whatever reason.
That's what enabled me to see this list of applications/updated/etc, however.. I was still unable to download them.

As for Envy, I'd heard about that, and gave it a whirl... but it said something about missing library dependancies....?
But, possibly it simply wasn't able to access wherever it needed to, to download either.
I'm just not sure.

Btw, this is not a wireless issue. If I make a direct connection from the cable modem to the laptop, it's all the same.
I just can't figure why it worked on the LiveCD.
But not once installed, and same style of issues on WinXP.

---

### Post by lintoon on 2007-12-19
Regarding your browsing problem, your router isn't a belkin by any chance is it.  Have you lowered the MTU on your router?  If not lower it to 1400 and see if that makes any difference.

---

### Post by tali3sin on 2007-12-19
> **lintoon said:**
> Regarding your browsing problem, your router isn't a belkin by any chance is it.  Have you lowered the MTU on your router?  If not lower it to 1400 and see if that makes any difference.

It's a linksys (:
Though I do have a belkin lying around somewhere.

And.. no. I can't find the setting on the router itself by which to drop the MTU.

I've found that on my WinXP install, it doesn't matter what I raise, or drop the MTU to.. it just plain doesn't solve the problem.
However, on my mother's laptop, another WinXP install.. it was dropped to a ridiculous 800.. and everything came back to life, albeit a more sluggish life. Hmm :-\

---

### Post by lintoon on 2007-12-19
I think the older versions of the firmware didn't allow you to alter the MTU on Linksys routers.  Try updating the firmware for your router model.  Be careful and make sure you get the correct firmware for your model.

---

### Post by tali3sin on 2007-12-19
> **lintoon said:**
> I think the older versions of the firmware didn't allow you to alter the MTU on Linksys routers.  Try updating the firmware for your router model.  Be careful and make sure you get the correct firmware for your model.

Hmm. Ok. I'll have to give that a whirl, I suppose.

I'm still a bit stumped on the incompatability business too, though.
For instance, in my.. newb-like blundering and experimentation, I managed to remove the Restricted Drivers Manager package from Ubuntu, foolishly believing I'd be able to download/reinstall it.
But, when I clicked it, it told me it's not compatible with my machine.
That can't be right though, or it wouldn't have installed in the first place from the CD, right?
Could this just be a side-effect of the add/remove program being unable to reach the internet properly?

---

### Post by tali3sin on 2007-12-19
Not to be horribly rude, but... bump (:

---

### Post by tali3sin on 2007-12-21
SOLVED.

By reducing my MTU (via my router settings) to a ridiculous 900, I was able to gain internet access on Ubuntu, which... seemed to solve the "compatibility" issues it told me I had.
As well as everything else.

Sure, now my internet works more slowly, but at least I can access every portion of it, and run this beautiful OS properly.

Thanks (:

---

### Post by hyper_ch on 2007-12-21
what linksys router have you got?

---

### Post by lintoon on 2007-12-21
That's a bit low.  I would still try updating the firmware on your router and change the mtu back to 1492.

[http://www.linksys.com/download/firmware.asp?fwid=160](http://www.linksys.com/download/firmware.asp?fwid=160)

Try 1492 first and if that doesn't work try 1462.  If that doesn't work try 1400.

Good luck.

I'm off on holiday tomorrow for 2 weeks :) but I'll check your progress when I get back because I'm intrigued now.  I know, sad eh!!

---

### Post by lintoon on 2007-12-21
I've just re-read your original post and because I went of on a tangent I forgot about the fact that it works ok from the livecd.  Now I am confused.

---

### Post by tali3sin on 2007-12-22
> **lintoon said:**
> I've just re-read your original post and because I went of on a tangent I forgot about the fact that it works ok from the livecd.  Now I am confused.

Cheers for the linksys link above, I  may well give that a try. Due to the bizarre MTU stuff, and the fact that it's so damn low.

I have no idea why it worked from the LiveCD, but not from the proper installation.
After adjusting the MTU, Ubuntu will access gmail/etc, and I'm attempting to configure it to get to my work VPN. So far, it's having a "connection failure" <-- but no more info than that.

Whereas since lowering the MTU, WinXP can still connect to the VPN... but still can't remote desktop, nor can it access gmail. Ridiculous.

However, on my mother's laptop, with the MTU lowered.. it can reach gmail/etc. Haven't tried the remote desktopping on it though. The whole thing is very confusing.

Everything works perfectly if I take my laptop to a friend's place, and use their connection.
And the same problems persist at my house, if I take the router out of the picture, and just connect direct to the modem.
That suggests to me that my ISP have a problem. But... what?

---

