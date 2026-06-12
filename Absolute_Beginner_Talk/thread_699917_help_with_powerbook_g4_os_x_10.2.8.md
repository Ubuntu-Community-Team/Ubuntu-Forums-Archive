---
title: "help with powerbook g4 os x 10.2.8"
date: 2008-02-17
forum: Absolute Beginner Talk
---

### Post by applehate on 2008-02-17
hello,
i am extremely interested in installing ubuntu on my prehistoric apple powerbook g4 (os x 10.2.8, bought in july 2003). i received the laptop as a graduation present and was quite thrilled with it at the beginning with the "superdrive" and iphoto application; however, it is currently collecting dust on the bottom of my bookshelf because i can barely connect to the internet with it. 

my friend installed ubuntu on his dell and it looks quite lovely. i watched him play around on it and although i didnt understand most of what he was doing, i saw that ubuntu was faster than the windows xp that he was running before and that ubuntu just might allow me to use my powerbook again. 

before anyone gets angry with me for being so green, i would like to say that i know absolutely NOTHING about computers. ive used apple computers for my entire life and the first time i even used a pc was 4 years ago. all i want is to be able to connect to the internet at a decent speed, download stuff and chat. 

i am downloading Ubuntu 7.10 (Gutsy Gibbon) as i type this post on my work computer and as far as i know, i am supposed to burn it onto a cd-r and install it on my powerbook? how do i delete os x? can i back everything up on an external hard drive? i have nothing of extreme importance on there besides my mp3s and photos.

i know there is something called gOS. would that be better for someone like me? it looks a lot like os x with the dock and all, but my friend configured his ubuntu to look like gOS to show me that you can do anything you want with ubuntu.

please forgive my ignorance. i was a fool for asking for a $2400 laptop that doesnt do a darn thing anymore. 

thank you in advance.

---

### Post by raydeen on 2008-02-18
Make sure that you download the PPC iso file. I'm not very familiar with 10.2 but if it has Disk Utility, you should be able to burn the ISO file to a blank disc. Or if you're doing it from a PC burn the ISO file to a blank disc with whatever program you use there. Then boot up with the disc on your laptop. If it's a Live CD, you'll be able to find out how well it will run. Depending on how much ram you have, it might be a good idea to go with an older version of Ubuntu or a smaller version like Xubuntu. I've put 7.04 on an old G4 but had to use the PPC Alternative install disc as the graphical installer was too much for the old beast. The Alternate CD uses a text based installer which is much faster the graphical install. Afterwards, if only the command line interface was installed, you can hook it up to the net and type

sudo apt-get update
sudo apt-get iinstall ubuntu-desktop

or 

sudo apt-get install kubuntu-desktop

if you like KDE. I often install both just to keep tabs on what's happening with each. It's also a good idea in case Gnome gets borked for some reason, you'll have another GUI to boot into.

And then you'll get the GUI after you reboot.

 gOS might work, d/l the live CD and find out. Edit: actually, that might not be an option as I don't know if they have a PPC version. Provided Enlightenment is in the repositories, you could make it look like gOS like your friend did.

Deleting OS X will pretty much happen automatically when you install Linux if you choose to use the entire disc. You *might* be able to do a dual boot with OS X but I'm not sure.

I'd hook an external drive up and get your stuff off first, or run a Firewire cable into another Mac and use Target Disk mode to transfer your music and pix off before you start clobbering the system.

---

