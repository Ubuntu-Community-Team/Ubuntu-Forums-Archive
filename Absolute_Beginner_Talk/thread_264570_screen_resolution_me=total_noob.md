---
title: "screen resolution me=total noob"
date: 2006-09-24
forum: Absolute Beginner Talk
---

### Post by Zarrinnis on 2006-09-24
I just installed ubuntu for the first time. I like it but I have a problem. The only resolution it offers me is 1024x768 and the refresh rate is only 60hrtz. Is there a way to fix this? Im still learning and have lots to learn so please be kind:)

---

### Post by Enjeru on 2006-09-24
Open terminal and type:

sudo dpkg-reconfigure xserver-xorg

This will lead you through a step by step guide to customizing some settings, which includes resolutions.  Once you get to the resoultion list, press space to add them to your list.  After you've done that, restart and you should be able to choose the all the resolutions you ever wanted.

---

### Post by orb9220 on 2006-09-24
Post your video card chipset. So we can point you to the right driver for your card.

---

### Post by Zarrinnis on 2006-09-25
o thanks guys, it seems to be working fine now but on the left of the screen is a bar of just black and the right its cut off a little. Any ideas on how to fix this?

---

### Post by bodhi.zazen on 2006-09-25
Use the knobs/buttons on your monitor to center/resize the image.

---

### Post by andypaxo on 2006-09-25
When you say the screen is cut off...

If you move your mouse as far to the left as it will go can you still see it?
- Yes: That's just your monitor settings, nothing to do with Ubuntu. Use the buttons on the front of your screen
- No: Might be your graphics card drivers, tell us what type of graphics card you have and we can help you to get the correct drivers installed

Hope this helps

---

### Post by Zarrinnis on 2006-09-25
no it isnt my monitor because the settings on it work fine for windows. If i move the mouse all the way to the left the mouse doesnt move over to the black screen, and I belive my graphics card is ATI Radeon X850, something like that, I cant really remember. Any Idea how to fix this? I also noticed another problem. When I start up ubuntu It doesnt show any video and is just a black screen. The video only shows up after i enter the username and password

---

### Post by bodhi.zazen on 2006-09-25
See my previous post.

Windows and Linux use slightly different drivers so the image is, in my experience, not always centered on the monitor in the same way. This depends on you monitor, of course.

---

### Post by orb9220 on 2006-09-25
Yes if the mouse stays on the screen then it is your monitor adjustment. I had to adjust the monitor's in linux even tho they are set for windows.

---

### Post by Zarrinnis on 2006-09-25
Ok, but what about the other problem im having which is when I start Ubuntu the login screen is all black. After I type in my username and password (even though I cant see it) I hit enter and then Ubuntu appears. Any Idea why this is happening?

---

### Post by white on 2006-09-25
Can you get to the desktop or are you still at the command line?

If you run **sudo dpkg-reconfigure xserver-xorg** you need to choose from a list of settings. I've had something like this before when I didn't use the vesa or ati option, I stayed at command line.

---

### Post by bodhi.zazen on 2006-09-25
> **Zarrinnis said:**
> Ok, but what about the other problem im having which is when I start Ubuntu the login screen is all black. After I type in my username and password (even though I cant see it) I hit enter and then Ubuntu appears. Any Idea why this is happening?

LOL :lol:

You can try this first:
Ctrl-Alt-F1 to go to tty1
You can return to your GUI with Ctrl-Alt-F7
Log in.
You are at the CLI.
Type the following commands```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak
sudo dpkg -reconfigure -phigh xserver-xorg
```

Now return to your GUI: Crtl-Alt-F7
Restart X Ctrl-Alt-Backspace.

If that breaks X (your gui)
Ctrl-Alt-F1
```
sudo cp /etc/X11/xorg.conf.bak /etc/X11/xorg.conf
sudo /etc/init.d/gdm restart
```

And post your results.

---

### Post by Zarrinnis on 2006-09-26
thanks guys! After i typed in those commands everything seems to be working just fine. Thanks for everything!:)

---

