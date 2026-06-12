---
title: "installing nvidia drivers for 6600 GT"
date: 2007-07-10
forum: Absolute Beginner Talk
---

### Post by helix_r on 2007-07-10
Hi,

I just installed ubuntu 7.04 onto my amd64 machine with a 6600GT pci-e graphics card.  The system boots, and I have a desktop but my resolution is only 1024x768 and there is no option under System>Preferences>Screen Resolution to increase it to the native resolution of my LCD (1600x1050).

I then saw that under System>Administration>Restricted Drivers Manager, I could "enable" nvidia-glx. I enabled it and rebooted.  Upon reboot, the screen resolution was still 1024x768 and I still cannot increase it. However, 3d acceleration appears to be working. I get ~7400 FPS when I run glxgears.

So my questions are...

1) I am getting 3d Hardware acceleration, right? How do I check if 2D also works?

2) What do I need to do to make it so I can increase my screen resolution and make that permanent?
 
rant follows ...
3) I've installed ubuntu several times in the last couple years and it has always worked great. But why do we _STILL_ have this hassle with mp3 support and video card drivers? I always had to bend over backwards to get those things working, and I always had to use different forgettable methods. Why can't ubuntu just install support for mp3's and video cards BY DEFAULT? What is the worst that could happen?

---

### Post by helix_r on 2007-07-10
Well I think I have my solution...

After "enabling the restricted driver" for the nvidia, I tried "nvidia-xconfig". I assume that this modified the xorg.conf file, right?

However, I still did not get the resolution I wanted. So, I ran "dpkg-reconfigure xserver-xorg" an answered the gobblity-gook questions to the best of my abilities. This seems to have worked, but I noticed that under "System>Preferences>Screen Resolution" I get "50" as the refresh rate. I happen to know that my monitor is optimal at 60Hz.

I used one of the online modeline generators, and pasted the modeline to the xorg.conf file in hopes that this would make it so my refresh rate was 60. No luck. I am thinking that the "screen resolution" menu item is not telling me the truth. 

I would like to forget all about xorg.conf forever, but before I do, **how can I verify what my actual refresh rate is?**

---

### Post by steve.horsley on 2007-07-10
I have a nvidia 6600GT.

You need to install these packages in synaptic (or aptitude on the command line):
[B]nvidia-glx-new
nvidia-settings[/B]
and then edit /etc/X11/xorg.conf changing:
**Driver "nv"**
to 
**Driver "nvidia"**

That should do the trick. nvidia-settings is a nice GUI configuration utility.

---

### Post by stchman on 2007-07-10
> **helix_r said:**
> Hi,

I just installed ubuntu 7.04 onto my amd64 machine with a 6600GT pci-e graphics card.  The system boots, and I have a desktop but my resolution is only 1024x768 and there is no option under System>Preferences>Screen Resolution to increase it to the native resolution of my LCD (1600x1050).

I then saw that under System>Administration>Restricted Drivers Manager, I could "enable" nvidia-glx. I enabled it and rebooted.  Upon reboot, the screen resolution was still 1024x768 and I still cannot increase it. However, 3d acceleration appears to be working. I get ~7400 FPS when I run glxgears.

So my questions are...

1) I am getting 3d Hardware acceleration, right? How do I check if 2D also works?

2) What do I need to do to make it so I can increase my screen resolution and make that permanent?
 
rant follows ...
3) I've installed ubuntu several times in the last couple years and it has always worked great. But why do we _STILL_ have this hassle with mp3 support and video card drivers? I always had to bend over backwards to get those things working, and I always had to use different forgettable methods. Why can't ubuntu just install support for mp3's and video cards BY DEFAULT? What is the worst that could happen?

IN your /etc/X11/xorg.conf you will need to add "1280x1024" (or whatever resolution you want to run) to the text file as the first resolution in the series of resolutions.

I had to do that with my LCD after I enabled the restricted driver.

---

### Post by helix_r on 2007-07-11
> **steve.horsley said:**
> I have a nvidia 6600GT.

You need to install these packages in synaptic (or aptitude on the command line):
[B]nvidia-glx-new
nvidia-settings[/B]
and then edit /etc/X11/xorg.conf changing:
**Driver "nv"**
to 
**Driver "nvidia"**

That should do the trick. nvidia-settings is a nice GUI configuration utility.

Thanks,

It appears that the nvidia-settings application was installed when I enabled the restricted driver from the system>administration menu. I can run it from the command line, even though it is not present in any menu. The nvidia setting dialog indicates that I am running at 60Hz refresh rate-- which is different from what the "screen resolution" menu item says.

---

