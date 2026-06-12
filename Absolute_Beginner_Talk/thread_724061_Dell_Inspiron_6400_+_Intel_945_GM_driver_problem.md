---
title: "Dell Inspiron 6400 + Intel 945 GM driver problem"
date: 2008-03-14
forum: Absolute Beginner Talk
---

### Post by aachen on 2008-03-14
Hi all,

I just installed ubuntu 1 day ago. I have Dell inspiron 6400 dual boot system XP and ubuntu with Intel 945 Graphics Media accelerator driver.

Initially my computer was working with max. resolution 1280x800.
But then I tried to play around and installed Intel i810 driver as I had heard that i810 works best with 945GM but now my computer doesnt boot at all.

It gives me some messages on black screen and fails to boot.
Is there any way out to revert back to the previous functioning driver from command line? I even dont remember the name of that previous driver. It was something Intel general driver, not any specialised driver.

I dont know how to use recovery mode as I am new to linux.
Please help otherwise I have to reinstall ubuntu.
Also let me know which is the best driver for 945GM.

---

### Post by dca on 2008-03-14
Don't quote me on this, but if you're using Gutsy then the '915resolution' package would've already been installed & config during OS installation.  You don't need any other(s)...  If you can get to CLI you can probably type in 'sudo apt-get -r 810resolution' or whatever the package name is and remove it...  I couldn't tell you if it automagically revert back to the orig driver.  And of course that's provided you d/l & installed the package from the repos, not from Intel's site.

---

### Post by (((X))) on 2008-03-14
I think it's just intel
I synaptic it is xserver-xorg-video-intel
i810 can be used, by selecting monitor you want use, not sure about gnome, kde has that option.

just reconfigure xorg from the terminal, boot in recovery mode and type:
dpkg-reconfigure xserver-xorg

---

### Post by aachen on 2008-03-14
Yes I am using Gutsy and the previous driver was installed from the repository. But I dont know anything about 915 resolution. I will check this and remove this 810i from recovery mode. and then let you know if it works again or not.
Thanks a lot.

---

### Post by dca on 2008-03-14
I'm not by my Ubuntu at this time to check the actual Intel package names on my system.  I just remember before Gutsy came out (6.06, 6.10, & 7.04) if I had a system running any kind of on-board Intel accelerator I needed to install the '915resolution' package to get widescreen or other settings besides just 1024x768...

---

### Post by (((X))) on 2008-03-14
945resolution is not installed on my ubuntu 7.10 and I have widescreen with several resolutions possible.

---

