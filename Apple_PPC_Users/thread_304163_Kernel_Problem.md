---
title: "Kernel Problem?"
date: 2006-11-21
forum: Apple PPC Users
---

### Post by RuDeE on 2006-11-21
I am running an ibook 700 mhz.

I upgraded to Ubuntu 6.10, and after lid close and reopen my screen appears. However when it tries to refresh the refreshed screen is made of vert. lines of color. The sweet sound of hardware doing its thing is also in the back ground, but still no good. I have tried restarting xorg with ctrl-mac-esc.. i have tried all ctrl-mac-... / ctrl-atl-... combinations in order to refresh xorg, but nothing works. I have to reboot. 

Now, I had a similar problem with the last release (after lid reopen my screen was blank instead, despite the gentle clicking of hardware in the back ground), 6.06. however, the kernel that was released as an update fixed my problem. 
the old kernel that worked was:
2.6.15-27-powerpc,
so i tried deleting /boot/vmlinux and /boot/initrd.img and recreating a link to the old kernel that was stable.

like so with both:
ln -s /boot/initrd.img-2.6.15-27-powerpc /boot/initrd.img
ln -s /boot/vmlinux-2.6.15-27-powerpc /boot/vmlinux

however after i reboot, uname -s gives me this reply:
Linux skooter 2.6.17-10-powerpc #2 Fri Oct 13 16:37:41 UTC 2006 ppc GNU/Linux

it's obvious that the link is not working, or something else is going on. does any one have any suggestions? and have any other ibook users encountered this problem since the most recent update?

all help is greatly appreciated.
-Rudy

---

