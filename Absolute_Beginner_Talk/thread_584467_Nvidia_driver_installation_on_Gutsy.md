---
title: "Nvidia driver installation on Gutsy"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by tarheels84 on 2007-10-21
Hi~

 I am a first time user of Ubuntu and I've been trying to get my nvidia driver to install on gutsy for a couple days now without success. I tried installing directly from Nvidia's website, but I get this error message "Unhandled MIME type: “application/x-shellscript”". When I try going into restricted drivers manager to enable Nvidia accelerated graphics driver is gives me this message "The software source for the package nvidia-glx-new is not enabled.". The status is "not in use". any help on what I should do would be greatly appreciated. Thanks.

---

### Post by FuturePilot on 2007-10-21
Go to System>Administration>Software Sources and make sure you have all of the repos enabled. Check all of the check boxes in the first tab. (Except the one for the CD-ROM). Reload the sources when prompted. Then try again with the Restricted Driver Manager.

---

### Post by FredB on 2007-10-21
Yes. You don't need to install nvidia drivers by hand anymore ! And that's great ;)

---

### Post by tarheels84 on 2007-10-21
Awesome! Thanks, that worked perfectly. Much obliged.

---

### Post by GSF1200S on 2007-10-21
Since this is resolved, I wont feel too bad jacking the thread. I was hoping you guys could teach me a little something.

I installed gutsy 64 bit yesterday, and I COULD NOT get my drivers to work. Im experienced with video drivers, having used the repos in Feisty and the website nvidia drivers in Edgy.

I tried the GLX-new drivers in the repos, and X would crash. I tried 9639, 9755, and the newest drivers from the Nvidia website and removing the nvidia common kernel, and X still failed.

As a last ditch effort, I simply checked the box in the restricted drivers setting window (im on kde), and it WORKED WITHOUT A HITCH! (haha, i almost cried)

Id like to know why.. is there something Im missing? How could I get all these errors even using the repos, but then the little restricted manager fixes it?

Hope someone knows... at least it works perfect now :)

---

### Post by weird_c00kie on 2007-11-06
> **FuturePilot said:**
> Go to System>Administration>Software Sources and make sure you have all of the repos enabled. Check all of the check boxes in the first tab. (Except the one for the CD-ROM). Reload the sources when prompted. Then try again with the Restricted Driver Manager.

Awesome! This worked for me. Now if only it would automatically detect the native resolution as well... I can't even remember how to change the options available...

---

