---
title: "Hard freezes on LiveCD.  Happen on install?"
date: 2007-10-24
forum: Absolute Beginner Talk
---

### Post by TheOrangePeanut on 2007-10-24
When I boot into 7.10 LiveCD, the "ati" open source drivers are loaded.  Unfortunately, they completely crash my computer.  A dead freeze, mouse stops working, num lock and caps lock buttons on my KB start blinking; theres no getting out of it.  The "ati" driver has been doing that since 7.04 (and hence the reason I haven't installed Ubuntu yet.)

So I rebooted the LiveCD and immediately enabled the restricted drivers.  I restarted X, I ran glxinfo | grep direct and direct rendering was "yes".  K, "fglrx" was loaded (and I confirmed this by checking xorg.conf).  I fired up Battle for Wesnoth to see if it could run any games.  Yup, Wesnoth ran fine, but it was only 2d.  I decided I'd better try a 3d game to see if it was working.  I fired up Neverball, it played fine for about 8 seconds and then hardfroze like the "ati" drivers freeze under normal circumstances.

I want to install Ubuntu this weekend, but I'm afraid that it's going to be plagued with video driver problems.  The 8.40 drivers (the ones in Ubuntus restricted driver menu, right?) are surely mature by despite not supporting aiglx.  I use my computer for programming because I am a CS major, and I can't very well have it crash and lose all my code when I try to render something in OpenGL.

This doesn't seem like a common problem because I NEVER see anyone talk about hard freezes like my machine goes through.  It has to be a driver problem; I can run intensive 3d applications just fine with Windows.  Anyone have any input?  Maybe there is a BIOS setting that is misconfigured for the drivers (AGP gart or something?  I don't know a lot about AGP bios settings but I do know I've had trouble with them in the past with Windows.)

My specs:

Athlon XP 2800+
1 gig DDR2700 ram
Radeon 9500 Pro (r300)

---

### Post by startherepodcast on 2007-10-24
I have no experience with this card, but as it is a radeon you might also want to try the opensource "radeon" xorg driver. Concerning the restricted driver problem with your games, I don't know if they perform better on an installed system or if this game just hard locks with this driver all the time.

Hope that helped a bit

Leon

---

### Post by TheOrangePeanut on 2007-10-24
Well, whatever it was, I tried to do it again today and everything worked fine.  I ran Neverball, Nevergolf, the penguin going down the snowy hill game (can't remember what it was called.) and Chromium.  3 of those are 3d and there was no crashes.

Maybe yesterday was because I ran out of ram or something, since it is running off a live CD.  I tried everything right away today and nothing crashed.  I'm going to install Ubunut on Friday I guess; I have to get my friend's external HDD to backup my music and then I'm good to go.

---

