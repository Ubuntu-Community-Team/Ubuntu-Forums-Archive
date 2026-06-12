---
title: "xserver-xorg issue"
date: 2006-05-04
forum: Absolute Beginner Talk
---

### Post by bt224 on 2006-05-04
I was trying to change my screen size (resolution) and did the following:

sudo /etc/init.d/gdm stop

then:

sudo dpkg-reconfigure xserver-xorg

I royally screwed something up the first time, and ended up with the same resolution, but 0 refresh rate. That's all there was in the drop down. Now everything is super slow.

So I am going through to try to reset using the autodetects and defaults, to at least get back to where I was. At the point where it asks me what the computer screen depth is, when I try to select something, the terminal opens at the bottom and says:

xserver-xorg postinst warning: overwriting possibly-customised configuration

Basically, I'm stuck.

---

### Post by bt224 on 2006-05-04
Oh yeah, and I have a prompt, I just have no idea what to type.

---

### Post by Jimmey on 2006-05-04
Ouch. That sounds particularly nasty.

>  Oh yeah, and I have a prompt, I just have no idea what to type.

It's bad-*** time.

First, It'd be a good idea to see if you have any backups of xorg.conf. To do this, type
> cd /etc/X11/; ls

If you see something titled "xorg.conf.bak", then you might be able to rescue your previous settings. If you don't, skip this step.

To recover your settings, type 
> sudo cp xorg.conf.bak xorg.conf, then try > startx.

Are you trying to reconfigure with sudo, or not? If not, try 
> sudo dpkg-reconfigure xserver-xorg.

If you already were, renaming the current xorg.conf, and then reconfiguring:
> sudo cp xorg.conf xorg.conf.old; sudo rm xorg.conf; sudo dpkg-reconfigure xserver-xorg

Hope this helps :)

Jimmey

---

### Post by bt224 on 2006-05-04
crap, sorry, it also says:

etc/x11/org.conf.200605041833

---

### Post by bt224 on 2006-05-04
ok, no back file existed (it said no such file)

tried the last line to rename, said it did not exist and nothing happened. I went back through the reconfig with the same results

---

### Post by bt224 on 2006-05-04
well, I got my refresh back, but the whole reconfig stills boots me into terminal in the same place. weird

---

### Post by Mustard on 2006-05-04
[QUOTE=bt224]well, I got my refresh back, but the whole reconfig stills boots me into terminal in the same place. weird[/QUOTE]

I'm not sure what you are saying here. Are you saying you rebooted the computer and your X server failed and dropped to terminal, or are you saying that you reconfigured xorg.conf and after doing so, it drops to a command prompt in terminal?

Try this command if it is just dropping to command line after reconfiguring xorg...

```
sudo /etc/init.d/gdm restart
```

---

### Post by bt224 on 2006-05-04
Sorry, I was near my new Linux computer learning new bad words....

The best way I can describe it is in the middle of the xserver-xorg configuration it opened what appeared to be a terminal at the bottom of the screen where you select depth. It pushed up the set up prog to do it. I totally screwed something, doing a reinstall now. 

What I will do then is install Xfce4, because this 400mhz 128 ram just ain't gonna do it. And 128 is the max for this old laptop.

---

### Post by Mustard on 2006-05-05
[QUOTE=bt224]Sorry, I was near my new Linux computer learning new bad words....

The best way I can describe it is in the middle of the xserver-xorg configuration it opened what appeared to be a terminal at the bottom of the screen where you select depth. It pushed up the set up prog to do it. I totally screwed something, doing a reinstall now. 

What I will do then is install Xfce4, because this 400mhz 128 ram just ain't gonna do it. And 128 is the max for this old laptop.[/QUOTE]

From what you describe above, it's what happens normally every time I use dpkg-reconfigure xserver-xorg.  I think you may have interpreted what is normal output as some type of error.  Basically it is exiting the program and dropping you to a prompt where you can start the xserver again with the appropriate command.

The message you saw, "xserver-xorg postinst warning: overwriting possibly-customised configuration", is a warning rather than an error, that tells you that the system believed that it had just overwritten a custom-made configuration.  You would interpret that as a 'for your information' type of message and generally only be concerned if for some reason you really didn't want to overwrite a custom configuration.  Not knowing this though sort of leaves you in the dark about the situation though, so I can understand your confusion.

---

