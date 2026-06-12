---
title: "No display on boot"
date: 2007-11-28
forum: Absolute Beginner Talk
---

### Post by Danondorf on 2007-11-28
I just installed ubuntu for the first time using a Live CD. When I boot to the harddrive I get past the loading screen and it goes straight to the BusyBox screen without any errors, and when I boot to the Live CD it gets past the loading screen and the monitor stops receiving a signal. I'm getting the drum music out of the speakers, so I'm fairly sure its just a display thing, but I'm also unable to pull up the text console. I've found one other person who had pretty much identical problem to mine, but he was able to get into the text console. his post is [here]("http://ubuntu-utah.ubuntuforums.org/showthread.php?t=612721").

Thanks in advance

---

### Post by master_kernel on 2007-11-28
What is your video card?

---

### Post by Dr Small on 2007-11-28
Have you tried accessing a virtual terminal by pressing CTRL + ALT + F1 ?

---

### Post by Aranthos on 2007-11-28
I have a similar problem: Whenever I boot (either from the Live CD or from the installed OS on my hard drive) it says at the bottom of the screen "Kernel Alive" and something I can't quite remember about Kernel something something table something something...   I really wish I could be more specific with the text it displays, but it only shows for less than a second before the screen goes black.

I'm running an AMD Athlon 64 X2 4200+, with 2GB of DDR2 667MHz of RAM and an nVidia GeForce 8800GTS 320MB.

BTW - I'll give the virtual terminal a shot now.  I'll report soon  =]

[EDIT] - Sorry if this sounds exceedingly stupid, but at what time am I supposed to do the 3-finger-salute?  Also, the second line of the message before it goes black is "Kernal directly mapping tables up to [long number, lots of zero's] @ 8000 6000" or something very similar.  Hope that helps.

---

### Post by Matthew Bartram on 2007-11-28
Don't know if this is quite the same - On my dell, although the live CD works just fine, when booting off the hard drive the screen goes blank after grub (and probably similar messages about the kernel) until X starts - after which it is fine. Although the virtual terminals appear to try using a screen size far larger than my screen - so I can only see the top left of what I should see. I wonder if that's also happening with the boot screen too - that it's displaying the stuff in what it thinks is the screen's centre - off the actual screen.
Maybe it's the same as your problem. I can't tell from your post - have you tried just waiting a few minutes to see if it starts up?

---

### Post by Aranthos on 2007-11-28
I've given it about 10 minutes, but my guess is that it's an issue with my graphics card, since the hard drive clunks away for a short while, though I don't have any sound.  I'm not sure if this is because Ubuntu doesn't have integrated drivers for my sound card (which I doubt) or if it's something else...  Either way, I think I'd be wise to put this in my own thread, to avoid confusion between mine and Danondorf's problem.

---

### Post by Danondorf on 2007-11-28
Wow, well I'm feeling pretty stupid, I guess I hit the F-lock at some point, thats why the text console wasn't popping up. And now for some reason when I boot from the harddrive it's working the same as the live cd. I have the VisionTek Radeon X1300. I tried doing the debian configuration thing by executing the line 'sudo dpkg-reconfigure xserver-xorg' but it couldn't detect my graphics card. I also tried going to the bios to disable the onboard graphics, cause I heard that can mess things up, but I couldn't the setting for that. I'm assuming I just need to install a driver for my card, so I'll just look that up and try it out.

---

### Post by Willye on 2007-11-28
.

---

### Post by Matthew Bartram on 2007-11-29
I had a problem on a friend's computer, where the live cd worked fine, but once running off the hard drive, X wouldn't work. We ran sudo dpkg-reconfigure xserver-xorg accepting all the defaults, and it didn't help. It was only when we ran it and changed the monitor size - his was a relatively high resolution laptop screen, so I thought that the script guessing values for a monitor larger than his, since it wasn't e.g. getting resolution values too big, would be alright. But we told it the screen's size and let it do the rest, and then it worked.

Similarly I had a problem some time ago with onboard graphics and external graphics, where the solution was to get a bit more involved in dpkg-reconfigure xserver-xorg.

---

### Post by Danondorf on 2007-11-29
Where do you change the screen resolution? I tried it through dpkg-reconfigure xserver-xorg, but it didn't seem to permanently change anything. One other thing I've noticed is that if I boot to the harddrive while the live cd's in it goes to the blank login screen, but if the live cd isnt in it goes to BusyBox. Oh, and I downloaded a driver with xp, how would I go about locating it on my harddrive through the text console?

---

### Post by Matthew Bartram on 2007-11-29
If you can't get into a proper GNOME session, I'd have thought the only way to change your resolution is through xserver-xorg. Perhaps by disabling the resolutions higher than the one you want?

To access the driver, you'll have to mount your Windows partitions. That's probably done with 'mount' - you could try looking through 'man mount' to see if it's helpful. After that, I don't know. Depends on quite what format this driver takes - is it a .deb? is it a windows driver? is it an RPM?

---

### Post by Danondorf on 2007-11-29
Oh, well theres another dumb thing, I just looked around a bit more and realized that that was actually a dumb question. So, I have the file ati-driver-installer-7-11_x86_64.run, I need a good way to get that driver installed on my machine. Would apt-get work for that?

---

### Post by master_kernel on 2007-11-29
You can install the ati drivers with XGL by typing:
```
sudo apt-get install xserver-xgl xorg-driver-fglrx
```

---

### Post by Danondorf on 2007-12-01
Alright, I have several possible ways I could go about fixing this problem now, but they all require I access the text console. Whenever I start ubuntu without the cd it goes through the loading screen and then goes straight to BusyBox. I've tried pressing ctrl-alt-f1, but it just says 'loading, please wait'. I've let it sit like that for a bout 30 minutes, but it doesn't do anything. So my first step is gonna need to be to figure out how I can fix it so that it runs like the live cd runs.

---

### Post by Danondorf on 2007-12-05
Alright, finally got it fixed, I've tried so many things I really have no idea how I got it to work, all I know is I rebooted and it worked.

---

