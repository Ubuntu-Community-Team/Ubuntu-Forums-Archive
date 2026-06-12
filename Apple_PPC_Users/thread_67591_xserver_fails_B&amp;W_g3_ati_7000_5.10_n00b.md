---
title: "xserver fails B&amp;W g3 ati 7000 5.10 n00b"
date: 2005-09-20
forum: Apple PPC Users
---

### Post by grimmson on 2005-09-20
I've got fdisk (or whatever the linux equivilant is) and I'm not afraid to use it. Just kidding. hello all. I think I have a somewhat simple problem that I just can't seem to fix. I've installed ubuntu twice and both times xserver fails.After the second install I've really been pouring over the newsgroup and trying different things (15-20 hours worth) to no avail.

sudo reconfig xserver several times
fglrsinfo      (works with a loaded gui only)
dmesd | grep fglrx    returned nothing (might have done something wrong)
md5sum /etc/x11/xorg.conf | sudo tee /var/lib/xfree86/xorg.conf.md5sum    didn't do anything
dpkg-reconfigure -a    no dice (had parts of xserver in it)
lspci said 00:10:00 or pciID 00:16:00 in decimal I think.

I might have a hint
Skipping"/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_clip.o": No symbols found 
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_norm.o": No symbols found 
Skipping "/usr/X11R6/lib/modules/extensions/libGLcore.a:m_debug_xform.o": No symbols found 

This was part of the error screen. this info was posted by a different user but never discussed much past that. I'd love to post strait from my ppc but i'm afraid I might hurt myself trying to find this website without a gui.
My next thought involves two or three different threads. All were very simmilar to my problem and fixed there system but none of the solutions fit my sinareo. First was update the driver downloaded from ati, ati only appears to support 8500 up. 8500 down went to the dri project. I viewed this page and just couldn't comprehend what it was talking about. Problem two, the top of this page said this project may be outdated. so it might not help anyway. The second solution thread dealt with an older ati card on an i386. the page did'nt have a link to a ppc driver download. The third was an interesting solution. It discussed using a debutant ati driver installer. I went to deb's website and sitesearch appeared to be down. Broused the results from www. and found a possible solution in Itialy. But it only dealt with 8500 up. I know I'm yappin a lot but I don't want you kind folks to think I didn't read and try. Just a refresher. B & W g3 256 ati 7000 5.10 newbie and the gui fails every time. can someone throw me a lifeline. Thanks. p.s. connect the dots real close. In this realm im in the id 10 t program.

---

### Post by grimmson on 2005-09-24
Update (that the geeks are gonna laugh at.) I downloaded 5.04 and installed. Had very similar problem. Screen stays black (right before login.)  Didn't want to reinstall again so I looked for safe mode F8 at boot. If you time it just right, one second after the white circle pop's up I can ctrl alt F1 and log into terminal without a gui. From there type

sudo /etc/init.d/gdm stop

On my system all the characters go nuts, the screen doesn't update properly etc... but that doesn't matter. Next hit the up arrow once to bring up prev. command, backspace 4 times (removing stop) and type start. Hit enter and thats the only way I can consistantly log in to the gui. It's unstable, it's ugly and it works. When I figure out  how to fix it I'll post (maybe fglrx) but this has been a 30+ hour install and I'm just glad to have it work. Good luck ppc users. I think we might be on a bumpy road. \\:D/

---

### Post by stuporglue on 2005-09-24
If you can stop gdm, you're in good shape!

Once you've got gdm stopped, type "startx" and see what happens. Hopefully it'll straighten out your charachters, even if it crashes. 

After running startx (assuming it didn't work) check the last couple of lines of /var/log/Xorg.0.log. Try something like "tail -20 /var/log/Xorg.0.log". Check that output for any "EE"s. 

Also, if you can manage, try running apt-get update and apt-get upgrade to see if anything that's broken gets upgraded to fixed...sometimes that's all it takes. :-)

---

