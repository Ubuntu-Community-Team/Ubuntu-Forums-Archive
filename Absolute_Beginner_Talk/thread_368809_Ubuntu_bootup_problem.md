---
title: "Ubuntu bootup problem"
date: 2007-02-23
forum: Absolute Beginner Talk
---

### Post by SoftTaco on 2007-02-23
I have been trying to get Ubuntu running on my home pc for some time now. I use it at work and have a personal laptop that have Ubuntu on them, so i am fairly familiar with the system. 

First, i tried loading up the standard Ubuntu 6.10 live cd, i ran the cd check on it and it came back no errors. That didn't work (will elaborate later).

Then, i downloaded and successfully installed using the alternate install cd, but what seems like the same problem as before came up. When I log into the sign-on screen the system hangs at the GUI loading screen.(pictured below) However the screen doesnt show up right the image of the loaderin the middle is all segmented and malformed

[IMG]http://i159.photobucket.com/albums/t158/Soft_Taco/Scshot.png[/IMG]
(this Image is from a PC running WMware, not the pc that is having the problem)

Any ideas?

I thought it might be because i was running a Nvidia 7800, so i tried setting up the nvidia driver, that had no effect.

 i can access th console so just say the word and i will cat any pat of any file you need to see

---

### Post by bernied on 2007-02-23
You could try to revert to a simple vga display driver, at least then you would know whether it was the nvidia driver that is giving you grief. To do this you need a terminal. If, when you get to the stage that you are picturing above, you hit Ctrl-Alt-F1, you get a terminal (there are six of these, using F1-F6, pre-loaded at boot time). So login there, then try:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.nvidia
sudo dpkg-reconfigure xserver-xorg
```
So the first command takes a backup copy of your main X configuration file (cp is copy, sudo means do it as administrator, and /etc/X11/xorg.conf is the file to take a copy of), so if there are (even bigger) problems after you run the second command, you can reverse the damage by repeating that command with the two file names reversed.

The second command will ask you a bunch of questions about your X install. If you don't know the answer choose the default that is offered to you. When it comes to display drivers, choose 'vesa'. This is a generic vga driver that should work.

When you have finished with the configuration, or anytime you want to see whether your changes have worked, you can do either (i) go back to your stalled X-session with Ctrl-Alt-F7, then restart it with Ctrl-Alt-Backspace or, if that doesn't work (ii) on the terminal type:
```
sudo /etc/init.d/gdm restart
```which should also restart the X-session.

The vesa driver won't give you the same display options as the nvidia driver, and it might be slow and blurry, but you will be able to surf the net and hopefully get a bit closer to the problem.

I'm sorry I know nothing about nvidia, but there are loads of howtos, tips and other documentation out there. just google

---

