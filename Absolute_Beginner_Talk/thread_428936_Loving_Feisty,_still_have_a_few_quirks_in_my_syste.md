---
title: "Loving Feisty, still have a few quirks in my system"
date: 2007-04-30
forum: Absolute Beginner Talk
---

### Post by mlhudson on 2007-04-30
I've got two problems...When I use the GL Desktop/Desktop Effects (which I understand is Compiz):

1. My metacity theme (specifically the top bar with the maximize/minimize buttons & themed bar) DISAPPEAR. I've ticked several of the options in the GL Desktop to see if any of them cause it to return...but no luck.

2. I can't use the terminal window. I get a completely white window for the terminal that will not allow any entry.

While neither of these render my system useless, I would love to know if anyone has found ways to around this. I love using the visual effects and making my XP friends drool a little. But, turning it on & off on a regular basis becomes a bit annoying. 

I know that these effects are more 'proof of concept' than actual features, but I would love to know how to make them work.

---

### Post by starcraft.man on 2007-04-30
These sound like problems with your graphics card driver. You did install your cards proprietary driver correct?  Through the restricted management or Envy (I prefer envy)?

---

### Post by Spike-X on 2007-04-30
You need to add the following lines to your xorg.conf file:

    Option         "AddARGBGLXVisuals" "True"
    Option         "TripleBuffer" "true"

To edit this file; 

```
gksudo gedit /etc/X11/xorg.conf
```

Then add the lines under where it says "Default Depth 24" down the bottom there.

Save the edited file, then Ctrl-Alt-Backspace to restart X, and you should be good to go!

**ALWAYS, BEFORE EDITING XORG.CONF, YOU SHOULD BACK IT UP:**

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```

To restore the backup:

```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```

---

### Post by mlhudson on 2007-04-30
i think i used automatix...i've got an Nvidia gforcefx 5200 using the Nvidia driver...i haven't tooled around in the preferences at all for the card. could there be an issue with needing to set something up differently in the card? most of the features work well in the GL Desktop (cube turn, rain, wobbly windows, etc) just my terminal & top bars seem to have been effected.

---

### Post by mlhudson on 2007-04-30
And, my "Default Depth" says "16", not "24". Does that make a difference?

---

### Post by Spike-X on 2007-04-30
I dunno. Give it a try!

---

### Post by mlhudson on 2007-04-30
Yeah...! We're one for two.
That code fixed the terminal.
However, I still don't have the top bar restored. Any further suggestions?

---

### Post by mlhudson on 2007-04-30
oops i spoke too soon. it worked as it restarted (the terminal was open when i shut it down, so it opened on restart).

Now, it's back as it was. No terminal w/ the GL Desktop running.

---

### Post by mlhudson on 2007-05-01
Are there ANY other ideas?

---

### Post by mlhudson on 2007-05-01
spike-x...THAAAAAAAAAAAAAAAAAAAAAAAAANK YOU! I retried your suggestion after reading through some of the posts in the Desktop Effects section. Your code works great! I didn't RESTART. Evidently, restarting the whole system restarts the NVIDIA kernel and implements the efffects!

The borders are BACK! And, YES, I did have to change the "Depth" to 24.

You ROCK! Many, Many thanks!

---

### Post by Spike-X on 2007-05-02
It's not my code! I got it from these here forums, same as you.

Glad you've got it sorted.

---

