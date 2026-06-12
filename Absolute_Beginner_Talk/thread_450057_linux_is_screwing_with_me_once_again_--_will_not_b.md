---
title: "linux is screwing with me once again -- will not boot"
date: 2007-05-20
forum: Absolute Beginner Talk
---

### Post by Miroku on 2007-05-20
man o man my linux system will not boot correctly. right now i logged in through my recovery mood of feisty. so here is the problem:

i choose my normal version of ubuntu from grub, it starts booting, the progress bar starts filling up, i see the nvidia splash screen, i get the normal orange screen, the mouse appears, everything seems good and THEN the monitor goes blank, its start readjusting, the screen appears once more and the nvidia splash again and then it turns into the mouse which is showing its busy signal and the rest of the screen is black. i can move my mouse around but its just showin the normal busy signal and not doing anything. please help! i dont know what happen because it was working fine when i booted an hour ago.

also, the first time this happened, it had to do a check of sda1 because it was mounted 30 times -- after that scan was complete, the above happened.

argh! and i just had it set up to how i liked it! very unhappy.

---

### Post by Miroku on 2007-05-20
come onnnn -- i need help here (very frustrated)

---

### Post by freebird54 on 2007-05-20
Must be bad timing - you have only ATI users cruising the forums right now...

pateince (if possible) someone will come.  I suspect it is a video issue - are there any change you recently made to any video setting (resolution. refresh, enabling effects etc etc...)

---

### Post by lamalex on 2007-05-20
check logs and such for any details as to what went wrong, maybe try reconfiguring xorg.conf.

---

### Post by jimrz on 2007-05-20
> **Miroku said:**
> come onnnn -- i need help here (very frustrated)

sounds as though your monitor is having issues with the xorg.conf or vice versa. have you just installed the nvidia driver? if so, try reverting to the "nv" driver and see if you can get booted into X that way

---

### Post by Miroku on 2007-05-20
i did reconfigure the xorg.conf, it didnt do anything -- now i just lost my custom nvidia drivers

what logs are you referring to exactly?

---

### Post by irish_flu on 2007-05-20
I'm with the last guy, I think I'd get myself to a command line and run:

sudo dpkg-reconfigure -phigh xserver-xorg

at the command prompt to re-configure Gnome.

I would be really surprised if that disk check made this happen, but I agree it's a weird coincidence.  Can I ask why you were rebooting?  Maybe it was an update that didn't play nice, or a change you had made before you rebooted that caused it.

EDIT: Oops, sorry I was posting that as you were posting your reply.

---

### Post by moffa on 2007-05-21
What video card do you have?  Also did you try to install the nvidia-glx drivers? The ones in the repository are broken for the 8800s

---

### Post by Miroku on 2007-05-21
well, i what i did do for my nvidia card was download the drivers from their website. i did not use the restricted drivers that came with feisty because they seem to not run as smooth as the ones from the website.

i am still not sure which logs to look at.

and i was rebooting out of my windows xp to get back into ubuntu.

the thing that is makin me upset is that it was running so nicely and all of a sudden, it just does this. i had the whole mac-like setup and everything.

i will try to get any information available to you guys that you need to help me figure this out. much thanks.

---

### Post by Miroku on 2007-05-21
i am a very impatient man it seems

i reformatted and reinstalled because that problem was just pissing me off.

i am kind of glad that i did though because now i have like a more complete feisty because before, i had upgraded from edgy so some things werent working correctly. but it seems like things are working correctly here and hopefully continue to go this way.

i will blame "an incorrect update" for that unexpected error.

i feel much better. =]

---

