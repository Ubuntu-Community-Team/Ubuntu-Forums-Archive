---
title: "If I split my laptop with vista/linux..."
date: 2007-10-23
forum: Absolute Beginner Talk
---

### Post by shucks on 2007-10-23
I have a laptop with vista right now but I want to try putting linux on it too. Not getting rid of vista but just trying both. I know how to do it, there are instructions on a site, but...

Are there any chances of messing up the laptop?

How much space does it take up?

Will the nVidia graphics card automatically work or will I need to download it again?

What's the difference between Ubuntu and all those other linux things? I forgot the other names..

---

### Post by chuckyp on 2007-10-23
There isn't really a chance of you messign up physical hardware on the laptop.   Anytime you install software or you are attempting to dual boot you could mess up the first operating system.  In your case possibly not being able to boot to vista without fixing it.  With the newer installers out there for linux it should pick up that vista is installed and create a bootloader for you etc... 

It will only take up as much space as you let it.  I recomend resizing your Vista partition from within windows with their disk management tool.

The nvidia card will function with a default install; however, 3d and GL won't be enabled by default you would need to install the nvidia-glx-new package.  The restricted device manager in ubuntu will notify of this on your first boot.

The difference between Ubuntu and the other distributions is kind of hard to explain.  I have found the best support and community right now is in Ubuntu.  But each distro has their own perks.

---

### Post by shucks on 2007-10-23
on average how much space would linux consume with all the basic functions needed? I only have 80gb total on my laptop and right now only 20gb free. How likely is it that installing linux will mess up my vista?

---

### Post by chuckyp on 2007-10-23
You could give it 5 gigs just to play arround.  I think once installed its a little over 1gig.  As long as your read everythign as you go you should be okay.  Just don't be dleeting your vista partition.   There is a possiblity that grub won't recognize vista but you can always fix that with a windows disk or just editing the menu.1st.   I would just find a good howto before you begin and read everythign on the screen.

---

### Post by shucks on 2007-10-23
ook thanks for replying so quickly. btw is there some sort of site that tells you all the basic commands for linux and what kind of programs to get? Like I'm not sure if ctrl-alt-delete has the same function on linux and whatnot.

---

### Post by hyper_ch on 2007-10-23
ctrl-alt-delete is by default starting the screensaver and locking the computer ;)

Programs: You'll see
Commands: ask if you need a specific one ;)

A good place to read before you start:
[http://www.psychocats.net/ubuntu/index.php](http://www.psychocats.net/ubuntu/index.php)

Once installed, a good place to read more:
[http://www.ubuntuguide.org](http://www.ubuntuguide.org)

Both are trimmed to Feisty (the previous release) but most of that should apply to Gutsy.

Regarding resizing your partition: Use the VISTA partitioning tool to do that and before you actually do it: BACKUP YOUR DATA!!!

---

### Post by natehatewindows on 2007-10-23
im doing what you want, dual booting vista and unbuntu 7.10. I have had no problems (no sound yet in gusty but that i hope will change soon). you dont need much room especially if you use 7.10 becasue you can write to your vista partition (ntfs).....i would give it a shot....ubuntu is a amazing OS and a must try. :)

good luck!

---

