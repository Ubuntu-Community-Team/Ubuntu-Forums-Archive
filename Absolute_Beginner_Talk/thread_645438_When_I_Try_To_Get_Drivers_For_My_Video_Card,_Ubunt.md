---
title: "When I Try To Get Drivers For My Video Card, Ubuntu Dies"
date: 2007-12-20
forum: Absolute Beginner Talk
---

### Post by Claan22 on 2007-12-20
Well, this should be an easy to solve issue (either I'm missing something or I won't be able to use Ubuntu).

After installing 7.04, and downloading the updates for all my applications, all is well.  But when I go to the restricted drivers manager, and tell it to enable the "ATI accelerated graphics driver", it begins installing.  In fact it finishes installing with no issue.  But when I reboot, so that it can take effect, I can't get into Ubuntu.  After my BIOS screen, I just get a black screen with a _ in the upper left corner.  Right now I'm typing this through a live CD.

I asked for help on this a while ago, and was told to enter "sudo dpkg-reconfigure xserver-xorg".  To be honest, I can't remember the specifics of how it turned out, but it didn't get me to a point where I could use Ubuntu.

I know the first thing I'm going to be asked is what my graphics card is.  It's an ATI All-In-Wonder, according to a little instructions manual thing I found in my closet.  I no longer have it's packaging, and after many attempts I can't figure out how to open my case so that I can actually look inside and find out myself...  I did not build, nor help in the purchasing, of this computer, hence why I know so little about it.  The sticker on the case of this HP says it has an nVidia card, but I specifically remember that my brother put an ATI card in, as the card it originally had was crappy.

So, any tips on how I can fix this?  I'd really like to use this computer, and especially with Ubuntu.  If there isn't a decent driver for my card, I'll just settle with not being able to use the graphics card, but I'm hoping it won't come to that.

UPDATE: Just found it's box!  It's an All-In-Wonder 9600.  I'll go download the driver from the ATI site then, and hope it works.

---

### Post by Claan22 on 2007-12-20
Okay, I've found this:

[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

It says it works for Radeon cards, would it work for mine too?

---

### Post by Presto123 on 2007-12-20
Don't quote me on this, but I have noticed several times that people have suggested that driver. Wait on another response to be sure, though.

---

### Post by GSF1200S on 2007-12-20
Im not sure on the ati driver portion of this, but there is a command you can use from the command line to regenerate xorg, and that will at least get you back to a GUI.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You may have to press Alt+F1 to get to the prompt once you see the black screen.

Also, have you tried to install your video drivers with Envy? A lot of people have had luck with it...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good Luck!

---

### Post by Claan22 on 2007-12-20
> **Presto123 said:**
> Don't quote me on this, but I have noticed several times that people have suggested that driver. Wait on another response to be sure, though.

The one from the ATI site?

It said it was only supported on SUSE and Red Hat, I believe, but anyway I tried this method instead:
[http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Feisty_Installation_Guide)

Anyway, after the Ubuntu screen with the loading bar I get black.  Nothing else.

I'm gonna try typin in "sudo dpkg-reconfigure xserver-xorg", see if that helps.

---

### Post by Claan22 on 2007-12-20
> **GSF1200S said:**
> Im not sure on the ati driver portion of this, but there is a command you can use from the command line to regenerate xorg, and that will at least get you back to a GUI.

```
sudo dpkg-reconfigure -phigh xserver-xorg
```

You may have to press Alt+F1 to get to the prompt once you see the black screen.

Also, have you tried to install your video drivers with Envy? A lot of people have had luck with it...

[http://albertomilone.com/nvidia_scripts1.html](http://albertomilone.com/nvidia_scripts1.html)

Good Luck!

Alt+F1 at the black screen does nothing, though I tried it at the screen that says "Press ESC for options" or whatever.  I followed it through, but it didn't change anything.

Also, I don't know what Envy is, but I'll check it out right now.  Thanks.

---

