---
title: "[SOLVED] Video Card Upgrade"
date: 2007-12-17
forum: Absolute Beginner Talk
---

### Post by flyby4 on 2007-12-17
Was thinking of upgrading my video card.  I have read on a post somewhere on this forum that this causes a problem with X but can not now find the post.   Is there a how to for this somewhere?  I would appreciate someone pointing me in the right direction.

Thanks

---

### Post by nowshining on 2007-12-17
well no actually, u just will have to install the driver if nvidia from the command line, do u plan on getting a nvidia brand video card, if so u'll just unable to startx

if u get stuck in a command line, sign in by typing ur name and then ur password NOTE: password will NOT show while u type this is for security - just type it out as usual and then hit enter.

now:

if getting a nvidia card:

download to a place on ur local computer such as the desktop

32bit computer:[http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run](http://us.download.nvidia.com/XFree86/Linux-x86/100.14.19/NVIDIA-Linux-x86-100.14.19-pkg1.run)
64bit computer:[ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run](ftp://download.nvidia.com/XFree86/Linux-ia64/1.0-5336/NVIDIA-Linux-ia64-1.0-5336-pkg1.run)

once in the console cli command line mode cd to the directory where u saved it

example saved to Desktop:

cd /Desktop

from there 

type

sudo sh NV and the hit the tab key to autocomplete assuming u don't have any other desktop files starting with NV (unix/linux is case sensative by the way), from there follow the directions when asked to download from the ftp site - i suggest a NO and then at the end yes for it to update ur config file, then at the terminal type

startx

or reboot.

u'll also need to do a re-install of it on a new kernel update so i suggest keeping it somewhere handy..

---

### Post by Severun on 2007-12-17
It causes a problem with X if you do not re-configure it to use your new video card.  If you tell X that you have a new video card and correctly tell it what kind it is, there is no problem.

I would post a different question:

I am thinking of upgrading my video card.  What cards have people had good experience with under Ubuntu.  Myself I won't go ATI again, I'll probably go Nvidia since I had far fewer problems getting it to work with all the bells and whistels.

Once you get your new card installed, depending on the card you have come back here to the forums and do a search in the forums for "cardname install howto" or something like that and you'll probably find multiple people that have posted howto's on how to properly setup your particular type of card.

---

### Post by flyby4 on 2007-12-19
Thanks for your help.  I ended up getting a nvidia card because I already had a very old nvidia card (TNT2 32Mb) in the box and most people seem to have less issues with them.  My assumption was that the newer card would understand what the old nvidia driver was doing.

Changing from one nvida card to another was very smooth.  I had already added the restricted driver repository (don't know if I have the correct words here) included.  I had done this to try and get Beryl working.  That was a disaster as the card was too old and was unsuported.  X would not start and ended up manually editing the config file.

Ubuntu detected the card change and reconfigured X, got new drivers etc.  Just a restart and effects etc worked ok.

I was expecting a disaster but it didn't happen.  I have an image anyway so just would have wasted some time.

---

