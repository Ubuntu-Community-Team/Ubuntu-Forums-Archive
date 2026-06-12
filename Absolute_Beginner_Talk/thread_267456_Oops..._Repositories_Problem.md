---
title: "Oops... Repositories Problem"
date: 2006-09-28
forum: Absolute Beginner Talk
---

### Post by meseleto on 2006-09-28
I went to this webiste [http://www.linuxjournal.com/node/1000081](http://www.linuxjournal.com/node/1000081) to take a look at the 3D Xgl Compiz thing I heard about. I tried adding the repositories required but I kept getting errors and now I can't even open up Synaptic Package Manager. :mad: 

 It says I need to edit my sources.list file but when I try to change it and save the changes it says I don't have permission. Any ideas?

---

### Post by echo $USER on 2006-09-28
> **meseleto said:**
> I went to this webiste [http://www.linuxjournal.com/node/1000081](http://www.linuxjournal.com/node/1000081) to take a look at the 3D Xgl Compiz thing I heard about. I tried adding the repositories required but I kept getting errors and now I can't even open up Synaptic Package Manager. :mad: 

 It says I need to edit my sources.list file but when I try to change it and save the changes it says I don't have permission. Any ideas?

You need to open it as super user, try...

> gksudo gedit /etc/apt/sources.list

---

### Post by meseleto on 2006-09-28
Yeah it worked. :p Thanks a million echo

But now when I try download compiz from synaptic I get an error saying I have unresolved dependencies specifically:

"compiz:
 Depends: compiz-plugins but it is not going to be installed"

And when I try downloading the plugin i get:

"compiz-plugins:
  Depends: compiz-core (>=0.0.13.54) but 0.0.13.38-0ubuntu3 is to be installed
 Depends: csm (>=0.5) but it is not installable"

I added all of the repositories that were listed on the site and yet it doesn't work.

---

### Post by echo $USER on 2006-09-28
> **meseleto said:**
> Yeah it worked. :p Thanks a million echo

But now when I try download compiz from synaptic I get an error saying I have unresolved dependencies specifically:

"compiz:
 Depends: compiz-plugins but it is not going to be installed"

And when I try downloading the plugin i get:

"compiz-plugins:
  Depends: compiz-core (>=0.0.13.54) but 0.0.13.38-0ubuntu3 is to be installed
 Depends: csm (>=0.5) but it is not installable"

I added all of the repositories that were listed on the site and yet it doesn't work.


First thing before you install xgl/compiz, what video card do you have, and have you installed the driver for the card?

---

### Post by meseleto on 2006-09-28
I have an integrated graphics card: Intel GMA 950. I didn't know you had to install a driver for it when I switched to ubuntu. For the sake of knowledge, why do you need to do so?

---

### Post by echo $USER on 2006-09-28
> **meseleto said:**
> I have an integrated graphics card: Intel GMA 950. I didn't know you had to install a driver for it when I switched to ubuntu. For the sake of knowledge, why do you need to do so?

XGL/Compiz is dependant upon hardware acceleration.  You need either a ati/nvidia card with the drivers installed to run compiz.  You need to buy a new card before you can proceed to install xgl/compiz.

---

### Post by meseleto on 2006-09-28
So Intel doesn't support hardware acceleration? Also, I'm using a laptop and i'm pretty sure you can't buy a graphics because it's integraded with the rest of the computer.

---

### Post by meseleto on 2006-09-28
OH and this is a partial description of the graphics card: 

With a powerful 400MHz core and DirectX* 9 3D hardware acceleration, Intel® GMA 950 graphics provides performance on par with mainstream graphics card solutions that would typically cost significantly more. 

Also, before when it was on Windows XP I ran many different games smoothly (Guild Wars, All the warcraft series, diablo 2, etc) It also is windows vista capable which, from what I understand, is going to be in 3d and be a system hog. 

Does this still mean I can't use xgl/compiz?

---

### Post by mpretti on 2006-09-28
I'm running with an nvidia card, with the driver already installed and I have come across the exact same issue that was explained in this thread.

Any ideas ?

---

### Post by joshyf on 2006-09-29
xgl/compiz is currently broken, as the repositories can't find this 'csm' package. i got xgl/compiz working a few weeks ago, but because compiz just forked (apparently, from other forums) all the repos are broken, so you can't install compiz or xgl atm... very frustrating, coz i want it back as well! :P

---

### Post by moncho on 2006-09-29
@joshyf - I had no problems installing it a few weeks ago, but I seem to be running on this package dependency issue as well, and it appears as if I'm not alone.  Are the repositories undergoing an upgrade?  It seems as if that's what's causing the inconsistencies (especially w/ compiz-plugins and csm).  Should people be notified? XGL IS IN DEMAND =-]

---

