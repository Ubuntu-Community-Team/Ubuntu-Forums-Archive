---
title: "how do you use ubuntu with lcd projectors for presentations?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by dugh on 2007-10-15
Hi,
  I'm giving a presentation and would rather not have to use windows.
I have a dell laptop with nvidia card and ubuntu gutsy.

If I connect my laptop to the projector, nothing happens.  If I run the 'screens and graphics' control panel and set a secondary mirror display, nothing changes, it won't even allow me to click the okay button.

If I restart the laptop or restart gnome (control-alt-backspace), the projector then shows the screen but nothing is shown on my laptop display.

The CRT/LCD button on laptop does nothing.

The control-alt-backspace way of connecting to the projector is acceptable (much better than having to wait minutes for my laptop to boot up), but I was wondering if there is a better way.  I way where I don't have to restart and/or can have the display on both my laptop and on the projector.

For example, would any of these xorg.conf options help?

Option		"Xinerama" "true"
Option "Clone" "true"

---

### Post by Chris S. on 2007-10-15
Those xorg options might help, but I don't know how they work.  Since you have an nVidia card (what type is it?) you might be able to use TwinView.  With that, you can clone the display onto mutliple output devices quite easily.  Just look up TwinView.

I don't know how to set it up through xorg, but when I installed the restricted driver for my nvidia card, I can use the "nvidia-settings" tool to detect new output devices (like TV, projector, second monitor, etc), set them up, and switch to them without restarting the laptop or gnome.  If you don't have that, then you should still be able to set it up in xorg.conf.

---

### Post by LowSky on 2007-10-15
sudo nvidia-settings

---

### Post by bapoumba on 2007-10-15
I cannot help here, sorry, because this is a me too :(

I have been looking around quite extensively (nVidia GeForce, Xfce and gutsy).
I can set up the Twinview, and it works, but the OOo slide show is split between the two screens, right in the middle (my laptop and a video projector), so that's of no use.

The best I can do for now is restart X with the video proj. on. The laptop screen remains off. If I have both screens on, as they do not have the same resolution, the OOo presentation is useless.

To be noted, I have an old laptop with intel chipset, and the multimedia keys work fine (so I can clone the desktop with the same video projector).

---

### Post by Chris S. on 2007-10-15
If you are using nvidia-settings to use TwinView, then make sure that the position of the screens are set to "Clones".  That prevents it from trying to set up a dual-monitor type desktop.

---

### Post by bapoumba on 2007-10-15
> **Chris S. said:**
> If you are using nvidia-settings to use TwinView, then make sure that the position of the screens are set to "Clones".  That prevents it from trying to set up a dual-monitor type desktop.
Yes, I did that too, but I cannot have the same resolution on the video projector and my laptop. Not good for the presentation ^^

I may be doing something wrong, I never used the restricted drivers before gutsy (I installed them _for_ the presentations..), and I have not edited xorg.conf manually, for now. I'm still reading about all of this.

Thanks for your input :)

---

### Post by bodhi.zazen on 2007-10-15
Often times on laptops there is a key-combination to do this for you.

On mine it is the Fn (Function key) and F4 ~ this toggles between 3 settings : the laptop only; external screen (LCD projector) only, and laptop + external screen (both). (On many laptops there is a purple rectangle to indicate the toggle key).

I have used this with several presentations , although not the new OOO 2.3

HTH

---

### Post by bapoumba on 2007-10-15
Yes, bodhi, but the Fn keys do not work here, that's what I tried first :/
On the other laptop (intel video, but still with feisty) they work fine. Hmm.

---

### Post by bodhi.zazen on 2007-10-15
> **bapoumba said:**
> Yes, bodhi, but the Fn keys do not work here, that's what I tried first :/
On the other laptop (intel video, but still with feisty) they work fine. Hmm.

>_< 

missed that ...

---

### Post by bapoumba on 2007-10-15
> **bodhi.zazen said:**
> >_< 

missed that ...
I was not so clear either ^^

To the OP: very sorry I hijacked your thread :)

---

### Post by dugh on 2007-10-15
The only thing nvidia-settings did was completely screw up my laptop.  It doesn't boot to normal resolution anymore, it ignores xorg.conf.  So I wouldn't recommend ANYONE use nvidia-settings.  Stick to restarting X/gnome by hitting control-alt-backspace after you hook up the projector.

Repeat: Do NOT install or use nvidia-settings.

---

### Post by bapoumba on 2007-10-15
> **dugh said:**
> The only thing nvidia-settings did was completely screw up my laptop.  It doesn't boot to normal resolution anymore, it ignores xorg.conf.  So I wouldn't recommend ANYONE use nvidia-settings.  Stick to restarting X/gnome by hitting control-alt-backspace after you hook up the projector.

Repeat: Do NOT install or use nvidia-settings.

Well, I did play with it. I had a backup copy of xorg.conf that I restored at some point because I probably messed up something. I really wanted to have the clone thing work, and it works with different resolutions, but that's not useful.
I also tried the Screens and Graphics menu (not sure how it is called in GNOME), and I cannot have both screens at all.

Please look in /etc/X11/, you should have automatic backup copies of your xorg.conf (I currently have 18 of them :D). The first one should ba a copy of your original xorg.conf, in case you did not save it yourself.

---

### Post by dugh on 2007-10-15
nvidia-settings does more than change xorg.conf.  Restoring a backup of xorg.conf is the first thing I did.

I had to completely remove nvidia-settings, and then re-install the nvidia-glx-new driver (you can also uncheck and re-check the nvidia driver in the restricted drivers control panel).  That plus restoring xorg.conf fixed the problem.

So it appears there is no solution to my original question.  I'll just have to turn around a lot when I am giving my presentation so I can use the mouse, or else use windows (it is a java app that runs on any platform anyway).

---

### Post by bapoumba on 2007-10-15
That's what I do too (apart from the windows stuff, I do not have it anymore).
I'll keep on looking.

---

### Post by kids_pro on 2007-10-30
I got the same problem except it is ATI X1400 card. I hope the next release cycle would cure this problem.

---

### Post by Arjunanda on 2007-10-31
Has anybody tried Output Switcher 0.4 [http://lilserenity.wordpress.com/2007/10/21/output-switcher-easy-linux-screen-management/](http://lilserenity.wordpress.com/2007/10/21/output-switcher-easy-linux-screen-management/)

That seems to be the thing many of you are looking for. I did not try it yet but will sure do in the coming days. Also, the new display settings tool should see some improvement in the future to auto-detect the projectors.

"For laptop users, full support external VGA (projector) support is available out-of-the-box with easy reconfiguration when hardware is switched. This new enhancement will eases laptop user preparing their presentation."
[http://www.gatzet.info/2007/ubuntu-latest-release/](http://www.gatzet.info/2007/ubuntu-latest-release/)

I do not know what that means in practice. On my Acer aspire laptop the Fn + F4 combination did not nothing, neither did the new screen config dialog work. So last time I had to use the Ctrl+Alt+backspace trick to view my presentation.

---

### Post by strikeback03 on 2007-11-03
One of the grad students I work with has a Thinkpad G41 and he can clone the screen to a projector and the laptop display, I saw it work yesterday.  Not sure what video card he has, but he used the nVidia application to change the display settings.  

My laptop has an ATI video card, which is why I'm looking for a way to switch displays.  Want to use my desktop screen while the desktop computer is unavailable due to downloading upgrade.

---

### Post by dugh on 2007-11-06
Well I tried control-alt-backspace with different projector and it didn't work at all.

I have no idea how to use ubuntu with any projector.  I just boot to windows when I am presenting.

---

