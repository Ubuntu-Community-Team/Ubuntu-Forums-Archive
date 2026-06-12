---
title: "Please Help!"
date: 2008-03-23
forum: Absolute Beginner Talk
---

### Post by annihilan on 2008-03-23
I need help desperately!

I've posted this in two different forums three times, all with one or two useless answers, and then they die!

I cannot get Ubuntu to show me login screen!
I had this problem with the 64-bit LiveCD, where I would get to the part where you hear the african drums, and then I would phase to a screen with a lowly underscore at the top left.

I had to use the alternate installer to even install it.
Now, whenever I boot from it, there's the same issue, I get to the african drums, but there is no login screen, nor underscore.

My specs:
M2N-SLI Deluxe
Athlon 3.0GHz X64 processor
4GB kingston ram
320GB SATA HDD
GeForce 7600GT - sli-linked and the link works in Vista

I don't think it's the VGA's per se, because I used these very same cards on an A8N-SLI Deluxe and a 2.2 Athlon motherboard.

PLEASE HELP!!!

---

### Post by overdrank on 2008-03-23
> **annihilan said:**
> I need help desperately!

I've posted this in two different forums three times, all with one or two useless answers, and then they die!

I cannot get Ubuntu to show me login screen!
I had this problem with the 64-bit LiveCD, where I would get to the part where you hear the african drums, and then I would phase to a screen with a lowly underscore at the top left.

I had to use the alternate installer to even install it.
Now, whenever I boot from it, there's the same issue, I get to the african drums, but there is no login screen, nor underscore.

My specs:
M2N-SLI Deluxe
Athlon 3.0GHz X64 processor
4GB kingston ram
320GB SATA HDD
GeForce 7600GT - sli-linked and the link works in Vista

I don't think it's the VGA's per se, because I used these very same cards on an A8N-SLI Deluxe and a 2.2 Athlon motherboard.

PLEASE HELP!!!

Hi and I have never used the SLI configuration and you say you have used it in Ubuntu on a different system? Have you reconfigured your xorg ```
sudo dpkg-reconfigure -phigh xserver-xorg
``` when you hear the drums use the ctrl, alt, F1 key and this will bring you to the command prompt and you can login.

---

### Post by annihilan on 2008-03-23
I know, I've tried that, and I do receive the command prompt, but I didn't install it so I could use command prompt. How does entering command prompt resolve the issue that I can't see my desktop?

---

### Post by overdrank on 2008-03-23
> **annihilan said:**
> I know, I've tried that, and I do receive the command prompt, but I didn't install it so I could use command prompt. How does entering command prompt resolve the issue that I can't see my desktop?

Hi and as I stated before I have not used the SLI configuration, I was merely offering a possible solution to your issue. If you reach the command prompt and can reconfigure your xorg then maybe you will receive a GUI. You may try and remove one of the graphics cards.

---

### Post by annihilan on 2008-03-23
Sorry if I sounded harsh. When reconfiguring the xorg, what should appear? The list of drivers to use for VGA? If so I've read these cards use vesa, any alternatives?

I have thought about taking one card out, tho I don't really see how it would help.

---

### Post by ByteJuggler on 2008-03-23
> **annihilan said:**
> Sorry if I sounded harsh. When reconfiguring the xorg, what should appear? The list of drivers to use for VGA? If so I've read these cards use vesa, any alternatives?

I have thought about taking one card out, tho I don't really see how it would help.

No, that reconfiguration just puts back the "default vanilla" config, in case the current one got screwed up somehow. It's a bit of a shot to nothing/in the dark.

You can also try editing the /etc/X11/xorg.conf file from the text mode console (and for example change to using the VESA driver) to see if that might get you a working desktop.  

In any event, what is clear is that there's some sort of issue with your graphics setup/config, and it's not inconceivable that SLI might have something to do with it. In order to eliminate that possibility, I would just take one card out and try it, just to see.

---

### Post by annihilan on 2008-03-23
ok, i tried that command, and it took it, and nothing happened.
i havent tried removing a card, but do you think that i could get the drivers, burn them to a disc, and try to install them under command prompt?

btw, how would I go about editing the xorg.conf?

---

### Post by overdrank on 2008-03-23
> **annihilan said:**
> ok, i tried that command, and it took it, and nothing happened.
i havent tried removing a card, but do you think that i could get the drivers, burn them to a disc, and try to install them under command prompt?

btw, how would I go about editing the xorg.conf?

Hi and you can try the command ```
sudo apt-get install nvidia-glx-new
```
Then you can use the command startx  if that is successful

---

### Post by smartboyathome on 2008-03-23
I think that you may want to try installing the nvidia proprietary drivers. If you can get these commands up and get the command line up (possibly if you have two computers use those, or print them out), type this in the terminal to install envy, which will install the drivers for you.
```
wget http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu7_all.deb
dpkg -i http://albertomilone.com/ubuntu/nvidia/scripts/legacy/envy_0.9.10-0ubuntu7_all.deb
sudo envy -t
```
This will download envy, install it for you, and then run the text-based installer. Once it installs the NVidia card for you, run this to get a settings manager with the code to get NVidia working with your Xorg:
```
sudo nvidia-settings
```
This should at least give you a gui to get on your install. Be wary of kernel upgrades though, as they will make you have to reinstall the driver, which is why I recommend using the restricted drivers manager right after you install it to use the NVidia drivers from the repo, which should upgrade with the kernel.

---

### Post by annihilan on 2008-03-23
ok, i tried both, had to work around a couple things, and i tried looking at ```
sudo nvidia-settings
```

but it told me that nothing was defined, so i did sudo nvidia-settings --help and i didnt know how to scroll up. so i had to stop there. the drivers installed, but i didnt know what to do next

---

### Post by handy on 2008-03-25
***_[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)_***

---

