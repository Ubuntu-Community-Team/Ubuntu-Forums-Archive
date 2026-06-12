---
title: "ATI Driver!!!"
date: 2007-10-21
forum: Absolute Beginner Talk
---

### Post by comatose-linux on 2007-10-21
Ok, I did a clean install to 7.10. Looks great, clicked to get proprietary driver. EXCELLENT! looked good. I enable all eyecandy effects, wow, looks great.  Ok, I logged off (not even a restart), it went to 800X600. Nothing I can do to get it back. I reconfigured X, and it looks fine, but it is SO unusable because of how slow it is.  Here is what I have:

P4, 256MB RAM, 40GB HD, ATI Radeon 9600 128MB, Dell 2005fpw LCD (1680X1050)

Why is it that it worked for a while, and then stopped? I tried reloading between the two proprietary drivers (gslx and gldev I think it was), but it just won't run at the full resolution. It is, however, running the prop drivers but at 800x600 but that's it.

What's really strange is that when I run the "test" mode to see if it all works, it looks good. However, after doing the reboot to make the change, it says it can't. WTF?

I tried changing to generic flat lcd panel at 1680X1050, but it just changed it back to the Dell and not on widescreen...good old 800x600...ERRRRRRR!](*,)

Please help! Oh, and I'm not THAT absolute beginner..i used to run mandrake server back in the day...
Just new to ubuntu/debian...

thanks

---

### Post by Pumalite on 2007-10-21
It's your RAM. With that RAM you should have Xubuntu if you want a fast system.

---

### Post by linuxlizard on 2007-10-21
"It's your RAM"

Maybe, maybe not. I set up feisty for my folks last spring and it is has specs similar with 256 m ram, amd athlon 2000+ or 1800+ (can't remember which), an old nvidia card with 64 or 128 mb (can't remember which but pretty sure it was 64) and beryl with the cube, emerald, 3d floating windows when the cube is activated and all the 3d games I could stick on there for my nephews like urban terror, warsow, legends, etc, and everything zips along very quick and looks smooth as silk.

That said, i have no solution to the problem. Just would be surprised if suddenly the system requirements jumped that much in a single release.

Oh- it was kubuntu though, not ubuntu. But I thought KDE is supposed to be a little more demanding on the system than gnome.

---

### Post by flawedreality5 on 2007-10-21
I too am having this exact problem with my 256mb Radeon x850xt. By default after a fresh install of Gusty, it goes to under Graphics Card (ATI Radeon): ati - ATI Mach8, Mach32....My monitor is offset by about 4 pixels to the right offscreen. All previous version of any Linux do this so I guess just problems detecting my cheap Proview monitor settings. When I installed the ATI proprietary drivers in 6.10 (my previous version), the screen goes center and 3d accel. is on, worked perfectly. 
However now when I try to install the Restricted Drivers, I get the exact same problem as the original poster. It says I'm using a plug and play monitor with max 800x600 at 61hz vs the default after the OS install, Monitor: Custom1 with 1280x1024 @ 60hz. Everytime I try to change a setting it says to restart. After doing so, it just defaults to 800x600 everytime. It doesn't even say FGLRX is being used, even though it's checked under the Restricted Drivers menu. I think it said Vesa drivers were being used for both. No matter what I couldn't change it.

---

### Post by asrnet on 2007-10-21
I had the same problem with vesa driver appearing.

This worked for me(new to Ubuntu):
System > Administration > Restricted drivers manager
Uncheck the ATI driver and reboot and go back and install it again

Then select fglrx driver under Screens and graphics

---

### Post by the_blur on 2007-10-21
Having the exact same issue, it worked perfectly when first installed, I wanted to make a media box out of my living room PC, but s-video is no longer working and I can't get the video driver installed.

What I really need is for the computer to use my svideo out as the default monitor with no other monitors attached, so that I can browse my server from here and select videos to watch.

So my question would be: How to install the driver and make it stick, how to have it use svideo out by default as the main screen with no other screen attached (this works in windows on this computer, however winxp is no longer installed).

A different problem somewhat in the same vein is my 424UB V.2 trendnet wireless adapter.

Using ndiswrapper, I can finangle a connection that once working, works great. But as soon as I reboot, the driver is installed but it doesn't connect to my base station I have to fiddle with it every single time... :(

help would be greatly appreciated, since this computer is actually a pilot project for me, I would like to have my file / torrent server running ubuntu as well...

---

### Post by Kymus on 2007-10-21
similar issues for me as well

Installed Gutsy without a hitch, then it's talking about restricted drivers so I'm all "yeah sure, ok *click*"after a reboot, it's forced into safe graphics (?) mode. I then select my video card and monitor from the list, change the resolution back to 1280x960, it says I gotta restart for the changes to be saved.. ok. Rise, lather, repeat... same problem. Ok. I uncheck the *ATI accelerated graphics driver*, reset screen resolution, blah blah blah, reset, and of course it's cursing me off again... fantastic. Tried using Envy to see if that would change anything and... nope! It seems to be stable as long as I don't reboot. But once I do... ugh, it doesn't like me much when it comes back to the login screen.:mad:

I'm using an ATI Radeon X800GTO

---

### Post by comatose-linux on 2007-10-21
Wow, nice quick  responses. Well, I would blame the RAM except that it worked for like 4 hours without a hitch. As soon as I logged off and came back in, graphics safe mode forever more. I'm tempted to reinstall again since it is a fresh install. I would loose a little customization since the install, but it was only a few hours worth of work.

---

### Post by doooh_head on 2007-10-21
I experienced this exact same problem.  What I did was to reboot my computer and boot up an older kernel.  After upgrading to Gutsy, I had two kernels in my GRUB boot screen.  When it came up I was able to choose my correct resolution and everything worked as expected.  I worked with it like this for a day or two, then I finally rebooted and started up the latest kernel again and lo and behold, all of my settings stuck!  

I've got all of the eye-candy working flawlessly.  My only outstanding issue is that I have dual monitors so I'm just waiting on the instructions for enabling that once again.  It'd be nice to have the dual monitors working with the eye-candy but under Fiesty I was satisfied with the eye-candy not working, so I imagine I'd be ok with it like that under Gutsy but I'd be really disappointed.

---

### Post by Kymus on 2007-10-21
> **doooh_head said:**
> I experienced this exact same problem.  What I did was to reboot my computer and boot up an older kernel.  After upgrading to Gutsy, I had two kernels in my GRUB boot screen.  When it came up I was able to choose my correct resolution and everything worked as expected.  I worked with it like this for a day or two, then I finally rebooted and started up the latest kernel again and lo and behold, all of my settings stuck!  

I've got all of the eye-candy working flawlessly.  My only outstanding issue is that I have dual monitors so I'm just waiting on the instructions for enabling that once again.  It'd be nice to have the dual monitors working with the eye-candy but under Fiesty I was satisfied with the eye-candy not working, so I imagine I'd be ok with it like that under Gutsy but I'd be really disappointed.

Interesting. So you just booted to the older kernel and that's it?

---

### Post by Pumalite on 2007-10-21
I'm amazed. If you have a fast system I'll eat my shoe.

---

### Post by doooh_head on 2007-10-22
> **Kymus said:**
> Interesting. So you just booted to the older kernel and that's it?

Yes, thats all I did.  Oh don't get me wrong, its not the magical cure-all.  I'm just describing what I did.  I have no explanation for it.  Perhaps if I'd simply rebooted and relaunched the same (New) kernel at that time, that it also would have worked.  It doesn't make any sense to me that things started working after launching the older kernel, but it did...for me.

---

### Post by comatose-linux on 2007-10-22
Ok, solved..Reloaded Gutsy :(  oh well. I'm am VERY afraid of trying the proprietary drivers now, but the open source ones seem to work quickly enough now after reinstall..what gives? When I reconfigured X before, it ran like a dog. Anyhow, thanks for all the help. It runs good with full eye candy, not blazing fast but good.

---

### Post by jdong on 2007-10-22
> **linuxlizard said:**
> "It's your RAM"

Maybe, maybe not. I set up feisty for my folks last spring and it is has specs similar with 256 m ram, amd athlon 2000+ or 1800+ (can't remember which), an old nvidia card with 64 or 128 mb (can't remember which but pretty sure it was 64) and beryl with the cube, emerald, 3d floating windows when the cube is activated and all the 3d games I could stick on there for my nephews like urban terror, warsow, legends, etc, and everything zips along very quick and looks smooth as silk.
]/quote]
256MB is a lot different than 128MB, especially considering that the "critical" bootup RAM consumption for Ubuntu is around 150MB. And you have an interesting definition of "old" nvidia card too -- my best desktop video card has 32MB RAM :)


[quote]

That said, i have no solution to the problem. Just would be surprised if suddenly the system requirements jumped that much in a single release.

Oh- it was kubuntu though, not ubuntu. But I thought KDE is supposed to be a little more demanding on the system than gnome.

The official recommendation is 256MB runs Ubuntu at the bare minimum level but should be installed with the only-ubiquity argument or by an alternate installer, while 384 is "ideal". The addition of desktop effects increases RAM consumption to a significant extent should you elect to use it, plus those who start running big applications like Firefox or Openoffice are bound to feel the disk thrash with just 256MB RAM.


P.S. Completely off topic, but KDE/GNOME are pretty equivalent in RAM usage, KDE is slightly lower if you "strip down" the default apps that load, and KDE is a big win for RAM consumption if you use all KDE apps. For example, launching Konqueror on top of a base KDE bootup requires like 1/4 the RAM that launching Firefox on top of GNOME requires.

---

### Post by flawedreality5 on 2007-10-22
Compiz and everything works fine for me right now with the default drivers. I'm just going to wait until the new ATI 8.42 drivers come out to upgrade and hope that solves the problem. I just hope they come out soon.

---

