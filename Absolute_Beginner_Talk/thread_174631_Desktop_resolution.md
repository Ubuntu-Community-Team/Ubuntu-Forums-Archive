---
title: "Desktop resolution"
date: 2006-05-12
forum: Absolute Beginner Talk
---

### Post by skippy81 on 2006-05-12
Hi, I have tried to increase my resolution to 1280*1024 (tested in windows).

After running the dpkg-reconfigure xserver-xorg I had a collection of new entrys in my /etc/X11/xorg.conf like this:-

> 
SubSection "Display"
		Depth		24
		Modes		"1280x1024" "1280x960" "1280x854" "1280x800" "1280x768" "1200x800" "1152x864" "1152x768" "1024x768" "800x600" "640x480"
	EndSubSection


Problem is it doesnt appear to have done anything, the "screen resolution" app in gnome still won't offer me anything highter than 1024x768.  Can anyone offer some ideas please?

---

### Post by tommcd on 2006-05-12
Sorry if this sounds like a stupid question, but wgen you ran:
dpkg-reconfigure xserver-xorg (need to put sudo in front), did you SELECT the monitor modes you wanted with the spacebar? If not they are not saved.
I made that mistake myself!! After selecting them with the spacebar I got my resolutions back. Hope this helps.

---

### Post by skippy81 on 2006-05-12
Yeah I definately selected the extra ones I wanted.  I compared my xorg.conf file to my backup afterwards, and the program definately added the extra resolutions.

It's as if the gnome utility isnt updating itself.  Is there another way of changing between resolutions?

---

### Post by CybaCowboy on 2006-05-12
Yeah, GNOME's 1024*768 resolution limit annoys the hell outta me...

I can't remember what it is off-the-top-of-my-head, but Windows XP is set to some stupidly high resolution (trust me, it's **high**!), so switching to Linux is like going back in time ten years!

---

### Post by tommcd on 2006-05-12
Hmm, don't know if this will help, but I ran
sudo dpkg-reconfigure xserver-xorg
from recovery mode and when it finished I typed
sudo reboot
and the resolutions were there! I also had to decline any autodetect options, or else xorg was all screwed up! That was my experience, but I now got 1280x1024 resolution.

---

### Post by Kobalt on 2006-05-12
Gnome is absolutely not limited to any resolution. In fact, it really has nothing to do with gnome, it's an Xorg problem only... 
My first question is : do you have an nvidia video card ? If yes, it can be the problem, you'll have to change something in your xorg.conf file, and that should do it. I suggest you make a backup first, 
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```
then, install the nvidai driver with Synpatic, search "nvidia-glx" and find the one corresponding to your video card...
After you installed it, in command line install this : 
```
sudo nvidia-glx-config enable
```
Then, edit your Xorg.conf file : 
```
sudo gedit /etc/X11/xorg.conf
```
Find this section (it's before the resolution section) :
> Section "Device"
    Identifier     "NVIDIA Corporation NV34 [GeForce FX 5200SE]"
    Driver         "nvidia"
EndSection
Change "nvidia" with "nv". 
Save & Close, log out and press Ctrl+Alt+Backspace. 

And then, I hope I helped you out ;)

---

### Post by tommcd on 2006-05-12
I have an nvidia card. When I ran 
sudo dpkg-reconfigure xserver-xorg
from recovery mode I selected nv (it was preselected anyway). I then had 1280x1024 resolution after reboot. After reboot I then had to reinstall nvidia driver.

---

### Post by Kobalt on 2006-05-12
Maybe the first time you forgot to reboot your Xorg (Ctrl+Alt+Backsapce) ? ... Is it working now ?

---

### Post by skippy81 on 2006-05-12
Thanks for the help guys. I'm afraid im still having problems.  I should have mentioned this earlier but my card is an SiS Real 256E integrated card with shared memory.   

I tried using the VGA driver instead of the "SIS" one, but X couldnt boot because VGA doesnt support 24 bit colour depth :(  I also tried using recovery mode and skipping the autodetects as tommcd suggested.

Any suggestion as to other drivers I could try? Im starting to think the SIS driver is the problem.

Thanks

---

### Post by skippy81 on 2006-05-12
I think ive cracked it.  I had to go into my xorg.conf and delete all the possible resolutions except the one I wanted.  I now appear to have forced ubuntu into giving me the res I want :)

---

