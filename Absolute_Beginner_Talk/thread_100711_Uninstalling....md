---
title: "Uninstalling..."
date: 2005-12-08
forum: Absolute Beginner Talk
---

### Post by SomethingTohide on 2005-12-08
How do I get it out of my boot system and take it off my computer?

---

### Post by linbetwin on 2005-12-08
Take what out? Ubuntu?

---

### Post by SomethingTohide on 2005-12-08
Yes Ubuntu, I tried deleting the partition but the bootloader gave me errors so I reinstalled and it still doesn't work and no one's help me solve it so I'm getting rid of it.

---

### Post by linbetwin on 2005-12-08
You can boot with the XP CD and type "fixmbr". I don't remember how to get to the "command line" withe the XP CD, but I remember it wasn't to hard when I did it. And ignore the warnings that XP will give you when you type "fixmbr".

---

### Post by SomethingTohide on 2005-12-08
Ok thanks. When I installed this it installed the packages and when I rebooted it loads ubuntu and then it asks for a login name and tells me ServerX couldn't be loaded or something, someone said to type startx or xstart and I tried them and one didn't work and the other said that ServerX didn't work.

---

### Post by ssam on 2005-12-08
if you want we can probably help you get the xserver working.

---

### Post by SomethingTohide on 2005-12-08
Yeah I'd rather that then taking it off my computer. Do you have any ideas?

---

### Post by Brunellus on 2005-12-08
[QUOTE=SomethingTohide]Yeah I'd rather that then taking it off my computer. Do you have any ideas?[/QUOTE]
To have ideas, we'd need data.

1) What EXACTLY is the error message being shown?  Do not paraphrase, do not interpret, do not summarize.  Tell us EXACTLY what you're seeing.

2) When the computer starts up, does it just hang, or are you taken to a plain text screen (white letters on black background) asking you to 

login:

if so, then enter your username and your password, and we can begin to see what is going on.

---

### Post by SomethingTohide on 2005-12-08
When it boots the GRUB loader I can pick the Ubuntu stuff or XP Pro. If I pick Ubuntu it goes to the loading screen and when it finishes it brings me to a black screen, white writing saying login. Before I can type anything it gives me a blue screen, grey box saying
" Failed to start the X server(your graphical interface). It is likely that it is not set up correctly. Would you like to see the X server output to diagnose the problem "

If I pick no it brings me to the black and white login screen, and I can login and run some commands. If I pick yes it gives me a log and the only bad thing I see is after it loads some it says

"Fatal server error:
no screen found"

---

### Post by Estariel on 2005-12-08
log into the text mode.

Then do the following, it will reconfigure your graphical system. You will have to input some stuff, so if you are unsure about any of the options, just ask, I will help you.

```

sudo dpkg-reconfigure xserver-xorg

```

---

### Post by SomethingTohide on 2005-12-08
I tried that before, and I set it up based on what I know of the system, and when it said if you're unsure set default. After finishing it said the same thing as before. I'll try again

---

### Post by linbetwin on 2005-12-08
try this:
```
dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by SomethingTohide on 2005-12-08
Ok guys I fixed it I just checked the error in the log and troubleshooted. The first problem was that it said my driver didn't support 24bit resolution, or 16bit. But I can run it fine in 32bit on XP. So now I'm stuck with 8bit, any ideas?

---

### Post by Estariel on 2005-12-08
what is your graphic board?

Also, please do the following on the Terminal:
```
less /etc/X11/xorg.conf
```

scroll down, till you find a line
```

driver         blablablabla

```
please paste that line here.

---

### Post by SomethingTohide on 2005-12-08
NVidia GeForce4 MX440, I'm getting a X800 for Christmas though.

I see this? Also my card is 64mb ram.

Section "Device"
        Identifier      "NVidia GeForce4 MX440"
        Driver          "nv"
        VideoRam        64000
EndSection

---

### Post by Estariel on 2005-12-08
Use Synaptic to install nvidias driver (and not the free driver that comes with ubuntu)
follow this how-to:
[https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29](https://wiki.ubuntu.com/BinaryDriverHowto/Nvidia?highlight=%28nvidia%29)

if it works, edit your /etc/X11/xorg.conf and change the bitdepth to a value of your liking...

---

### Post by Qrk on 2005-12-08
Definatly get the non-free nvidia driver. Then, when doing

```
sudo dpkg-reconfigure xserver-xorg
```

choose it (right under "nv") in the dialog. It should work a lot better. 

I have never found nv to work very well at all.

---

