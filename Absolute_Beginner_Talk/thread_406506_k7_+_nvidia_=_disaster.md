---
title: "k7 + nvidia = disaster?"
date: 2007-04-11
forum: Absolute Beginner Talk
---

### Post by wog on 2007-04-11
Okay. 
I'm trying to install the k7 image and then get the nvidia drivers to work, because experience tells me if I get nvidia working first and then switch to k7, the nvidia drivers no longer work.

My notes tell me to install linux-image-k7.
I did that in Synaptic, and now I *seem* to be using the k7 image.
Cool. So now all I have to do is get the nvidia drivers to work.

My notes tell me to install:
nvidia-glx
nvidia-settings

then type:
```
sudo nvidia-glx-config enable
```

then reboot.

I quickly discovered in Synaptic that if I select nvidia-settings, that unsets nvidia-glx and vice-versa. So I installed nvidia-glx in the hopes that Edgy made nvidia-settings obsolete, and then tried the nvidia-glx-config line.

And this is what I got:
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

...help???

---

### Post by nudnik on 2007-04-11
> **wog said:**
> Okay. 
I'm trying to install the k7 image and then get the nvidia drivers to work, because experience tells me if I get nvidia working first and then switch to k7, the nvidia drivers no longer work.

My notes tell me to install linux-image-k7.
I did that in Synaptic, and now I *seem* to be using the k7 image.
Cool. So now all I have to do is get the nvidia drivers to work.

My notes tell me to install:
nvidia-glx
nvidia-settings

then type:
```
sudo nvidia-glx-config enable
```

then reboot.

I quickly discovered in Synaptic that if I select nvidia-settings, that unsets nvidia-glx and vice-versa. So I installed nvidia-glx in the hopes that Edgy made nvidia-settings obsolete, and then tried the nvidia-glx-config line.

And this is what I got:
Error: your X configuration has been altered.
This script cannot proceed automatically. If you believe that this
not correct, you can update the md5sum entry executing the following
command:
md5sum /etc/X11/xorg.conf | sudo tee /var/lib/x11/xorg.conf.md5sum
otherwise edit manually /etc/X11/xorg.conf to change the Driver section
from nv to nvidia.

...help???

Try:

sudo gedit /etc/X11/xorg.conf

When the file appears in the text editor, find the Driver section and change the "nv" to "nvidia". Save and close the file. If it is still broken, you can try the following:

gksudo gedit /etc/default/linux-restricted-modules-common

Scroll down to the very last line and enter "nv" between the quotes, save and exit. 

If that doesnt work, see mascot below:)  and try pleading to a member of the forum staff or some other highly evolved member of the Ubuntim for expert X help. Dont PM the forum staff or moderators, they will beat you until a vision of Bill Gates appears asking for your credit card number.

---

### Post by igknighted on 2007-04-11
First question, if you are using Edgy, why are you using a k7 kernel?  You want the generic kernel.

Second, the nvidia-setting package isn't that important.  All you need to do is edit the xorg.conf file so that in the section "Device" where it says the driver is "nv", simply change it to "nvidia" and reboot.

Final thought, if you want to use the script, reconfigure your xorg.conf by running "sudo dpkg-reconfigure xserver-xorg".  You will answer a bunch of questions and it will write  a new xorg.conf for you.  And you can even specify to use the nvidia driver as well (as opposed to nv).

---

### Post by wog on 2007-04-26
Under Dapper I was told that if I was experiencing speed or power problems, I should be using the k7 kernal. I assumed that was still true, although now that I'm using Fiesty I'm no longer experiencing those speed problems. I guess they fixed it.

Thank you for the advice about "nv" to "nvidia" in xorg.conf, tho I didn't really have much time to test it before the Fiesty upgrade. They seem to have made installing the nvidia drivers much easier to do now, so as far as I can tell, this whole issue is now solved. :)

---

