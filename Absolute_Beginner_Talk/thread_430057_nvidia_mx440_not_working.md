---
title: "nvidia mx440 not working"
date: 2007-05-01
forum: Absolute Beginner Talk
---

### Post by halo6819 on 2007-05-01
hey guys, i have a NVIDIA mx 440 vid card that is giving no end of problems. I have Fiesty loaded onto an old Dell optiplex that has onboard video, and it works fine, but i want to use this old MX440 card that i have so i can have TVout.

so i installed the NVIDIA legacy driver witch says it suports the MX440 card but then when Xserv trys to start up again it fails...

ther error is as follows:
[IMG]http://img.photobucket.com/albums/v493/halo6819/100_0087.jpg[/IMG]

[IMG]http://img.photobucket.com/albums/v493/halo6819/100_0088.jpg[/IMG]

---

### Post by starcraft.man on 2007-05-01
Hmmm, I don't think the mx 440 is that old, hehe, its came on my PC :p. Can I recommend that you reconfigure your xorg to boot with the nv 2d drivers. When you get back in, remove the legacy drivers completely. Then, use this [script.]("http://www.albertomilone.com/nvidia_scripts1.html"), just pick automatically install nvidia driver. Should fix it :)

---

### Post by Bachstelze on 2007-05-01
Are you sure you have nvidia-glx-legacy installed and not nvidia-glx ?

```
sudo dpkg -l | grep nvidia
```

---

### Post by tophatandy on 2007-05-01
first off, 
dont make a decision off of what I am about to tell you.
 
I had a GeForceMX440 GO just like yours and had trouble to no end enabling Nvidia Drivers.. the mx440's are very odd, I would recomend pluging in the 30 dollars and getting yourself a better video card It seems like anything above the mx440 will work.. 

I upgraded from the mx440 to the 6200, and am currently at a Geforce 7800 GTX (can you tell I got into pc gaming?). after my upgrade to the 6200 all problems ceased. Make the upgrade.. its worth it.. 

Did you use the restricted drivers manager?

or did you use the old method of downloading the drivers off the repos and Installing them?

---

### Post by Bachstelze on 2007-05-01
I have an old Compaq laptop with a GeForce Go 440 card too and it worked like a charm, but in Gentoo, using the installer from nvidia...

---

### Post by halo6819 on 2007-05-01
> **starcraft.man said:**
> Hmmm, I don't think the mx 440 is that old, hehe, its came on my PC :p. Can I recommend that you reconfigure your xorg to boot with the nv 2d drivers. When you get back in, remove the legacy drivers completely. Then, use this [script.]("http://www.albertomilone.com/nvidia_scripts1.html"), just pick automatically install nvidia driver. Should fix it :)

i cant seem to figure out how to configure the xorg... (realy realy new user :))

---

### Post by halo6819 on 2007-05-01
> **tophatandy said:**
> first off, 
dont make a decision off of what I am about to tell you.
 
I had a GeForceMX440 GO just like yours and had trouble to no end enabling Nvidia Drivers.. the mx440's are very odd, I would recomend pluging in the 30 dollars and getting yourself a better video card It seems like anything above the mx440 will work.. 

I upgraded from the mx440 to the 6200, and am currently at a Geforce 7800 GTX (can you tell I got into pc gaming?). after my upgrade to the 6200 all problems ceased. Make the upgrade.. its worth it.. 

Did you use the restricted drivers manager?

or did you use the old method of downloading the drivers off the repos and Installing them?

unfortunetly i need a small regular pci card for this machine, its a Optiplex GX110 desktop with only two pci expansion slots (one is the video capture card, the other is this cursed MX440)

---

### Post by halo6819 on 2007-05-01
> **HymnToLife said:**
> Are you sure you have nvidia-glx-legacy installed and not nvidia-glx ?

```
sudo dpkg -l | grep nvidia
```

i might be entering the code in incorectly, but this does not seem to work:

dpkg: unkown option -1

---

### Post by jimrz on 2007-05-01
> **halo6819 said:**
> unfortunetly i need a small regular pci card for this machine, its a Optiplex GX110 desktop with only two pci expansion slots (one is the video capture card, the other is this cursed MX440)

think the problem is with the GX110. not long ago,i built one of these for a friend and tried putting a nvidia mx4000 pci card in it and never could get it to work. i believe the problems is that there is no option in the BIOS to disable the on-board video, only allows for on-board or auto and selecting auto justs get you a blank screen. Even tried putting xp on it to see if that would work, but with auto selected the machine would not even boot and just freeze up. at least feisty would boot (you could hear it fine, but see nothing).of course, this may have been a separate issue specific to that box but maybe not. in any event, the box is running feisty pretty nicely considering it'a age and specs.

---

### Post by Bachstelze on 2007-05-01
> **halo6819 said:**
> i might be entering the code in incorectly, but this does not seem to work:

dpkg: unkown option -1

It is a lowercase L, not the nuber one ;)

---

### Post by halo6819 on 2007-05-01
> **jimrz said:**
> think the problem is with the GX110. not long ago,i built one of these for a friend and tried putting a nvidia mx4000 pci card in it and never could get it to work. i believe the problems is that there is no option in the BIOS to disable the on-board video, only allows for on-board or auto and selecting auto justs get you a blank screen. Even tried putting xp on it to see if that would work, but with auto selected the machine would not even boot and just freeze up. at least feisty would boot (you could hear it fine, but see nothing).of course, this may have been a separate issue specific to that box but maybe not. in any event, the box is running feisty pretty nicely considering it'a age and specs.

the card works alright in XP, even the vidout works...
but yes i just updated my BIOS and still its either on-board or auto... damn, i hope its not the box cause then i would have sank alot of money into it for nuttin...

---

### Post by jimrz on 2007-05-02
> **halo6819 said:**
> the card works alright in XP, even the vidout works...
but yes i just updated my BIOS and still its either on-board or auto... damn, i hope its not the box cause then i would have sank alot of money into it for nuttin...

hope not ... since it works for you in windows, maybe the issue with the one I mentioned was something specific to that box

---

