---
title: "Imac g5 won't boot"
date: 2008-02-13
forum: Apple PPC Users
---

### Post by maspiotis on 2008-02-13
I made an ISO of 6.06 and tried to boot it.  I turned on the computer and held down the "c" key and also tried the mouse button.  Neither of these seem to work.  

Is their another way? Should I bother?  I just got this computer and before was using ubuntu on my Sony laptop, the main reason I switched was so I would not have to bother with anti virus software.  

How do I get 6.06 on here and is it worth it?

Thanks,

Michael

cosmoandlola

---

### Post by stream303 on 2008-02-14
Same issue with another user, although I am running it successfully on my Rev-A G5 iMac (no als automatic light sensor or isight camera)

Are you burning the image at a low speed?  My fav right now for the G5 iMac is Feisty - with the "alternate" text-based installer:

[http://cdimage.ubuntu.com/ports/releases/feisty/release/](http://cdimage.ubuntu.com/ports/releases/feisty/release/)

I'm trying to remember if there was a firmware update in OSX for the G5 iMac drives....have to look that up later...

Quick thought - instead of holding down the "C" key, do you get anywhere if you hold down the OPTION or ALT key when booting?

---

### Post by maspiotis on 2008-02-14
I burned the ISO at low speed,

I did not try any of the other keys,

I willl try that later today.

Why is fiesty your favorite, does that work better than 6.06? Is the switch is worth it?

To me the Mac OS is awkward and I am concerned about virus protection, because I refuse to pay for anti-virus software.

Thanks for your reply and thoughts

Michael

---

### Post by stream303 on 2008-02-14
> **maspiotis said:**
> Why is fiesty your favorite, does that work better than 6.06? Is the switch is worth it?

I like it for the improvements to gnome, and some of the packages like Gimp are a bit more up to date.  Feisty has proven to be pretty good at hardware detection, but 6.06 worked fine for me too - it all depends on the machine and your tastes.  Fortunately, you can try them both if you like and see if the differences are worth it.  6.06 being an LTS, has longer support than Feisty even though it was released earlier.

> To me the Mac OS is awkward and I am concerned about virus protection, because I refuse to pay for anti-virus software.

I can relate - although this discussion is probably better left to the security forum.  I think you'll find Ubuntu a breath of fresh air.  Aside from machine/os specific virii, the latest attack vector is through the browser, so that's why I feel good running Firefox and the "noscript" add-on, which you can do on all the major os's.

There are a few other things I do just to lock doors, like enabling my router's internal firewall (just to keep the amount of "background noise" down, disable windows-centric features like UpNP if I see it etc.  More in the security forum.

Welcome aboard!  Let's get your ppc up and running!

---

### Post by maspiotis on 2008-02-14
I tried 7.04, the alternate disk and still no luck, I only tried the C key though, if I have time later I will try some other keys.

The c key should work, it worked with the Mac OS cd, so I don't know what the problem is.

Any help would be appreciated.

Thanks

---

### Post by maspiotis on 2008-02-16
I have had no luck with this, does any one iknow how to get ubuntu on an imac g5?

---

### Post by stream303 on 2008-02-16
My apologies if some of these questions are too simplistic.  Might help some new lurkers.

Are you actually burning the iso image rather than copying it over to a cd?

Are you using OSX's disk-utility program to burn it by dragging the iso to the left hand pane of disk-utility, highlighting it, and then clicking on burn?

Are you burning the image on a different machine with 3rd-party software?

Btw, what model of G5 iMac are you using, and what type of keyboard - apple, wired etc?

Have you tried holding down the Alt or Option key instead of the "C" key?

---

### Post by maspiotis on 2008-02-16
> **stream303 said:**
> My apologies if some of these questions are too simplistic.  Might help some new lurkers.

Are you actually burning the iso image rather than copying it over to a cd?

Are you using OSX's disk-utility program to burn it by dragging the iso to the left hand pane of disk-utility, highlighting it, and then clicking on burn?

Are you burning the image on a different machine with 3rd-party software?

Btw, what model of G5 iMac are you using, and what type of keyboard - apple, wired etc?

Have you tried holding down the Alt or Option key instead of the "C" key?

 After downloading I put in a blank disk I clicked on it and dragged the file dropped it highlighted and chose the burn option.  

Is that right?

I tried the alt/opt key and a screen came up with a return arrow a forward arrow and a mac hd icon.  

It would not boot from the cd though.

I have what I believe is the last version of the g5, it has a built in camera, wireless keyboard, and a remote control

I am using mac osx software to burn the disc.

I must be doing something wrong.  This was really easy when I did it on my Sony.

Thanks,
Michael

---

### Post by stream303 on 2008-02-16
> **maspiotis said:**
> After downloading I put in a blank disk I clicked on it and dragged the file dropped it highlighted and chose the burn option.

Gotcha. :)  Looks like it was just copied to a cd, so that's why it won't boot.  It needs to be burned in a special format because it is an iso file.

Ok, now that you have an iso image downloaded, put in a CD, and when a window comes up, just ignore or kill the window.

Find the apple disk-utility (applications > utilities > disk utility) and bring that up.

Now drag your iso image into the left pane of disk-utility, highlight the iso with a single click, and then hit the burn icon at the top.

drum roll ......

---

### Post by stream303 on 2008-02-16
Uh oh.  Forgot about the wireless keyboard.

I'm not sure if it is fixed yet, but the catch-22 is that after you successfully boot, you may no longer be able to use the keyboard, thus preventing you from working in the commandline to fix bluetooth issues. :(

To keep yourself sane, do you have access to wired keyboard / mouse in the meantime?

---

### Post by maspiotis on 2008-02-16
I have a wired mouse, but only the wireless keyboard,

Does 6.06 have the same problem with the wireless keyboard?

Thanks very much for your help.

---

### Post by stream303 on 2008-02-16
I believe it does, but haven't tried it.  Perhaps the 6.06.2 version will fare better.

I've used a variety of non-apple keyboards and havent had too many problems, so you can pick up a cheap one just to get it installed.

Happy to help!

---

### Post by stream303 on 2008-02-19
AHA!  With the bluetooth keyboard, this may be just what the doctor ordered!

[http://ubuntuforums.org/showthread.php?t=279883](http://ubuntuforums.org/showthread.php?t=279883)

Looks like removing the bluez* utilities does the job.  Since you have a wired mouse, getting to synaptic package manager should be a snap.

Hope you havent gone too far ....

---

### Post by maspiotis on 2008-02-21
Okay,

I burned the iso properly this time.  The first time I used the 7.04 alternate text based installer that you recommended.  Everything seemed to go well, then after reboot the computer just sat there and the fan went on and nothing happened.  Did I not wait long enough. I really don't care about keeping a partition for the mac os to run side by side, so somewhere in there I think I blitzed the mac partition. 

I thought that was the problem or maybe it was a 7.04 issue. 

So I tried again, this time with the standard 6.06 iso. I got the same problem again.

Any ideas? 

As far as the keyboard thing goes, won't I need the keyboard to type in a password to access synaptic?

Thanks again for your help.

---

### Post by stream303 on 2008-02-21
Looks like you did everything right.  We're caught in a trap - you have to press the "C" key to get the system to load from CD, and you'll need it in synaptic to help remove the bluez* packages. :)

FYI, I'm happily using Microsoft scrollwheel mouse and Microsoft keyboard on my Imac, whereas the apple stuff is in the closet.  Can you borrow or pick up a dimestore keyboard just to get past this?

---

### Post by maspiotis on 2008-02-21
Getting a ketboard should not be a problem,

But the biggest problem is that once ubuntu was installed it failed to boot.  I just get a black screen and the fan comes on.  Did I not wait long enough?

---

### Post by stream303 on 2008-02-22
Just to clarify...

You don't yet have a wired keyboard.

However, you have a properly burned iso image cd.

When you boot from the cd, you get a black screen.  Does the screen show the yaboot menu in the upper left to allow you to choose L for linux or C for CD, or is it just completely black?

If it is completely black with no menu, our last hope is that the system isn't waiting on some sort of keyboard...

---

### Post by maspiotis on 2008-02-22
It is completely black.

Again, I was able to burn the iso, boot up from the iso/cd, I saw the ubuntu logo etc. then on the initial reboot, I get a black screen with nothing on it.

The fan was on and nothing happened. I probably gave it two maybe three minutes and nothing.  

Thanks again for helping me out.

---

### Post by stream303 on 2008-02-23
What model G5 iMac do you have?  Is it a late-model C type with the iSight camera, the Rev-B type with the ALS light sensor on the front, or the early model Rev-A like mine that has neither?

Reason I ask is that if you have the late-model C with iSight, you may have to wait until Hardy is released (or dare to install the alpha).

The fan will go into vacuum-cleaner mode during installation, and should settle down after a good install.  That's one thing the impressed me with the Debian install I performed earlier - the thermal support was built into the installer.

Dying to hook up a wired keyboard to that box! :)

---

### Post by maspiotis on 2008-02-23
I have the g5 with the camera, I think this is the latest version with the remote control etc.

Does this mean that ubunt¨won't work? What is the story?

Thanks

---

### Post by stream303 on 2008-02-24
Just some early issues about fan control in your machine which I believe was cured by Feisty or Gutsy 7.10.  Fans scream during installation, but are under control after first successful reboot.

---

### Post by maspiotis on 2008-02-24
Ok,

So, how do I get Ubuntu onto my machine?

---

### Post by stream303 on 2008-02-24
I'm afraid that we can't assure that the lack of a wired keyboard isn't hampering your install  until we try it.

Unless you've already tried it and I'm full of hot air. :)

---

