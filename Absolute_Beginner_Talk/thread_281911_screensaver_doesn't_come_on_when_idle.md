---
title: "screensaver doesn't come on when idle"
date: 2006-10-21
forum: Absolute Beginner Talk
---

### Post by shanepardue on 2006-10-21
my screensaver isn't coming on as if it's not recognizing my idleness. i'm not sure where to start for troubleshooting this problem. any help is greatly appreciated. here's my screensaver settings.

i did purchase a new wireless mouse a little bit ago, but i don't know if the screensaver hasn't worked since then or not.

---

### Post by podunk on 2006-10-21
Mice configuration info lives in xorg.conf along with your video card info.

You might want to type in
```
glxinfo
```

You'll get a bunch of gobbly gook - but up almost at the very top it needs to say
```
direct rendering: Yes
``` for your 3D screen savers to work.

If it says no the only thing *I* know to do is reinstall the video drivers.

---

### Post by shanepardue on 2006-10-21
it definitely says "no". i would rather not deal with reinstalling the video drivers if at all possible. is that for sure the issue?

---

### Post by Anduu on 2006-10-21
Regardless of whether your video drivers are installed correctly or not ***something*** should happen when the screesaver is set to activate.

Try going back to your regular mouse and see what happens...you'll know for sure then.

---

### Post by shanepardue on 2006-10-22
I have found the problem is intermittent and not associated with my mouse.
I will continue to monitor my activity to see what is stopping it from
working correctly. I'll reply if I find anything. Thanks for your help!

---

### Post by raqball on 2006-10-22
Most of the open gl screensavers NEED 3d.. Try usinf a differnet one

---

### Post by shanepardue on 2006-10-22
why does glxinfo say "direct rendering NO"? I have a modern NVIDIA video card. I'm using beryl and all. When the screensavers work, they're all opengl. When they don't work, they don't even attempt to. It's not like it attempts, then fails.

---

### Post by shanepardue on 2006-10-22
Wait! That makes sense. My screensavers are set for random and it probably 
isn't working when it gets to certain screensavers. I was thinking it would
show some sign of it not working, but it very well may not. I just need to 
get my direct rendering option to say yes and I may be in business. I know
this video card can handle it.

---

### Post by shanepardue on 2006-10-22
Sorry for the frequent posts to the issue, but I resolved it. I simply commented out the DRI option in my xorg.conf. It allowed for direct rendering and I should be good. If this is a bad approach to fixing the problem, let me know!

Thanks!!

---

### Post by shanepardue on 2006-10-22
UGH! I realized my XGL/Beryl was not working properly when I commented out DRI. Now I'm back to square one. Direct Rendering says no again.

---

### Post by Anduu on 2006-10-22
Me being the dumbass I am didn't clue in to the fact that you had the screensaver set to random(...from your screenshot)and that possibly OpenGL screensavers were the problem...duh.

Anywho glad you got it sorted out :)

---

### Post by shanepardue on 2006-10-22
> **Anduu said:**
> Me being the dumbass I am didn't clue in to the fact that you had the screensaver set to random(...from your screenshot)and that possibly OpenGL screensavers were the problem...duh.

Anywho glad you got it sorted out :)
But I haven't really sorted it out! hehe

---

### Post by Anduu on 2006-10-22
> **shanepardue said:**
> But I haven't really sorted it out! hehe

Doh!

Back to square one it is :P

I guess you need to get your drivers woking properly...what kind of card?

---

### Post by shanepardue on 2006-10-22
NVIDIA. I installed the driver beforehand, but am willing to do it again if need be.

---

### Post by BackInTimeMan on 2006-10-22
> **shanepardue said:**
> UGH! I realized my XGL/Beryl was not working properly when I commented out DRI. Now I'm back to square one. Direct Rendering says no again.

I'm using 3D Desktop Changer and FWIW, if I do the "glxinfo" command, sometimes it says: direct rendering: Yes and sometimes: direct rendering: No. It seems completely random.

---

### Post by shanepardue on 2006-10-22
**NEWS FLASH**

The problem doesn't pertain to specific screensavers as I've tried many 
that do work (when the screensavers decide to work). I don't believe it has
 anything to do with direct rendering, although I would like to have that 
fixed also. hehe

I did notice that when the screensavers aren't working it's because the 
process "gnome-screensaver" wasn't running (it stopped sometime after booting). 
This may sound weird, but I think with the latest Beryl update 
that's been causing many problems for many people, it caused this problem. I
 too, have had flickering windows and such since the update, but I have found
 a workaround that involves resetting my emerald theme each time it freaks
 out. 

If anyone has any other ideas, I'd be happy to hear them!!

---

### Post by blendmaster on 2006-10-22
Whilw I'm not sure of the reason the screensavers aren't coming on, you can install nvidia drivers easily through [automatix]("http://getautomatix.com/wiki/index.php?title=Installation&Itemid=38").

follow the installation guide for automatix2 (and be sure it's for dapper, or edgy eft (depending on what you have, as there are different installation methods)).

Then run it, and tell it to install nvidia drivers.

P.S. While this is good for you to have 3d rendering up, it probably still won't fix your screensaver problem.

---

### Post by shanepardue on 2006-10-22
I have installed the Nvidia driver through automatix already. I'm also using
 XGL/Compiz so I'm not sure why it says I'm not getting direct rendering. I 
was able to get direct rendering saying yes by commenting out "DRI" in my 
xorg.conf, but that disabled my XGL. Not sure where to go from here on that
 issue.

---

### Post by blendmaster on 2006-10-22
Hmm.

I think I remember going through a tutorial changing the default GNOME screensaver menu (system >> preferences >> screensaver) to one that was in "beta", or something to that effect, to allow for greater preference usage.

When I did all of that though, the screensavers wouldn't come up. I had to change it back to get them to come on. Have you too tried that tutorial?

---

### Post by shanepardue on 2006-10-22
No, I haven't tampered with anything screensaver-related. It just stopped 
working. It works fine when I load gnome-screensaver, but I think whenever I
 have to close Beryl-Manager and start over with that stuff, it's disabling
 the screensaver or something. Wierdness.

The XGL issue seems more disturbing to me than the screensaver now.

---

