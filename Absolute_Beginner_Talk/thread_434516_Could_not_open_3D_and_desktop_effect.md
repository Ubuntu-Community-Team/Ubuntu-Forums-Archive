---
title: "Could not open 3D and desktop effect"
date: 2007-05-06
forum: Absolute Beginner Talk
---

### Post by mrflowerpot on 2007-05-06
I have installed nvidia-xgl, open GL&#65292;Gtk GL&#65292;compiz manager, ect. I used the gnome desktop effect to set the desktop effect, but no use at all. And when I tried to enable the 3d effect of the chess it said:Your system does not have the required software to enable 3D mode. Please contact your system administrator and ask them to install the OpenGL Python bindings and the GtkGLExt Python bindings.(Which I've already installed)
How can I solve it? Thanks.

UPDATE:
This time it seems the nvidia driver is OK, I can open the desktop effect now, but another problem appears= =! I can't drag and move the windows@@I can seen the cube rotation, but I can't drag and move any windows, and all the windows become wried looking= = all the close, maximum or minimum icon are gone@@
Here is the screen shot
How to solve it?
[IMG]http://forum.ubuntu.org.cn/files/thumbs/t_1_79697.png[/IMG]

---

### Post by teddybairs1 on 2007-05-06
Where the 3-D chess is concerned, I've no idea. I ran into the same problem after installing all the packages involved.

Where the 3D desktop effects are concerned, I'm assuming you have an Nvidia card. Is it a GeForce 2? My wifes computer has this card, and I can't ever seem to get OpenGL or the Desktop Effects to work at all, ever, even after installing the proprietary drivers. Her card is a 64MB SDRAM. What's yours?

---

### Post by kvonb on 2007-05-06
What video card do you have?

To find out if direct rendering is working (3d), open a terminal and type this:

```
glxinfo | grep direct
```

If it returns "yes", everything is ok, if not then you need to look at video drivers.

---

### Post by mrflowerpot on 2007-05-06
My video card is nivida GeForce Go7600.

---

### Post by kvonb on 2007-05-06
Teddybairz:

I have an Nvidia GeForce2-MX/400 in the computer that I am using right now (a spare system) and it works perfectly with both Compiz and Beryl.

What you need to do is use the 9631 driver from [www.nvidia,com]("http://www.nvidia,com").

To install it, see this thread here:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Use the first post, and scroll down to Step2, Option2, disregard the rest.

If you follow that to the letter, and simply replace this line:

```
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
```with this:

```
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```You should end up with direct rendering working, simply either enable Compiz from the "desktop effects" thing, or better still install beryl through synaptic.

---

### Post by teddybairs1 on 2007-05-06
What do I do to reset the driver if for some reason it fails completely and shoves me into a command line? This is my wife's computer and she'll kill me if I make it so she can't use it.

---

### Post by Malta paul on 2007-05-06
Ctrl /Alt   F7 returns to graphic mode  from Text mode. :)  Ctrl/Alt F1 to go into Text mode.

---

### Post by igknighted on 2007-05-06
> **kvonb said:**
> Teddybairz:

I have an Nvidia GeForce2-MX/400 in the computer that I am using right now (a spare system) and it works perfectly with both Compiz and Beryl.

What you need to do is use the 9631 driver from [www.nvidia,com]("http://www.nvidia,com").

To install it, see this thread here:

[http://ubuntuforums.org/showthread.php?t=263851](http://ubuntuforums.org/showthread.php?t=263851)

Use the first post, and scroll down to Step2, Option2, disregard the rest.

If you follow that to the letter, and simply replace this line:

```
sudo sh NVIDIA-Linux-x86-1.0-9629-pkg1.run
```with this:

```
sudo sh NVIDIA-Linux-x86-1.0-9631-pkg1.run
```You should end up with direct rendering working, simply either enable Compiz from the "desktop effects" thing, or better still install beryl through synaptic.

This is old, the proper way on feisty is to install the package nvidia-glx-new and change xorg.conf to use the "nvidia" driver instead of "nv".  There is a terminal command for this, but its weird in Ubuntu and not the normal one included with the drivers from nvidia's site.  Also, if he does use your method, the 9631 are legacy drivers (like for your card).  The new drivers are 9755, and with a new card like the go 7600 he should use the newest drivers

EDIT, sorry, thought this was @ the OP... for teddy, use the nvidia-glx package, it has the 9631 driver in a nice debian package with the proper kernel module for the Ubuntu kernel.

---

### Post by kvonb on 2007-05-06
> **igknighted said:**
> This is old, the proper way on feisty is to install the package nvidia-glx-new and change xorg.conf to use the "nvidia" driver instead of "nv".

Yes but a lot of people seem to be having problems with the "proper" driver.  I have about 5 threads going at the moment trying to sort out their driver problems, and unfortunately it seems as this is the problem :(.

Plus if you install the official Nvidia driver you get to use the excellent "Nvidia X server settings" util to change your screen resolution and refresh rate, which again is a big problem with Feisty!

---

### Post by kvonb on 2007-05-06
> **teddybairs1 said:**
> What do I do to reset the driver if for some reason it fails completely and shoves me into a command line? This is my wife's computer and she'll kill me if I make it so she can't use it.

Simply drop to the terminal if you get an error, and change "nvidia" to "vesa" in /etc/X11/xorg.conf like so:

```
sudo nano /etc/X11/xorg.conf
```

Scroll down until you see:

```
Driver         "nvidia"
```

and change it to:

```
Driver         "vesa"
```

Save and exit, then either reboot or issue this command:

```
sudo /etc/init.d/gdm start
```

That should get you back to a desktop, although it will be in reduced performance until you sort the problem out.

Try to note what errors it gives you if you have any problem, and post on the forums.

---

### Post by mrflowerpot on 2007-05-06
Well, after tried a few times to config my nividia it seems the trouble is that the driver could not be  installed properly. I even tried Envy, but it always come out "source was not built successfully" = =

---

### Post by igknighted on 2007-05-06
> **mrflowerpot said:**
> Well, after tried a few times to config my nividia it seems the trouble is that the driver could not be  installed properly. I even tried Envy, but it always come out "source was not built successfully" = =

Make sure you have the "linux-headers" package installed via synaptic so the proper module can be built.

---

### Post by mrflowerpot on 2007-05-07
This time it seems the nvidia driver is OK, I can open the desktop effect now, but another problem appears= =! I can't drag and move the windows@@I can seen the cube rotation, but I can't drag and move any windows, and all the windows become wried looking= = all the close, maximum or minimum icon are gone@@
Here is the screen shot
How to solve it?
[IMG]http://forum.ubuntu.org.cn/files/thumbs/t_1_79697.png[/IMG]

---

### Post by treeby on 2007-05-08
i copied this from someone else in another post...i had the same problem and this solved it:

"First, try changing the emerald theme with beryl-manager, and if that doesn't work, add this to your xorg.conf file (in /etc/X11/) under "screens":

Option "AddARGBGLXVisuals" "True"

Then restart X."

---

