---
title: "How can I increase resolution from a GUI?"
date: 2007-06-02
forum: Absolute Beginner Talk
---

### Post by Lord Illidan on 2007-06-02
I have installed Ubuntu Feisty Fawn 7.04. I have installed the restricted Nvidia drivers and upgraded my system.

My LCD screen is capable of a good 1280x1024 resolution, yet from the screen resolution preferences I cannot choose a higher resolution than 1024x768. How do I increase the resolution **without going into a CLI and typing the command **```
dpkg-reconfigure xserver-xorg
``` Also, no editing of xorg.conf please.. That stuff is quite beyond me.[I]

Disclaimer : For this post, I'd like you to ignore my high bean count, and imagine I am a new windows user, who never saw a terminal in his life before, **and doesn't want to see one**. Why do I ask this? Because I believe that Ubuntu should be able of providing a GUI tool. Thanks.[/I]

---

### Post by jiminycricket on 2007-06-02
You'd probably have to wait for a new version of Ubuntu with that Xorg 7.3 goodness :P

If  you have an Intel card, installing 915resolution from Synaptic can help.  Same with installing the non-free nVidia driver + configuration tool.

---

### Post by Lord Illidan on 2007-06-02
> **jiminycricket said:**
> You'd probably have to wait for a new version of Ubuntu with that Xorg 7.3 goodness :P

If  you have an Intel card, installing 915resolution from Synaptic can help.  Same with installing the non-free nVidia driver + configuration tool.

I said I had an Nvidia card, didn't I? Why would I install the nvidia drivers otherwise? ;)

And, no, it didn't help. I know this desktop can manage 1280x1024 but how do I do it?

---

### Post by bigken on 2007-06-02
this is only other way I know

sudo dpkg-reconfigure -phigh xserver-xorg

---

### Post by blue_shift on 2007-06-02
This is sort of cheating, but you can edit xorg.conf from the gui:
```
sudo gedit /etc/X11/xorg.conf
```
It's really pretty simple, and if you backup the xorg.conf file it's pretty harmless (as long as you avoid playing with the refresh rates / vsync)
There are plenty of guides, or you could upload your xorg.conf here.
```
sudo cp /etc/X11/xorg.conf etc/X11/xorg.conf.old
```
Was all I ever did, and then:
```
sudo cp /etc/X11/xorg.conf.old etc/X11/xorg.conf
```
If the gui failed to boot.

---

### Post by RomeReactor on 2007-06-02
Hi. The only thing I can think of at the moment would be to call **nvidia-settings** from the terminal or by pressing ALT+F2, but it would kind of defeat the purpose of your disclaimer. Once running, though, it *is* a graphical application; it even let me increase the refresh rate of my monitor...

---

### Post by blue_shift on 2007-06-02
> **RomeReactor said:**
> Hi. The only thing I can think of at the moment would be to call **nvidia-settings**
Can that overwrite /etc/X11/xorg.conf?

---

### Post by RomeReactor on 2007-06-02
I really can't say; I see no change in my xorg.conf, but i have used nvidia-settings to change screen resolution and refresh rate, and the changes are not volatile. Maybe it keeps it's settings elsewhere?

---

### Post by blue_shift on 2007-06-02
Yes, that would make sense. It's just the the problems I've usually had relate to the resolution I want not being offered by the gui because it's not written in xorg.conf.
That's why - in my case - the resolution 1024x768 was the highest offered in the settings menu.

---

### Post by RomeReactor on 2007-06-02
blue_shift, if you have an nvidia card and are also having resolution problems, I recommend you try it; in my case it lets me choose from a bunch of resolutions that don't appear in xorg, and also a higher refresh rate.

---

### Post by blue_shift on 2007-06-02
Thanks, but I'm fine. It's just that there was no autodetection of 1440x900 resolution, and the way I solved it was by hand using xorg.conf after messing about with xorg reconfigure to no avail. Thought it could be relevant.

---

### Post by Lord Illidan on 2007-06-02
> **RomeReactor said:**
> Hi. The only thing I can think of at the moment would be to call **nvidia-settings** from the terminal or by pressing ALT+F2, but it would kind of defeat the purpose of your disclaimer. Once running, though, it *is* a graphical application; it even let me increase the refresh rate of my monitor...

That's a good one...thanks. But there should be a menu link. I think I will suggest it for Gutsy.

---

### Post by RomeReactor on 2007-06-02
I agree. Since it _is_ a graphical application, it only makes sense it had a launcher.

---

