---
title: "Can install Nvidia driver for GeForce 7600GT"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by doriard on 2007-04-23
Sorry, I meant CAN'T install Nvidia driver... couldn't edit title.

I just installed Fiesty Fawn today and I'm new to Linux.  The install went okay, but only after going to pcmech.com to find really useful installation instructions.  The instructions here don't give enough information on how to set up partitions for a Linux install.  pcmech.com saved me on that.

Anyway, my next step is to get the Nvidia drivers installed so I can try a few games, and especially to get my dual monitors both working.  Only one monitor is recognized now.

I first tried installing the nvidia drivers via Automatix (suggested by pcmech.com article).  That didn't work.  Ubuntu shows the listing under apps but won't enable them.  Next I tried using Nvidia's recommended install method from their website.  I got an error saying libc (headers I think) was missing.  In these forums I found some messages saying I should install libc6-dev.

I tried installing libc6-dev but the Synaptics installeer gave me the error message:

The following packages have unresolvable dependencies...
Depends: libc6 (=2.3.5-1ubuntu12.5.10.1) but 2.5-0ubuntu14 is to be installed

I looked for marked packages waiting to be installed (is that what it was talking about?) but didn't see any. What is the '2.5-0ubuntu14' waiting to be installed that it's talking about?  I am getting lost on these dependencies, and then I found the beginners forum, so I'm posting my message here.

What should I do next to get my nvidia drivers installed?

---

### Post by devnulljp on 2007-04-23
Did you try envy? I just ripped out my ATI card in frustration and replaced it with an nvidia 7600GS,andenvy had me up and running in a few minutes. Great stuff.

---

### Post by Spr0k3t on 2007-04-23
Open a console and do the following:```
sudo apt-get install nvidia-glx-new
```Also, make sure you have turned on the nvidia drivers in the restricted drivers manager set.  From there, open the nvidia settings as such:```
gksudo nvidia-manager
```Let me know how things work out once you've got that far.  Also, Automatix2 isn't needed since Feisty... I would call it redundant now.

---

### Post by doriard on 2007-04-23
What is envy?

I will try your suggestions tomorrow.  For tonight, I thought I was supposed to stay away from glx and restricted drivers per nvidia's web forums.  From their forum:

If you wish to install the NVIDIA Linux graphics driver on a Debian GNU/Linux or Ubuntu system that ships with Xorg 7.x, please ensure that your system meets the following requirements:

    * development tools like make and gcc are installed
    * the linux-headers package matching the installed Linux kernel is installed
    * the pkg-config and xserver-xorg-dev packages are installed
    * the nvidia-glx package has been uninstalled with the --purge option and the file /etc/init.d/nvidia-glx does not exist.

If you use Ubuntu, please also ensure that the linux-restricted-modules packages have been uninstalled. Alternatively, you can edit the /etc/default/linux-restricted-modules or /etc/default/linux-restricted-modules-common configuration file and disable the NVIDIA linux-restricted kernel modules (nvidia, nvidia_legacy) via:

    DISABLED_MODULES="nv"

If you require further assistance after following the instructions above, please see:
[http://www.nvnews.net/vbulletin/showthread.php?t=46678](http://www.nvnews.net/vbulletin/showthread.php?t=46678).


Should I ignore all of that above?  If I follow your suggestions will I get the actual Nvidia drivers, or a generic, reduced-functionality set?  Will dual monitor support work?

---

### Post by barmazal on 2007-04-23
there are thousands of methods online to make nvidia cards to work from which none working

---

### Post by doriard on 2007-04-23
Which version of Envy did you use?  0.9.1 or 0.9.2?  Do you have Fiesty, and does 0.9.1 work with Fiesty?

---

### Post by danielm on 2007-05-10
I have a 7600GT. However, in my case, the problem seems to be that the driver is locking up my system. I have tried envy, the nv driver, nvidia-glx and nvidia-glx-new. By doing things like changing desktops frequently, I am able to trigger a system lock up (usually any music I have playing to test this stops, although I've had once incidence where the music kept playing, even though I was unable to SSH inl oddly enough apache was responding, but this could be a fluke). 

I am also using a dual head display with TwinView, although I don't believe this is related since nv doesn't support TwinView.

This is an incredibly frustrating problem. I experienced this in edgy also (i just bought these computer parts recently). Everything ran smoothly under WinXP x64 when I was testing it. Also, the lock ups don't occur when using 3D acceleration. They're usually triggered by mundane desktop use. Additionally, when dragging windows, the choppiness seems to worsen a bit after dragging a few windows around.

Any help would be much appreciated. (Sorry for hijacking the thread; this may prove to be a problem for you also which is why I posted in the first place).

PS. There is no such nvidia-manager in the glx packages. :) There are other configuration programs however.

---

