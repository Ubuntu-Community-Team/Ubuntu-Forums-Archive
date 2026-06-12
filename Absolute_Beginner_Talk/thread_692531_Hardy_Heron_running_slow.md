---
title: "Hardy Heron running slow"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by nosushi4you on 2008-02-09
I installed Ubuntu 8.04 Hardy Heron, and I have noticed that it is running a bit choppy. Not entirely slow, but the web browser is a bit choppy. Opening programs takes a bit of time. My system specs are decent:
512MB RAM
2.66GHz
Intel Pentium 4
Radeon 7000 graphics card
Intel 82865g card. (I don't know which card it's using)

When I go to browse videos on youtube, they are a bit choppy and sluggish. I realize that this could be because of the flash, but I don't know. Is there a way to speed things up? What could be the problem?

---

### Post by nosushi4you on 2008-02-09
Also, just to let you know, 7.10 is not an option, as it doesn't detect my graphics cards.

---

### Post by R@inm@n on 2008-02-09
Isn't this release still in Beta?

 I didn't think it had been released for general use yet, just for development.


   R.

---

### Post by wabbster on 2008-05-05
I have a similar issue. I upgraded to Hardy from Gutsy (not a clean install). Here's a list of the few issues I've been having:

1. Startup is slow. The speed with which Gutsy booted amazed me, but Hardy is kind of making me tap my fingers (which was reserved for Windows bootups :P).

2. Compiz runs slow. Very slow indeed. The animations are a bit choppy and sometimes I get the impression that the system has temporarily died.

3. Video plugins are not working that well with Hardy too. Mplayer works the best with Hardy, but with Gutsy I had more options, like VLC, Totem and the rest.

I have an Intel Dual Core 3 GHz CPU with 1 GB RAM.

Any ideas??

Thanks!

Wabb.

---

### Post by Malta paul on 2008-05-06
Check and see if Grub is loading the latest Kernel.
I did an upgrade like you and Grub still booted up with the old kernel, making the system run slow. Changing the boot menu so that Grub booted with the latest kernel gave me a fast system again.
Have fun:)

---

### Post by Rever75 on 2008-05-17
Same here for me on my laptop. I did an upgrade to Hardy from Gutsy. I am also running an Intel Core Duo T7700 w/ 2GB of Ram and a 256 Nvidia 8600 GT. Start up time is horrible and display of GDM is even worse. Log in time is worse than my XP machine which SUCKED. With Gutsy everything was great and flew. I decided to move to Hardy since I like some of the new features. May have to reload back to Gutsy. I am also running the latest kernel, and have been following the bug reports for Firefox3 and the kernel scheduler issue.

---

### Post by janz84 on 2008-05-17
Just returned to Ubuntu yesterday... boy those new effects are nice... I enabled all the installation sources available and after fully updating the system I noticed all the sluggishness subside.

---

### Post by joshfulgencio on 2008-05-17
mine runs fine on 1 gig of RAM, Mite be ur unclean install?

---

### Post by egil_g on 2008-05-22
Mine run very slow when im on the internet (wireless). takes forever to open programs. when I disconnect the internet it runs normal. 

And according to the system monitor i have plenty of cpu-power and memory unused (both when im on the internet and not).

---

### Post by janz84 on 2008-05-22
egil_g: bad wireless driver?

---

### Post by phoenix_abhi on 2008-05-22
Wabb

I 2 have same specs and from mumbai. Initially I also updated from Gutsy to Hardy. But everything run smoothly. Later accidentally i removed Gnome and forced to make a clean installation. Woh It is running like 100 mtr sprinter compared to my Vista yaar. Making a clean installation and enabling restricted repos for hardy will do the magic again, I believe

---

### Post by lastknight02 on 2008-05-26
Hardy Heron running slow, eh? Try this: 

Go to System > Prefs > Appearance

Turn the Visual Effects to none. If you see a marked improvement in speed, your graphics card is probably not up to par - especially for the folks running Radeon cards. 

Just a thought. I've been working my tail off trying to get my Radeon 9250 to work right and, so far, I've got it at least doing something.

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
> **nosushi4you said:**
> I installed Ubuntu 8.04 Hardy Heron, and I have noticed that it is running a bit choppy. Not entirely slow, but the web browser is a bit choppy. Opening programs takes a bit of time. My system specs are decent:
512MB RAM
2.66GHz
Intel Pentium 4
Radeon 7000 graphics card
Intel 82865g card. (I don't know which card it's using)

When I go to browse videos on youtube, they are a bit choppy and sluggish. I realize that this could be because of the flash, but I don't know. Is there a way to speed things up? What could be the problem?

I have the **exact same problem**. My system also the **exact same specifications and models as yours**, except the graphics card( which I don't have). I would advice you to switch to alternate browsers like Opera, which don't consume 100-300 MB of RAM, like Firefox does. Ur _problem will be solved_.:)

---

### Post by d.kusummmanth@gmail.com on 2008-05-26
> **phoenix_abhi said:**
> Wabb

I 2 have same specs and from mumbai. Initially I also updated from Gutsy to Hardy. But everything run smoothly. Later accidentally i removed Gnome and forced to make a clean installation. Woh It is running like 100 mtr sprinter compared to my Vista yaar. Making a clean installation and enabling restricted repos for hardy will do the magic again, I believe

How will **enabling restricted repos** help? I don't get it!

---

### Post by Langsdorf on 2008-06-02
Ok, had the same problem with an Acer Travelmate 4650 and could solve it. Apparently Intels WLAN-drivers are somewhat messed up after upgrading from gutsy to hardy.

discussion: [http://ubuntuforums.org/showthread.php?t=704365](http://ubuntuforums.org/showthread.php?t=704365)
solution (at the end, delete /etc/udev/rules.d/70-persistent-net.rules and reboot): [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192845](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/192845)

Additionally, if you encounter long waiting time during "waiting for file systems" (or something like that), than you should slightly change your /boot/grub/menu.lst: [https://answers.launchpad.net/ubuntu/+question/29321](https://answers.launchpad.net/ubuntu/+question/29321)

Both lowered my starting time from 110secs to 50secs. Still much, but ok

Hope I could help

---

### Post by Si-Ddevil on 2008-06-04
I am having a similar problem, I am fairly new to linux (about 3 months) so please bear with my n00b like ramblings!

I was running gutsy before and it was silky smooth with little or no bugs (beside the screen saver showing as blank). last night i decided to upgrade to hardy (not a clean install) and the entire system is running sluggish (even with advanced desktop effects off!) the main problem seems to be a graphics issue as when playing a video in full screen i get around 5-10 fps but perfect sound, when the video is windowed to say half the screen size (around 640x480ish res) the frame rate improves slightly and is almost watchable. other problems like previewing a screen saver are ridiculously slow (previews worked fine before), compiz seems to run slow where it was beautiful before, opening windows (with effects enabled or disabled) is choppy, the internet is also very slow (dial-up slow) even though im using a 4 meg line which worked fine before, the system is not really usable by any stretch of the imagination as there seems to be a problem with almost everything! the CPU usage is a constant 30-40% when idle! can anyone enlighten me to any common problems with hardy that may be causing this? should I revert to gutsy? should i download the hardy dvd and do a clean install? any suggestions that don't include the word Microsoft are welcome and appreciated! :-D

Thanks
Si 

My system specs are as follows:
Athlon 64 3500+
2gig corsair ddr400
Asus a8n sli deluxe mobo
Sapphire radeon x800 gto2 (flashed to x850) PCI-E
2x ide drives and 1x sata drive 
Creative audigy 4 oem pci sound card

---

### Post by Langsdorf on 2008-06-08
hm, sounds strange. i encountered several problems upgrading from gutsy to hardy, maybe you should make a clean install. i did recently and everything works fine now.
perhaps you should try to activate your graphics card driver, this could be a reason. download new drivers, or deactive and activate them again. perhaps this will help

---

### Post by Si-Ddevil on 2008-06-15
I decided to bite the bullet and download the hardy LTS live cd and whaddya know... IT WORKS! only problem now being every few minutes my ntfs media drive clicks, spins down and is unreadable! :-( the root directory of it shows with folders and files but none of the files are readable (even though the thumbnails of the images are showing)!? anyone got any idea as to why? it works on boot or after a re-boot, i can watch videos,listen to music look at the photos but if i wanna change track or something and its been, say, 5/15/30 mins (seems to be random!) the folders show but no tracks! :-( this makes me sad, very sad! can anyone help me?....again :-P
Si

---

### Post by Uchiha_madara on 2008-06-15
I installed hardy clean Install 

The Slow Begin When I active the Effects


i don't now why???  :(

---

### Post by L337_K3y5 on 2008-06-15
> **wabbster said:**
> Mplayer works the best with Hardy, but with Gutsy I had more options, like VLC, Totem and the rest.
Wabb.
I think you can still have Totem, Vlc, and some more, just go into the synaptic package manager. :tongue:
I just downloaded Vlc, and some others today...:)

---

### Post by twilp on 2008-06-17
I was running Fiesty and did a clean install to Hardy Heron and everything ran well (lovely improvement) but kernel became corrupted after update and would not reload via Synaptic. Did second fresh install and encountered this painfully slow phenomena. All vis.effects are off and I'm wondering if this is caused by Evolution messing around and doing it's bit in Gnome (20secs into OO WP). Previously I had good speeds from....
(512MB RAM - AMD XP2000+ - NVidia 128MB (prop drivers) - ABIT KG7) Any help please, I'm getting frazzled?

---

