---
title: "Resolution problem"
date: 2006-09-27
forum: Absolute Beginner Talk
---

### Post by #1 stunna on 2006-09-27
I've read the howto, but the terminal and shell prompt says that the file doesn't exist or can't be found whenever I type:

sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.custom

I don't know what that opens, but I'm following the Howto guide.  I know this topic has been brought up a lot, but I'm confused so any help would be greatly appreciated.

Oh yeah, Ubuntu only recognizes resolutions up to 1024x768 @ 60.

Trying to get 1280x1024 @ 75, 32 bit.

---

### Post by caimex on 2006-09-27
I don't know which HowTo you are following, but when you do a ```
sudo dpkg-reconfigure xserver-xorg
```

And you get the window to select resolution and such you have to highlight it with the arrow keys and press SPACE BAR before pressing enter. I had trouble with this and many other people as well.

---

### Post by henriquemaia on 2006-09-27
> **#1 stunna said:**
> I've read the howto, but the terminal and shell prompt says that the file doesn't exist or can't be found whenever I type:

sudo cp /etc/x11/xorg.conf /etc/x11/xorg.conf.custom

I don't know what that opens, but I'm following the Howto guide.  I know this topic has been brought up a lot, but I'm confused so any help would be greatly appreciated.

Oh yeah, Ubuntu only recognizes resolutions up to 1024x768 @ 60.

Trying to get 1280x1024 @ 75, 32 bit.

One thing:

The command is 

sudo cp /etc/**X**11/xorg.conf /etc/x11/xorg.conf.custom

with a major X and not a small one. You can complete paths (as well as commands) by pressing tab on the terminal. If you type, for instance:

sudo cp /et 

and then press tab, you'll see different possible options to choose. If it's only one available, it completes it on the command line. In this way you never get the paths wrong.

---

### Post by #1 stunna on 2006-09-27
Oh wait nevermind, haha.

Umm, I made all the changes, now how do I apply them?

---

### Post by henriquemaia on 2006-09-27
> **#1 stunna said:**
> Oh wait nevermind, haha.

Umm, I made all the changes, now how do I apply them?

Restart your X server... save everything you're working at and press

ctrl+alt+backspace


You can test the confs first, doing a 

```
sudo xinit -- :2
```

If they are ok, you'll see a another X session opening with a terminal in it. To exit it, press ctrl+alt+backspace. Since everything is ok, do the same on your normal X server.

---

### Post by #1 stunna on 2006-09-27
Thanks henriquemaia and caimex for the help.  All is working well, Thank You!!

---

