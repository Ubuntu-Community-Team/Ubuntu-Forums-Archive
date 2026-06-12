---
title: "Restricted Drivers"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by rafkin on 2007-10-20
I started on Ubuntu about a month ago and really enjoying it. Not  quite ready to make the complete switch yet but still looking for programs to cover the ones I need in windoze. My question is, I just upgraded to Gutsy and did not have any problems. I want to try out this compiz everybody is raving about but it says I have to install my NVIDIA drivers thorough restricted drivers. I do that but after the restart I loose my screen resolution. Only options I have are 800X600 and 640X480... much to small when you are used to 1280X1024. When I go back to the nv driver I get my resolution back. Is there a fix for this or is this a bug. My card is a NVIDIA legacy btw, 1000mhz with 512 ram. Great site by the way, wouldn't be this far without the community here. Thanks

---

### Post by Pumalite on 2007-10-20
Check this:

[http://ubuntuforums.org/showthread.php?t=582956](http://ubuntuforums.org/showthread.php?t=582956)

---

### Post by rafkin on 2007-10-21
Checked out the link, my problem is not quite the same. When I install the restricted drivers my only options for screen res, is 800X600 and 640X480. I do not have an option other than these two. If I go back to the nv driver then I get a whole list of displays to use.

EDIT: I had the same problem with feisty, thought I would wait till Gutsy to see if it was still there....it is :[

---

### Post by Qwerty_ on 2007-10-21
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by shad0w_walker on 2007-10-21
Try this:

1. Press alt + F2 and run this command

```
gksu nvidia-settings
```

2. Find the monitors/screens section (Can't remember which it is) and select the resolution you want.

3. Click the save to xorg.conf button

4. Restart X in whatever way you want.

---

### Post by rafkin on 2007-10-21
Thanks for the replies guys. Shadow.. I tried your suggestion but did not work, although I did notice that the restricted driver is for a legacy card and mine is a TNT2. I started trying Qwerty answer but got a bit nervous. What excactly is this doing? Just tgrying to locate my correct driver? When it got into changing my xconf. file I got nervous and bailed!! hehe. am I able to revert back to the nv ubuntu driver if this fails? Again, thanks alot for all your quick replies.

---

### Post by rafkin on 2007-10-21
Ok, just noticed in a later post another member with the same card as me had the same problem and said that the TNT2 cards do not have enough memory. gives me a reason to buy a better computer I quess. Thanks again for all the help...I spend most of my free time reading through these posts and I am really learning alot! Hopefully I will be on the answer side of these posts someday!

---

### Post by shad0w_walker on 2007-10-21
Depending on the rest of your system it might just be an idea to get a new graphics card. Then again, if you want a pc this is a pretty good excuse and of course finding a Linux compatible setup is much easier nowadays *cough*Dell*cough* ;)

Or theres the self built way (Of which i am a firm believer) and around these forums there is no shortage of information on what hardware works and what doesn't.

---

### Post by JohnSGruber on 2007-10-21
> **rafkin said:**
> Ok, just noticed in a later post another member with the same card as me had the same problem and said that the TNT2 cards do not have enough memory. gives me a reason to buy a better computer I quess. Thanks again for all the help...I spend most of my free time reading through these posts and I am really learning alot! Hopefully I will be on the answer side of these posts someday!

I don't know if you have enough memory to run what you want, but I have an nvidia card of the same generation. I found two ways to solve the problem. One is to use the Screens and Graphics program under System->Administration while using the old driver. I know it sounds redundant to change settings while using a driver that is working ok but the idea is to have your configuration set up right before enabling the proprietary driver.

The problem I had is that the nv driver will communicate with your monitor, through your graphics card, to get the frequencies that can be used for the signal sent to the monitor. By default the nvidia driver gets the data but doesn't use it. If you add the package nvidia-xconfig (it comes with the later nvidia-glx packages but must be loaded separately when using a legacy card with nvidia-glx-legacy) you can make a setting change.

You can try this while using the proprietary driver:

```

sudo nvidia-xconfig -c /etc/X11/xorg.conf -d 24 --use-edid-freqs --allow-glx-with-composite --no-logo

```
The second option tells the driver to trust the frequency data the lcd returns. The third option is one that the restricted driver manager adds but the screens and graphics program removes. I think the last one just speeds up logging on. Without it you see
a flash of an Nvidia logo when you log on. I don't know specifically why the restricted driver manager adds that option. The -d 24 sets a pixel depth if I'm not mistaken. This second option is nice when the information returned through the the monitor and graphics card is correct. It's automatic like the old driver.

The first method, using Screens and Graphics is probably the recommended approach. They've added this program to address all of the resolution problems were having because not all displays return appropriate information, and not all graphics cards are fault free, and drivers have bugs. Temporarily it may be necessary to get the display set up while using the open source "nv" driver that is used by default if you are trying to get things like Compiz working, particularly with xgl and legacy cards.

If you try the second method, you should remember to run the following before a change using Screens and Graphics or a manual edit of the xorg.conf file will work:

```

sudo nvidia-xconfig -c /etc/X11/xorg.conf -d 24 --no-use-edid-freqs

```

That's necessary because this particular legacy driver would otherwise ignore what's in the file and continue to use the data returned by the monitor.

---

