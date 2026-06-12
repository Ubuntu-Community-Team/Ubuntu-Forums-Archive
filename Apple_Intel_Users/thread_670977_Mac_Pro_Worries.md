---
title: "Mac Pro Worries"
date: 2008-01-18
forum: Apple Intel Users
---

### Post by bunted on 2008-01-18
Just installed 7.10 on my Mac Pro, 4xXeon 2.66, ati x1900 512 mb, 23" Cinema HD.  Even without a custom kernel, everything runs great!

However, I am a little worried by some of the posts I've read.  I use this machine to render projects with Blender.  If I let this render for a day and a half, am I going to find a pool of molten CPU afterwards?  The ATI fan spins constantly with no load, and from what I've read frequency scaling of the CPU doesn't work properly.

Should I be worried, or are there just a bunch of doomsayers I've been listening to?  I used to just use blender and the gimp on Leopard, but things run so much more smoothly on Linux for the programs I mostly use.  Leopard's X11 integration isn't great, especially with my wacom tablet.  Any ideas, thoughts, or more preferably experiences?

---

### Post by cyberdork33 on 2008-01-18
No experience, but a question: If the fan spins constantly even without load, then why are you worried it will get too hot?

Someone documented the customization they did during their Mac Pro install. You might find it helpful:
[http://macprolinux.blogspot.com/](http://macprolinux.blogspot.com/)

In this thread, some of the "issues" are discussed:
[http://ubuntuforums.org/showthread.php?t=578698](http://ubuntuforums.org/showthread.php?t=578698)

You should be able to control the fans manually:
[http://ubuntuforums.org/showthread.php?p=3710810#post3710810](http://ubuntuforums.org/showthread.php?p=3710810#post3710810)
You might have to make sure the applesmc module is loading before using the above.

---

### Post by tgalati4 on 2008-01-18
You are relying on Apple engineering for robustness.  A laptop is really not suitable for workstation use, such as rendering.  Not that it can't do it, but a laptop is not intended to run 100% CPU for long periods.  It will get hot and certain bits that can't take the heat (like wireless chipsets) will rebel.

If you have Applecare, then render for 48 hours and see what still works.  Just make sure it's not near anything flammable.

---

### Post by cyberdork33 on 2008-01-18
> **tgalati4 said:**
> You are relying on Apple engineering for robustness.  A laptop is really not suitable for workstation use, such as rendering.  Not that it can't do it, but a laptop is not intended to run 100% CPU for long periods.  It will get hot and certain bits that can't take the heat (like wireless chipsets) will rebel.

If you have Applecare, then render for 48 hours and see what still works.  Just make sure it's not near anything flammable.
He said _Mac_ Pro, not _Macbook_ Pro

---

### Post by bunted on 2008-01-18
@cyberdork

Thanks for the advice, but I've already found the search function.  Thanks again for being literate, unlike some other posters.  I really only post here when I feel like I've exhausted my options.  I've compiled four separate custom kernels two for 2.6.22 and two for 2.6.23, all with the mactel patches, one each with macprolinux.blogspot.com's config and one each with the gentoo wiki's config and I still can't get those working.  I always end up with a PCI BIOS BUG warning, and then i8042.c: no controller found.  Hang, repeat ad infinitum.  I'm really not sure what I'm doing wrong right now.

The purpose of this post was to see if anyone else in these forums had some experience with Ubuntu, custom kernels, CPU intensive tasks, and a last generation Mac Pro hardware setup.

---

### Post by cyberdork33 on 2008-01-20
> **bunted said:**
> @cyberdork

Thanks for the advice, but I've already found the search function.  Thanks again for being literate, unlike some other posters.  I really only post here when I feel like I've exhausted my options.  I've compiled four separate custom kernels two for 2.6.22 and two for 2.6.23, all with the mactel patches, one each with macprolinux.blogspot.com's config and one each with the gentoo wiki's config and I still can't get those working.  I always end up with a PCI BIOS BUG warning, and then i8042.c: no controller found.  Hang, repeat ad infinitum.  I'm really not sure what I'm doing wrong right now.

The purpose of this post was to see if anyone else in these forums had some experience with Ubuntu, custom kernels, CPU intensive tasks, and a last generation Mac Pro hardware setup.you can't just rely on a kernel config to be right especially since you have newer hardware. You need to run menuconfig and check the hardware options. You could also just use the Ubuntu config and add the mactel patches to it. 

To get to the bottom line... You will not "melt" your computer. The Mac firmware wil prevent that anyway.

---

### Post by jamieno10 on 2008-01-28
Hi,

I use a couple of Mac pros (8-core) with Nvidia cards (received them in Oct and Dec 2007). I use them for heavy numerical work.

7.10 installs fine, but the applesmc module doesn't load although its seems that in the current release of Ubuntu (Hardy Heron? & you can find instructions at: [https://bugs.launchpad.net/bugs/153888](https://bugs.launchpad.net/bugs/153888)) this issue has been addressed. I have yet to try the HH release due to crazy workload, but if you do, I would be most interested (and grateful!) if you post something about it. 
The coretemp program from the mactel packages works with 7.10 and you can use it to monitor the temperature.
If you use Mac OS, you can download fancontrolsmc and set the fan speeds in Mac OS. If you do not switch off (resetting is ok) your computer, the settings will stay. This option however, is very troublesome since one has to constantly reboot to change the fan speed if the need arises. One option would be to leave it on a "high" setting.

With the Mactel patches + custom kernel + no Mac OS (instructions listed in the blog given in the earlier post), applesmc is loaded and I can manually change the fan speed. While not ideal (i.e. manual fan control), I think its a minor/trivial annoyance.


From reading the technical specs, it appears that the CPU can operate at a max temp of ~61-62C. My mac pros seem very very sensitive to the "environment". For instance, if I draw the blinds, which are located 40-50cm from the main exhaust, the temperature can shoot up 10+ degrees C. 

Hope this might be of some help to you.

---

