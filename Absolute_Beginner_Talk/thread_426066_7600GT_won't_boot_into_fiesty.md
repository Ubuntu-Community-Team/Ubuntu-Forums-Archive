---
title: "7600GT won't boot into fiesty"
date: 2007-04-28
forum: Absolute Beginner Talk
---

### Post by Scummo on 2007-04-28
I have fiesty installed on a HP dual boot with XP machine with built in intel graphics. I have just bought and installed an XFX 7600GT 256mb and now fiesty will not boot. I get a long list of updating numbers on a black screen and nothing else!
I have now removed the card and switched back to the onboard graphics. I guess I need to install some drivers...but how,where from etc...
any help much appreciated!

---

### Post by Legionox on 2007-04-28
I think you'll need to enable the "vesa" driver and then boot into fiesty to install the nvidia driver

---

### Post by Scummo on 2007-04-28
how do i do that?

---

### Post by Legionox on 2007-04-28
Sorry I didn't explain earlier
After you start up I'd assume that X server crashes and gdm doesn't start (correct me if i am wrong)
Move into a recovery console (Ctrl+Alt+1)
Enter command```
sudo dpkg-reconfigure xserver-xorg
```
Leave ALL settings alone except for which driver to use which should be changed to "vesa"
Restart your computer```
sudo reboot
```
When you start up you should see your old login screen
Login then download the Nvidia driver from [here]("http://www.nvidia.com/object/linux_display_ia32_1.0-9755.html")
Follow the instructions included on the page
Run the reconfigure xserver-xorg command in normal Terminal (Applications->Accessories->Terminal)
Leave ALL settings alone except for which driver to use which should be changed to "nvidia"
Now restart X Server by pushing Ctrl+Alt+Backspace
Hope this works:)

---

### Post by Compyx on 2007-04-28
Why download the driver from nVidia? It's in the repositories, just do:
```

sudo apt-get install nvidia-glx-new

```
This will install the driver, then you run:
```

sudo nvidia-xconfig

```
to make xorg use the nvidia driver, and perhaps:
```

sudo nvidia-glx-config enable

```
to enable 3d-acceleration.

I haven't tested this, since my box already had an nVidia card when I installed Ubuntu.
Just post here if you're having problems.

Hope this helps.

---

### Post by Scummo on 2007-05-01
thanks guys. I am now able to get into Ubuntu, but i am unclear as to which driver i am actually using.
When i run the xorg config it has the Vesa driver as the default....
So, how can I check which driver i am actually using? and
I tried enabling the nvidia driver(as above) but this resulted in the same problem as before.ie cant boot in to ubuntu. Any more advice is greatly appreciated!

---

