---
title: "Dell video card ridiculousness"
date: 2006-08-15
forum: Absolute Beginner Talk
---

### Post by hAvAAck on 2006-08-15
I have a dell desktop PC (boo Dell) and I'm looking to install ubuntu on a blank 40gig partition I have and dual-boot with XP. I've never used linux, but I'm interested in giving it a try. A problem I've run into with windows is that I use a "All-in-wonder VE PCI" video card in windows. I have to disable the video card that came with the dell computer (and is saudered in place). It is a "Intel 82845G/GL/GE/PE/GV graphics controller" whatever that is. The problem I run into is that my monitor is plugged into the PCI slot video card and therefore I cannot view anything pre-windows boot-up unless I unplug my monitor and put it back in the default video card. I'm wondering a few things.
1) To use GRUB will I need to run off of the default video card? as that is what I need to use when going into BIOS
2) How will Ubuntu react to the two video controllers? Will I need to disable one in Ubuntu like I did in windows or will I be given options upon install?
3) Will Ubuntu even recognize the PCI slot controller if I have to run off of the default "Intel" controller in order to install anyway?
Thanks for any answers, and I can't wait to dive into Ubuntu and start learning (and most likely asking more questions in these forums)
hAvAAck

---

### Post by VirtuAlex on 2006-08-15
Are you sure you do not have an option in BIOS to disable onboard video card?

---

### Post by Greycloak on 2006-08-15
The BIOS should definitely have the option to disable the onboard. I had to do that on my old Dell Optiplex machine when using my Radeon 9200 PCI.

---

### Post by hAvAAck on 2006-08-15
In my infinite wisdom I never thought of that. I went ahead and did that but now windows (in its infinite wisdom) detects 6 new unknown hardware devices. *sigh*
Thanks for advice though!
Now to install Ubuntu :)

---

### Post by hAvAAck on 2006-08-16
As noted [here](http://www.ubuntuforums.org/showthread.php?t=237214) this video card ridiculousness is in fact messing with my attempts to install Ubuntu. I figured I'd update this in case anyone in the future did a search and came up with this solution, it is not working properly. I had to re-enabled the onboard card for Ubuntu to even boot up without giving Kernel Panic errors.

---

### Post by orb9220 on 2006-08-16
Well if you disable the onboard video after installing unbuntu then yes it wil mess everything up.

I had to reinstall ubuntu on a friemds computer after disabling the on board video because he was in the same boat as you. He still had the concept of plug and play scenaro in his brain.

After that no more problems.

---

### Post by hAvAAck on 2006-08-16
So is it most likely that I will just need to use my onboard video card for Ubuntu and my PCI slot video card will only be useful in windows? Or will Ubuntu have options within it to disable the onboard one through it instead of the BIOS and run through the PCI slot card? I'm just worried because I have the feeling I'll need the onboard card to see the GRUB, but I only have one monitor and that will require a lot of plugging and unplugging. Might it be that Ubuntu just doesn't support this particular PCI video card and I need to go out and get a newer one?
Thanks for your help.

---

### Post by orb9220 on 2006-08-16
If you reinstall ubuntu with the onboard video disabled first then ubuntu should see the video card.

To test this ahead of time go into bios and disable onboard video, set cdrom as first boot device and boot the liveCD again and see if that works.If you get to desktop then you just need to reinstall clean again.

That would probally fix it and I am not knowledgable enough to know of another easier way.

---

### Post by hAvAAck on 2006-08-16
Thanks orb9220
When I disabled the onboard video card through BIOS Ubuntu will not load. It freezes with Kernel Panic.
When I re-enabled the onboard video card Ubuntu loaded fine, but I have not installed it yet.
My concern is that I use the PCI video card in windows XP and I'm planning on dual booting. I can't get to the BIOS or linux without unplugging my monitor from PCI and putting it back into the default card.
Is there a better way around this? Will the GRUB always require me to be plugged into the original card? Will linux recognize the PCI card after I install using the original card?
I'm sorry if I'm not conveying myself clearly enough, it's sort of confusing to me, myself.
I just want to get Ubuntu in, have the option to dual boot, and begin to experiment and learn Ubuntu without having to keep changing in to where my monitor is plugged.
Is the problem the way Dell set up the onboard card, or is the problem that the PCI card just isn't linux-compatable?

---

### Post by Tuxtur on 2006-08-16
I have a Dell and had the same kernal panic when trying to use an nVidia video PCI card. Looks to me like a bug in Dell's bios. What I had to do was first set the BIOs to use the onboard video to install Ubuntu. This will get the OS installed. Once Ubuntu is installed then in terminal I had to "sudo nano -w /etc/modprobe.d/blacklist" at the bottom add

"blacklist agpgart"
"blacklist intel_agp"

control+X to exit and save file

what that does is prevent the kernal panic. Now you can go about trying to get your video card working. The forums are full of instructions. Search on Tseliot and NVIDIA he seems to know the most about this stuff. His tips have helped me.

---

### Post by hAvAAck on 2006-08-16
Awesome Tuxtur, thanks a lot. I'll install the OS later today and fiddle around with what you said. After I prevent the kernal panic should I go back into BIOS and disable the onboard video and see if Ubuntu will still boot up (so I can still hit the GRUB with my PCI video)? Or should I look to disable the onboard video from within Ubuntu (similar to how I did it with XP)?
Regards,
hAvAAck

---

### Post by Tuxtur on 2006-08-16
1. set bios to use onboard video and connect your monitor to the onboard video connector. This will avoid the kernal panic
2. install ubunto to hard drive
3. blacklist the onboard video. this will prevent the kernal panic.
4. now you can basically use either the onboard video or the PCI video card, it will all depend on what your bios is set to use and where you have the monitor plugged in. If you want to use onboard video set the bios to onboard and plug the monitor into that port. to use the PCI video card you set the bios to that cards setting (sorry can't recall how they phrase it) and plug the monitor into the PCI video card port on the back. NOTE: your onboard video is going to act strange because you have blacklisted it, but in my case it does still work.
5. Now you have to setup your PCI Video card. Tons of instructions around here on that. Like I said look for Tseliot's posts he could write a book on this issue. Thats where I picked up what little I know

---

### Post by hAvAAck on 2006-08-16
Thanks so much Tuxtur, I also found a [thread ](http://www.ubuntuforums.org/showthread.php?t=235145&highlight=ATI+all-in-wonder) by Kilz that seems it might be able to help me out. I appreciate your patience and support! I'm going to go ahead with the Ubuntu install and mess around with what you suggested and just hope it doesn't inadvertantly currupt my other 2 partitions. 
Regards,
hAvAAck

---

### Post by Tuxtur on 2006-08-16
The important thing is to learn about the blacklist trick. Once you got that sorted out its basically just following the normal setup instructions for your card.

Good Luck!

---

