---
title: "Where's the command line? and more"
date: 2006-04-11
forum: Absolute Beginner Talk
---

### Post by esteban2x on 2006-04-11
I just spent HOURS getting Ubuntu to work. It does. I actually got my wired network card to work too. However, I have a desktop screen and how do I get to a command line? Plus, the screen is only about 6 inches wide by 5 inches tall. I only have a choice of 640 X 480 so what do I do to make this horribly small screen bigger? I am VERY new and need real good directions. Also, I have a netgear wireless pcmcia card oh yea I'm on an old gateway laptop...the wireless card doesn't work. Any hints there too. Thank you in advance. I can't believe I finally got this system to work. So glad to get out of windows but I need help.

Steve in Mazatlan Mexico

---

### Post by taurus on 2006-04-11
To open a terminal, click on Applications -> Accessories -> Terminal.  Now, you may want to fix your X by running this command from the terminal...
```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by nalmeth on 2006-04-11
You sound very suprised. In fact I'm a little suprised it took such a long time to get running. Wired ethernet *should* be operation out of the box. Wireless usually involves a couple extra steps.
The command line (terminal) is in APPLICATIONS --> ACCESSORIES --> Terminal
To reconfigure your display through the terminal, enter this:
sudo dpkg-reconfigure xserver-xorg 
and pick the extra resolutions you want.
I always link to here for a place to start with wireless:
[https://wiki.ubuntu.com/WirelessTroubleshootingGuide](https://wiki.ubuntu.com/WirelessTroubleshootingGuide)

---

### Post by NeghVar on 2006-04-11
Applications>Accessories>Terminal

for CLI. Have you tried installing the drivers for your video card, also I believe it can be fixed with editing the xorg file, althoughg I have no clue how to.

[https://wiki.ubuntu.com/UserDocumentation](https://wiki.ubuntu.com/UserDocumentation)

The wiki is your friend, especially for new users. You can find alot of advice there, I believe it talks indepth about Wrieless net cards and xorg as well as many other possible issues.

---

### Post by esteban2x on 2006-04-11
when I go to applications/accessories   there is no "terminal" choice?
I have archive manager, character map, calculator, dictionary and text editor.

---

### Post by nalmeth on 2006-04-11
Did you install dapper, the as yet unreleased next release of ubuntu (breezy is the current stable release)? I think they might be throwing it in APPLICATIONS --> SYSTEM TOOLS now.
If all else fails hit ALT-F2 and type gnome-terminal.

---

### Post by esteban2x on 2006-04-11
Thanks for the help. Found it. I used to run redhat a long time ago and have to relearn everything.  with no root like redhat, i was confused.

---

