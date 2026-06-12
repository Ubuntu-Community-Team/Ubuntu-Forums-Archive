---
title: "How do I know/discern if my gfx card is driven?"
date: 2006-07-08
forum: Absolute Beginner Talk
---

### Post by Susan.Desanco on 2006-07-08
So, a graphics card with drivers is a driven card.

Anyway, I was wondering how to tell whether my Ubuntu OS is talking to my video card, which is a nVidia GeForce 6800.  I am new to GNU/Linux.  I know how to deal with video adapter drivers on Windows products.

I see some grabbing/delaying of the Ubuntu screen and it makes me feel as though I might be dealing with some sort of default VGA service.

Thank you.

---

### Post by catlett on 2006-07-08
To find out whether 3D acceleration is working.Enter this in the terminal.
```
glxinfo | grep rendering
```If it is enable it will return something like this ```
direct rendering: Yes
```If not you are going to have to enable then which is a litle bit of work but first see if you have it enabled.

---

### Post by noynac on 2006-07-08
Type "nvidia-settings" (omit quotes) in a terminal window and an nvidia control panel utility that provides information and settings for your video card should load. If it doesn't, you may need to install the nvidia-glx drivers.

---

### Post by Susan.Desanco on 2006-07-08
Thanks to you both.  I got a return of 'No' for the rendering command, and the nvidia-settings command returned nothing, so I guess I need to start poking around now to learn how to install Linux drivers from nVidia!

---

### Post by woedend on 2006-07-08
install the package
nvidia-glx
from the repos using synaptic or sudo apt-get install nvidia-glx
then you would want to do
gksudo gedit /etc/X11/xorg.conf

at the top, put a # in front of the line Load "dri". then find the section "Device" that will refer to your video card.  change driver to read "nvidia" , save and reboot.
you may want basic understanding of vi just in case it doesnt quite work.
if it doesnt work, remember what was written as driver before you changed it to "nvidia", then you would be in command line to use
sudo vi /etc/X11/xorg.conf
use the arrows to get down to the driver section, push insert key to begin typing, and change the driver section back to what it was.  to save push escape, then colon, then wq
(:wq)
and push enter.


I dont mean to scare you, it should work without a hitch i think...it always has for me.

---

### Post by catlett on 2006-07-08
Here are 3 ways.
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)
[http://doc.gwos.org/index.php/DapperGuide#How_to_install_Graphics_Driver_.28NVIDIA.29](http://doc.gwos.org/index.php/DapperGuide#How_to_install_Graphics_Driver_.28NVIDIA.29)
[http://www.albertomilone.eu/europeo/nvidia_scripts1.html](http://www.albertomilone.eu/europeo/nvidia_scripts1.html)

I used the last link. It is a script that automates the install. The sites creator is a member of the Ubuntu Forum Staff. I posted the other sites in case you didn't like the idea of running a script.

---

### Post by woedend on 2006-07-08
In response to catlett's post, the script does work WONDERFULLY.  The only problem with this is that in the event of a kernel upgrade(and, i'm sure there will be one), your xserver will be left broken.  If you use the first method, upgrading nvidia with the kernel is automated.

---

### Post by catlett on 2006-07-08
Thanks for the warning woodend. I didn't know that. I tried installing with the Dapper Guides commands but it didn't work. I just happened to hit on Tselliot's avatar one day and ended up at his blog and tried envy. I didn't even think to look into it further. Thanks for the heads up.

---

### Post by spikeyone on 2006-07-08
Although I am not the opening poster, I must thank you catlett for providing the instructions to get my drivers working. I used the first method on the first link, and everything worked perfectly! (although I was holding my breath; this is only my third day with Ubuntu and I'm terrified of breaking it) ;)

---

### Post by Apple 101 on 2006-07-08
I was under the impression that you installed *nvidia-glx* and ran the command that is in the Synaptic description.  That's it.  It worked for me.

---

### Post by Susan.Desanco on 2006-07-08
Thanks, everyone.  I followed the seven manual (terminal non-scripted) steps found on the following page, and it worked great.  I now have my familiar NVIDIA settings control panel, thank you.  Display update is much faster and peeeeerrrrrtier, too.

I followed the section entitled "
**METHOD 1**

 **Make sure you have both the Universe and Multiverse repositories enabled."**


and, the link was here:
[http://doc.gwos.org/index.php/Latest_Nvidia_Dapper](http://doc.gwos.org/index.php/Latest_Nvidia_Dapper)

---

