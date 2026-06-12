---
title: "suspend works, but brightness control is lost!"
date: 2007-06-27
forum: Apple Intel Users
---

### Post by darkcarnival on 2007-06-27
Hello all!

I've fiddled around, initially I used macbook-backlight to control my brightness, this stops working after I suspend the machine and bring it back.
Assuming it was the macbook-backlight program that was to blame, I followed the instructions at:
[http://ubuntuforums.org/showthread.php?t=467001](http://ubuntuforums.org/showthread.php?t=467001)

and made the appropiate entries (changed to Macbook2,1 and "Apple Inc.") and then the brightness applet works after I rebooted.
However, when I suspend the machine and bring it back, the applet is still displayed as if it works. But adjusting the slider produces no effect.

So in short: whenever I suspend my machine, I loose the ability to adjust my brightness levels afterwards.

Oh and btw:
I suspend using "s2ram -f" and I practically removed all the entries in the original suspend script as it would render suspend unuseable.

---

### Post by ivesjd on 2007-06-28
Some of my apps do this after restarting X. Like katapult, amarok. They get a failure with the DCOP server. and sometimes knetwork manager (use it cause I get a better connection, kinda funny the programs I have problems with are kde :P) but what I do is do sudo killall and then the application. like "sudo killall DCOPserver" and then restart is with "gksudo DCOPserver".

---

### Post by kzm. on 2007-06-28
> Oh and btw:
I suspend using "s2ram -f" and I practically removed all the entries in the original suspend script as it would render suspend unuseable

my brightness doesnt come back after suspend.. i can see my desktop but its so dark as i would sit with sunglasses on my toilet with lights switch of at midnight trying to read the days poem on the paper... did you experienced something like this, too?

---

### Post by darkcarnival on 2007-06-28
hahaha, you're funny :P

**To fix missing backlight, read my guide! ^^ ^^**

Well. I did.. Also.. I wrote a guide on EVERYTHING I've battled with (well, actually it's missing a few steps for newer problems, but it's pretty thorough)

I put it up on insanelymac.com in their *nix forum, but it might do better here.. Anyway, I'll give you a linky :)

[http://forum.insanelymac.com/index.php?showtopic=54513](http://forum.insanelymac.com/index.php?showtopic=54513)

Here.. I've seen what you're experiencing right now too, check step 5. What you gotta do is follow step 5 to change your video-driver. After that it should work just fine :)

**To fix brightness controls after suspend**

1) Read this, if you're interested in why it happens

2) Download his code for fixing it at:
[http://launchpadlibrarian.net/5827146/fixbacklight.c](http://launchpadlibrarian.net/5827146/fixbacklight.c)

3) Compile (on ubuntu) like so:
gcc fixbacklight.c -lpci -lz -o fixbacklight
You MUST link to the z-library thingie or else it will complain about undefined references to 'gzopen' and so.
People think it's because pci-utils is bugged, it's not. It's just something with the libraries which I can't explain (sorry - other people on the net should be able to tell you why)

---

### Post by kzm. on 2007-06-28
ok.. i bookedmark it. i gonna try this weekend. thanx a lot. would be nice to suspend and see something afterwards... i also will try your battery advise after i tried ulfs... sweet-sweet, cant wait having everything working!!!
\\:D/  (<--weird icons they have on this forum, what does this supose to mean?)

---

### Post by thonuz on 2007-06-28
to fix backlight for core 2 duo here is what I did: just change the value from 1 to 2. If there is some reason not to do this and its easier let me know?

go to /usr/share/hal/fdi/policy/10osvendor$
and edit 10-macbook-backlight.fdi
so that the product matched c2d by changing the value to "2.1" as below:
<match key="smbios.system.product" string="MacBook2,1">

---

### Post by kzm. on 2007-06-28
> go to /usr/share/hal/fdi/policy/10osvendor$
and edit 10-macbook-backlight.fdi
so that the product matched c2d by changing the value to "2.1" as below:
<match key="smbios.system.product" string="MacBook2,1">

i did this:
```
    sudo gedit /usr/share/hal/fdi/policy/10osvendor/10-macbook-backlight.fdi 
    line 6 change "Apple Computer, Inc" to "Apple Inc."

```
because the number fix wasnt working for me.

---

### Post by kzm. on 2007-06-28
but those fix has no effect on my suspend to "darkness"

---

### Post by darkcarnival on 2007-06-28
While those things admittedly work (I've used those things later on for an easier alternative to macbook-backlight) they *don't* work after my computer wakes up from suspend - that's why I use the little ugly hack ;)
If I can get around to it, I'll probably revise my guide and repost it here since more people may have use of it here than on the linux section of a pro-Mac website.
Although, right now I'm busy doing other things.

---

