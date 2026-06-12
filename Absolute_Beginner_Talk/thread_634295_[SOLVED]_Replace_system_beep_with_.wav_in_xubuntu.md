---
title: "[SOLVED] Replace system beep with .wav in xubuntu"
date: 2007-12-07
forum: Absolute Beginner Talk
---

### Post by Odd-rationale on 2007-12-07
So I found a way to play my own .wav file on logout and login ([http://ubuntuforums.org/showthread.php?t=633563](http://ubuntuforums.org/showthread.php?t=633563)).

Now is there a way to replace all system beeps with a .wav in xubuntu?

Thanks!

---

### Post by picpak on 2008-01-04
I don't know how to change it to a .wav but I know how to turn it off:

1) Edit /etc/modprobe.d/blacklist:

```
gksudo mousepad /etc/modprobe.d/blacklist
```

2) Add the following line:

```
blacklist pcspkr
```

Save it, exit and restart.

---

### Post by JoshuaRL on 2008-01-04
I don't think you can put a .wav in there since it's a system beep.  But you can make one that sounds more pleasing.

I took the following from this article:  [http://www.pcworld.com/article/id,138903-page,2-c,linux/article.html](http://www.pcworld.com/article/id,138903-page,2-c,linux/article.html)

"**Disembeep Your Internal Speaker**
It's a crying shame but true: Though we are well into the 21st century, a lot of Linux apps, ranging from the Gnome Terminal to the OpenOffice.org word processor, beep your PC's internal speaker when they need your attention. What is this, 1982? Seriously.

There are several solutions to this problem. First, you can disable the internal speaker entirely. To do so, open a Terminal and enter these two lines:

```

sudo rmmod pcspkr
sudo gedit /etc/modprobe.d/blacklist

```

In the text file that opens, add the following lines at the bottom, save, and close:

```

# internal pc speaker
pcspkr

```

Personally, though, I like to humanize the beep rather than eliminate it. To find a beep you can stomach, fire up a Terminal and enter this command:

```

xset b 100 2000 20

```

Now press Backspace a few times without entering a command. The Terminal should emit a quick, high-pitched beep. Now enter:

```

xset b 100 50 10

```

...and press Backspace a few more times. You'll hear a dull thump. Which is more to your liking? Or would you prefer to pick a beep all your own? The numbers that follow 'xset b' determine the internal speaker beep's volume (as a percentage of total), pitch (in hertz), and duration (in milliseconds). Experiment!

When you've found the beep you want, make it the default by clicking System, Preferences, Sessions. On the Startup Programs tab, click Add. Enter Beeps for Name, and the entire 'xset b' command line you settled on for Command. Click OK and then Close."

Hope that helps!

---

### Post by Odd-rationale on 2008-01-05
Thanks! That helps!

---

