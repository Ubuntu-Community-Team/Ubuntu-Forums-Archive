---
title: "Messed up system, total reinstall add nVidia drivers, totally messed up again?"
date: 2006-08-30
forum: Absolute Beginner Talk
---

### Post by handy on 2006-08-30
I'm thoroughly peed off, at the moment, I've just reinstalled due to my system being messed up for unknown reasons? I add nVidia closed source drivers in the process of putting it all back together again & I'm in as bad a shape as I was many hours ago before I did all this tedious installation work...

I'm locked out of my own machine, x has failed!!??  & I am obviously out of patience! :(

---

### Post by handy on 2006-08-30
So, are the updates safe yet?

---

### Post by toasted on 2006-08-30
> **handy said:**
> So, are the updates safe yet?

The updates are reported as ok now

Did you run a memory test?

You may be having some hardware issues...
Try stripping the box down to bare essentials. 
Just MB, one ram chip, floppy (with boot disk), video card
Unplug everything else and remove other ram chips. Try to boot... if not then try other ram chips 

The idea is to start with bare minimum - known good hardware and add the rest back in one component at a time till the problem is identified. Hope it works out for you....

---

### Post by handy on 2006-08-30
> **toasted said:**
> The updates are reported as ok now

Did you run a memory test?

You may be having some hardware issues...
Try stripping the box down to bare essentials. 
Just MB, one ram chip, floppy (with boot disk), video card
Unplug everything else and remove other ram chips. Try to boot... if not then try other ram chips 

The idea is to start with bare minimum - known good hardware and add the rest back in one component at a time till the problem is identified. Hope it works out for you....

Thanks for your reply. :) 

I am a just retired self employed computer tech'. I don't have a hardware problem, I have a Ubuntu problem (I still love Ubuntu:) ) just not as much at the moment!

If I remove the 1280x1024 from my xorg.conf I can boot into gnome, if I put it back I can't?

Riddle me that?:confused:

---

### Post by toasted on 2006-08-30
Well lets see....
Your machine was running good for quite some time I take it
Then it broke
You reinstalled Ubuntu and its still broke

That doesnt sound like an Ubuntu problem to me...  but who know, sometimes strange things happen.

If it were Ubuntu wouldnt you think a clean install would be ok? I would and I would be upset too!

I assume you used the same drivers as before... hmmmmmm

What else could be different with this install?

With the resolution thing... I assume that the monitor is queried during driver config. Never used nvidia so im unfamiliar

It must have determined that that res wouldnt work not maybe?

---

### Post by handy on 2006-08-30
Ok, I just did major updating, after finding away around a bug that separates me from the repo's.

So, I am still inclined to think that my problem is arriving via the internet.  I had no problems whilst I was some weeks behind in updates!

My machine as far as the reinstall is concerned, was fine, & broke after I had updated...

By the way, I have here besides me another inferior in every way machine, running on the same monitor all the res' that this one used to, with it's nvidia 6800gt card on a sony g400 19" monitor!

---

### Post by tomBorgia on 2006-08-30
Sounds like the xorg-server update that broke my X... have you tried the "latest update broke my system" thread...?
Its a bit wierd that you can get X at, say, 800x600 but not at 1280x1024... 
If you quickly need to revert to an older xserver-xorg version do this -
open terminal... and change to this directory...
/var/cache/apt/archives
Then ls / grep for xorg...
tom@tom-ubuntu-desktop:/var/cache/apt/archives$ ls | grep xorg
xserver-xorg-core_1%3a1.0.2-0ubuntu10.1_i386.deb
xserver-xorg-core_1%3a1.0.2-0ubuntu10.3_i386.deb
xserver-xorg-core_1%3a1.0.2-0ubuntu10.4_i386.deb
xserver-xorg-input-mouse_1%3a1.0.3.1+cvs.20060109-0ubuntu1.1_i386.deb
you can see older versions of the "broken" xserver-xorg-core
instal it with -
tom@tom-ubuntu-desktop:/var/cache/apt/archives$dpkg -i xserver-xorg-core_1%3a1.0.2-0ubuntu10.1_i386.deb
then restart x 
tom@tom-ubuntu-desktop:/var/cache/apt/archives/startx

If that doesnt work then post the last bit of your /etc/X11/xorg/Xorg.0.log

Tom.

---

### Post by handy on 2006-08-30
Thanks Tom, you are 100% :KS 

I'll continue the good fight tomorrow, it's getting late on this side of the world.

I'll let you know how I go...

Goodnight!

---

### Post by handy on 2006-08-30
After removing & reinstalling the nVidia drivers the problem went away!? :confused: 

Something was crooked, & is now straight! :cool: 

I'll see what the short term future brings re: the reinstallation, it's not over yet! :rolleyes: 

I must say that it certainly is a less painful operation when you have a dedicated /home partition.

Thanks to all who offered me help last night, I was just a little techy... ](*,)

---

