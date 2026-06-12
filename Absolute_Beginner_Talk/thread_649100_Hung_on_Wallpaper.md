---
title: "Hung on Wallpaper"
date: 2007-12-24
forum: Absolute Beginner Talk
---

### Post by glaze0101 on 2007-12-24
I have been using Gutsy for a while and just installed a bunch of fonts (around 1000) to ~.fonts

Now I cant get past my wallpaper.  

I posted about this earlier ([http://ubuntuforums.org/showthread.php?t=649030](http://ubuntuforums.org/showthread.php?t=649030)) but still have not found a solution.

Any help?  I removed the .fonts dir that I had created.

Can I just re-install the desktop environment?

Would this work? 
```
sudo apt-get install ubuntu-desktop
```

---

### Post by LowSky on 2007-12-24
why did you vreate a new thread?

how did you install the fonts?

---

### Post by glaze0101 on 2007-12-24
I started the new thread cause I realized that it was hanging on the wallpaper, not that GNOME was not starting.  

In fact the issue seems to be just that all I see is thge wallpaper (yes, the image I set even) and not any of my navigation.  I also dont see anything when I right click.  but I can switch to terminal using crtl-alt-f1 and back to the wallpaper using ctrl-alt-f7 so Xserver is running, right? it says it is when I do startx

To install the fonts I created ~.fonts and dumped them in there.  That is all that had happened before this issue started.

I have now removed that dir and all the contents

---

### Post by spiderbatdad on 2007-12-24
it cant hurt. you probably already have it. are you running compiz as your windows manager or metacity? or what? there is a tool called fontforge that may help. not sure, and it has documentation. you might try this to get your environment back ```
metacity --replace
```

---

### Post by glaze0101 on 2007-12-24
Great Idea, 
I am running compiz BTW
When I did the metacity replace I got this
Window manager error: Unable to open X display

So then I did compiz --replace and it said unable to open display as well.

Any thoughts?

What happens if I do:
<code>apt-get install ubuntu-desktop</code>
????????????

---

### Post by p_quarles on 2007-12-24
> **glaze0101 said:**
> 
What happens if I do:
<code>apt-get install ubuntu-desktop</code>
????????????
Nothing would happen. That package is just a list of dependencies, most or all of which you likely already have. It would find that those packages are already installed, and ignore the request. 

What's the output of this?:
```
cat /var/log/Xorg.0.log | grep EE
```

---

### Post by glaze0101 on 2007-12-24
*I get *
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(II) Loading extension MIT-SCREEN-SAVER

* When I do grep WW I get a bunch of warnings*:
(WW) intel(0): Option "UseFBDev" is not used
etc.....

---

### Post by glaze0101 on 2007-12-24
I just saw in the WW log the following:
(WW) The directory "/usr/share/fonts/X11/cryillic" does not exist.

This might be it.  But how do I bring the default font files back??

---

### Post by p_quarles on 2007-12-24
> **glaze0101 said:**
> I just saw in the WW log the following:
(WW) The directory "/usr/share/fonts/X11/cryillic" does not exist.

This might be it.  But how do I bring the default font files back??
Nah, I have that line too. The default Xorg in Ubuntu comes with a long list of warnings written to the log, but it should work fine in spite of those. 

You could always trying reconfiguring the X server:
```
sudo dpkg-reconfigure xorg
```
You could also look through some of the other log files to see if you can find any clues. Xorg.log.0 didn't have any actual errors, so it's possible that this issue has nothing to do with X.

---

### Post by glaze0101 on 2007-12-24
I am starting to think that it might have to do with the fact that when I try to do either
compiz --replace
or
metacity --replace 

I get the message:
unable to open X display

---

### Post by glaze0101 on 2007-12-24
Whenever I see someone post their xorg.conf file here it has a section about fonts and where the font files are.  Mine does not.  SHould it??

---

### Post by glaze0101 on 2007-12-24
Another discovery, I still need help.

X seems to be working and so does Compiz.  I can use the cube and see the other workspaces but all my workspaces have on them is the wallpaper image, no navigation at the top or bottom to choose a program and open it (or do anything)

---

### Post by p_quarles on 2007-12-24
I see. And what about keyboard shortcuts? Do any of those work? (e.g, alt-F1 to open a terminal, alt-F2 to open a "run" prompt). It may just be that the Gnome-panel went missing, and you'll just need to bring it back manually.

---

### Post by glaze0101 on 2007-12-24
Well they work with ctrl-alt-f1  so sorta

How do I bring back the panel???

---

### Post by p_quarles on 2007-12-24
Ctrl-alt-F1 brings up the full-screen terminal, right? I'm not sure if that will work. Anyway, the command to display the panel is just:
```
gnome-panel
```

---

### Post by glaze0101 on 2007-12-24
Well, it was a good idea, but didnt work.

What would happen if I removed all the customization??

with:
rm -rf .gnome .gnome2 .gconf .gconfd .metacity

---

### Post by p_quarles on 2007-12-24
I think the safer way to do that would be to add a new user and log in as that. 
```
useradd -m *newusername*
```

---

### Post by glaze0101 on 2007-12-24
OMG - That did it.

Ok, so how can I fix my other user??

Thank you so much for helping me with this p_quarles

---

### Post by asmiller-ke6seh on 2007-12-24
Sounds like hosing ALL of your fonts did the damage, cause when X tries to build a display, and it can't find any fonts, what is it supposed to do.

Now that you have a working user space, maybe you can restore the old fonts information by copying it from the new user space? Look into your xorg.conf file, first, and compare it with the fonts section of the damaged user space...

Good luck - and Happy Holidays.

---

### Post by p_quarles on 2007-12-24
> **glaze0101 said:**
> Ok, so how can I fix my other user??
Well, basically, it looks like your hunch was right: there's a configuration somewhere in your home folder that's messing things up.

Instead of just deleting everything wholesale, though, I'd try renaming various configuration folders. That way, they should still be regenerated, but you won't be losing everything (if you did that, you may as well just switch to the new user you just made). 

For instance:
```
mv .gconf gconf.bak
```
Do this one step at a time, so you don't wind up changing more than you need to.

---

### Post by spiderbatdad on 2007-12-24
do you have xorg installed? also xserver-xorg, xserver-xorg-dev, xserver-xorg-core....and you might need xserver-xgl   all are in synaptic

---

### Post by glaze0101 on 2007-12-24
Thanks again and Im marking this as solved!

---

