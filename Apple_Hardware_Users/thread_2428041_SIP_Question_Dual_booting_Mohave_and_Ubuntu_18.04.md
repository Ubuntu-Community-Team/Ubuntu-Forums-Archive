---
title: "SIP Question: Dual booting Mohave and Ubuntu 18.04"
date: 2019-09-29
forum: Apple Hardware Users
---

### Post by llamabr on 2019-09-29
Hello, Mac Ubuntuers. I triple boot OSX, Ubuntu, and Debian on my late 2015 imac. According to the instructions I followed, I disabled SIP to install refind, which now runs correctly.

I've finished installing the OS's. I boot into refind, select the OS, and boot correctly. Hooray!

Question: Now that I have everything set up and I'm happy, should I re-enable SIP? That is, was disabling it just for the install? Or, if I re-enable it, will it mess with something important that refind is doing, such as reading or writing to the booloader, etc? I'm not really an OSX expert and I don't want to leave it vulnerable, since I don't really know what to watch for.

Thanks a bunch

---

### Post by llamabr on 2019-10-01
Not to hijack my own thread, but I was able to fix a weirdness about the resolution. Although it's 5K, I'm able to load both    3840x2160   and    2560x1440. However, at 3840x2160, everything is tiny, particularly in Windowmaker, which is my preferred WM (along with dozens of other people in 2019, probably). 2560x1440 looked much better, but the weirdness was that the screen was bigger than the screen: that is, some elements would float off to the right and be unfindable. Likewise putting a video full screen would only show me the left 2/3 of it or so, meaning that the display thought it was wider than my screen, despite the correct 16:9 aspect ratio.

xrandr to the rescue. I installed LightDM, because it's a superior DM in basically every way, obviously. I created:

~/bin/resolutionxrandr.sh
> #!/usr/bin/env sh
xrandr --output eDP --primary --mode 2560x1440

Run it with:
> cd bin
chmod 755 resolutionxrandr.sh
./resolutionxrandr.sh

Then a very simple:

> brock@phasma:~$ sudo ln ~/.config/monitors.xml /var/lib/lightdm/.config/monitors.xml 

No. A symbolic link won't work. And voila (or as my students write, "walla"): LightDM's resolution is fixed, my WM's resolution is fixed and permanant, and the right-fading weirdness is gone. In case it helps someone else with a late 2015 imac dual boot Ubuntu OSX MacOS.

I am still curious about the SIP question, if anyone has any feedback. Bump! Thanks.

---

