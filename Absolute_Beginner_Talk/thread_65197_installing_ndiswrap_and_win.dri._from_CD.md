---
title: "installing ndiswrap and win.dri. from CD?"
date: 2005-09-13
forum: Absolute Beginner Talk
---

### Post by fuscia on 2005-09-13
i'm thinking about installing ubuntu. i have a netgear USB wireless adapter and have just read of someone else's success in getting this thing working following this process [https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)
unfortunately, getting the wireless going is my only way to access the internet on this computer. can i download the ndiswrapper files and the windows driver files on my windows computer and then install those files onto the ubuntu installation from a CD? can i even use the installation CD that came with the adapter, or do  i need to somehow extract specific files from somewhere else?

---

### Post by davmac on 2005-09-13
You can do this. You'll need to get hold of the relevant *.inf and *.sys files for your wireless device. It should be possible to pick these out of the CD that came with the device but it could be that they're packed up in the installation stuff. You'll probably be best doing this under windows although it may be better to download the drivers from the manufacturers site and then you're sure of having the latest versions.

If you've got the space I'd recommend starting off with a dual boot setup. You can then download the relevant files using windows, reboot into Ubuntu, mount the windows partition (see [http://ubuntuguide.org/#windows](http://ubuntuguide.org/#windows)) and copy the files across to Ubuntu. If its not working you can then go back to windows, search around for the solution, download other bits 'n' pieces, etc.

Even if you don't intend to keep a windows partition on the machine it might be worth starting with a dual boot setup and then, once everything is working, getting rid of the windows partition.

HTH,

Dave Mac

---

### Post by fuscia on 2005-09-13
thanks, for the response, dave. unfortunately, i only have a 10gig hard drive and i'm running windows ME. i've looked into the possibility of partitioning, but that's even more confusing to me. fortunately, i don't need my computer for anything else than as a toy. 

so, check to see if i have this straight: 

i can download both ndiswrapper and the .inf and .sys files for my adapter, while still using ME, put them all on a CD while still using ME. then, install ubuntu and load these things from the CD on to ubuntu?

thanks.

---

### Post by davmac on 2005-09-13
Yes that should be OK. The problem here is, that if it doesn't work you're stuck. 

I think the safest way of doing this would be to get hold of the drivers and ndiswrapper stuff, keeping them on your windows drive, and then to have a go with the Ubuntu live-cd and get this working.

This means that you won't have had to trash your windows first and should give you the confidence that you've gathered together everything you need before doing a full Ubuntu install.

Dave Mac

---

### Post by fuscia on 2005-09-13
dave, are you suggesting i can do this on the live boot? i guess i would have to load the files in question with floppies, is that right? thanks.

---

### Post by davmac on 2005-09-14
Whoa! I've just being reading the howto for setting up ndiswrapper ([https://wiki.ubuntu.com//SetupNdiswrapperHowto](https://wiki.ubuntu.com//SetupNdiswrapperHowto)) and noticed the comment "...are you using a Live CD? If you are, give up now..." so this probably isn't the best way to proceed.

Working back through your posts, you mention that you've got a 10GB drive. How much space is Win ME taking up? I would have thought that, at a squeeze, you'll be able to set up a temporary dual boot system. If you uninstall and delete everything from windows that you can, then defragment the drive, how much space do you have left? 

Dave Mac

---

### Post by fuscia on 2005-09-14
i have 7.33gigs left. i really just want to get rid of windows, though. i'm sick of it. if the installation doesn't go well, i'll just re-install ME. it's freezing several times a day now, so if i stayed with it, i'd probably need to re-install it anyway. i don't have a whole lot of stuff to back up, so it's not really a big deal. also, partitioning adds another element i'm unfamiliar with and therefore, one more thing i could totally screw up.

despite the warning on trying to do this with the live CD, if there's a way to get the files on there, i can't imagine why i wouldn't be able to. it would be a lot of work for nothing, i suppose, but in the long run, it may make sense for a gnub like me to do. am i overlooking something on that?

---

### Post by davmac on 2005-09-14
If you're really not too worried about having to reinstall windows, then I'd say go for it! Gather together all of the files you think you'll need, including saving a copy of the Ubuntu Starter guide ([http://ubuntuguide.org/](http://ubuntuguide.org/)) to some removable media. Pop in the Ubuntu installation disk and give it a go.

Hope everything works out well, but I guess we won't hear anything until you get it sorted ;-) 

Regards,

Dave Mac

---

