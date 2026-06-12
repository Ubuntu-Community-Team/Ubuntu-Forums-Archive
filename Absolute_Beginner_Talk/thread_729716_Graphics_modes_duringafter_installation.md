---
title: "Graphics modes during/after installation"
date: 2008-03-20
forum: Absolute Beginner Talk
---

### Post by costre on 2008-03-20
Just a quickie to point out something weird. 

When I boot from the Ubuntu AMD64 CD, the basic ubuntu system starts, and I can choose to install Ubuntu from the desktop. The resolution is 1920x1080, fits perfectly on my TV screen (DVI -> HDMI), and there is also 720p and standard 640x480. It's perfect for my needs.

But, then I actually install the OS and boot as usual. The graphics mode is still flawless, I can't believe how it seems to know my setup so well! 
I start the update manager, download the recommended updates, and reboot the computer. Then everything gets messed up.

When it boots, the resolution is 640x480 at the login screen. I can change the resolution somewhat, but it's stuck on 4:3 ratio resolutions, and not the 16:9 it was from scratch. If I choose a 1920x1080 LCD as my monitor (instead of "custom") it still only gives me 1440 as highest resolution possible. 
It doesnt seem to matter what I do, change the display settings, or change the graphics driver. I have downloaded Envy and let it try to sort things out, and I have downloaded the driver from Nvidia's site manually. Nothing works. 
And the worst part is, I can't shift back! I can't just disable the driver and go back to the old one. It's fu*ked for lack of a better word :)

I formatted and reinstalled four times yesterday, eventually I gave up and disabled the update manager altogether. Now the resolutions are still right for HD movies, also the 5.1 system works (it's a home cinema setup), but I lack the proper updates.

Ranting and raving ...

Anyone got any ideas, at all? I know I'm not listing any specifications, but if it's asked for I'll post them. Just not sure where to start ...

Thanks :)

---

### Post by ajgreeny on 2008-03-20
What graphics card do you use?  I assume you have used the Restricted Drivers manager in the system menu, but if it's something you've missed try that first and if no luck, then it's a case of doing some command line work to try and get the graphics driver working properly.  Alternatively you could try copying the** /etc/X11/xorg.conf** file from a running live CD to the same place in your installed version and see if that does the trick.

---

### Post by costre on 2008-03-20
I've gone back and forth between the restricted driver and the original ("nvidia" vs. "nv"), nothing seems to work. 
Good idea about the xorg.conf, I'll see what happens. 

For now, I'll settle running an not-up-to-date system. At least the fundamentals are working flawlessly :)

---

### Post by costre on 2008-03-23
Well, it's ****** up again.
I don't even know what happened. I noticed my 5.1 output wasn't working, I rebooted, and the screen turned to 640x480. I can't change anything, resolution, monitor, graphics card ...

My system appearantly is up-to-date, which is odd since I disabled automatic updates. Nothing to do but to install again, again, and hope things work out. 

Any tips on where to find xorg.conf in the ubuntu install-cd is appreciated. I can't get the search-function to work, I can even search for files that are clearly present, and nothing shows up.

EDIT: UPDATE

I installed Ubuntu fresh. Had 1920x1080 all during installation. Formatted the filesystem partition clean. Booted after installation, Only had 640 and 720p to choose from. Rebooted, and found myself with 640x480, only. Resolutions just drop off without reason. I'm going to tweak a bit more, the probably go back to XP. I can't take much more.

---

### Post by costre on 2008-03-26
Another update.

I reinstalled again. As usual, everything was perfect right after the installation. I chose to download all updates, make my system up-to-date, and reboot. All was still well!
Yesterday my internet went down for some reason. When I got back from work today, my computer had rebooted, and I only had 640x480 to choose from ...
Perhaps I should try Hardy Heron? I saw Envy had a Heron-only version, perhaps there is more graphics-related changes made?

EDIT:

I chose a different monitor, "Generic widescreen 1920x1080" instead of the one selected, "Plug'n'Play". I was then able to choose 1280x720. It's not perfect, but it's something.

Also, when I boot with the installation CD (and everything works), it says my monitor is "Custom". After installation, I can't even select "Custom" from the list :|

---

### Post by costre on 2008-03-31
Just wanted to say that an upgrade to Hardy made all problems go away, at least up until this moment.

The graphics card displays graphics during boot-up (in Gutsy the screen lost signal during boot-up), the Nvidia driver supplied by Envy works, it doesn't change modes or drop resolutions on me, and the screen autodetects and all it's settings remain intact over time.

God knows what went wrong for me in Gutsy, but all is well now. Can't wait for the official release of Hardy. :KS

---

