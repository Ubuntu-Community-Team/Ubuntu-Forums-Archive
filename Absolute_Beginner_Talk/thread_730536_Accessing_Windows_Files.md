---
title: "Accessing Windows Files"
date: 2008-03-21
forum: Absolute Beginner Talk
---

### Post by brandonclyon on 2008-03-21
Hey all,

Just got around to installing 7.1 as my first distro of linux...well I had played around with suse for a bit but didnt really like it at the time...


Anyways, I was able to mount all of my NTFS drives, even my primary windows partition..though that took some doing since its a SATA drive, but thats done...now I have another issue that I really really hope I can get resolved.

I recently read an article about running windows apps seamlessly in Ubuntu using Virtualbox, I looked into this but this wants you to install a new copy of XP inside of a virtual shell.

Is there anyway that I can use my existing install of XP and run the apps seamlessly? I tried using WINE but there are some apps that it either wont load or loads in a barely usable mode (Myspace IM for instance).

Any assistance would be greatly appreciated.

---

### Post by igknighted on 2008-03-21
> **brandonclyon said:**
> Hey all,

Just got around to installing 7.1 as my first distro of linux...well I had played around with suse for a bit but didnt really like it at the time...


Anyways, I was able to mount all of my NTFS drives, even my primary windows partition..though that took some doing since its a SATA drive, but thats done...now I have another issue that I really really hope I can get resolved.

I recently read an article about running windows apps seamlessly in Ubuntu using Virtualbox, I looked into this but this wants you to install a new copy of XP inside of a virtual shell.

Is there anyway that I can use my existing install of XP and run the apps seamlessly? I tried using WINE but there are some apps that it either wont load or loads in a barely usable mode (Myspace IM for instance).

Any assistance would be greatly appreciated.

While it is *possible*, you cannot do so without breaking the EULA and tripping WGA into forcing you to re-activate every time you reboot (virtualized hardware != actual hardware... so unless you are running a retail version you cannot transfer it.  Not to mention even if it is legal (with the retail version) who wants to re-activate every reboot?).

---

### Post by brandonclyon on 2008-03-21
thanks for the quick reply. I suppose I might just have to run the virtual box way.

I would like to switch entirely to ubuntu but I would hate to have to install all my windows programs again since WINEs compatibility with some XP progs isnt the best.

---

### Post by asmoore82 on 2008-03-21
IMO, re-installing inside VirtualBox is well worth the effort if you have enough Horsepower/RAM.

VirtualBox also gives you the added benefit of being able to Snapshot your entire virtualized OS.
It's the only way to 100% safely test out "new" Windows Apps without risk of junking up the registry.

---

### Post by igknighted on 2008-03-21
> **brandonclyon said:**
> thanks for the quick reply. I suppose I might just have to run the virtual box way.

I would like to switch entirely to ubuntu but I would hate to have to install all my windows programs again since WINEs compatibility with some XP progs isnt the best.

What programs do you need?  99 times out or 100 there is an equally capable linux-native application that just is buried in the repo's somewhere that could do what you need.

---

### Post by brandonclyon on 2008-03-21
The main ones I am concerned with are Total Video Converter, ConvertXtoDVD and Ultima Online.

I do a lot of video editing/ripping/burning and I loves my classic MMOs.

---

### Post by Paqman on 2008-03-21
Have a look in the repos, there's loads of aps in there for DVD ripping/converting.

---

### Post by brandonclyon on 2008-03-21
Ill be sure to take a look when I get home. The other issue that I would like some assistance with is that I have 2 monitors set up, looking around in the settings I did not see an option to enable my second screen so I could have the extra workspace.

Also it will only allow me to set my resolution to a max of 1280x1024. This is normally fine but I am confused as to why it wont let me set it to something higher.

I currently have an ATI x1650 512MB PCI-ex video card using the drivers that were already installed. I recieved an error message that it was proprietary but that ubuntu will try to load it anyway, could this be causing the problem?

---

### Post by Paqman on 2008-03-21
> **brandonclyon said:**
> 
I recieved an error message that it was proprietary but that ubuntu will try to load it anyway, could this be causing the problem?

No, that's just Ubuntu automating something that used to be a real pain. It's a really good feature that has made lots of people's lives easier.

---

### Post by brandonclyon on 2008-03-21
Thanks for all the help, as far as gaming goes on Ubuntu, how good is the support for Windows based games through Wine?

I have seen people that were able to do WoW and Diablo 2, but what about some of the even newer games like Gears of War and soon to be Mass Effect PC versions?

---

